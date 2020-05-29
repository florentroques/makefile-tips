# makefile-tips

## detect OS
TODO: add list of OS names to use in makefile
```makefile
ifeq ($(OS),Windows_NT)
	SHELL = CMD
endif
```

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

makefile documentation systems
https://www.cmcrossroads.com/print/article/self-documenting-makefiles
		
https://github.com/simonmichael/hledger/commit/1b912387fab8384619cc037731df0ba971c16de7

