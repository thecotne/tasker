# tasker
bash alias runner

## install

install via npm

```bash
npm install @thecotne/tasker --save
# or
npm install @thecotne/tasker --save-dev
```

create file `tasker`

```bash
#!/usr/bin/env bash
set -e

if [ ! -f ./node_modules/@thecotne/tasker/tasker-core ]; then
    npm install @thecotne/tasker
fi

source ./node_modules/@thecotne/tasker/tasker-core

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
source /path/to/tasker/zsh-comp
```

