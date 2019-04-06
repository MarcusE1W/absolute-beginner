+++
title = "Manjaro ARM on Pinebook"
date = "2019-02-02"
hide_authorbox = false
disable_comments = false
categories = ["Pinebook"]
tags = ["Manjaro"]
aliases = [""]
draft = true
+++

Feb 2019 review of Manjaro on Pinebook

<!--more-->



# Let's start

## Installation

## Works out of the box

## Errate

- Local settings dot no persist
- Sound widget in Panel seems not to work. After you select the mixer in the Panel  you can change the volumen there
- Display brightness cannot be changed with anything than the LXQt Widget.

  lxqt-config-brightness output:
     (0xffffe8317da8) Debug: No outputs have backlight property
     (0xffffe8317da8) Debug: Found output: "eDP-1"
     (0xffffe8317da8) Debug: Output: "eDP-1" added
     (0xffffe8317da8) Debug: Found output: "HDMI-1"
     (0xffffe8317da8) Debug: Output is not connected

- Icons in the Taskmanager are not centered whereas the icosn in the QuickLauncher are.
- sometimes the system just freezes, occasionally in small steps -> rans out of memory ?
- suspend does not really wake up. it first shows the screen but then the display becomes dark and stays dark .. ?
- .config/lxqt/session: one entry has environment spellt wrongly
- dmesg error: sun50i-de2-bus 1000000.de2: Error couldn't map SRAM to device
  Seems to be related to this device tree code (29/12/2017)
  ``` C
   + if (sunxi_de2_clk_has_sram(pdev->dev.of_node)) {
   + ret = sunxi_sram_claim(&pdev->dev);
   + if (ret) {
   + dev_err(&pdev->dev,
   + "Error couldn't map SRAM to device\n");
   + return ret;
   + }
  Another code snippet: (16/03/2018)
  ```
  
  ``` C
   + static int sun50i_de2_bus_probe(struct platform_device *pdev)
   + {
   +	 struct device_node *np = pdev->dev.of_node;
   +	 int ret;
   +
   +	 ret = sunxi_sram_claim(&pdev->dev);
   +	 if (ret) {
   +		dev_err(&pdev->dev, "Error couldn't map SRAM to device\n");
   +		return ret;
   +	 }
   +
   +	 if (np) 
   +		of_platform_populate(np, NULL, NULL, &pdev->dev);
   +
   + 	return 0;
  ```

# Fine tuning
- [Solved] Some LXQt widgets cannot be added to the Panel at all Sysinfo etc..
	- > add `libstatgrab` to get cpu monitor working
	- > add `libsysstat` to get system statistics
- Moving windows with the mouse can be very slow. The Graphic creates a tail effect.
  - Termite is super fast
  - File manager is so so
  - Emacs looks very strange
  - Firefox is super super slow
	-> `compton` helps
	