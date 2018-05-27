## About apt

- apt policy *pkg*

  This shows the installed version of *pkg*
  
- test



# About LXDE

[About customization](https://www.addictivetips.com/ubuntu-linux-tips/customize-the-lxde-desktop/)

- Selecting Themes

A simple tool to choose better theme (I like Breeze-ob)
```
sudo apt install obconf
```

- Install other icons

Icon themes take around 100MB.
If you have access to the icon-theme file (xxx.tar.gz), then you can untar it in folder ~/.icons  
Then start Preferences -> Look and Feel -> Select icon-theme -> Apply

Some icon sets are available through launchpad
```
sudo add-apt-repository ppa:moka/daily
sudo apt-get update
sudo apt-get install moka-icon-theme
```


