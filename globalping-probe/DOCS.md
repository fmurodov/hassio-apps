# Globalping Probe

Runs a [Globalping](https://globalping.io) network probe. The probe connects out to the
Globalping API and runs measurements (ping, traceroute, mtr, DNS, HTTP) requested by
users of the platform. It does not open any ports.

## Configuration

| Option | Description | Default |
|---|---|---|
| `adoption_token` | Adoption token from [dash.globalping.io](https://dash.globalping.io). Automatically adds the probe to your account. | _(empty)_ |
| `log_level` | Log verbosity: `trace`, `debug`, `info`, `notice`, `warning`, `error` or `fatal`. | `info` |

Without an adoption token the probe still joins the network; you can adopt it manually
from the dashboard later.

## Notes

- The app uses host networking so container networking does not affect latency results.
- The probe updates itself automatically. It restarts inside the app when a new version
  is applied, so the probe version in the logs may be newer than the app version.
- The probe identity is stored in `/data/probe_uuid` and survives app restarts and updates.
  Delete it (by uninstalling the app) to register as a new probe.
