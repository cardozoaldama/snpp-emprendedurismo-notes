# Competencias Emprendedoras

Notas educativas sobre competencias emprendedoras para audiencia paraguaya.

## Autores

- **Autor original:** Prof. Lic. Enriqueta Benítez
- **Notas compiladas por:** Ing. Fernando Cardozo

## Compilar el documento

### Compilación local

Requiere LuaLaTeX instalado:

```bash
cd latex
lualatex main.tex
lualatex main.tex  # Segunda pasada para referencias
```

El PDF se generará como `latex/main.pdf`.

### Compilación automática (CI/CD)

El documento se compila automáticamente en GitHub Actions cada vez que se hace push a `main`. El PDF compilado está disponible como artifact en la pestaña Actions.

Para descargar el PDF más reciente:
1. Ve a la pestaña "Actions"
2. Selecciona el workflow "Build LaTeX Document" más reciente
3. Descarga el artifact "competencias-emprendedoras"

## Estructura del proyecto

```
latex/
├── main.tex              # Documento principal
├── preamble.tex          # Configuración de paquetes
├── commands.tex          # Comandos personalizados
└── content/              # Contenido por temas
    ├── 01-propuesta-valor-branding.tex
    ├── 02-marketing-comercializacion.tex
    ├── 03-finanzas-personales.tex
    ├── 04-costos-precios.tex
    └── 05-formalizacion-paraguay.tex
```
