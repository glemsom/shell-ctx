# shell-ctx
Kubernetes context switcher for shells.  
With *shell-ctx* each shell will operate in its own isolated Kubernetes context.  
Switching between contexts is done by invoking `kubectl shell-ctx` in your current shell.  

### Supported shells
Bash, Zsh and Fish


## Installation
### Krew
`kubectl krew install shell-ctx`

### Manual
`sudo curl https://raw.githubusercontent.com/glemsom/shell-ctx/main/kubectl-shell_ctx -o /usr/local/bin/kubectl-shell_ctx`  
`sudo chmod +x /usr/local/bin/kubectl-shell_ctx`

## Dependencies
For this plugin to operate the following dependencies are required:
 - awk
 - sed
 - fzf
 - kubectl

### Demo install
![Install](shell-ctx-install.gif)

## Setup
Set a custom `KUBECONFIG`, if you use one, before loading the shell-ctx hook.

### Bash
Bash plugin-argument completion requires Bash 4+ and an existing upstream
`kubectl` completion registration. Normal shell-ctx operation has no new Bash
version requirement. shell-ctx does not install or source kubectl completion
for you.

Add the following to `~/.bashrc` in this order (using your usual upstream
kubectl-completion setup):

```sh
export KUBECONFIG=/path/to/config       # optional
source <(kubectl completion bash)       # load upstream kubectl completion
# Declare supported aliases here; see "Aliases" below.
eval "$(kubectl-shell_ctx hook bash)"
```

### Zsh
Zsh plugin-argument completion requires upstream `kubectl` completion to be
loaded first. Initialize completion before the hook; shell-ctx does not invoke
`compinit` or otherwise configure upstream kubectl completion.

Add the following to `~/.zshrc` in this order (using your usual upstream
kubectl-completion setup):

```sh
export KUBECONFIG=/path/to/config       # optional
autoload -Uz compinit
compinit
source <(kubectl completion zsh)        # load upstream kubectl completion
# Declare supported aliases here; see "Aliases" below.
eval "$(kubectl-shell_ctx hook zsh)"
```

### Fish
The Fish hook installs completion for `kubectl shell-ctx` directly. It does not
require upstream Fish kubectl completion, and coexists with it when present.
Add the following to `~/.config/fish/config.fish` after any custom
`KUBECONFIG` setting:

```fish
set -x KUBECONFIG /path/to/config       # optional
kubectl completion fish | source        # optional upstream completion
kubectl-shell_ctx hook fish | source
```

### Aliases
Automatic alias completion is supported only in Bash and Zsh. Declare the
alias before evaluating the shell-ctx hook, and make it expand exactly to
`kubectl shell-ctx` (whitespace variation is allowed):

```sh
alias kctx='kubectl shell-ctx'
eval "$(kubectl-shell_ctx hook bash)"
```

Aliases with added flags, wrappers, or chained commands are not supported, nor
are aliases declared after the hook or aliases to `kubectl-shell_ctx`. Fish
alias functions and aliases are not discovered automatically.

## Usage
  `kubectl shell-ctx` Select context; Use arrow-keys or start typing to search  
  `kubectl shell-ctx clone` Clone context; Use arrow-keys or start typing to search  
  `kubectl shell-ctx <context>` Switch directly to context  
