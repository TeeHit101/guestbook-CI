Guestbook Application (Source Code) 🚀

Detta repository innehåller källkoden för applikationen Guestbook. Här sker all utveckling av funktionalitet för frontend och backend.

Detta repo är den första delen i vår GitOps-kedja och ansvarar för Continuous Integration (CI).

Struktur


├── .github/workflows/   # GitHub Actions (CI-pipeline)

├── backend/             # Backend-kod (Go) + Dockerfile

└── frontend/            # Frontend-kod (HTML/Nginx) + Dockerfile


Teknisk Stack

Backend: Go (Golang) REST API.

Frontend: Nginx som serverar statisk HTML & JavaScript.

Container: Docker (Multi-stage builds).

CI: GitHub Actions.

CI-Flöde (Automatisering)

När kod pushas till main-branschen startar en GitHub Action som automatiskt utför följande steg:

Bygger: Skapar optimerade Docker-images för både frontend och backend.

Publicerar: Pushar bilderna till GitHub Container Registry (GHCR).

Tagging: Varje image taggas med unikt Git Commit SHA (t.ex. :abc1234) för spårbarhet.

Triggar CD: CI-roboten checkar ut vårt konfigurations-repo (guestbook-argoCD) och uppdaterar deployments med den nya image-taggen.

Koppling till GitOps

Detta repo innehåller ingen Kubernetes-konfiguration.
All deployment-konfiguration (YAML, Services, PVC) hanteras i vårt separata config-repo:
guestbook-argoCD

Detta projekt är en del av kursen Containerteknologi (DevOps24).
