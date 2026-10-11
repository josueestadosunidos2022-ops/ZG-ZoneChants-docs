# ZG ZoneChants 1.4.0 — configuration / configuración

Source-checked for the protected 1.4.0 release. Paths are relative to the Forge server `config/` directory. The server creates the TOML files on first start. Back up custom settings before changing them; `/za reload` or `/zonecore reload` reloads all three. A malformed file keeps its previous valid in-memory settings, and the command reports an error. Restart when installing or replacing a JAR.

Comprobado contra las fuentes de la versión protegida 1.4.0. Las rutas parten de `config/` del servidor Forge. El servidor crea los TOML en el primer arranque. Respalda los ajustes; `/za reload` o `/zonecore reload` recarga los tres. Si un archivo falla la validación, conserva la última configuración válida en memoria e informa el error. Para cambiar el JAR, reinicia.

## `ZONEMODS/zonechants/ajustes.toml`

| TOML key | Default | Effect / Efecto |
|---|---:|---|
| `niveles.maximo_predeterminado` | `25` | Default per-enchantment maximum, 1–25 / máximo general, 1–25. |
| `encantamientos.<modid:id>` | generated | Override for each registered enchantment, 1–25 / límite por ID registrado. New IDs are added on reload / los ID nuevos se añaden al recargar. |
| `flying.velocidad` | `0.025` | Flying base speed, `0.005 <= value < 0.05`; it does not scale with level / velocidad base sin escalar por nivel. |
| `fuego.activo` | `true` | Enable armor fire effect / activar efecto de armadura. |
| `fuego.intervalo_ticks` | `10` | Tick interval, 5–200 / intervalo de 5 a 200 ticks. |
| `fuego.particulas` | `2` | Particle count, 1–6 / cantidad de partículas. |
| `fuego.radio_bloques` | `24` | Effect radius, 1–48 blocks / radio en bloques. |
| `atributos.maximo_suma` | `1024.0` | Maximum absolute additive attribute value / máximo absoluto de suma. |
| `atributos.maximo_multiplicador` | `10.0` | Maximum absolute multiplier; minimum is -1 / máximo absoluto de multiplicador; mínimo -1. |
| `presentacion.titulo` | colored title | Template applied manually, not on reload / plantilla manual, no renombra al recargar. Empty keeps existing name / vacío conserva el nombre. |
| `presentacion.descripcion` | two lines | List of text lines; empty removes ZONECHANTS lines / lista de líneas; vacía quita las líneas de ZONECHANTS. |
| `presentacion.mostrar_estadisticas` | `true` | Show native item attributes when applying presentation / mostrar atributos nativos al aplicar. `false` preserves existing visibility / conserva la visibilidad actual. |

Color formats / formatos de color: `&#RRGGBB`, `&x&R&R&G&G&B&B`, `<#RRGGBB>`, `&a`, `&l`, `&r`.

## `zoneenchantlimit-server.toml`

| TOML key | Default | Effect / Efecto |
|---|---:|---|
| `general.enabled` | `true` | Enables global level rules / activa límites globales. |
| `general.apply_to_existing_items` | `true` | Applies rules to existing items / aplica límites a objetos existentes. |
| `general.log_changes` | `true` | Logs changes / registra cambios. |
| `[[enchantments]]` | two Tombstone rules | One `id = "modid:name"` and integer `max_level` (1–32767) per rule / un ID y nivel por regla. Duplicate IDs are rejected / los ID duplicados se rechazan. |

The default rules cap `tombstone:incurable` and `tombstone:decrepitude` at level 2. Unknown mod IDs remain configured and produce a warning; they become usable only when that enchantment's mod is installed. A global cap can further reduce a level granted by `/za enchant` or a design.

Por defecto, `tombstone:incurable` y `tombstone:decrepitude` tienen nivel máximo 2. Un ID de otro mod no instalado conserva su regla, pero produce una advertencia; necesita el mod correspondiente para funcionar. El límite global también puede reducir el nivel aplicado por `/za enchant` o un diseño.

## `ZONEMODS/zonechants/disenos.toml`

`[general]` has `enabled = true`, `tag_label = "&8TAG: &7"`, and `rarity_label = "&8RAREZA: &r"`. Up to 64 `[[designs]]` blocks are accepted. Each design needs `id` (1–32 lowercase letters, digits or underscores), `title`, `description` (list of strings), `rarity`, `tag`, and `allowed_items` (list of `modid:item` IDs; empty permits any item). Optional nested `[[designs.enchantments]]` blocks use `id` and `level` (1–25); `[[designs.attributes]]` blocks use `id`, `amount`, `operation` (`sumar`, `multiplicar_base`, `multiplicar_total`), and `slot` (`mano_principal`, `mano_secundaria`, `cabeza`, `pecho`, `piernas`, `pies`). The generated file has four example designs. A design checks the live item, enchantment, attribute, and limits before changing the held item. External models and textures need a client resource pack.

`[general]` contiene `enabled = true`, `tag_label` y `rarity_label`. Se aceptan hasta 64 bloques `[[designs]]`. Cada diseño define `id` (1–32 caracteres `a-z`, `0-9` o `_`), `title`, `description` (lista), `rarity`, `tag` y `allowed_items` (ID `modid:item`; lista vacía = cualquier objeto). Los bloques opcionales de encantamientos usan `id` y `level` (1–25). Los atributos usan `id`, `amount`, `operation` y `slot` con los valores indicados arriba. El archivo generado incluye cuatro diseños. Se valida el objeto y sus límites antes de modificarlo. Modelos y texturas externos requieren un paquete de recursos del cliente.

## Commands and compatibility / Comandos y compatibilidad

- `/za diseno listar`, `/za diseno ver <id>`, `/za diseno aplicar <id>`: inspect and apply configured designs / consultar y aplicar diseños. Hold the item in the main hand / sostén el objeto en la mano principal.
- `/za enchant <modid:id> <level>` and `/za eliminar <modid:id>`: manage enchantments / administrar encantamientos.
- `/za reload` or `/zonecore reload`: reload configuration / recargar configuración.
- Player permission nodes are `zonechants.admin`, `.enchant`, `.eliminar`, `.reload`, `.editar`, `.atributo`, `.inspeccionar`; assign through a permission provider using ZoneCore. Console access uses operator level 2 / la consola utiliza nivel de operador 2.
- Required / obligatorio: **ZG ZoneCore** version `[2.1.1,3)`; protected 2.1.3 was smoke tested with this protected 1.4.0 server JAR. Forge 1.20.1 / Java 17. Forge registries allow enchantment and attribute IDs from installed mods, subject to their own compatibility and item support / los registros Forge aceptan ID de mods instalados, según sus propias reglas de compatibilidad y soporte del objeto.

No private server TOML, credentials, mapping file or source code is included here. / Aquí no se publican TOML privados del servidor, credenciales, mapas de ofuscación ni código fuente.

