# vendor_jenkins
Bunch of useful build scripts and tools I use on my Jenkins setup.

## To setup build environment

Firsly, install `git`, using whatever package manager has.

Then, run the command below

```bash
git clone https://github.com/divadsn/vendor_jenkins
```

To run it with Jenkins, add following commands in your job to be executed in shell

Change `JENKINS_HOME` to the directory where your workspace is stored

```bash
#!/bin/bash
export SERVER_NB_COMPILE=2
export ANDROID_JACK_VM_ARGS="-Xmx8g -Dfile.encoding=UTF-8 -XX:+TieredCompilation"
prebuilts/sdk/tools/jack-admin kill-server && rm -rf ~/.jack*

export JENKINS_HOME=$HOME/Jenkins
source $JENKINS_HOME/tools/build-scripts/build-purenexus.sh
```

Enjoy!
