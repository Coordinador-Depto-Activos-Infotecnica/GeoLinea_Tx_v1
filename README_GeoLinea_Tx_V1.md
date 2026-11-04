# GeoLínea Tx — Manual de usuario (V1)

**Desarrollado por: GA – DAIT**

## ¿Qué es GeoLínea Tx?

GeoLínea Tx es una herramienta para **reconstruir y visualizar el trazado de líneas de transmisión** a partir del **Listado de Distribución de Estructuras (LDE)** disponible en BDIT. Opcionalmente, permite **comparar sus estructuras con las torres registradas en BDATx**.

Su propósito es facilitar la revisión geográfica, identificar coincidencias y reducir el trabajo manual.

## ¿Qué permite hacer?

- Buscar una **línea BDIT** por ID o nombre, o seleccionar una o varias **secciones tramo**.
- Revisar los documentos ordenados por fecha de modificación (**del más reciente al más antiguo**), **sin selección automática**.
- Descargar los LDE elegidos; cuando estén comprimidos, seleccionar los archivos útiles dentro de ZIP/RAR.
- Leer los LDE y dibujar sus estructuras y trazado en el **mapa Esri integrado**.
- Comparar, de forma opcional, las estructuras LDE con las torres BDATx de la misma línea, **sin restringir por propietario**.
- Generar un reporte Excel y archivos geográficos para revisar resultados.

> **Recomendación:** utilizar preferentemente LDE en **formato CEN**, con coordenadas y orden de estructuras identificables.

## Cómo utilizar la herramienta

### 1. Buscar y descargar

1. Abre `GeoLinea_Tx_V1.py` (o el ejecutable distribuido por el responsable de la herramienta).
2. En la pestaña **1 · Buscar y descargar**, pulsa **Consultar API Líneas**.
3. Busca la línea por **ID o nombre**, o selecciona las **secciones tramo** que necesitas.
4. Pulsa **Ver documentos**. Los archivos aparecerán ordenados por su fecha de modificación.
5. **Marca manualmente** el o los LDE que deseas utilizar (doble clic en cada documento) y pulsa **Descargar seleccionados**.
6. Si el documento viene en ZIP/RAR, elige los anexos LDE desde la ventana de selección.

**Importante:** el documento más reciente se muestra primero, pero **no se selecciona ni se descarga automáticamente**.

### 2. Dibujar el trazado

1. Pulsa **Leer anexos y dibujar** una vez descargados los documentos.
2. Revisa el trazado, las estructuras y sus ubicaciones en el **mapa Esri integrado**.
3. También puedes utilizar la pestaña **3 · LDE locales** para trabajar con anexos guardados en tu computador.

### 3. Comparar con BDATx (opcional)

1. Ve a **2 · Trazado y BDATx**.
2. Ejecuta la opción de **comparación con BDATx**.
3. La herramienta identifica la línea homóloga mediante `inf_id` y consulta sus **torres**, sin filtrar por propietario.
4. Compara las coordenadas de cada estructura LDE con las torres BDATx, con una **tolerancia de 5 metros**.
5. Revisa las coincidencias, las estructuras sin coincidencia y las torres adicionales BDATx.

**Si BDATx no devuelve torres o la consulta falla, el trazado LDE se conserva.** La ausencia de coincidencia **no implica una propuesta de creación**.

## ¿Qué información entrega el Excel?

El reporte está pensado como un **inventario comparativo sencillo**, no como una solicitud de creación de instalaciones.

| Hoja | Contenido |
| --- | --- |
| `00_GUIA` | Explicación breve de los estados. |
| `01_COMPARACION_TORRES` | Estructuras LDE en orden por sección tramo, coordenadas, propietario BDIT de la sección, ID/nombre y coordenadas de torre BDATx, **propietario BDATx**, distancia y resultado. Incluye torres BDATx adicionales. |
| `02_RESUMEN` | Totales de estructuras, coincidencias y registros para revisar. |

**Estados principales:** **COINCIDE** (coordenadas dentro de 5 m), **NO COINCIDE** (sin torre asociada dentro de la tolerancia), **SOLO BDATX** (torre adicional) y **AMBIGUO** (más de una coincidencia posible; requiere revisión).

## ¿Dónde quedan los archivos?

Los documentos y resultados se guardan, por línea, en una carpeta como:

```text
DOCUMENTOS_BDIT/
└── LT1995/
    ├── ST_4808/
    ├── ST_4809/
    ├── Reporte_LT1995.xlsx
    └── [archivos GeoJSON y otros resultados]
```

La ruta corresponde a la carpeta de trabajo del aplicativo. Los archivos específicos pueden variar según las opciones ejecutadas.

## Consideraciones

- El mapa Esri y las consultas BDIT/BDATx requieren conexión a Internet.
- La herramienta **no crea ni modifica** registros en BDIT o BDATx.
- Las coincidencias se determinan por coordenadas; las asociaciones ambiguas deben revisarse.
- Para uso institucional, el código y los documentos descargados deben gestionarse conforme a las políticas de seguridad de la organización.

---

**GeoLínea Tx V1** · Herramienta de apoyo para la revisión y georreferenciación de líneas de transmisión.
