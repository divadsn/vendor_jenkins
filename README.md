# vendor_jenkins
Bunch of useful build scripts and tools I use on my Jenkins setup.

### To setup build environment

Firsly, install `git`, using whatever package manager has.

Then, run the command below:

```bash
git clone https://github.com/divadsn/vendor_jenkins
```

To run it with Jenkins, add following commands in your job to be executed in shell:

```bash
#!/bin/bash
export SERVER_NB_COMPILE=2
export ANDROID_JACK_VM_ARGS="-Xmx8g -Dfile.encoding=UTF-8 -XX:+TieredCompilation"
prebuilts/sdk/tools/jack-admin kill-server && rm -rf ~/.jack*

export JENKINS_HOME=$HOME/Jenkins
source $JENKINS_HOME/tools/build-scripts/build-*.sh
```

Change `JENKINS_HOME` to the directory where your workspace is stored.

If running Arch Linux, please enable multilib, and install yaourt, before running the script.
Please choose the name dependending on the distro you have.

Enjoy!


### Customise kernel's version string

For details, please refer to [this article over at tjworld.net](http://tjworld.net/wiki/linux/kernel/build/customiseversionstring)

The three scripts are placed in `utils`. Once copied into their respective locations they should be given executable permissions:

```bash
sudo cp utils/whoami /usr/local/bin/
sudo cp utils/hostname /usr/local/bin/
sudo cp utils/gcc /usr/local/sbin/
sudo chmod a+x /usr/local/bin/whoami /usr/local/bin/hostname /usr/local/sbin/gcc
```

Create the custom value files in the user home directory:

```bash
echo "jenkins" > $HOME/linux-compile-by
echo "build" > $HOME/linux-compile-host
```

With the scripts installed and configured all that is left is to do a kernel build as usual. If necessary, remove the existing include/generated/compile.h before starting the build.

### Repo package installation

The `repo` binary is already available in `utils`, just install it by typing following commands:

```bash
sudo cp utils/repo /usr/local/bin/
sudo chmod a+x /usr/local/bin/repo
```
