# Bellum Civile: traducción al español latinoamericano

Traducción del `strings.xml` proporcionado por el usuario: 6,963 entradas. Traducción automática local con ajustes terminológicos, revisión de las 228 entradas de configuración y revisión de muestras adicionales; no tiene revisión humana completa ni validación dentro del juego. El usuario utiliza Bannerlord **1.4.x**; faltan el parche exacto y la versión del mod original.

## Descarga e instalación manual

1. Descarga [traduccion_es-419_instalar.zip](https://github.com/oxteabel-ship-it/PROP-O/raw/refs/heads/main/traduccion_es-419_instalar.zip).
2. Con el juego cerrado, extrae su contenido **dentro de la carpeta del mod original**, donde se encuentra su `SubModule.xml`. Conserva una copia de cualquier traducción que ya tengas antes de reemplazarla.
3. Deben quedar estos archivos:

   ```text
   CarpetaDelMod/ModuleData/Languages/SP/language_data.xml
   CarpetaDelMod/ModuleData/Languages/SP/strings_es-419.xml
   ```

4. Mantén activado el mod original y selecciona **Español (LA)** en las opciones del juego. Este paquete no añade un módulo independiente al launcher.

El registro de idioma está dentro de `SP` y utiliza `SP/strings_es-419.xml`, siguiendo el prefijo de carpeta del paquete portugués de Bellum Civile proporcionado por el usuario. Sustituye la referencia anterior de archivos hermanos tomada de Diplomacy. Se mantiene el identificador `Español (LA)` coherente en ambos XML. La carga dentro de la versión concreta del juego sigue pendiente de comprobar.

## Corrección del paquete inicial

Se corrigieron el identificador genérico `Español` a `Español (LA)`, la carpeta a la convención `SP` y el registro de la ruta al formato del ejemplo actual consultado. El contenido de las 6,963 cadenas no cambió con esta corrección.

El ZIP anterior usaba `ES` y el ID `Español`. Si lo instalaste, retira **solo los dos archivos de aquella traducción** de `ModuleData/Languages/ES` antes de instalar este paquete. No elimines otros archivos o carpetas de idioma del mod.

## Comprobaciones

Los XML se pueden analizar; el identificador de idioma coincide; las rutas internas y ambos ZIP fueron verificados. Las 6,963 cadenas conservan sus IDs. La revisión posterior también comprobó variables, etiquetas de animación, valores numéricos, signos y rutas internas; corrigió 289 textos respecto a la edición anterior. Que estos controles pasen no demuestra que Bannerlord cargue la traducción: esa prueba y la revisión lingüística completa siguen pendientes.

La traducción corresponde únicamente al archivo proporcionado. No se ha comprobado si faltan otros archivos de localización del mod.

Para futuras traducciones, consultar [la guía y sus fuentes](GUIA_TRADUCCIONES_BANNERLORD.md).

## Otras traducciones

- [Affairs of Calradia — Español (LA), descarga e instalación](AffairsOfCalradia/README.md).

## Revisión a partir del paquete portugués

[Informe de revisión](REVISION_BELLUM_PT_BR.md). El paquete portugués no incluye `SubModule.xml`, contiene 2,346 entradas y presenta una discrepancia entre el idioma del registro y el de las cadenas. Se utilizó como referencia de empaquetado, sin copiar su contenido ni reducir la cobertura de nuestro archivo inglés. Las correcciones y comprobaciones de nuestra edición están registradas en `validacion_bellum.json`; `bellum_mcm_revisado.json` conserva las 228 entradas de configuración revisadas.
