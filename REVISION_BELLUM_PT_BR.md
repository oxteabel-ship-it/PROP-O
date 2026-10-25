# Revisión de Bellum Civile a partir del paquete portugués

## Qué se inspeccionó

El ZIP que proporcionó el usuario contiene únicamente:

```text
Bellum Civile PT-BR/
└── BellumCivile/
    └── ModuleData/
        └── Languages/
            └── BR/
                ├── language_data.xml
                └── strings_BR.xml
```

No contiene `SubModule.xml`, DLLs ni manifiesto de módulo independiente. Su carpeta `BellumCivile` está pensada para fusionarse con la del mod original dentro de `Modules`; la carpeta exterior del archivo no crea una nueva entrada en el launcher. No se ejecutó ni instaló el ZIP portugués.

## Comparación de cobertura

| Comprobación | Resultado |
|---|---:|
| Entradas portuguesas | 2,346 |
| Entradas del inglés proporcionado y de nuestra edición española | 6,963 |
| IDs compartidos | 2,124 |
| IDs presentes solo en nuestro archivo | 4,839 |
| IDs presentes solo en el portugués | 222 |

Las coberturas son diferentes; no se ha determinado la versión exacta del mod de la que procede cada archivo. No se incorporaron los 222 IDs exclusivos del portugués sin confirmar su correspondencia con la versión objetivo. Tampoco se reemplazó nuestro archivo por aquel de menor cobertura.

El registro portugués declara `Português (BR)`, pero `strings_BR.xml` declara `<tag language="English" />`. Es una inconsistencia de metadatos que no se ha replicado; estos archivos por sí solos no demuestran que el juego cargue correctamente el portugués.

## Cambios en nuestra edición

- Revisadas las 228 entradas de configuración, incluidos sus nombres, descripciones y mensajes.
- Corregidos términos como corte, voluntad bélica, reinos dependientes, convocatorias militares y sucesión.
- Corregidas las tres líneas detectadas en las que faltaban signos `+` o `-` respecto al inglés; se comprobaron los valores numéricos del archivo completo.
- Restauradas las ocho etiquetas de animación `[if:...]` y `[ib:...]` que aparecen en siete cadenas del inglés. Varias se habían alterado o perdido durante la traducción automática.
- Corregidas las 39 cadenas detectadas con caracteres `⁇` de traducción desconocida, incluidos multiplicadores `×`, letras acentuadas, separadores y la ruta `bellum_title_styles_*.xml`.
- Unificada la moneda como denares en las cadenas cuyo original menciona denars.
- El registro español utiliza `SP/strings_es-419.xml`, siguiendo la convención de carpeta del paquete específico de Bellum Civile. El ID de idioma sigue siendo `Español (LA)` tanto en el registro como en el archivo de cadenas.
- Se reconstruyeron ambos ZIP. El paquete instalable mantiene la extracción dentro de la carpeta del mod original, donde se encuentra su `SubModule.xml`.

En total cambiaron 289 cadenas de nuestra edición anterior. No se modificó el mod original, su código ni el paquete portugués.

## Validaciones ejecutadas

XML analizable; 6,963 IDs únicos conservados en su orden original; coincidencia de variables y etiquetas; etiquetas de animación exactas y en el orden original; valores numéricos y signos conservados; rutas XML internas conservadas; ausencia de `⁇` y `�`; coherencia del idioma; referencias presentes dentro del ZIP y archivos ZIP íntegros. El resultado está en `validacion_bellum.json`.

La coincidencia numérica literal es un control deliberado de esta edición: se conservaron los separadores del inglés en las constantes, en lugar de inferir equivalencias entre formatos regionales.

No se ha ejecutado Bannerlord. La prueba de carga y la revisión lingüística completa de las 6,963 entradas siguen pendientes. Las fuentes inglesas continúan siendo la referencia para el contenido; el ZIP portugués aportó un ejemplo de distribución y una comparación adicional.
