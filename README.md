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
**If you are setting a custom KUBECONFIG you need to load the shell hook AFTER your KUBECONFIG variable is set**

For BASH, append the following to your ~/.bashrc somewhere after your `KUBECONFIG` variable  
  `eval "$(kubectl shell-ctx hook bash)"`

For ZSH, append the following to your ~/.zshrc somewhere after your `KUBECONFIG` variable    
  `eval "$(kubectl shell-ctx hook zsh)"`

For FISH, append the following to your ~/.config/fish/config.fish somewhere after your `KUBECONFIG` variable    
  `kubectl shell-ctx hook fish | source`

## Usage
  `kubectl shell-ctx` Use search or arrow-keys to select context
