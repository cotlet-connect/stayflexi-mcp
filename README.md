# Stayflexi MCP server for Claude and ChatGPT

**Yes, ChatGPT, Claude and other AI agents can work with your Stayflexi account.** Cotlet.dev connects your signed-in Cloud Browser to a hosted Stayflexi MCP server for hotel Shops / POS work. Orders, folio charges and outlet changes wait for your confirmation.

## What you can ask

> Review last night's outlet sales by source and status.

> Take a table order for the kitchen.

> Post room service to a guest folio for my approval.

> Free settled tables after service.

> Set up a new outlet and its tables.

## Connect in 2 minutes

Get your API key at https://cotlet.dev/app and export it as `COTLET_API_KEY`.

### Claude Code

```bash
claude mcp add --transport http cotlet https://cotlet.dev/mcp/v1 --header "Authorization: Bearer $COTLET_API_KEY"
```

### ChatGPT

Settings → Apps → add connector URL `https://cotlet.dev/mcp/v1`, then sign in with Cotlet.dev. No API key needed.

### Cursor

Copy `.cursor/mcp.json` from this repo into your project:

```json
{
  "mcpServers": {
    "cotlet": {
      "url": "https://cotlet.dev/mcp/v1",
      "headers": {
        "Authorization": "Bearer ${COTLET_API_KEY}"
      }
    }
  }
}
```

## Run it locally (stdio)

This repo is a real MCP server. It speaks MCP over stdio, lists its Stayflexi tools without any key, and forwards every tool call to the hosted Cotlet.dev server. The hosted URL above stays the recommended way. Use this when your client only starts local servers.

```json
{"mcpServers":{"stayflexi":{"command":"uvx","args":["stayflexi-mcp"],"env":{"COTLET_API_KEY":"your-key"}}}}
```

Or with Docker:

```bash
docker build -t stayflexi-mcp .
docker run -i --rm -e COTLET_API_KEY stayflexi-mcp
```

Tools: `stayflexi_guide`, `stayflexi_status`, `stayflexi_open`, `stayflexi_read`, `stayflexi_click`, `stayflexi_type`, `stayflexi_close`. Without `COTLET_API_KEY` a tool call answers: "Set COTLET_API_KEY. Get a key at https://cotlet.dev/app".

## Command line

Python 3.10+, nothing else to install. From PyPI:

```bash
pip install stayflexi-mcp        # or run it once: uvx stayflexi-mcp connect
stayflexi-mcp connect
```

Or straight from this repo:

```bash
export COTLET_API_KEY="your-key"
python3 stayflexi_agent.py connect   # ready config for Claude Code, Cursor, ChatGPT
python3 stayflexi_agent.py status    # is Stayflexi ready in your Cotlet.dev account
python3 stayflexi_agent.py guide     # Stayflexi screens and sign-in link
python3 stayflexi_agent.py read      # open Stayflexi, read the page, close the browser
python3 stayflexi_agent.py tools     # list Cotlet.dev tools
python3 stayflexi_agent.py serve     # start the stdio MCP server (same as no argument)
```

## Questions from Stayflexi users

**Does Stayflexi have an MCP server or an API?**

Stayflexi gives API keys to partner integrations but publishes no general API documentation or API price. The Cotlet.dev page checked 16 November 2026 found no Stayflexi MCP server or official ChatGPT or Claude connector.

**How do I connect Stayflexi to ChatGPT?**

Sign up at https://cotlet.dev/signup?app=stayflexi, enable Stayflexi and sign in at app.stayflexi.com in your Cotlet.dev Cloud Browser. Add https://cotlet.dev/mcp/v1/connect to ChatGPT with OAuth.

**Can I use Stayflexi with Claude?**

Yes. Add https://cotlet.dev/mcp/v1/connect as a custom connector in Claude and sign in to Cotlet.dev.

**Is this an official Stayflexi MCP server?**

No. Cotlet.dev is independent and is not affiliated with Stayflexi. The hosted integration works in your own signed-in hotel account.

## Find it on

