# 🚀 SpaceCorp — Mon homelab

Bienvenue dans mon labo perso ! C'est ici que je teste, que je casse et que
j'apprends tout ce que je ne peux pas (ou ne dois pas 😅) essayer en
production. Tout est auto-hébergé, documenté et en évolution permanente.

[⬅️ Retour au profil](README.md)

---

## 🎯 Pourquoi un homelab ?

- **Apprendre** : la virtualisation, le stockage, le réseau et la sécurité, mais en vrai, pas seulement dans des tutos
- **Reprendre le contrôle** de mes données grâce au self-hosting
- **Automatiser** la maison avec la domotique
- **M'amuser**, tout simplement 🔧

## 🖥️ Le matériel

| Rôle | Matériel |
|------|----------|
| Hyperviseur | Serveur HP ProLiant Gen8 (2 CPU, 256 Go de RAM) |
| Stockage principal | NAS DIY sous TrueNAS SCALE (Intel Core i7) |
| Stockage secondaire / backups | NAS Synology |
| Domotique | Home Assistant OS |
| Impression 3D | Elegoo Neptune 4 Plus |

## 🧱 L'architecture

```text
                 ┌──────────────┐
   Internet ───► │ Proxy / WAF  │ ──► Services exposés
                 └──────┬───────┘
                        │
        ┌───────────────┼────────────────┐
        ▼               ▼                ▼
 ┌─────────────┐ ┌──────────────┐ ┌───────────────┐
 │ Proxmox VE  │ │ TrueNAS SCALE│ │ Home Assistant│
 │ VM + LXC    │ │ Stockage ZFS │ │ Domotique     │
 │ Docker (VM) │ │ Apps         │ │               │
 └──────┬──────┘ └──────────────┘ └───────────────┘
        │
        ▼
 ┌─────────────────────┐
 │ Proxmox Backup      │ ──► NAS Synology
 │ Server              │
 └─────────────────────┘
```

- **Proxmox VE** : l'hyperviseur, avec des VM et des conteneurs LXC
- **TrueNAS SCALE** : le stockage ZFS et quelques apps
- **Docker** : la majorité des services tournent dans une VM dédiée, gérée avec Arcane
- **Home Assistant** : le cerveau de la maison connectée
- **Proxmox Backup Server** : les sauvegardes des VM et des conteneurs

## 📦 Les services

| Catégorie | Services |
|-----------|----------|
| 🎬 Médias | Jellyfin, Navidrome |
| 📄 Documents | Paperless-ngx, Nextcloud |
| 📊 Monitoring | Checkmk, Grafana |
| 📚 Documentation | Docmost, NetBox |
| 🏠 Domotique | Home Assistant, Frigate (NVR) |
| 🧭 Dashboard | Homepage |
| 🐳 Gestion Docker | Arcane |

## 🔐 Sécurité

- Reverse proxy avec WAF devant tout ce qui est exposé
- Rien n'est exposé directement : je passe par un proxy ou un tunnel
- Gestionnaire de mots de passe auto-hébergé
- Segmentation réseau par VLANs (gestion, serveurs, apps, IoT, clients, caméras, invités)
- Sauvegardes régulières et testées (la règle 3-2-1, on essaie 😉)

## 🛣️ Roadmap

- [ ] Migration du routeur vers **OPNsense** sur un mini-PC dédié
- [ ] Mise en place complète des **VLANs**
- [ ] Installation d'un **rack 19"** pour centraliser tout le matériel
- [ ] Arrivée de la **fibre** directement au rack
- [ ] Remplacement du serveur HP par une machine plus économe ⚡

## 💬 Me contacter

Une question sur mon setup ou envie d'échanger sur le self-hosting ?
Les liens sont sur [mon profil](README.md) !
