# Bellum Civile: traducción al español latinoamericano

Traducción del `strings.xml` proporcionado por el usuario: 6,963 entradas. Traducción automática local con ajustes terminológicos y revisión de muestras; no tiene revisión humana completa ni validación dentro del juego. No se ha confirmado la versión exacta del mod ni del juego del usuario.

## Descarga e instalación manual

1. Descarga [traduccion_es-419_instalar.zip](https://github.com/oxteabel-ship-it/PROP-O/raw/refs/heads/main/traduccion_es-419_instalar.zip).
2. Con el juego cerrado, extrae su contenido **dentro de la carpeta del mod original**, donde se encuentra su `SubModule.xml`. Conserva una copia de cualquier traducción que ya tengas antes de reemplazarla.
3. Deben quedar estos archivos:

   ```text
   CarpetaDelMod/ModuleData/Languages/SP/language_data.xml
   CarpetaDelMod/ModuleData/Languages/SP/strings_es-419.xml
   ```

4. Mantén activado el mod original y selecciona **Español (LA)** en las opciones del juego. Este paquete no añade un módulo independiente al launcher.

La estructura sigue el ejemplo actual de Diplomacy: el registro de idioma está dentro de `SP` y enumera `strings_es-419.xml` sin anteponer otra vez la carpeta. Hay ejemplos antiguos con otra convención de rutas; confirmar con la versión concreta del juego si los textos no cargan.

## Corrección del paquete inicial

Se corrigieron el identificador genérico `Español` a `Español (LA)`, la carpeta a la convención `SP` y el registro de la ruta al formato del ejemplo actual consultado. El contenido de las 6,963 cadenas no cambió con esta corrección.

El ZIP anterior usaba `ES` y el ID `Español`. Si lo instalaste, retira **solo los dos archivos de aquella traducción** de `ModuleData/Languages/ES` antes de instalar este paquete. No elimines otros archivos o carpetas de idioma del mod.

## Comprobaciones

Los XML se pueden analizar; el identificador de idioma coincide; las rutas internas y ambos ZIP fueron verificados. Las 6,963 cadenas conservaron sus IDs y textos durante la corrección de metadatos. Que estos controles pasen no demuestra que Bannerlord cargue la traducción: esa prueba y la revisión lingüística completa siguen pendientes.

La traducción corresponde únicamente al archivo proporcionado. No se ha comprobado si faltan otros archivos de localización del mod.

Para futuras traducciones, consultar [la guía y sus fuentes](GUIA_TRADUCCIONES_BANNERLORD.md).
