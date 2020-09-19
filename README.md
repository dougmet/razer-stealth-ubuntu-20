# Razer Stealth on Ubuntu 20.04

> It ain't easy peasy

## Which Razer?

I've got a Razer Blade Stealth, late 2019, NVIDIA GTX 1650, 10th gen i7, 1080p screen.

## Which Ubuntu?

I've found it works on 19.04 upwards. There's some kernel things that 18 doesn't have that proved to be a deal breaker. This guide is 20.04 which I'll probably stick with as the LTS versions tend to get a lot of the packages that I'm interested in.

# Ordered List of Issues/Fixes

## 1. NVIDIA Drivers

I'd put the proprietary drivers on. I had some issues with not waking from sleep and other things that putting NVIDIA's drivers on, instead of the noveau thing, seemed to solve.

1. Go to the "Software and Updates" program in the GUI
2. Click additional drivers
3. Find a driver version that works with your card. For me it was the **nvidia-driver-435**. I checked on the NVIDIA website as to which drivers were appropriate.
4. Click install. Restart etc.

## 2. Wake from Sleep

For me, whenever the laptop goes to sleep there was no way to bring it back other than a hard reset. I fixed this from these instructions:

https://askubuntu.com/questions/1207156/ubuntu-19-10-on-razer-blade-after-wake-up-laptop-automatically-suspends

```sh
sudo vim /etc/default/grub
```

Then change thenline `GRUB_CMDLINE_LINUX_DEFAULT=""` to

```
GRUB_CMDLINE_LINUX_DEFAULT="button.lid_init_state=open"
GRUB_CMDLINE_LINUX="button.lid_init_state=open"
```

Quit out and run

```sh
sudo update-grub
```


