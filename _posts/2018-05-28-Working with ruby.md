## Intro

I think that programming environments should never be installed as root, unless there is no alternative.
Cases in point are ruby and nodejs (having different versions which need to remain separately available). 
Since each of these languages are really ecosystems with lots of related tools, switching versions often introduces difficult bugs.
So: no root installs for these tools.

For ruby, I have not really been happy with the shell modifying tools, but I did not find better:
- using a docker image might be nice, but there are problems with user permissions (e.g. mounting a volume gives root rights from the image to the host!)
- maybe lxd might be better, but I didn't find easily how to manage all the system resources.

## Installation of rvm

[RVM can be found here](https://github.com/rvm) along with tools such as an ansible playbook. 
Intallation for ubuntu goes as follows:
```shell
sudo apt-get install rvm
usermod -a -G rvm $USER
#following is needed! otherwise `rvm use xx` fails
sudo apt update
```

It is easiest to reboot/log-out the machine now, to ensure that /etc/profile.d/rvm.sh is sourced.

## Installation of ruby environment

```
rvm install ruby
rvm alias create default ruby-2.4.1
#the next command fails in gui, and requires 'bash --login' first. Alternatively, quit GUI and do the cmd in console, then startx again 
rvm use default
```



