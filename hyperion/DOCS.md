# Hyperion - Documentation

## Présentation
Hyperion NG permet l’éclairage “ambilight” et la visualisation de contenu. Cet add-on lance Hyperion dans Home Assistant via une image préconstruite GHCR, avec UI intégrée (Ingress).

## Installation
1. Ajoutez le dépôt: `https://github.com/MichelBaie/homeassistant-addons`
2. Dans la Boutique d’add-ons, installez “Hyperion”.
3. Démarrez l’add-on et activez “Démarrer au démarrage” et “Surveiller” si souhaité.
4. Cliquez sur “Ouvrir l’interface Web” ou utilisez la rubrique “Hyperion” dans la barre latérale.

## Réseau / Ports
- Mode réseau: host
- L’UI Hyperion écoute par défaut sur 8090 (configuré pour l’Ingress).
- Les ports spécifiques de Hyperion (ex: 8090, 8092, 19444, 19445) restent accessibles en host si nécessaire par d’autres clients du réseau local.

## Persistance des données
- La configuration Hyperion est stockée dans `/config` au sein du conteneur.
- Côté Home Assistant, cet emplacement correspond au dossier `addon_configs/<repo_hash>_hyperion`.

## Accès aux périphériques
- L’add-on expose les bus `usb`, `video` (V4L2 /dev/video*), `uart` (/dev/tty*), et `udev`.
- Branchez votre grabber USB (ex: /dev/video0) et sélectionnez-le dans l’UI Hyperion (Configuration > Capturer).
- Pour les contrôleurs LED série (ex: /dev/ttyUSB0), sélectionnez l’interface correspondante dans Hyperion.

Note: Les options d’add-on ne permettent pas d’ajouter dynamiquement des montages de devices. Le Supervisor gère des mappages génériques (usb/uart/video). Sélectionnez ensuite le device exact dans Hyperion.

## Ingress
- L’add-on active Ingress, ce qui permet d’ouvrir Hyperion directement dans Home Assistant (menu latéral “Hyperion”).
- Aucune authentification supplémentaire n’est nécessaire (gérée par Home Assistant).

## Dépannage
- Si l’UI ne s’ouvre pas: vérifiez que l’add-on est démarré et consultez les logs de l’add-on.
- Si aucun device vidéo n’apparaît: vérifiez le branchement, et que votre machine expose /dev/video* (ex: sur un hôte Linux avec grabber USB V4L2).
- Si vous utilisez un Raspberry Pi avec sorties matérielles spécifiques (SPI/GPIO), des permissions supplémentaires peuvent être nécessaires. Cet add-on n’active pas `full_access` ni des capacités privilégiées par défaut.