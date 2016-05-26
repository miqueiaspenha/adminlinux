Editar o arquivo /etc/rc.local

```
sudo nano /etc/rc.local
```

colocar antes de exit 0

```
#Bloquear o bluetooth
rfkill block bluetooth

#Setar valor de brilho default
echo 300 > /sys/class/backlight/intel_backlight/max_brightness
