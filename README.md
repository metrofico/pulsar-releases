# Pulsar Launcher — Releases públicas

Instaladores oficiales de **Pulsar Launcher** y los árboles de actualización.

- Landing: https://pulsarlauncher.com
- Repo del launcher (privado): mantenido aparte
- Publicación: automática desde el workflow `release.yml` del repo del launcher cuando se empuja un tag `vX.Y.Z` anotado.

## Qué hay en cada release

Cada tag `vX.Y.Z` lleva como assets:

- `pulsar-launcher-X.Y.Z-windows.exe` — instalador Windows (Inno Setup)
- `pulsar-launcher-X.Y.Z-linux.AppImage`, `.tar.gz` — Linux
- `pulsar-launcher-X.Y.Z-macos.dmg` — macOS (ARM)
- `tree-X.Y.Z-<os>.json` — árbol de archivos firmado (spec 0033/0034)
- `objects-X.Y.Z-<os>.tar.gz` — objetos de actualización por contenido
- `legit-X.Y.Z-<os>.json.gz` — tablas de retos del Legit Module (spec 0047)
- `LegitModulePulsar-X.Y.Z.jar` — plugin para servidores Paper/Spigot/Velocity

El launcher ya instalado descarga los deltas directamente de este repo (CDN gratis de GitHub). La landing redirige al
instalador correcto según el sistema operativo del navegador.

## Integridad

Los archivos `tree-*.json` están firmados Ed25519 con la clave privada del proyecto. La pública (`pulsar-release.pub`)
viaja embebida en cada launcher. Un atacante que reemplace un asset no puede forjar una firma válida; el launcher lo
rechaza.
