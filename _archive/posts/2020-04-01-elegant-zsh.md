---
layout: post
title: Build Your Own Elegant zsh
---

If you just want to put all the zsh files, e.g., `.zshrc`, `.zprofile`, into
`$XDG_CONFIG_HOME/zsh` folder, you just need to set the environment variable
`ZDOTDIR`: `ZDOTDIR=$XDG_CONFIG_HOME/zsh`, for `HOME` is used instead when
`$ZDOTDIR` is unset.

## Set $ZDOTDIR
If you are using login manager(also called display manager, e.g., `lightdm`,
`gdm`, `sddm`), you could write it in the `$HOME/.xprofile`:

```sh
if [[ -z "$XDG_CONFIG_HOME" ]]
then
        export XDG_CONFIG_HOME="$HOME/.config"
fi

if [[ -d "$XDG_CONFIG_HOME/zsh" ]]
then
        export ZDOTDIR="$XDG_CONFIG_HOME/zsh"
fi
```

If you are just using `startx` to initialize your X session, it will read your
`ZDOTDIR/.zprofile`, so put this in your `$HOME/.zprofile`
```sh
#!/bin/sh
[[ -f ~/.config/zsh/.zshenv ]] && source ~/.config/zsh/.zshenv
```

`or Put this`

```sh
if [[ -z "$XDG_CONFIG_HOME" ]]
then
        export XDG_CONFIG_HOME="$HOME/.config"
fi

if [[ -d "$XDG_CONFIG_HOME/zsh" ]]
then
        export ZDOTDIR="$XDG_CONFIG_HOME/zsh"
fi
```

## other useful stuff in .zshrc
the interactive shell read the `$ZDOTDIR/.zshrc`

#### oh my zsh
```sh
ZSH_THEME="ys"
plugins=(git zsh-syntax-highlighting zsh-autosuggestions) # I use these 3 plugins
source $ZSH/oh-my-zsh.sh # Put this line before vi mode
```
#### zsh: Include hidden files in tab complete menu:
```sh
_comp_options+=(globdots)
```

#### zsh vi mode
```sh
bindkey -v
bindkey -M vicmd "k" vi-insert
bindkey -M vicmd "K" vi-insert-bol
bindkey -M vicmd "n" vi-backward-char
bindkey -M vicmd "i" vi-forward-char
bindkey -M vicmd "N" vi-beginning-of-line
bindkey -M vicmd "I" vi-end-of-line
bindkey -M vicmd "e" down-line-or-history
bindkey -M vicmd "u" up-line-or-history
bindkey -M vicmd "l" undo
bindkey -M vicmd "=" vi-repeat-search
bindkey -M vicmd "h" vi-forward-word-end

# Use vim keys in tab complete menu:
bindkey -M menuselect 'n' vi-backward-char
bindkey -M menuselect 'u' vi-up-line-or-history
bindkey -M menuselect 'i' vi-forward-char
bindkey -M menuselect 'e' vi-down-line-or-history
bindkey -v '^?' backward-delete-char

function zle-line-init zle-keymap-select {
	RPS1="${${KEYMAP/vicmd/-- NOR --}/(main|viins)/-- INS --}"
	RPS2=$RPS1
	zle reset-prompt
}
```

#### Beam cursor
```sh
function zle-keymap-select {
	if [[ ${KEYMAP} == vicmd ]] || [[ $1 = 'block' ]]; then
		echo -ne '\e[1 q'
	elif [[ ${KEYMAP} == main ]] || [[ ${KEYMAP} == viins ]] || [[ ${KEYMAP} = '' ]] || [[ $1 = 'beam' ]]; then
		echo -ne '\e[5 q'
  fi
}
zle -N zle-keymap-select

# Use beam shape cursor on startup.
echo -ne '\e[5 q'

# Use beam shape cursor for each new prompt.
preexec() {
	echo -ne '\e[5 q'
}

_fix_cursor() {
	echo -ne '\e[5 q'
}
precmd_functions+=(_fix_cursor)

zle -N zle-line-init
zle -N zle-keymap-select

KEYTIMEOUT=1
```

#### Plugin: zsh-autosuggestions
`ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=#808080'`

#### Alias
`$XDG_CONFIG_HOME/.zshrc`:
```sh
source $XDG_CONFIG_HOME/zsh/aliasrc`
```

-------------
An example:
`$XDG_CONFIG_HOME/aliasrc` :
```sh
#!/bin/sh

alias \
	ls="ls -hN --color=auto --group-directories-first" \
	grep="grep --color=auto" \
	diff="diff --color=auto" \
	hi="highlight --out-format=ansi"

alias \
	bat="cat /sys/class/power_supply/BAT?/capacity" \
	cp="cp -iv" \
	mv="mv -iv" \
	rm="rm -v" \
	mkd="mkdir -pv"
```
