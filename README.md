# CM Suite Module Store

Repositorio oficial del **catálogo de módulos** para [CM Suite](https://github.com/2b2g/CMSUITE-TAURI).

Este repositorio contiene:
- 📦 **Catálogo** (`modules.json`) — lista de módulos disponibles para instalar
- 🔧 **CI/CD** — build automático de módulos y publicación de releases
- 🤝 **Guía de contribución** — cómo agregar tu propio módulo

---

## 🌐 URL del Catálogo

```
https://cmsuite.github.io/modules/modules.json
```

CM Suite consulta esta URL desde la pestaña **Tienda** del Centro de Complementos.

---

## 📋 Estructura del Catálogo

```json
{
  "schema_version": "1",
  "core_version": "1.0.0",
  "description": "Catálogo oficial de módulos para CM Suite",
  "modules": [
    {
      "id": "mi-modulo",
      "name": "Mi Módulo",
      "version": "1.0.0",
      "author": "Tu Nombre",
      "description": "Descripción de tu módulo",
      "minCoreVersion": "1.0.0",
      "icon": "Package",
      "hasFrontend": true,
      "download_url": "https://github.com/tu-usuario/modules/releases/download/mi-modulo-v1.0.0/mi-modulo.zip",
      "download_size": null,
      "checksum_sha256": null,
      "dependencies": [],
      "category": "utilidades",
      "screenshots": [],
      "release_notes": "Versión inicial",
      "license": "MIT",
      "translations": {}
    }
  ]
}
```

### Campos del módulo

| Campo | Tipo | Descripción |
|-------|------|-------------|
| `id` | string | Identificador único (minúsculas, guiones) |
| `name` | string | Nombre visible |
| `version` | string | Versión semántica (X.Y.Z) |
| `author` | string | Autor del módulo |
| `description` | string | Descripción breve |
| `minCoreVersion` | string | Versión mínima del core |
| `icon` | string | Icono Lucide (PascalCase) o ruta SVG |
| `hasFrontend` | bool | Si tiene interfaz React |
| `download_url` | string | URL del ZIP (GitHub Release) |
| `download_size` | number | Tamaño en bytes (opcional) |
| `checksum_sha256` | string | SHA-256 del ZIP (opcional) |
| `dependencies` | string[] | IDs de módulos requeridos |
| `category` | string | Categoría: `conversion`, `analisis`, `consultas`, `utilidades` |
| `translations` | object | Traducciones ES/EN del módulo |

---

## 🚀 Cómo Contribuir un Módulo

### Requisitos del Módulo

Tu módulo debe tener esta estructura:

```
mi-modulo/
├── manifest.json        # Metadatos del módulo
├── main.js              # Entry point backend
├── backend/             # Código backend
├── frontend/            # Componentes React (opcional)
│   └── index.js         # Bundle compilado como IIFE
├── migrations/          # Migraciones SQL (opcional)
└── assets/              # Recursos estáticos (opcional)
```

### Pasos

1. **Fork** este repositorio
2. Agrega tu módulo en `modules/<id>/` con toda la estructura
3. Agrega la entrada en `modules.json` con los metadatos
4. Crea un **Pull Request**
5. El CI valida y compila tu módulo automáticamente
6. Se aprueba el PR → se genera un Release con el ZIP

---

## 🔧 CI/CD Pipeline

El workflow de GitHub Actions:

1. **Valida** estructura del módulo (manifest, directorios, entry)
2. **Compila** frontend React con esbuild
3. **Empaqueta** ZIP con todos los archivos
4. **Publica** como GitHub Release
5. **Actualiza** `modules.json` con los nuevos checksums

---

## 📝 Licencia

MIT — los módulos son de sus respectivos autores.
