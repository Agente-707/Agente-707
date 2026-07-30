## Configuracion de Starship dentro de VS Code (Windows)

Esta es una guía para personalizar la terminal de VS Code con Starship junto con iconos de Nerd Font y temas de colores tipo píldoras.

## 1. Instalar una Nerd Font

Todos estos iconos requieren de una fuente con glifos especiales.

1. Descargar una fuente de su preferencia desde https://www.nerdfonts.com/font-downloads
2. Descomprimir el archivo ZIP
3. Instalar los archivos `.ttf`, solo las variantes que digan **"Mono"** (Regular, Bold, Medium/Retina, SemiBold)

## 2. Configurar la fuente en VS Code

1. Entrar a VS Code, abrir Configuración (Ctrl + ,) y buscar: `terminal font family`
2. Dentro de **Terminal > Integrated: Font Family** ejecutar:
```
FiraCode Nerd Font Mono
```

## 3. Instalar Starship

En una terminal de windows (PowerShell) ejecutar:
```
winget install --id Starship.Starship
```

**NOTA:** Después haber instalado Starship con éxito dentro de la terminal, debemos reiniciar la PC para que el PATH se actualice correctamente y, tanto Windows como VS Code puedan reconocer el comando `starship`.

## 4. Verificar la instalación

Ejecutar el siguiente comando dentro de la terminal de VS Code o en la terminal de Windows (PowerShell) para verificar que Starship opere correctamente:

```
starship --version
```

## 5. Activar Starship en el perfil de PowerShell

1. Verificar si existe el perfil:
```
Test-Path $PROFILE
```
2. Si nos da **False** es porque no existe y debemos crearlo:
```
New-Item -Path $PROFILE -Type File -Force
```
3. Abrir el perfil para editarlo
```
notepad $PROFILE
```
4. El comando anterior nos abrirá un bloc de notas (vacío), dentro de este escribir:
```
Invoke-Expression (&starship init powershell)
```

5. Guardar el archivo.

Si nos salta un error de "ejecución de scripts deshabilitada", ejecutar una sola vez:
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

6. Cerrar y abrir una nueva terminal en VS Code para ver los cambios

## 6. Aplicar un preset de colores (estilo de píldoras)

1. Crear la carpeta de configuracion en caso no exista:
```
New-Item -ItemType Directory -Force -Path "$HOME\.config"
```
2. Aplicar un preset de tu preferencia (ejem: Pastel Powerline):
```
starship preset pastel-powerline -o "$HOME\.config\starship.toml"
```

**NOTA:** Si quieres cambiar a otro preset despues de haber probado con uno, tienes que ejecutar el mismo comando agregando al final ` --force`

**Ejemplo:**
```
starship preset tokyo-night -o "$HOME\.config\starship.toml" --force
```

## Lista de presets disponibles
- `nerd-font-symbols`
- `no-nerd-font`
- `bracketed-segments`
- `plain-text-symbols`
- `hide-runtime-versions`
- `pure-preset`
- `pastel-powerline`
- `tokyo-night`
- `gruvbox-rainbow`
- `catppuccin-powerline`
- `jetpack`

Mas detalles en: https://starship.rs/presets/




