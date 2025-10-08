# File Save Dialog 

[Documentation](https://docs.omniverse.nvidia.com/kit/docs/omni.kit.window.file_exporter/latest/Overview.html)

add dependency 
```toml
[dependencies]
"omni.kit.window.file_exporter" = {}
```

get singleton

```python
# Get the singleton extension object, but as weakref to guard against the extension being removed. 
file_exporter = get_file_exporter()
if not file_exporter:
    return
```
usage

```python

def export_handler(self, filename: str, dirname: str, extension: str = "", selections: List[str] = []):
    # NOTE: Get user inputs from self._export_options, if needed.
    print(f"> Export As '{filename}{extension}' to '{dirname}' with additional selections '{selections}'")

file_exporter.show_window(
    title="Save As ...",
    export_button_label="Save",
    export_handler=self.export_handler,    
)
```