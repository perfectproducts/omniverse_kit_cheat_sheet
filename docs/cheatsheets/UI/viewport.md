# Show Notifications in Viewport
![image-20251018140334468](notificationdialog.png)

see documentation: https://docs.omniverse.nvidia.com/kit/docs/kit-sdk/latest/source/extensions/omni.kit.notification_manager/docs/index.html#omni.kit.notification_manager.post_notification 

```python
from omni.kit.notification_manager import post_notification, NotificationStatus

post_notification("Notification 1, default duration")
post_notification("Notification 4 (warning), with 4 second duration", duration=4, status=NotificationStatus.WARNING)

# status values: 
# NotificationStatus.INFO | NotificationStatus.WARNING

# simple ok box with callback 
import omni.kit.notification_manager as nm

ok_button = nm.NotificationButtonInfo("OK", on_complete=lambda:print("clicked"))
notification = nm.post_notification(
            "Notification Example", hide_after_timeout=False, duration=0,
            status=nm.NotificationStatus.INFO, button_infos=[ok_button])

```

## Menubar in Viewport

[omni.kit.viewport.menubar.core](https://docs.omniverse.nvidia.com/kit/docs/omni.kit.viewport.menubar.core/latest/USAGE_PYTHON.html)

## Frame selection

see documentation: [Focus, Zoom or Frame a Prim — Omniverse Developer Guide](https://docs.omniverse.nvidia.com/dev-guide/latest/programmer_ref/viewport/frame-prim.html)

```python
from omni.kit.viewport.utility import get_active_viewport, frame_viewport_selection
import omni.usd

prim_path = "/World/My/Prim"
ctx = omni.usd.get_context()

# The second arg is unused. Any boolean can be used.

ctx.get_selection().set_selected_prim_paths([prim_path], True)
frame_viewport_selection(active_viewport)
```

