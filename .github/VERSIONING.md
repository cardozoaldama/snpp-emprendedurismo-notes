# Versionado del Proyecto

Este documento explica cómo funciona el versionado y las publicaciones (releases) del proyecto "Competencias Emprendedoras SNPP".

## Convención de Versionado

Utilizamos **Semantic Versioning (SemVer)** en el formato `vMAYOR.MENOR.PARCHE` (ej: `v1.2.3`).

### Cuándo incrementar cada número:

- **MAYOR** (v**X**.0.0): Cambios grandes, reorganización de contenido, cambios que rompen compatibilidad
  - Ejemplo: Reestructuración completa de los módulos, cambio de formato del documento

- **MENOR** (v0.**X**.0): Nuevas secciones, nuevos capítulos, adiciones significativas al contenido
  - Ejemplo: Agregar nuevo módulo sobre legalización, agregar nuevas lecciones

- **PARCHE** (v0.0.**X**): Correcciones de contenido, mejoras tipográficas, arreglos de formato
  - Ejemplo: Corregir errores de ortografía, mejorar explicaciones existentes, actualizar gráficos

## Creando una Publicación (Release)

### Método 1: Usar el Asistente Automatizado (Recomendado)

1. Ve a **Actions** en GitHub
2. Selecciona **"Prepare Release"**
3. Haz clic en **"Run workflow"**
4. Completa el formulario:
   - **Tipo de versión**: Elige `major`, `minor` o `patch`
   - **Versión personalizada** (opcional): Déjalo vacío para que se calcule automáticamente
   - **Pre-release**: Marca solo si es un borrador/versión preliminar

El sistema calculará automáticamente el siguiente número de versión.

### Método 2: Crear Etiqueta Manualmente

```bash
# Crear una etiqueta anotada
git tag -a v1.2.3 -m "Release v1.2.3"

# Enviar la etiqueta a GitHub
git push origin v1.2.3
```

Reemplaza `v1.2.3` con tu nueva versión.

## Marcado de Pre-releases (Borradores)

Para versiones preliminares o en prueba, agrega el sufijo `-draft`:

- `v1.0.0-draft`: Primera versión de un nuevo módulo importante
- `v0.3.0-rc`: Release candidate (candidato a publicación)

**Ejemplo usando el asistente:**
1. Elige tipo de versión: `minor`
2. Marca la opción "Pre-release"
3. Se creará: `v0.3.0-draft`

**Ejemplo manual:**
```bash
git tag -a v0.3.0-draft -m "Pre-release v0.3.0 (draft)"
git push origin v0.3.0-draft
```

## Flujo Automático

Una vez creada la etiqueta, GitHub Actions automáticamente:

1. **Descarga** el código en esa versión
2. **Inserta** el número de versión en el pie de página del PDF
3. **Compila** el documento con LuaLaTeX
4. **Genera** dos PDFs:
   - `competencias-emprendedoras-v0.2.1.pdf` (con número de versión)
   - `competencias-emprendedoras.pdf` (enlace estable para descargar siempre la última)
5. **Crea** una publicación en GitHub con:
   - El PDF descargable
   - Resumen automático de cambios
   - Indicación de si es pre-release o release estable

## Historial de Versiones

### v0.2.1
- Cambio de color del índice a negro
- Mejoras tipográficas generales
- Adición de callout de advertencia

### v0.2.0
- Contenido de formalización de negocios para Paraguay
- Actualización de licencia a CC BY-NC-SA
- Mejora de README

### v0.1.0
- Versión inicial del proyecto
- Módulos base de emprendimiento

## Notas Importantes

- Las versiones siguen siendo visibles en el pie de página del PDF
- El `commitsha` también se registra para rastreabilidad completa
- Los PRs en desarrollo no generan releases, solo se hacen al crear etiquetas en `main`
- Las pre-releases se marcan automáticamente si contienen `-draft`, `-rc`, etc.

## Preguntas Frecuentes

**P: ¿Qué pasa si me equivoco en el número de versión?**
R: Puedes eliminar la etiqueta con `git tag -d v0.2.1 && git push origin :v0.2.1` y crear una nueva.

**P: ¿Puedo hacer releases desde una rama que no es main?**
R: No. Las etiquetas solo crean releases si están en `main`. Para probar, usa una rama separada.

**P: ¿Cómo veo el historial de versiones?**
R: Ve a https://github.com/fcardozo/snpp-emprendedurismo-notes/releases

**P: ¿Qué sucede si el compile LaTeX falla?**
R: Se cancelará el flujo y NO se creará la publicación. Revisa los logs en Actions para ver el error.
