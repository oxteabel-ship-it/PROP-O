# Traducciones de Mount & Blade II: Bannerlord

Guía de trabajo para traducciones al español latinoamericano. Consultada el 24 de octubre de 2026. Se basa en documentación comunitaria, archivos públicos de Diplomacy y ejemplos de Nexus Mods; no sustituye una prueba dentro de la versión concreta del juego.

## 1. Identificar el contenido y las versiones

Registrar la versión de Bannerlord y del mod original. En este proyecto el usuario confirmó **Bannerlord 1.4.x**; aún no indicó el parche exacto ni la versión del mod. Examinar sus archivos de `ModuleData/Languages`, el idioma inglés de referencia, `SubModule.xml` y otras cadenas localizables incluidas en XML o en código. Un solo `strings.xml` no demuestra que se haya localizado todo el mod.

Las cadenas del código necesitan un identificador, normalmente mediante `TextObject` y un prefijo como `{=ID}`. Un XML de traducción no corrige por sí solo textos incrustados en una DLL sin soporte de localización. Eso requiere trabajo separado sobre el código del mod.

## 2. Usar el identificador del idioma que ya carga el juego

Los nombres de idioma son identificadores exactos. Para el español latinoamericano, los archivos actuales consultados de Diplomacy y Bannerlord Localization Helper utilizan **`Español (LA)`**. Un registro de cambios de DuelCompanions en Nexus también documenta que tuvo que corregir `Español` a `Español (LA)` para que la traducción se cargara.

En nuestro paquete deben coincidir:

```xml
<LanguageData id="Español (LA)" name="Español (LA)" ...>
```

```xml
<tags>
  <tag language="Español (LA)" />
</tags>
```

No crear una variante con otro ID solo para cambiar el nombre visible: el resto de los módulos podría no tener traducciones para ese nuevo ID y volver al texto original. Verificar siempre el `language_data.xml` de `Modules/Native/ModuleData/Languages/SP` de la instalación concreta.

## 3. Estructura y registro de archivos

El paquete de este repositorio es una traducción que se copia **dentro del mod original**:

```text
CarpetaDelMod/
└── ModuleData/
    └── Languages/
        └── SP/
            ├── language_data.xml
            └── strings_es-419.xml
```

`SP` es la convención observada para español; el nombre del archivo no define el idioma. Cada XML de traducción debe estar registrado en `language_data.xml`.

Los archivos actuales de Diplomacy consultados, con `language_data.xml` dentro de `SP`, registran los nombres de archivo sin volver a anteponer `SP/`. El paquete sigue ese ejemplo:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LanguageData id="Español (LA)" name="Español (LA)"
              subtitle_extension="es-SP"
              supported_iso="es-ar,spa,es-es,es-ve,es-uy,es-bo,es-cl,es-co,es-cr,es-do,es-ec,es-sv,es-gt,es-hn,es-mx,es-ni,es-pa,es-py,es-pe,es-pr"
              under_development="false">
  <LanguageFile xml_path="strings_es-419.xml" />
</LanguageData>
```

**Diferencias entre ejemplos y versiones:** guías y herramientas anteriores también generan rutas como `SP/archivo.xml`. No tratar ambas convenciones como intercambiables sin comprobar el cargador de la versión objetivo. La comprobación local de rutas del ZIP demuestra su coherencia, no que el juego haya cargado los textos. Si la versión objetivo requiere otra convención, adaptar el registro a esa versión y verificarlo jugando.

Este paquete no es un módulo independiente y no necesita su propio `SubModule.xml` ni una casilla adicional en el launcher. No se debe desactivar el mod original.

Un parche independiente sí necesita su estructura de módulo, `SubModule.xml`, identificación y dependencias adecuadas; debe cargarse después del mod cuyos textos sustituye. No inventar el ID del módulo original: leerlo de su `SubModule.xml`.

## 4. Traducir sin romper el formato

Conservar todos los atributos `id` de las cadenas. Mantener los nombres y el número de variables, como `{HERO.NAME}`, `{CLAN_NAME}` o `{DAYS}`. Las variables se pueden recolocar para expresar una oración natural, conservando la lógica del texto.

Preservar los controles y el anidamiento de los condicionales, por ejemplo:

```text
{?NUMBER_OF_DAYS.PLURAL_FORM}días{?}día{\?}
```

No traducir `{newline}`, etiquetas de formato, nombres de atributos ni rutas internas. Proteger también las etiquetas de animación de diálogos como `[if:convo_happy]` y `[ib:hip]`, conservando su contenido y orden. Conservar las secuencias de escape. Dentro de atributos XML, escapar correctamente `&`, `<`, `>` y las comillas. Los saltos de línea reales dentro de atributos se guardan como `&#10;` y las tabulaciones como `&#9;`, para evitar que el analizador los normalice a espacios.

