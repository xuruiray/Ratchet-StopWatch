# Ratchet-StopWatch

Ratchet gear app extracted from the M5Stack StopWatch firmware work.

This repository contains two related parts:

- `web/`: standalone HTML prototype for interaction and motion tuning.
- `hardware/mooncake/`: reusable Mooncake/LVGL hardware app module.

## Web Prototype

Open the page directly in a browser:

```bash
open web/index.html
```

The prototype mirrors the device interaction model:

- Drag the gear to rotate it.
- Release after motion to continue with short inertia.
- Left key/button kicks the gear counterclockwise.
- Right key/button kicks the gear clockwise.
- Press both keys while inertia is active to stop the gear.
- Tooth-crossing feedback follows the same 9-tooth, 120ms minimum interval logic.

## Hardware App

The hardware app source is stored under the same path shape used by the
StopWatch firmware:

```text
hardware/mooncake/main/apps/app_ratchet/
hardware/mooncake/main/assets/images/icon_ratchet.c
```

The app provides a rotary ratchet interaction for the StopWatch device:

- A 9-tooth gear rendered from runtime-generated frames.
- Touch drag rotation with short mechanical inertia.
- Left and right hardware buttons can kick the gear in either direction.
- Tooth-crossing feedback drives vibration and a synthesized click sound.
- A+B long press returns to the launcher through the host firmware key manager.

It is not a standalone ESP-IDF firmware project by itself. It depends on the
host StopWatch firmware for Mooncake lifecycle, LVGL, HAL audio/vibration,
touch, button handling, and shared launcher assets.

## Integration

See `hardware/mooncake/INTEGRATION.md` for the host firmware changes required
to compile this app from a submodule.

## Source

Extracted from commit `b7cc4a4` in `xuruiray/M5StopWatch-UserDemo`.

## License

MIT. See `LICENSE`.
