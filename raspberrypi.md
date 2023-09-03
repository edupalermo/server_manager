# Raspiberry PI Configuration

## Configuring wireless network


File:  `/etc/wpa_supplicant/wpa_supplicant.conf`

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
