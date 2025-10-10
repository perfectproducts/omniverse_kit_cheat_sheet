# File Dialogs

## File Save Dialog (file_exporter)

[Documentation](https://docs.omniverse.nvidia.com/kit/docs/omni.kit.window.file_exporter/latest/Overview.html)

add dependency 
```toml
[dependencies]
"omni.kit.window.file_exporter" = {}
```

get singleton

```python
# get file_exporter 
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


## File Open Dialog (file_importer)

[Documentation](https://docs.omniverse.nvidia.com/kit/docs/omni.kit.window.file_importer/latest/Overview.html)

```toml
[dependencies]
"omni.kit.window.file_importer" = {}
```


```python
# Get the singleton extension.
file_importer = get_file_importer()
if not file_importer:
    return

def import_handler(self, filename: str, dirname: str, selections: List[str] = []):
    # NOTE: Get user inputs from self._import_options, if needed.
    print(f"> Import '{filename}' from '{dirname}' or selected files '{selections}'")

file_importer.show_window(
    title="Import File",
    import_handler=self.import_handler,
    #filename_url="omniverse://ov-rc/NVIDIA/Samples/Marbles/Marbles_Assets.usd",
)
```