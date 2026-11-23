# claude-marketplace

Marketplace propio de plugins de Claude Code. Sirve para fijar cada plugin a un commit exacto, de modo que la CI no descargue la última versión sin que nadie la haya revisado.

Lo usa el workflow de revisión de Claude del kit «método de trabajo con Claude» (`.github/workflows/claude-revision.yml` de cada repo).

## Plugins

| Plugin | Origen | Commit fijado | Versión |
|---|---|---|---|
| `code-review` | `anthropics/claude-plugins-official`, `plugins/code-review` (licencia Apache 2.0) | `73c8cf3ea7e296057b467990f2f5d61b4c922260` | 1.0.1 |

## Actualizar un plugin

1. Último commit del origen: `git ls-remote https://github.com/anthropics/claude-plugins-official HEAD`
2. Revisa qué ha cambiado en el plugin entre el commit fijado y el nuevo:
   `https://github.com/anthropics/claude-plugins-official/compare/<commit-fijado>...<commit-nuevo>` (mira solo `plugins/code-review/`).
3. Si estás de acuerdo, cambia `sha` en `.claude-plugin/marketplace.json` y la tabla de arriba, haz commit y push. La siguiente ejecución de la CI ya usa el commit nuevo.
