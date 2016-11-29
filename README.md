# tasker
bash alias runner

## install

install via npm

```bash
npm install thecotne/tasker --save
# or
npm install thecotne/tasker --save-dev
```

create file `tasker`

```bash
#!/usr/bin/env bash
set -e

if [ ! -f ./node_modules/tasker/tasker-core ]; then
    npm install thecotne/tasker
fi

source ./node_modules/tasker/tasker-core

function test1 { # first test
    echo "first test success"
}

function test2 { # second test
    echo "second test success"
}

_bootstrap "${@}"

```

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

