Deploy multiple testnets on a single host


Run the following commands from Terminal:

    # -p number of nodes containing Producers (each node can serve 0 or multiple Producers)
    # -n number of nodes (each node forms a testnet)
    # --producers total number of producers
    # Right here, we want to have 2 nodes and both of them contain producers (totally 4 producers)
    # Besides the normal nodeos, there is always the bios nodeos
    # Network topology is "mesh" (or can be changed to "star")
    # The -o option will cause to generate the network file
    eosio-launcher -n 2 -p 2 --producers 4 -s mesh --network-name trung_net -o my_testnet.json


    # After running this cmd, a folder called "staging" is generated.
    # It contains all config.ini and genesis.ini files for each node
    # Please edit the config.ini files for adapting the http-server-address so that it can reached externally
    # Otherwise, only localhost is used


    # Run this cmd with the generated network file
    # This will start up the node daemons and also execute the boot sequence
    eosio-launcher --shape my_testnet.json --boot --force --nogen


    # Run this cmd to check if nodeos daemons are really running or not
    ps aux | grep nodeos
