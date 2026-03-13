# Role-Based CLI

## View Types
- Root View: It contains all command, it have the highest privilige. Only a root view user can configure new view and add or remove commands from existing views.
- CLI View: You can add commands into a CLI view
- Superview: it consists one or more CLI view. You assign for users multiple CLI view at once. You cannot define command for it, if you wan to add commands first add it to a CLI view, than give it for a superview. If you delete a superview it does not delete the associated CLi views

## Configure CLI Views

1. Enable AAA with `aaa new-model`
2. Change to root view `enable view` 
3. Create a view `praser view` *view-name*
4. Assign a password `secret` *password*
5. Assign commands `Router(config-view)# commands parser-mode {include | include-exclusive | exclude} [all] [interface interface-name | command]`

| Commands | Description |
|----------|-------------|
| **commands** | Adds commands or interfaces to a view. |
| *parser-mode* | The mode in which the specified command exists; for example, EXEC mode. |
| **include** | Adds a command or an interface to the view and allows the same command or interface to be added to other views. |
| **include-exclusive** | Adds a command or an interface to the view and excludes the same command or interface from being added to all other views. |
| **exclude** | Excludes a command or an interface from the view. |
| **all** | A "wildcard" that allows every command in a specified configuration mode that begins with the same keyword or every subinterface for a specified interface to be part of the view. |
| **interface** *interface-name* | Interface that is added to the view. |
| *command* | Command that is added to the view. |

### Example Configuration

```CLI
R1(config)# aaa new-model
R1(config)# parser view SHOWVIEW
R1(config-view)# secret ?
0     Specifies an UNENCRYPTED password will follow
5     Specifies an ENCRYPTED secret will follow
LINE  The UNENCRYPTED (cleartext) view secret string
R1(config-view)# secret cisco
R1(config-view)# commands exec include show
R1(config-view)# exit
```

## Configure Superviews

1. Make a superview `praser view` *view-name* `superview`
2. Add a password `secret` *password*
3. Assign views `view` *view-name*

### Example configuration

```Superview
R1(config)# parser view JR-ADMIN superview
R1(config-view)# secret cisco
R1(config-view)# view SHOWVIEW
R1(config-view)# view VERIFYVIEW
R1(config-view)# view REBOOTVIEW
R1(config-view)# exit
```

## Show commands

```Show
enable view JR-ADMIN - logs in to a view

show parser view - show the current view

show parser view all - show all available view
```