# Notes for Future Agents

## Repository Setup
- Git is already initialized; `origin` points to `https://github.com/MattieGit/Open-AIR`.
- `.gitignore` currently ignores `.DS_Store`. Add other ignores as needed.

## Valve Firmware Configuration
- The authoritative YAML lives in `Open AIR Valve/Software/Open_AIR_Valve.yaml`.
- We removed the duplicate `Valve/Open_AIR_Valve.yaml`; keep the configuration centralized under `Open AIR Valve/Software/`.
- The valve template now includes a `fast_update_ticks` global plus a 1 s interval loop to publish quick status updates right after commands. Preserve this structure and adjust the tick count if you need longer/shorter refresh bursts.
- Hall sensor input on GPIO35 uses `pin.inverted: true` by default and bumps the fast update timer whenever the sensor toggles; only flip to `false` if you encounter a legacy mechanical switch that reports the closed state correctly without inversion.

## Testing & Deployment
- No automated tests exist in the repo. Validate changes by compiling/deploying with ESPHome as needed.
- When pulling from upstream, fetch + rebase before pushing to avoid conflicts with existing history.
