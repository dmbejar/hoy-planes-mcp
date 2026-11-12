# Hoy Planes MCP server

What's on in 12 Spanish provinces: concerts, theater, exhibitions, family and free plans by date, topic, price and distance, from your AI assistant.

Hoy Planes is the network of daily-updated local guides Hoy Madrid, Hoy Barcelona, Hoy Valencia, Hoy Sevilla, Hoy Zaragoza, Hoy Baleares, Hoy Castellón, Hoy Alicante, Hoy Málaga, Hoy Asturias, Hoy Murcia and Hoy Cádiz. This hosted MCP server lets Claude, ChatGPT, Cursor and other MCP clients search those listings. Every plan links to its page on the website, where tickets are bought.

This repository holds documentation only. The server is hosted; there is nothing to install.

| | |
|---|---|
| Endpoint | `https://mcp.hoyplanes.com` (Streamable HTTP, at the root) |
| Authentication | None. No account, no API key |
| Cost | Free |
| Official MCP Registry | [`com.hoyplanes/hoy-planes`](https://registry.modelcontextprotocol.io/v0/servers?search=com.hoyplanes/hoy-planes) |
| Docs | https://www.hoyplanes.com/mcp/ |
| Privacy | https://www.hoyplanes.com/politica-de-privacidad/#conector |
| Contact | info@wandary.com |

## Tools

All three are read-only. Listings and tool texts are in Spanish.

| Tool | What it does |
|---|---|
| `buscar_planes` | Search plans in a Spanish province by date, topic, occasion, words, free only, maximum price and distance from a point. Returns up to 20, most popular first (or nearest first when a point is given), with a link to the full listing. |
| `ver_plan` | Details of one plan: upcoming days, price, venue with address and coordinates, full description and its page on the website. |
| `listar_provincias` | The provinces with a guide and the topic, occasion and date values `buscar_planes` accepts. |

The optional `lat`/`lng` of `buscar_planes` are the point for the distance filter, not the user's location. They are used only for that query and never stored.

## Connect

**Claude**: Settings → Connectors → Add custom connector → `https://mcp.hoyplanes.com`.

**ChatGPT**: add it as a custom app/connector with the URL `https://mcp.hoyplanes.com` and no authentication.

**Cursor, VS Code and other clients** (`mcp.json`):

```json
{
  "mcpServers": {
    "hoy-planes": {
      "type": "http",
      "url": "https://mcp.hoyplanes.com"
    }
  }
}
```

Clients without remote support can use [`mcp-remote`](https://www.npmjs.com/package/mcp-remote): `npx -y mcp-remote https://mcp.hoyplanes.com`.

## Example questions

- ¿Qué conciertos hay en Madrid este fin de semana?
- Planes gratis con niños en Valencia el sábado
- Teatro en Sevilla por menos de 20 euros esta semana
- What's on near Plaza Mayor in Madrid tonight?

## Privacy

No account and no personal data. The server never receives your conversation or files, only the parameters of each query. Full policy: https://www.hoyplanes.com/politica-de-privacidad/#conector

`server.json` is the entry published in the official MCP Registry.

Made by [Wandary](https://www.wandary.com) in Spain.
