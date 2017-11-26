## How to configure WiFi network connection

1. Add to `/etc/wpa_supplicant/wpa_supplicant.conf` WiFi credentials

```
network={
  ssid="<my-SSID>"
  psk="<my-passphrase>"
}
```

or if you want to use some encrypted password:

`$> wpa_passphrase "my-SSID" "my-passphrase"`

and use the output for the *psk* value

```
network={
  ssid="<my-SSID>"
  psk=<abcdefghilmnopqrstuvz123456789......>
}
```

2. Reconfigure your interface

`$> wpa_cli -i wlan0 reconfigure`

3. Add to `/etc/network/interfaces.d` the following lines

```
allow-hotplug wlan0
iface wlan0 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```
