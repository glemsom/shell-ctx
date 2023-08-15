# shell-ctx
Kubernetes context switcher for shells.  
With shell-ctx each shell will operate in its own isolated Kubernetes context.

### Supported shells
Bash, Zsh and Fish


## Installation
`sudo curl https://raw.githubusercontent.com/glemsom/shell-ctx/main/kubectl-shell_ctx -o /usr/local/bin/kubectl-shell_ctx`  
`sudo chmod +x /usr/local/bin/kubectl-shell_ctx`

## Setup
For BASH, append the following to your ~/.bashrc  
  `eval "$(kubectl shell-ctx hook bash)"`

For ZSH, append the following to your ~/.zshrc  
  `eval "$(kubectl shell-ctx hook zsh)"`

For FISH, append the following to your ~/.config/fish/config.fish  
  `kubectl shell-ctx hook fish | source`

## Usage
  `kubectl shell-ctx` Use search or arrow-keys to select context
