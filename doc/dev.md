# Development hints

## Quick tests in Thonny

An easy way to run the current version of the plug-in without installing is to run Thonny from its package, not as the distributed application.
First install all the required packages, except the plug-in which is found in the current directory.
```
python3 -m pip install thonny
python3 -m pip install tdmclient
```

Then launch Thonny with
```
python3 -c "import thonny; thonny.launch()"
```

## Patching commands

Commands are stored in `get_workbench()._commands` with `get_workbench().add_command`. To patch a command easily, e.g. to run a script either on the Thymio II if the file suffix is `.pythii` or as usual for any other suffix, we've defined the following functions.
```py
def patch_command(command_id, patched_handler):
    """Replace the handler of a command specified by its id with a function
    patched_handler(handler).
    """
    workbench = get_workbench()
    workbench._commands = [
        c if c["command_id"] != command_id else {
            **c,
            "handler": (lambda c: lambda: patched_handler(c))(c)
        }
        for c in workbench._commands
    ]

def patch(command_id):
    def register(fun):
        patch_command(command_id, fun)
        return fun
    return register
```

The arguments of `patch_command` are the command id and a new handler function which has a single argument, the original dict in `_commands` (the original `**kwargs` passed to `add_command`). Or just prepend the function decorator `patch("command_id")` to the patched function definition.
