# mini-soc-wazuh

Labo de pratique blue team (ESGI) : mini SOC basé sur **Wazuh** pour s'entraîner à la détection, à l'investigation et à la réponse à incident, dans un environnement isolé.

> Tout se passe dans un réseau de labo isolé. Aucune cible externe, aucun système tiers.

## Architecture (prévue)

| VM | Rôle | Source |
|----|------|--------|
| Wazuh | Manager + Indexer + Dashboard (SIEM/XDR) | `wazuh-4.14.11.ova` |
| Ubuntu Server 24.04 | Endpoint surveillé (agent Wazuh) | `ubuntu-24.04.5-live-server-amd64.iso` |
| Kali Linux 2026.3 | Machine d'attaque, uniquement contre les VM du labo | `kali-linux-2026.3-virtualbox-amd64.7z` |

Réseau : réseau interne / host-only VirtualBox, sans accès direct à Internet pour les VM d'attaque et les cibles.

## Structure du dépôt

```
rules/        règles de détection et décodeurs Wazuh personnalisés
scripts/      scripts d'installation, de déploiement d'agents, de simulation
reports/      comptes rendus de TP et d'investigations
screenshots/  captures (dashboard, alertes, configuration)
```

Les images de VM (`*.ova`, `*.iso`, `*.7z`, `*.vdi`, `*.vmdk`) sont exclues du dépôt via `.gitignore`.

## Référentiels visés

- MITRE ATT&CK (mapping des règles et des alertes)
- NIST SP 800-61 (gestion des incidents)
- ANSSI (guides de journalisation et de détection)

## Avancement

- [x] Images téléchargées
- [x] Vérification des checksums (SHA256 Ubuntu/Kali, SHA512 Wazuh), voir `CHECKSUMS.txt`
- [ ] Déploiement de la VM Wazuh
- [ ] Déploiement de l'endpoint Ubuntu + agent
- [ ] Premières règles personnalisées
- [ ] Premier scénario d'attaque / détection
