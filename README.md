# EthereumSystemd
Scripts to auto launch a proxied ethereum miner on boot with Systemd


### Setup

- Install and configure Eth-Proxy: https://github.com/Atrides/eth-proxy

- Place or symlink the `*.service` files into `/etc/systemd/system`
- Configure `eth-proxy.serivce` with the location of eth-proxy
- Configure `eth-miner.serivce` with your username and name of miner:

      WorkingDirectory=/home/your-username/
      ExecStart=/bin/bash --login -c "ethminer -G --farm-recheck 200 -F http://127.0.0.1:8080/Name-of-rig-here"
 - encourage Systemd to see the new files: `sudo systemctl daemon-reload`
 - tail the logs in another tab: `sudo journalctl -f`
 - Start proxy: `sudo systemctl start eth-proxy.service`
 - Start miner: `sudo systemctl start eth-miner.service`

Services also respond to `stop`

### View logs

All logs go to Journal, to tail the logs run: `sudo journalctl -f`
