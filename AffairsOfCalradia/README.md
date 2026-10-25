# Affairs of Calradia — Español (LA)

**[Descargar ZIP para instalar](https://github.com/oxteabel-ship-it/PROP-O/raw/refs/heads/main/AffairsOfCalradia/affairs_of_calradia_es-419.zip)**

Con Bannerlord cerrado, extrae el ZIP **dentro de la carpeta de Affairs of Calradia que contiene su `SubModule.xml`**, dentro de `Modules`. Acepta combinar carpetas. Selecciona **Español (LA)** en el juego y reinícialo. No se añade un mod independiente al launcher.

```text
CarpetaDelMod/
└── ModuleData/
    └── Languages/
        └── SP/
            ├── language_data.xml
            └── std_FriendsWithBenefits_strings.xml
```

Se conserva el nombre interno `FriendsWithBenefits` del archivo original. Los archivos ingleses que están directamente en `Languages` no se reemplazan. Si ya tienes una traducción en `SP`, conserva una copia antes de reemplazar archivos; si su registro incluye otros XML, conserva sus entradas adicionales.

## Contenido y validación

- 4,626 entradas del XML proporcionado por el usuario, con IDs, variables y formato conservados.
- 16 valores técnicos de sonido e iconos conservados exactamente.
- Revisión manual de los nombres de las 219 opciones de configuración y de una selección de diálogos y descripciones. El resto se obtuvo mediante traducción automática local con ajustes terminológicos; no hay revisión humana completa.
- XML, registro de idioma, referencias internas e integridad del ZIP comprobados.
- Estructura de idioma preparada para la familia Bannerlord 1.4.x indicada por el usuario, siguiendo las referencias de la [guía del repositorio](../GUIA_TRADUCCIONES_BANNERLORD.md).

No se ha ejecutado Bannerlord ni se conoce la versión exacta de Affairs of Calradia de la que proceden estos archivos. No se ha comprobado si hay textos adicionales en otros archivos del mod. El registro traducido no fuerza el procesador de texto inglés que figuraba en el registro original.

`validacion.json` registra los controles y las huellas SHA-256 de los dos archivos de origen. `opciones_revisadas.json` guarda las traducciones revisadas de opciones y algunas descripciones para facilitar futuras actualizaciones.

Para desinstalar, retira únicamente los archivos añadidos por este paquete en `Languages/SP` y restaura cualquier copia de seguridad de archivos que hubieras sustituido.
