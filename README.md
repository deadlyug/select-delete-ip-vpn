# select-delete-ip-vpn
This is tools for managing pptp client, connect with spesific address.

## Install pptp client

### Arch Base
`sudo pacman -S pptpclient`

### Debian Base
`sudo apt-get install pptp-linux`

## Install net tools

### Arch Base
`sudo pacman -S net-tools`

### Debian Base
`sudo apt-get install net-tools`

## Setup pptp tunnel
`sudo pptpsetup --create myVPN --server vpn.example.com --username alice --password foo --encrypt`

## Clone repo
`git clone https://github.com/deadlyug/select-delete-ip-vpn.git`
 
you can copy the scripts to bin folder or make link to bin folder

### Give execute permission to the scripts
```
cd select-delete-ip-vpn
chmod +x delIpVPN selectIpVPN
```

### copy to bin forder
```
sudo cp delIpVPN selectIpVPN /usr/local/bin
```

### link to bin folder
```
sudo ln -s $(pwd)/selectIpVPN $(pwd)/delIpVPN /usr/local/bin/
```

### Troubleshoot

#### - Cannot find ppp0
cek if tunnel works `sudo pon myVPN`, if error, you have troubleshoot the error base in your error you get. 

#### - Solution if get errot "cannot load ppp_generic module"
edit the /etc/modprobe.d/modules.conf file and change
```
alias char-major-108 ppp
```
to
```
alias char-major-108 ppp_generic
```
or just add such alias if it does not exist.<br>
The correct module will be loaded after reboot.

ref : https://wiki.archlinux.org/title/Ppp#pppd_cannot_load_kernel_module_ppp_generic
