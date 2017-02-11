---
layout: post
#author: FW
title: "How to check hard drive health in Linux"
date: 2017-01-17 13:33:33 +0200
image: http://placekitten.com/740/150"
categories: coding
tag: linux
---
There are several ways to check the hard drive health in linux. All newer hard drives support S.M.A.R.T. and can be checked quite simple. Many tools are available in your distributions package manager, but the most known is smartmontools.

# smartmontools
~~~
sudo smartctl -a /dev/sda | less
~~~
This should output something like this.
~~~
tbd
~~~
If not, you can run
~~~
sudo smartctl -s on -a /dev/sda
~~~
and initialize a first health check.



# badblocks
~~~
sudo badblocks -nsv /dev/sda
~~~
Now telling the filesystem not to use the bad blocks anymore.
~~~
sudo fsck -vcck /dev/sda
~~~
