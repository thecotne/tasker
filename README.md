# tasker
bash alias runner



## autocomplete

for zsh you can add this to your `.zshrc`

```bash
# Tasker basic command completion
_tasker_get_command_list () {
    tasker \
        | sed -r "s/\x1B\[([0-9]{1,2}(;[0-9]{1,2})?)?[mGK]//g" \
        | sed "1,/Available commands/d" \
        | gawk '/^ +[a-zA-Z0-9\_]+/ { print $1 }'
}

_tasker () {
    if [ -f tasker ]; then
        compadd `_tasker_get_command_list`
    fi
}

compdef _tasker tasker
```

