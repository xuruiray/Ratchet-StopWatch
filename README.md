# Ratchet-StopWatch

Ratchet gear app extracted from the M5Stack StopWatch firmware work.

This repository contains the reusable Mooncake/LVGL hardware app module:

```text
hardware/mooncake/main/apps/app_ratchet/
hardware/mooncake/main/assets/images/icon_ratchet.c
```

## Hardware App

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
