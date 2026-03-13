# Configure Privilege Levels

>[!IMPORTANT]
>Use privilege levels 2-14 for custom privileges. </br>**Level 0**: Rarely used - includes only `disable`, `enable`, `exit`, `help`, `logout` </br>
> **Level 1**: Default user mode (`Router>`) </br>
> **Level 15**: Enable mode (`Router#`)

> [!IMPORTANT]
> Higher levels inherit lower-level commands. Adding `show` enables all `show` variations. Adding `show ip route` enables the base `show` command on every other variable.

## Syntax
```cisco
privilege {exec | configure | interface | line} {level level_number | reset} command
```

## Parameters
- **mode**: Command mode (`exec`, `configure`, `interface`, or `line`)
- **level**: Keyword to assign a privilege level
- *level_number*: Numeric level (range **2-14**)
- **reset**: Removes command from custom level
- *command*: The CLI command to privilege

## Example Configuration
```cisco
! Allow ping at level 5
privilege exec level 5 ping

! Set password for level 5 access
enable secret level 5 cisco

! Create user with level 5 privileges
username SUPPORT privilege 5 secret cisco

! Verify configuration
show privilege
```