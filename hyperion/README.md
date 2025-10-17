# Hyperion (Add-on Home Assistant)

Cet add-on exécute Hyperion NG via l’image GHCR `ghcr.io/michelbaie/hyperionng-dockerized` en mode host, avec UI intégrée (Ingress) dans Home Assistant.

- UI intégrée: Rubrique “Hyperion” dans la barre latérale.
- Persistance: Config Hyperion stockée dans `/config` (montée depuis l’addon_config).
- Accès matériel: USB/vidéo/série (mappages standard Home Assistant).

Documentation détaillée: voir `DOCS.md`.