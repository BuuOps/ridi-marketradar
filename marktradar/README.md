# MarktRadar

Weboberfläche für die Marktsuche. MarktRadar hat keine Qdrant-Zugangsdaten, sondern
schickt Suchen an den Container aus dem Repo **ridi-data-sources**, der mit Qdrant spricht.

## Start (Docker Desktop)

1. `.env.example` nach `.env` kopieren, `QDRANT_URL` und `QDRANT_API_KEY` (Read-only) eintragen.
2. In `docker-compose.yml` bei `DATASOURCES_REPO` die URL zum Repo ridi-data-sources eintragen
   (oder in `.env` setzen).
3. `docker compose up --build`
4. http://localhost:8000 öffnen, Strg+K, z. B. „smart lighting“ suchen.

## Lokale Entwicklung mit beiden Repos

Beide Repos nebeneinander klonen (`marktradar/` und `ridi-data-sources/`), dann in `marktradar/`:

    docker compose -f docker-compose.yml -f docker-compose.local.yml up --build

## Ohne Docker

Data Sources starten (`py interface_server.py`), dann hier `py server.py`, http://127.0.0.1:8000.
