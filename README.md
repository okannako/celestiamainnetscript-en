<img width="2752" height="1536" alt="celestia3" src="https://github.com/user-attachments/assets/25d320aa-d8f5-4b67-950c-e55e0a2583df" />

You can install a Validator, Fibre, Bridge and Light Node on Celestia Mainnet Beta by running the command below. The script is based on the current releases (celestia-app v10.5.0, celestia-node v0.34.4). Along with the other details, this script lets you complete the setup in a very short time.

NOTE: The Full Storage Node type has been removed from celestia-node. If you want to keep all data, run a Bridge Node with --archival.

```
curl -s https://raw.githubusercontent.com/okannako/celestiamainnetscript-en/refs/heads/main/nodescript.sh > nodescript.sh && chmod +x nodescript.sh && ./nodescript.sh
```

### Enabling bbr (Required)
- The script does this automatically during the Validator setup. If you installed a Bridge or Light Node, or want to check it, run the commands below.
```
cd $HOME/celestia-app
make bbr-enable
make bbr-check
```

- If you get an error with the commands above, you can enable it with the commands below.
```
sudo modprobe tcp_bbr
echo "net.core.default_qdisc=fq" | sudo tee -a /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

- To check that it is active, run the command below. The result should be `bbr`.
```
sysctl net.ipv4.tcp_congestion_control | awk '{print $3}'
```

If you have any questions during or after setup, you can reach me via Telegram, Mail or Discord.