Proteger un token no garantiza una buena traducción: revisar el género y los artículos alrededor de nombres dinámicos, singular/plural y las alternativas condicionales.

## 5. Glosario y revisión contextual

| Inglés | Traducción base | Contexto |
|---|---|---|
| fief | feudo | Posesión feudal |
| realm / kingdom | reino | Revisar cuando el rango sea imperio o ducado |
| clan / noble house | clan / casa noble | Seguir el significado del sistema |
| court | corte | Corte nobiliaria; no «tribunal» automáticamente |
| party | grupo | Grupo de tropas; no «fiesta» ni «partido» |
| companion | compañero | Personaje del grupo |
| claim | reclamación / derecho reclamado | Mantener coherencia en títulos y herencias |
| feud | disputa | No confundir con `fief` |
| regency / regent | regencia / regente | Sucesión y minoría de edad |
| holding | posesión | Revisar si se usa como verbo |
| mercenary company | compañía mercenaria | No «empresa» |
| default value | valor predeterminado | No «falta» ni impago |
| war score | puntuación de guerra | Métrica del conflicto |
| war exhaustion | agotamiento de guerra | Métrica distinta de la anterior |

Usar español latinoamericano natural y terminología coherente con el juego. Preservar nombres propios y títulos culturales cuando corresponda. Revisar frases completas y la intención de cada opción; los reemplazos automáticos de palabras no sustituyen esa revisión.

La traducción actual se produjo mediante traducción automática local, con correcciones terminológicas y revisión de muestras. **No tiene una revisión humana completa.** No presentarla como equivalente a una traducción editorial revisada solo porque el XML sea válido.

## 6. Actualizar sin perder trabajo

Comparar por ID el inglés anterior, el inglés nuevo y la traducción:

- ID nuevo: traducir.
- ID existente con inglés cambiado: marcar para revisar, aunque se pueda reutilizar parte de la traducción.
- ID eliminado: retirar de la edición actual o conservar solo en el historial.
- Variable, condición o formato modificado: revisar la traducción completa.

Guardar el origen y la versión del archivo que se tradujo. Evitar mezclar cadenas de versiones incompatibles del mod.

## 7. Validación antes de distribuir

### Comprobaciones que se pueden ejecutar aquí

- XML analizable y codificación UTF-8.
- IDs y contenido completo comparados con el origen proporcionado.
- Conservación de variables, controles, formato y saltos de línea, incluidas las etiquetas de animación entre corchetes.
- Ausencia de caracteres de traducción desconocida `⁇` o de sustitución `�`; comprobar también símbolos como `×` y `~`.
- Conservación de valores numéricos y signos de bonificaciones y penalizaciones. Una traducción puede conservar todas sus variables y aun así invertir el sentido de una regla al perder un signo.
- Coincidencia de ID de idioma entre el registro y las cadenas.
- Existencia de todos los archivos registrados, según la convención elegida.
- ZIP íntegro, sin carpetas duplicadas y con instrucciones inequívocas.

### Comprobaciones que necesitan el juego

Seleccionar `Español (LA)` y comprobar textos inequívocos del mod: menús, opciones de MCM si existen, diálogos, notificaciones y enciclopedia. Probar nombres de personajes, género, singular/plural y explicaciones largas. Revisar texto cortado, caracteres incorrectos y mensajes de error de carga.

Si sigue apareciendo inglés, comprobar primero la instalación, la versión, el idioma seleccionado, el registro de archivos y posibles traducciones que sobrescriban los mismos IDs. Una ventana que abre sin error no demuestra que la traducción se haya cargado.

Aquí no se ha ejecutado Bannerlord. Para la familia 1.4.x indicada por el usuario, se contrastaron el ID `Español (LA)`, `es-SP` y el registro de archivos hermanos con el archivo español de Diplomacy v1.5.5. Esa publicación declara soporte para Bannerlord 1.4.0–1.4.8. Los tres criterios coinciden con nuestro paquete. La comprobación dentro del juego y la compatibilidad con la versión concreta del mod original siguen pendientes.

