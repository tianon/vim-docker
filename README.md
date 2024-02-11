# vim-docker

This was previously a mirror of [github.com/docker/docker/contrib/syntax/vim](https://github.com/docker/docker/tree/master/contrib/syntax/vim), but in [docker/docker@5511f45](https://github.com/moby/moby/commit/5511f45767e78b136c292dbb989296fb6e4d12fc), that entire directory was deprecated in favor of `ftplugin/dockerfile.vim` and `syntax/dockerfile.vim` in [github.com/vim/vim](https://github.com/vim/vim), which is then also part of the popular Vim fork, [github.com/neovim/neovim](https://github.com/neovim/neovim).

The [`docker` branch](https://github.com/tianon/vim-docker/commits/docker) contains the old Docker-based commit history.

The [`neovim` branch](https://github.com/tianon/vim-docker/tree/neovim) and the [`vim` branch](https://github.com/tianon/vim-docker/tree/vim) contain the new (Neo)Vim-based commit history (and are now the useful ones to include/use via vim-pack, etc; [compare `vim..neovim`](https://github.com/tianon/vim-docker/compare/vim..neovim)).

The [`tianon` branch](https://github.com/tianon/vim-docker/tree/tianon) contains my personal fork of the `vim` branch with some minor changes (which I'd normally try to contribute back upstream, but [...](https://twitter.com/tianon/status/1258463662357876736)).
