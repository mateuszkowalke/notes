# I3wm

### Brightness control

For ubuntu 20.04.
```bash
sudo apt install light

sudo chmod +s /usr/bin/light
```
And config is:
```
bindsym XF86MonBrightnessUp exec light -A 1 # increase screen brightness
bindsym XF86MonBrightnessDown exec light -U 1 # decrease screen brightness
```