## 8. Preparar una publicación como las de Nexus Mods

Indicar el mod requerido y su versión, la versión del juego, el idioma seleccionado, las instrucciones de instalación y desinstalación, el contenido cubierto y el estado de revisión. Distinguir entre copiar archivos al mod original e instalar un módulo independiente. El soporte de Vortex requiere comprobar el empaquetado para ese gestor; un ZIP con `ModuleData` pensado para extracción manual dentro del mod no demuestra soporte automático de Vortex.

Enlazar al mod original, acreditar su autoría y comprobar sus condiciones antes de publicar archivos de terceros. No incluir DLLs u otros recursos del mod original para distribuir una traducción de textos. Mantener un historial de cambios y describir los problemas conocidos.

## Fuentes consultadas

- [Diplomacy v1.5.5: publicación con soporte declarado para Bannerlord 1.4.0–1.4.8](https://github.com/DiplomacyTeam/Bannerlord.Diplomacy/releases/tag/v1.5.5) y [su registro de idioma español](https://github.com/DiplomacyTeam/Bannerlord.Diplomacy/blob/v1.5.5/src/Bannerlord.Diplomacy/_Module/ModuleData/Languages/SP/language_data.xml): referencia comprobada al recibir la versión del usuario.

- [Documentación comunitaria: Localization](https://docs.bannerlordmodding.com/_csharp-api/localization/): TextObject, IDs globales, variables y condicionales; advierte que IDs de idioma distintos no se fusionan automáticamente. Incluye información de versiones antiguas.
- [BannerlordModding.LT: Localization](https://docs.bannerlordmodding.lt/modding/localization/): estructura de carpetas, registro y entidades XML; muestra una convención anterior de rutas.
- [Diplomacy: registro español actual](https://github.com/DiplomacyTeam/Bannerlord.Diplomacy/blob/dev/src/Bannerlord.Diplomacy/_Module/ModuleData/Languages/SP/language_data.xml): `Español (LA)`, `es-SP` y nombres de archivo sin prefijo `SP/`.
- [Diplomacy: cadenas en español](https://github.com/DiplomacyTeam/Bannerlord.Diplomacy/blob/dev/src/Bannerlord.Diplomacy/_Module/ModuleData/Languages/SP/help_strings_xml.xml): etiquetas de idioma y saltos `&#10;`.
- [Diplomacy en Nexus Mods](https://www.nexusmods.com/mountandblade2bannerlord/mods/832): distribución de un mod con traducciones y versiones/dependencias concretas.
- [DuelCompanions en Nexus Mods](https://www.nexusmods.com/mountandblade2bannerlord/mods/11020): registro de cambios v1.0.1 que corrige `Español` a `Español (LA)`.
- [AutoTraslation en Nexus Mods](https://www.nexusmods.com/mountandblade2bannerlord/mods/13178): ejemplo de entrega como módulo de idioma independiente y orden de carga posterior.
- [XML Translator en Nexus Mods](https://www.nexusmods.com/mountandblade2bannerlord/mods/5131): protección de variables durante traducción automática; no demuestra revisión lingüística.
- [Bannerlord Localization Helper](https://github.com/gengark/bannerlord-helper): herramientas de extracción y generación, con convenciones que deben contrastarse con la versión objetivo; su README indica soporte solo para Windows.
- [Esquema comunitario ModuleLanguageData.xsd](https://github.com/BUTR/Bannerlord.XmlSchemas/blob/master/ModuleLanguageData.xsd): estructura y atributos del registro.

No se descargaron ni ejecutaron mods desde Nexus. Las fuentes sirven para comprobar convenciones y ejemplos; no equivalen a una prueba en una instalación real del juego.

## Evidencia posterior del propio mod

El paquete portugués de Bellum Civile aportado por el usuario utiliza `BR/strings_BR.xml` en su registro. Nuestra edición española sigue ahora el patrón `SP/strings_es-419.xml`. El paquete no contiene `SubModule.xml` y su cobertura difiere de la del inglés proporcionado. Ver el [informe de revisión](REVISION_BELLUM_PT_BR.md). El archivo de una traducción de terceros debe inspeccionarse antes de utilizarlo como referencia: en este caso su registro portugués y su etiqueta de idioma English no coincidían.
