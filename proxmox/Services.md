This document outlines services configurations.

---

### Prowlarr
**1.1 Install Flaresolverr**
- Purpose: allows for cloudflare torrents to be accessed.
- Used: Docker compose file from website
- How: within Prowlarr go to Settings > Indexers > FlareSolverr > Add Tag (Flare)

**1.2 Add Indexers**
- Purpose: Sonarr and Raddar will search these indexers for torrents
- Used: Indexers form old server, orginally got from reddit and basic browsing
- How: Indexers > Add Indexer ? Search (can filter language, media type, public/private)

**1.3 Add Sonarr & Radarr**
- Purpose: Connects tv and movie manager so it can access the indexers added
- How: Settings > Apps > Sonanr/Radarr > API key (obtained from Sonarr/Radarr
