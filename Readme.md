# Vagrant Deb Cache

This vagrant machine is a deb cache, implemented using `squid-deb-cache`.

When this vagrant machine is running on your network, any client with `squid-deb-cache-client` installed will discover the proxy via `zeroconf` and send all requests for debs through it. The debs are cached on the proxy using squid.

## Usage

To build and start the VM that runs the cache:

    $ vagrant up

On each client you want to use the cache:

    $ apt-get install -y squid-deb-cache

Each client needs to be on the same network as the VM with the cache. I do this by keeping them both on a private host-only VirtualBox network.

## Security

Note that I've removed the default limitation to only allow downloads from a set list of sites. This proxy can be used to access any web URL.

## Author

Aidan Nagorcka-Smith (aidanns@gmail.com)

## License

MIT.