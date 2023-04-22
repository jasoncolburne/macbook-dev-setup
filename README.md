# macbook-dev-setup
my preferred setup. only works on a new macbook. assumes you want to use `Terminal` (I know everyone loves iTerm2 - maybe I'll add support for that in the future).

## Instructions

1. Install basic tools like git and curl:

```sh
xcode-select --install
```

2. Set up a colorful alias for ls:

```sh
echo "alias ls='ls -G'" >> ~/.zshrc
```

3. Install [fonts](https://github.com/romkatv/powerlevel10k#manual-font-installation) and [prompt](https://github.com/romkatv/powerlevel10k#manual).

Alternatively, you may wish to install powerlevel10k under a `github.com` directory to organize things a bit:

```sh
mkdir -p ~/github.com/romkatv
cd ~/github.com/romkatv
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git
echo 'source ~/github.com/romkatv/powerlevel10k/powerlevel10k.zsh-theme' >> ~/.zshrc
exec zsh
```

3. After you configure your prompt, in `Terminal`, check out this repository:

```sh
mkdir -p ~/github.com/jasoncolburne
cd ~/github.com/jasoncolburne
git clone --depth=1 https://github.com/jasoncolburne/macbook-dev-setup.git
```

4. Import `Developer.terminal` by going to `Terminal` settings, `Profiles` tab.

5. Generate `ssh` keys.

```sh
ssh-keygen -t ed25519 -C "your_email.your_domain.com"
eval "$(ssh-agent -s)"
echo "Host github.com" >> ~/.ssh/config
echo "  AddKeysToAgent yes" >> ~/.ssh/config
echo "  UseKeychain yes" >> ~/.ssh/config
echo "  IdentityFile ~/.ssh/id_ed25519" >> ~/.ssh/config
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub | pbcopy
```

In github navigate to your personal settings and add a new ssh key by pasting what's already in your buffer (via the `pbcopy` command above).

