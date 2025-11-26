# Competencias Emprendedoras

Notas educativas sobre competencias emprendedoras para audiencia paraguaya.

## Autores

- **Autor original:** Prof. Lic. Enriqueta Benítez
- **Notas compiladas por:** Ing. Fernando Cardozo

## Descargar PDF

**Última versión estable:** [Descargar PDF](https://github.com/fcardozo/snpp-emprendedurismo-notes/releases/latest/download/competencias-emprendedoras.pdf)

**Todas las versiones:** [Ver releases](https://github.com/fcardozo/snpp-emprendedurismo-notes/releases)

**Versión en desarrollo:** Los builds del código más reciente están disponibles en la [pestaña Actions](https://github.com/fcardozo/snpp-emprendedurismo-notes/actions/workflows/build-latex.yml) (requiere estar autenticado en GitHub).

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

El documento se compila automáticamente en GitHub Actions:
- **En cada push a `main`:** Se genera un artifact disponible por 30 días
- **Al crear un tag:** Se crea automáticamente un release con el PDF descargable

Para crear una nueva versión, consulta `.github/VERSIONING.md`.

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