- [Stayflexi on Cotlet.dev](https://cotlet.dev/integrations/stayflexi-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=stayflexi&utm_content=find)
- [PyPI package stayflexi-mcp](https://pypi.org/project/stayflexi-mcp/)
- [Odel](https://odel.app/modules/cotlet/stayflexi)
- [mcpbeat](https://mcpbeat.com/mcp-servers/cotlet/stayflexi/)
- [Step-by-step guide (PDF) on Internet Archive](https://archive.org/details/cotlet-connect-stayflexi-to-ai-agents-guide)

## Also works with

- [Mangomint MCP](https://github.com/cotlet-connect/mangomint-mcp)
- [Wanderlog MCP](https://github.com/cotlet-connect/wanderlog-mcp)
- [SmugMug MCP](https://github.com/cotlet-connect/smugmug-mcp)
- [Garmin Connect MCP](https://github.com/cotlet-connect/garmin-mcp)
- [Housecall Pro MCP](https://github.com/cotlet-connect/housecall-pro-mcp)
- [Medium MCP](https://github.com/cotlet-connect/medium-mcp)
- [Crexi MCP](https://github.com/cotlet-connect/crexi-mcp)
- [DistroKid MCP](https://github.com/cotlet-connect/distrokid-mcp)
- [LinkedIn MCP](https://github.com/cotlet-connect/linkedin-mcp)
- [EstimateOne MCP](https://github.com/cotlet-connect/estimateone-mcp)
- [Google Search Console MCP](https://github.com/cotlet-connect/google-search-console-mcp)
- [Lichess MCP](https://github.com/cotlet-connect/lichess-mcp)
- [Strava MCP](https://github.com/cotlet-connect/strava-mcp)
- [StreamElements MCP](https://github.com/cotlet-connect/streamelements-mcp)
- [Meetup MCP](https://github.com/cotlet-connect/meetup-mcp)
- [AccuRanker MCP](https://github.com/cotlet-connect/accuranker-mcp)
- [GetYourGuide MCP](https://github.com/cotlet-connect/getyourguide-mcp)
- [Idealista MCP](https://github.com/cotlet-connect/idealista-mcp)
- [Riverside MCP](https://github.com/cotlet-connect/riverside-mcp)
- [Udemy MCP](https://github.com/cotlet-connect/udemy-mcp)
- [Faire MCP](https://github.com/cotlet-connect/faire-mcp)
- [Teachable MCP](https://github.com/cotlet-connect/teachable-mcp)
- [Vagaro MCP](https://github.com/cotlet-connect/vagaro-mcp)
- [Buildertrend MCP](https://github.com/cotlet-connect/buildertrend-mcp)
- [Zoopla MCP](https://github.com/cotlet-connect/zoopla-mcp)
- [Dribbble MCP](https://github.com/cotlet-connect/dribbble-mcp)
- [Hostelworld MCP](https://github.com/cotlet-connect/hostelworld-mcp)
- [Mashvisor MCP](https://github.com/cotlet-connect/mashvisor-mcp)
- [Rent Manager MCP](https://github.com/cotlet-connect/rent-manager-mcp)
- [ThriveCart MCP](https://github.com/cotlet-connect/thrivecart-mcp)
- [Fresha MCP](https://github.com/cotlet-connect/fresha-mcp)
- [Booksy MCP](https://github.com/cotlet-connect/booksy-mcp)
- [BookingKoala MCP](https://github.com/cotlet-connect/bookingkoala-mcp)
- [Milanote MCP](https://github.com/cotlet-connect/milanote-mcp)
- [Partiful MCP](https://github.com/cotlet-connect/partiful-mcp)
- [Contractor Foreman MCP](https://github.com/cotlet-connect/contractor-foreman-mcp)
- [Pixieset MCP](https://github.com/cotlet-connect/pixieset-mcp)
- [GlossGenius MCP](https://github.com/cotlet-connect/glossgenius-mcp)
- [ZenMaid MCP](https://github.com/cotlet-connect/zenmaid-mcp)
- [AroFlo MCP](https://github.com/cotlet-connect/aroflo-mcp)
- [Simpro MCP](https://github.com/cotlet-connect/simpro-mcp)
- [Workiz MCP](https://github.com/cotlet-connect/workiz-mcp)
- [Kickserv MCP](https://github.com/cotlet-connect/kickserv-mcp)
- [Service Autopilot MCP](https://github.com/cotlet-connect/service-autopilot-mcp)
- [Boulevard MCP](https://github.com/cotlet-connect/boulevard-mcp)
- [Mindbody MCP](https://github.com/cotlet-connect/mindbody-mcp)
- [Meevo MCP](https://github.com/cotlet-connect/meevo-mcp)
- [DaySmart MCP](https://github.com/cotlet-connect/daysmart-mcp)
- [Acuity Scheduling MCP](https://github.com/cotlet-connect/acuity-scheduling-mcp)
- [Jane App MCP](https://github.com/cotlet-connect/jane-app-mcp)
- [FieldEdge MCP](https://github.com/cotlet-connect/fieldedge-mcp)
- [Phorest MCP](https://github.com/cotlet-connect/phorest-mcp)
- [DINGG MCP](https://github.com/cotlet-connect/dingg-mcp)
- [Invoice Simple MCP](https://github.com/cotlet-connect/invoice-simple-mcp)
- [PhotoShelter MCP](https://github.com/cotlet-connect/photoshelter-mcp)
- [RazorSync MCP](https://github.com/cotlet-connect/razorsync-mcp)
- [ShootProof MCP](https://github.com/cotlet-connect/shootproof-mcp)
- [Invoice2go MCP](https://github.com/cotlet-connect/invoice2go-mcp)
- [Appointy MCP](https://github.com/cotlet-connect/appointy-mcp)
- [Contractor+ MCP](https://github.com/cotlet-connect/contractor-plus-mcp)
- [Petpooja MCP](https://github.com/cotlet-connect/petpooja-mcp)
- [Teachers Pay Teachers MCP](https://github.com/cotlet-connect/teachers-pay-teachers-mcp)
- [Bloom MCP](https://github.com/cotlet-connect/bloom-mcp)
- [AestheticsPro MCP](https://github.com/cotlet-connect/aestheticspro-mcp)
- [Club OS MCP](https://github.com/cotlet-connect/club-os-mcp)
- [EZ Lawn Biller MCP](https://github.com/cotlet-connect/ez-lawn-biller-mcp)
- [Eversports Studio Manager MCP](https://github.com/cotlet-connect/eversports-studio-manager-mcp)
- [Exercise.com MCP](https://github.com/cotlet-connect/exercise-com-mcp)
- [Gymdesk MCP](https://github.com/cotlet-connect/gymdesk-mcp)
- [Iris Works MCP](https://github.com/cotlet-connect/iris-works-mcp)
- [CoachingPortal MCP](https://github.com/cotlet-connect/coachingportal-mcp)
- [CrewNest MCP](https://github.com/cotlet-connect/crewnest-mcp)
- [Paired Plus MCP](https://github.com/cotlet-connect/paired-plus-mcp)
- [ClubReady MCP](https://github.com/cotlet-connect/clubready-mcp)
- [Joist MCP](https://github.com/cotlet-connect/joist-mcp)
- [Trainerize MCP](https://github.com/cotlet-connect/trainerize-mcp)
- [Substack MCP](https://github.com/cotlet-connect/substack-mcp)
- [AnyList MCP](https://github.com/cotlet-connect/anylist-mcp)
- [Midjourney MCP](https://github.com/cotlet-connect/midjourney-mcp)
- [Systeme.io MCP](https://github.com/cotlet-connect/systeme-io-mcp)
- [VaultRE MCP](https://github.com/cotlet-connect/vaultre-mcp)
- [Hopper.so MCP](https://github.com/cotlet-connect/hopper-so-mcp)
- [oto.photo MCP](https://github.com/cotlet-connect/oto-photo-mcp)
- [Zolmi MCP](https://github.com/cotlet-connect/zolmi-mcp)
- [Estimate Rocket MCP](https://github.com/cotlet-connect/estimate-rocket-mcp)
- [Pikit MCP](https://github.com/cotlet-connect/pikit-mcp)
- [All apps connected through Cotlet.dev](https://github.com/cotlet-connect)

---

More: https://cotlet.dev/integrations/stayflexi-api-mcp-server?utm_source=github&utm_medium=readme&utm_campaign=stayflexi

Start free: https://cotlet.dev/signup?app=stayflexi&utm_source=github&utm_medium=readme&utm_campaign=stayflexi
