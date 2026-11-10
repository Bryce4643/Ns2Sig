# Ns2Sig

## Research: Why some games require online when no Virtual Game Card is loaded

This repository tracks findings related to Switch 2 game-launch behavior seen while testing ns2jb-modloader-style payload workflows.

### What causes the online requirement

If a game is launched without a loaded **Virtual Game Card**, Nintendo can require an **online license entitlement check** ("checking if the software can be played").  
In that state, the console must contact Nintendo services to validate ownership before launch.

### Trigger conditions observed

- No Virtual Game Card currently loaded for the title.
- Launch path uses online-license validation instead of an already-loaded local card state.
- Connectivity/account state prevents entitlement verification.

### Why this matters for mod payload usage

This behavior is part of Nintendo's launch/license flow and is **not** caused by the mod payload itself.  
Payloads like ns2jb-modloader can patch RomFS/ExeFS content, but they do not replace Nintendo entitlement checks.  
So when license validation fails, launch is blocked before mods are relevant.

### Sources

- Nintendo support: Virtual Game Card guide  
  https://support.nintendo.com/my/switch2/play/digital/vgc/index.html
- Nintendo support: Online License setting (Switch 2 / Switch)  
  https://en-americas-support.nintendo.com/app/answers/detail/a_id/68663/~/how-to-enable-or-disable-the-online-license-setting-on-nintendo-switch-2-and
- Nintendo support: "Checking if the software can be played..."  
  https://en-americas-support.nintendo.com/app/answers/detail/a_id/47555/~/“checking-if-the-software-can-be-played…”-message-when-starting-software
- ns2jb-modloader reference repository  
  https://github.com/SebaaMG/ns2jb-modloader
