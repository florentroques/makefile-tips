# makefile-tips

## define a function
```makefile
define command_exists
  $(if $(shell where $(1)),$(info $(1) in PATH),$(error No $(1) in PATH))
endef
```
To call the function:
```makefile
$(call command_exists,command)
```

## TODO: define a function which includes a loop
Here's an attempt for now, unfortunately not working
```makefile
define commands_exist
  k := $(foreach exec,$($@),\
        $(if $(shell where $(exec)),$(info $(exec) in PATH),$(error "No $(exec) in PATH")))
endef
```
source: https://stackoverflow.com/a/25668869/1152843
