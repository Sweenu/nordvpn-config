# nordvpn-config
A PKGBUILD that simplifies NordVPN installation and usage on archlinux.

## Install
```bash
git clone https://github.com/Sweenu/nordvpn-config
cd nordvpn-config
makepkg -ic
```
This will install every NordVPN config files under /etc/openvpn/client with
simpler names and with the .conf extension in order to be easily used with systemd.

Then setup the credentials in the login.key file:
```bash
sudoedit /etc/openvpn/client/login.key
```
Fill with the following content:
```
your_nordvpn_username
your_nordvpn_password
```
Don't forget to properly setup permissions:
```
sudo chmod 600 /etc/openvpn/client/login.key
```

## Usage
Start and stop the VPN with:
```bash
systemctl start openvpn-client@<config-file>
systemctl stop openvpn-client@<config-file>
```
where `config-file` is of the form region.protocol (e.g. us754.tcp).

To make the VPN persistent across reboots:
```bash
systemctl enable openvpn-client@<config-file>
```
