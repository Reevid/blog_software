---
layout: post
comments: ture
title: "[Shell] Exit and exit status"
description: ""
categories: [Shell]
tags: [Shell, bash, exit]
redirect_from:
  - /2018/12/06/
---

* Kramdown table of contents
{:toc .toc}

# Exit and exit status

The `exit` command is used to end the script as in the C program. It can also return some value to the script's parent process.

All commands return an exit status (sometimes referred to as return status), which returns a zero on success, or a non-zero that can be interpreted as an error code on failure. However, UNIX-compliant commands, programs, and utilities return zero on success.

Similarly, the script's function or script itself returns the exit status. The last command executed in the script function or script determines the exit status. In the script, `exit nnn` tells the shell the exit status of `nnn` (`nnn` must be a decimal number between `0` and `255`).

> Note: If you just `exit` with no parameters, the exit status of the last executed command (except exit itself) will be the exit status of the script.

`$?` Shows the exit status of the last instruction. If `$?` Is returned after the function returns, the exit status of the last instruction of the function is reported. Bash does this by returning the ***return value*** of the function. After the script exits, you can use `$?` On the command line to determine the exit status of the last command in the script. Conventionally, `0` indicates success and numbers `1` through `255` indicate an error.

# Example

## Exit and exit status

``` bash
#!/bin/bash
echo hello
echo $?    # 명령어가 성공했기 때문에 종료 상태 0이 리턴됨.

lskdf      # 알수없는 명령어.
echo $?    # 0이 아닌 종료 상태가 리턴됨.

exit 113   # 쉘에게 113을 리턴함.
```

To check, type `echo $?` After this script exits.

> Conventionally `exit 0` means success.A value other than `0` indicates an error or exception.

`$?` Is particularly useful for checking the results of a command to be executed in a script

## Deny the condition with `!`

The logical no qualifier `!` Affects the exit status by reversing the result of a test or command.

``` bash
$ true  # 쉘 내장명령어인 "true".
$ echo "\"true\"의 종료 상태 = $?"
"true"의 종료 상태 = 0
```

``` bash
$ ! true
$ echo "\"! true\"의 종료 상태 = $?"
"! true"의 종료 상태 = 1
```

One thing to be careful about is that when you use `!`, There must be a blank space. Just write `!True` to get a ***command not found*** error.
