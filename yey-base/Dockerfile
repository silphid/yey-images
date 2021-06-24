FROM ubuntu:bionic
SHELL ["/bin/bash", "-c"]

# make /bin/sh point to bash (instead of the default dash)
RUN ln -sf bash /bin/sh

#
# various helpful shell tools
#
RUN apt-get update && \
    apt-get upgrade -y bsdmainutils curl dnsutils gcc gettext git gnupg groff iproute2 iputils-ping jq man-db \
      manpages manpages-posix netcat unzip uuid-runtime vim wget

#
# zsh
#
# zsh is a shell designed for interactive use, although it is also a powerful scripting language.
# Many of the useful features of bash, ksh, and tcsh were incorporated into zsh; many original
# features were added.
#
# https://zsh.sourceforge.io/
#
RUN apt-get install -y zsh

#
# oh-my-zsh
#
# Oh My Zsh is a delightful, open source, community-driven framework for managing your Zsh
# configuration. It comes bundled with thousands of helpful functions, helpers, plugins, themes,
# and a few things that make you shout... "Oh My ZSH!"
#
# https://ohmyz.sh/
#
RUN apt-get install -y powerline fonts-powerline && \
    sh -c $(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh) && \
    git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh && \
    git clone https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k && \
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git "$HOME/.zsh-syntax-highlighting" --depth 1

#
# gh
#
# cli to manage github repositories
#
# https://cli.github.com/
#
RUN APT_KEY_DONT_WARN_ON_DANGEROUS_USAGE=1 apt-key adv --keyserver keyserver.ubuntu.com --recv-key C99B11DEB97541F0 && \
    apt-get install -y software-properties-common && \
    apt-add-repository https://cli.github.com/packages && \
    apt-get update && \
    apt-get install gh

#
# gomplate
#
# template renderer leveraging the golang templating syntax and supporting a growing list of
# datasources (ie: JSON, YAML, AWS EC2 metadata, Hashicorp Vault secrets...)
#
# https://docs.gomplate.ca/
#
ARG GOMPLATE_VERSION=3.7.0
RUN curl -fsL --output /usr/local/bin/gomplate -sSL https://github.com/hairyhenderson/gomplate/releases/download/v$GOMPLATE_VERSION/gomplate_linux-amd64 && \
    chmod +x /usr/local/bin/gomplate

#
# tldr
#
# cli to display tldr-pages, a collection of community-maintained help pages for command-line
# tools, that aims to be a simpler, more approachable complement to traditional man pages.
#
# https://github.com/tldr-pages/tldr
#
RUN curl -o /usr/local/bin/tldr https://raw.githubusercontent.com/raylee/tldr/master/tldr && \
    chmod +x /usr/local/bin/tldr && \
    tldr -u

# finalize
COPY files/ /
ENV PATH="/root/bin:$PATH"
CMD ["zsh"]
