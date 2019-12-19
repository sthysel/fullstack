# LABStack (Version 0.0.1)

Raspberry Pi 4.0 running Arch ARM with a predominantly docker hosted stack of
usefull LAB IIOT Tools. 

- ansible is used to prep the pi for docker and keep things tight
- dotfiles to keep the pi env sane
- docker-compose is used to maintain the service stack

LABStack running on server `labstack` provides

| Service   | Description                    | Port or URL          |
|-----------|--------------------------------|----------------------|
| portainer | Container management           | http://labstack:9000 |
| mqtt      | MQTT Broker                    | 1883                 |
| influx    | Time series database           | 8086/8083/2003       |
| telegraf  | System metrics harvester       |                      |
| grafana   | Time series data visualization | http://labstack:3000 |


## Prep SD card

From
[Archlinux|ARM](https://archlinuxarm.org/platforms/armv8/broadcom/raspberry-pi-4)
install Arch on SD Card.


## Bootstrap the basics on the pi

Boot the pi, find it on the local LAN `$ nmap -sn 10.0.0.1/24`, its called
`alarmpi`, user `alarm`, root password is `root`, change if so inclined.

ssh to `alarmpi`

 - make a user, say `thys`
 - add `thys` to wheel using `visudo`

Like so:

```
# pacman -Syyu
# useradd -G wheel -m thys
# pacman -S sudo vim
# visudo
```

## Run ansible over pi

In the `ansible` run `play $PI_IP`
