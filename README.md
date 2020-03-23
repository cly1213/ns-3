# ns-3

Following:

https://www.nsnam.org/docs/release/3.30/tutorial/html/getting-started.html#downloading-ns-3-using-git

## ns-3.30 installation in Ubuntu 18.04

### Install ns-3 visualization

As For Ubuntu 18.04, python-pygoocanvas is no longer provided. The ns-3.29 release and later upgrades the support to GTK+ version 3, and requires these packages:

```=bash
sudo apt-get install gir1.2-goocanvas-2.0 python-gi python-gi-cairo python-pygraphviz python3-gi python3-gi-cairo python3-pygraphviz gir1.2-gtk-3.0 ipython
```

### test

```=bash
./waf --pyrun src/flow-monitor/examples/wifi-olsr-flowmon.py --visualize
```
![image](https://github.com/cly1213/ns-3/blob/master/test.png)

## Congratulations! You are now an ns-3 user!
