ngxbrew
=======

[nginx](http://nginx.org/) install manager.

# Intall

Using curl one liner.

    $ curl https://raw.github.com/nyarla/ngxbrew/master/ngxbrew | perl - setup

or Download and setup.

    $ wget https://raw.github.com/nyarla/ngxbrew/master/ngxbrew
    $ perl ngxbrew setup

Add PATH env value your shell dotfile, eg: .bashrc or .zshrc

    export PATH=${HOME}/.ngxbrew/bin:${PATH}

And reload dotfiles.

# `NGXBREW_ROOT`

`NGXBREW_ROOT` env value can chagne ngxbrew's install directory.
default is `${HOME}/.ngxbrew`;

    export NGXBREW_ROOT=~/local/nginx

# Intall NGINX

install command exmaple:

    $ ngxbrew install 1.2.1 2012-01-01 \
        --enable="{module.name}" \
        --disable="{module.name}"
        --module="{extra.module}"
        --configure="--conf-path='/path/to/conf'"
    $ ngxbrew use 2012-01-01

You can do nginx core module enable or disable using an `--enable`
or `--disable` option.

These options are pass to `./configure` as `--with(out)?-{module.name}_module`.

And you can specify `./configure` options by `--configure` option.

# Adding and Installing 3rd party module

   $ cd ~/.ngxbrew/modules
   $ git clone git://github.com/arut/nginx-dav-ext-module.git
   $ ls -F
   nginx-dav-ext-module/ yet-another-nginx-module/

   $ ngxbrew install 1.2.1 --module="nginx-dav-ext-module,yet-another-nginx-module"


# Command

    $ ngxbrew help
    ngxbrew $VERSION
    
    Usage:
        ngxbrew help
        ngxbrew version
    
        ngxbrew install <version> <name>
        ngxbrew uninstall <name>

        ngxbrew use <name>
   
        ngxbrew list
        ngxbrew ls
        ngxbrew ls-remote
        
        ngxbrew buildargs <name>
    
        ngxbrew clean <version> | all
       
        ngxbrew selfupdate
    
     Example:
        ngxbrew install 1.2.1 default \
            --enable="http_dav_module" \
            --modules="ngx_dav_ext_module"

        ngxbrew use default
