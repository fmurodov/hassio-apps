# iSponsorBlockTV Setup

This is a **one-time** setup tool. Once you have your Screen IDs, you can stop and
uninstall this add-on.

## How it works

The add-on uses SSDP and mDNS to discover YouTube-compatible devices on your network,
then walks you through selecting each device. The resulting Screen IDs are displayed
clearly so you can paste them into the main **iSponsorBlockTV** add-on.

## Steps

1. Make sure your Home Assistant and the TV are on the same network.
2. Start this add-on.
3. Click **Open Web UI**.
4. Follow the on-screen wizard to discover and pair your devices.
5. After the wizard finishes, your Screen IDs are shown — copy them.
6. Open the **iSponsorBlockTV** add-on configuration and enter the Screen IDs
   under **Devices**.
7. Stop this add-on.

## Running the wizard again

Press **Enter** at the prompt inside the web UI to restart the wizard without
restarting the add-on.

## Troubleshooting

- **No devices found**: Confirm your TV is on, the YouTube app is open, and both
  your HA host and the TV are on the same subnet.
- **Discovery works but pairing fails**: Try the manual option in the wizard —
  it will prompt you to enter the code shown on the TV screen
  (YouTube → Settings → Link with TV code).
