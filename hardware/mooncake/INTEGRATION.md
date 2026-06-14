# Mooncake Integration

These files are the reusable Ratchet app module:

```text
main/apps/app_ratchet/
main/assets/images/icon_ratchet.c
```

To install it into `M5StopWatch-UserDemo`, compile the app and icon source from
this repository and apply the following integration points.

## App Registration

Add the app include to `main/apps/apps.h`:

```cpp
#include "app_ratchet/app_ratchet.h"
```

Register the app in `main/main.cpp`, for example after `AppLuckyWheel` and
before `AppSchulte`:

```cpp
GetMooncake().installApp(std::make_unique<AppRatchet>());
```

## Icon Declaration

Declare the launcher icon in `main/assets/assets.h`:

```cpp
LV_IMG_DECLARE(icon_ratchet);
```

## Dependencies

The app uses existing StopWatch firmware facilities:

- Mooncake app lifecycle.
- `apps/common/key_manager/key_manager.h`.
- `hal/hal.h` for touch, audio, vibration, and LVGL locking.
- `assets/assets.h` for the launcher icon.
- `smooth_lvgl.hpp`, `smooth_ui_toolkit`, and `uitk` wrappers.
- ESP-IDF FreeRTOS task APIs for background gear frame generation.

It is not a standalone ESP-IDF firmware project by itself.
