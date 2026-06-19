# Architecture CI/CD DevSecOps - Juice Shop

## Objectif

Mettre en place une chaîne CI/CD complète pour OWASP Juice Shop intégrant :

- build
- tests
- analyse statique du code
- analyse des dépendances
- détection de secrets
- build d'image Docker
- analyse de l'image Docker
- déploiement automatique en environnement de test
- analyse dynamique DAST
- conservation des rapports

## Architecture du pipeline

Développeur
→ Git Push
→ GitHub Actions
→ Build Node.js
→ Tests
→ Semgrep SAST
→ Trivy SCA
→ Gitleaks Secrets
→ Docker Build
→ Trivy Image Scan
→ Déploiement test Docker
→ OWASP ZAP DAST
→ Rapports sauvegardés en artefacts

## Outils utilisés

| Besoin | Outil |
|---|---|
| CI/CD | GitHub Actions |
| Build/Test | Node.js / npm |
| SAST | Semgrep |
| SCA | Trivy |
| Secrets | Gitleaks |
| Conteneurisation | Docker |
| Scan image | Trivy |
| DAST | OWASP ZAP |
| Rapports | GitHub Actions Artifacts |

## Vulnérabilités attendues

Juice Shop étant volontairement vulnérable, les outils peuvent détecter :

- dépendances vulnérables
- failles OWASP Top 10
- mauvaises pratiques de code
- failles web détectables dynamiquement
- risques liés à l'image Docker

## Pistes d'amélioration

- bloquer la pipeline si vulnérabilité critique
- ajouter Dependabot
- signer les images Docker
- publier l'image dans GitHub Container Registry
- déployer sur Kubernetes
- ajouter une étape de revue manuelle avant production
