# performance-standards

Fuente única de la tabla del **Estándar de Performance** que usa el framework
config-driven. Antes vivía dentro del Jenkinsfile (`derivarParametros()`).

## Archivos
- `estandar-v2.0.yml` — perfiles (tipo, complejidad, operación, BD → TPS, duración, P95, VUs) y límites de recursos.

## Política de versiones
- Los builds leen una versión concreta con el parámetro `STANDARD_VERSION` (por defecto `v2.0`).
- **Nunca se edita un tag ya publicado.** Un cambio de valores crea un tag nuevo (`v2.0.1`, `v2.1`, `v3.0`).
- Para cambiar un valor: edita el YAML, haz commit, crea el tag y actualiza el default del pipeline cuando quieras adoptarlo.

```bash
git add estandar-v2.0.yml
git commit -m "estandar: ajustar TPS de MICRO-MEDIA-MIXTA-SQL"
git tag v2.0.1
git push origin main --tags
```

## Nota sobre duraciones
Los valores de `duracion` son los de la plantilla oficial (10m, 15m, 20m).
Para pruebas cortas de laboratorio usa el parámetro `DURATION_OVERRIDE` del pipeline;
no cambies el estándar.
