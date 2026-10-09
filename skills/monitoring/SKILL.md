---
name: monitoring
description: Connect a project's server and monitoring to Kai and the Bridge: health endpoint, CI status, metrics over an SSH tunnel, alerts. Use when a project gets a server, when "is it deployed" or "is it healthy" must be answerable in one request, or when a tile in the Bridge is wanted.
---

# Server and monitoring

What a project's server exposes, so Kai can answer "is it up, is it the right commit, is anything stuck" without an agent:

1. **Health endpoint**: `GET /api/health` returning JSON with at least `ok` and the running `commit`. Deploys are verified by reading it.
2. **CI**: images built by a GitHub workflow and pulled by the server; the workflow name is what the Bridge watches.
3. **Metrics**: Prometheus scraping the app on a private address; the box exposes only 22 and 443. From the Mac the path is an SSH tunnel owned by the Bridge; the app never reads or stores a key, it uses the person's ssh agent.
4. **Alerts**: a few gauges worth a red tile: jobs stuck longer than N minutes, failures in the last hour, disk, queue depth. Name them in the project's adapter note.

Register the project in the Bridge: `~/Library/Application Support/Kai Bridge/config.json`, `projects` entry

    { "id": "<slug>", "name": "<Name>",
      "github": { "repo": "<owner>/<repo>", "workflow": "ci.yml" },
      "health": { "url": "https://<domain>/api/health", "commitField": "commit" },
      "prometheus": { "tunnel": { "host": "<server>", "user": "<user>", "localPort": <port> } } }

Keep the project's adapter note in `projects/<name>/adapter.md`: how the server is reached, which series exist and what each tile means. Facts only, no secrets. The `ops` agent (see the `agents` skill) is the only one that changes anything on the server, and only on the person's word.
