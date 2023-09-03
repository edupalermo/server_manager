# Raspiberry PI Configuration

## Configuring wireless network

### File /etc/wpa_supplicant/wpa_supplicant.conf
```conf
country=DE
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
network={
  ssid="FRITZ!Box 7530 SR"
  scan_ssid=1
  psk="35161372369399590049"
  key_mgmt=WPA-PSK
}
```

### File /lib/systemd/system/wpa_supplicant.service
```
ExecStart=/usr/sbin/wpa_supplicant -Dwext -u -s -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
```

### Reload systemd manager configuration and restart wap_supplicant daemon
```bash
systemctl daemon-reload
systemctl restart wpa_supplicant
```

## Installing Grafana
```
apt-get install -y apt-transport-https software-properties-common wget
wget -q -O /usr/share/keyrings/grafana.key https://apt.grafana.com/gpg.key
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
apt update
apt install grafana
systemctl daemon-reload
systemctl enable grafana-server.service
```
Now grafana can be accessed on the address http://<host>:3000.
