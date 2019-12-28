# Setup Xdebug

1. install xdebug according to [install xdebug](https://xdebug.org/docs/install)
2. make sure xdebug.remote_host, xdebug.remote_port and xdebug.remote_enable are set in php.ini [xdebug configuration](https://xdebug.org/docs/remote)
3. in PhpStorm set preferences>Language>Php>debug port accordingly
4. in PhpStorm set preferences>Language>Php>Server
   - server address
   - path mapping of root (for local symfony server local directory is same as server directory)
5. in PhpStorm add run configuration (PHP Remote Debug -> no special settings needed)
6. Start/Enable xdebug in Browser and PhpStorm
