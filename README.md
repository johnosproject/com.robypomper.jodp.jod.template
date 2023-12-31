# JOD Distribution TEMPLATE

**Source Code project of the JOD Distribution TEMPLATE.**

* Current version: 1.0.3</td></tr>
* References: [JOD_Dist_TEMPLATE @ JOSP Docs](href="https://www.johnosproject.org/docs/references/jod_dists/jod_dist_template/)
* Repository: [com.robypomper.josp.jod.template @ Bitbucket](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/)
* Downloads: [com.robypomper.josp.jod.template > Downloads @ Bitbucket](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/)

The **JOD Distribution TEMPLATE is the starting point for Makers to generates custom JOD Distributions**. Generated distributions can be executed by end users on their local machine, deployed on remote objects or shared with other users.
*A JOD Distribution, once executed, represent an IoT Object for the [John O.S. Platform](https://www.johnosproject.org/docs/index.html) Ecosystem.* During JOD Distribution TEMPLATE's configuration, makers can customize object's structure and any other config of the [John Object Daemon](https://www.johnosproject.org/docs/references/josp/jod/). <br>
Once the JOD Distribution is installed on desired location (machine/path), it becomes a JOD instance that represent a [JOSP Object](https://www.johnosproject.org/docs/what/IoT%20Components/Object).

![JOD Distribution TEMPLATE LifeCycle diagram](docs/JODDistTMPL_Overview.png "JOD Distribution TEMPLATE LifeCycle")

With JOD Distribution TEMPLATE makers can:

* Customize object's info, configs and structure
* Choose the JOD versions to include in the distribution
* Add custom firmware files
* Build JOD distributions via Bash and PowerShell scripts
* Include in JOD distributions:
  * JOD Instance's management scripts via Bash and PowerShell
  * Custom Pre/Post scripts on management scripts

At [JOD Distributions list](https://www.johnosproject.org/docs/references/jod_dists/) page of the JOSP Docs, you can find many ready-to-use JOD Distributions. Depending on what you would integrate to the JOSP EcoSystem as an Object, maybe there is already a JOD Distribution for your needs. Otherwise, use them as examples for your custom JOD Distribution.<br>
*To publish your own distribution on this list, please contact us at [tech@johnosproject.com](mailto:tech@johnosproject.com).*

### JOD Distribution Life-cycle

From the JOD Distributions TEMPLATE source code (this project) to an operative JOSP Objects there are few steps performed by 3 different actors.

![JOD Distribution TEMPLATE LifeCycle diagram](docs/JODDistTMPL_LifeCycle.png "JOD Distribution TEMPLATE LifeCycle")

First, there is the **JOSP Developer** (or any maintainer of this project) that would build, test, improve and then publish this project's artifacts. All JOD Distribution TEMPLATES artifacts are public available at [Downloads @ Bitbucket](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/). <br>
Then **Makers** can download and extract it. The resulting folder will be the project dir for a new custom JOD Distribution. So Makers can configure their own JOD Distribution simply updating extracted files. For more info check the README.md file in extracted dir or (at this [link](src/tmpl/resources/README.md)). Once, it's ready, Maker can build and publish his own JOD Distribution. <br>
Finally, the **End User**, who received built JOD Distribution, can copy it on his PC or deploy it on a remote machine (like a RaspberryPi). At this point, a JOD Distribution can be installed as a background service/daemon (managed by the guest OS). Otherwise, it can be executed as a foreground command that expose a shell to interact with running JOD Instance.

**NB!:** the JOD Distribution TEMPLATE support Linux, MacOS and Windows, and it's agnostic along all those steps.<br>
In other worlds, any actor can perform any steps with his favourite OS. Then, following steps can still be executed by other actors using different OS. That's always true except for JOD Distribution configuration steps, because Makers can add scripts, executables or other resources that are OS dependant. Each JOD Distribution must specify in his README.md file which OS can support.

For each phase, this project provides different commands to automate his management:

* **Development:** this phase can be handled with [Gradle project](docs/gradle/gradle.md)'s tasks like ```buildTMPL``` or ```publishTMPL``` to build or publish JOD Dist TMPL artifacts.
* **Customization:** Makers can use [JOD Template Commands](docs/tmpl/tmpl.md) contained in ```$JOD_Custom_DIR/scripts``` dir. Those scripts help maker to build, test, install and publish their own JOD Distriubutions.
* **Usage:** Each JOD Distribution includes the [JOD Distribution Commands](docs/dists/dists.md). End User can execute those commands to manage (start/stop, install/uninstall) current JOD installation.

----

## Getting started

### Requirements

The JOD Distribution TEMPLATE support Linux, MacOS and Windows operating systems. The gradle wrapper support by himself all operating systems. On other hands JOD Template and JOD Distribution Commands can be executed as Bash (for Linux and MacOS) or Powershell (for Windows) scripts. Moreover, artifacts are OS independent, so you can build the JOD Distribution TEMPLATE on a MacOS, then build a custom distribution on a Linux and finally execute resulting JOD instance on Windows.

Other software are required by JOD Distribution TEMPLATE:

Linux reuirements:
* Java Runtime Environment (prefered java version 8)<br>
  ```sudo apt install default-jdk```
* curl<br>
  ```sudo apt install curl```
* zip (optional)<br>
  ```sudo apt install zip```

Mac requirements:
* Java Runtime Environment (prefered java version 8)<br>
  (Download and install it from [java.com](https://www.java.com/download/ie_manual.jsp))

Windows reuirements:
* Java Runtime Environment (prefered java version 8)<br>
  (Download and install it from [java.com](https://www.java.com/download/ie_manual.jsp))
* Enable powershell scripts execution<br>
  (More inf at [microsoft](https:/go.microsoft.com/fwlink/?LinkID=135170)<br>
  ```Set-ExecutionPolicy -ExecutionPolicy remotesigned -Scope CurrentUser```

### Build JOD Distribution TEMPLATE

First lets **build the JOD Distribution TEMPLATE**. This project includes a
Gradle config that provide the ```buildTMPL``` task. Execute that task to
assemble and generate the JOD Distribution TEMPLATE:

```shell
$ ./gradlew buildTMPL
```

Once executed, you can find assembled JOD Distribution TEMPLATE in the
```build/assemble/$JOD_TEMPL_VER``` dir, or in the ```build/publications```
folder as distributable files. Alternatively, you can download published
JOD Distribution TEMPLATE at [Repository > Downloads @ Bitbucket](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/). Visit
that page to list all available versions and then execute following command to
download it.

For Bash:
```shell
$ curl -fo JOD_Dist_TMPL-{VER}.tgz https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-{VER}.tgz
```

For Powershell:
```powershell
$ Invoke-WebRequest -Uri "https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-{VER}.zip" -OutFile "JOD_Dist_TMPL-{VER}.tgz"
```

### Create your own JOD Distribution

Now you can **customize and build your own JOD Distribution**. Extract the
JOD Distribution TEMPLATE dist and rename his dir according to your own
distribution (p.e. 'MyLamp'). Enter to the JOD Distribution project's folder
and customize it.<br>
The ```jod_dist_configs.(sh|ps1)``` files contains the main distribution's configs
like his name and version, the JOD version to use, the JCP credentials, etc...
Populate all properties from both files and remove the "customization check" at
the top of the files.<br>
More details on JOD distribution customization in the [Start a new JOD Dist](https://www.johnosproject.org/docs/references/jod_dists/jod_dist_template/create_your_own_jod_distribution/start_new_jod_distribution) script references  or in the ```README.md``` file of the corresponding JOD Distribution TEMPLATE (Latest [README.md](src/tmpl/resources/README.md) version).

For Bash:
```shell
# Create new JOD Distribution
#$ curl -fo JOD_Dist_TMPL-{VER}.tgz https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-{VER}.tgz
$ tar zxvf build/publications/JOD_Dist_TMPL-{VER}.tgz
$ mv JOD_Dist_TMPL-{VER} {MY_JOD_DIST}
$ cd {MY_JOD_DIST}

# Configure JOD Distribution
# On both files delete "customization check" line and update variables according
# to your needs (mandatory DIST_JCP_ID and DIST_JCP_SECRET).
# For more customization option see the README.md file $ cat README.md
$ nano configs/jod_dist_configs.sh
$ nano configs/jod_dist_configs.ps1
```

For Powershell:
```powershell
# Create new JOD Distribution
$ Expand-Archive -Path build/publications/JOD_Dist_TMPL-{VER}.zip
$ mv JOD_Dist_TMPL-{VER} {MY_JOD_DIST}
$ Rename-Item JOD_Dist_TMPL-{VER} {MY_JOD_DIST}
$ cd {MY_JOD_DIST}

# Configure JOD Distribution
# On both files delete "customization check" line and update variables according
# to your needs (mandatory DIST_JCP_ID and DIST_JCP_SECRET).
# For more customization option see the README.md file $ cat README.md
$ notepad configs/jod_dist_configs.sh
$ notepad configs/jod_dist_configs.ps1
```

When the JOD Distribution customization is terminated, you can **build and share
your own JOD Distribution**. Generated file can be used to run a John Object.
Depending on JOD distribution's configs, the John Object represented can vary.
To run it on local machine, you can copy ```build/{DIST_NAME}/{DIST_VER}/```
files to local dir and then execute the ```start.sh``` script. Otherwise, you
The ```publish.(sh|ps1)``` script compress generated JOD Distribution and output
the two files ```build/publications/{DIST_NAME}-{DIST_VER}.(tgz|zip)```.

For Bash:
```shell
#Build JOD Distribution
$ bash scripts/build.sh

# Opt: Install JOD Distribution
# Extract JOD Distribution files to local dir 'envs/{DIST_NAME-VERSION}/{RANDOM_NUMBER}
$ bash scripts/install.sh

# Opt: Publish JOD Distribution
# Generate distributable files (tgz and zip) for JOD Distribution
$ bash scripts/publish.sh
```

For Powershell:
```powershell
#Build JOD Distribution
$ powershell scripts/build.ps1

# Opt: Install JOD Distribution
# Extract JOD Distribution files to local dir 'envs/{DIST_NAME-VERSION}/{RANDOM_NUMBER}
$ powershell scripts/install.ps1

# Opt: Publish JOD Distribution
# Generate distributable files (tgz and zip) for JOD Distribution
$ powershell scripts/publish.ps1
```

---

## Collaborate

**Any kind of collaboration is welcome!** This is an Open Source project, so we are happy to share our experience with other developers, makers and users. Bug reporting, extension development, documentation and guides etc... are activities where anybody can help to improve this project.

You can help us also sharing your own JOD Distribution. Simply send an email to the bellow address and describing your distribution (distribution purpose, setup guide, object's structure, hardware requirements...). Then we will be happy to publish your distribution and help other user.

Please email to [tech@johnosproject.com](mailto:tech@johnosproject.com).

----

## Versions

* v [1.0-DEV](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/src/1.0-DEV/) (
  [tgz](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0-DEV.tgz) | 
  [zip](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0-DEV.zip))
* v [1.0-DEVb](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/src/1.0-DEVb/) (
  [tgz](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0-DEVb.tgz) | 
  [zip](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0-DEVb.zip))
* v [1.0](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/src/1.0/) (
  [tgz](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.tgz) |
  [zip](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.zip))
* v [1.0.1](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/src/1.0.1/) (
  [tgz](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.1.tgz) |
  [zip](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.1.zip))
* v [1.0.2](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/src/1.0.2/) (
  [tgz](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.2.tgz) |
  [zip](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.2.zip))
* v [1.0.3](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/src/1.0.3/) (
  [tgz](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.3.tgz) |
  [zip](https://bitbucket.org/johnosproject_shared/com.robypomper.josp.jod.template/downloads/JOD_Dist_TMPL-1.0.3.zip))

Each JOD Distribution TEMPLATE can download and build a JOD Distribution using different versions of the JOD agent. Here the table of JOD Distribution TEMPLATE versions and corresponding supported JOD versions.

| JOD Distribution TEMPLATE Version | Supported JOD Versions      |
|-----------------------------------|-----------------------------|
| 1.0-DEV                           | 2.2.0                       |
| 1.0-DEVb                          | 2.2.0                       |
| 1.0                               | 2.2.0*, 2.2.1               |
| 1.0.1                             | 2.2.0, 2.2.1*               |
| 1.0.2                             | 2.2.0, 2.2.1, 2.2.2*        |
| 1.0.3                             | 2.2.0, 2.2.1, 2.2.2, 2.2.3* |

----

## Licences

The JOD Distribution TEMPLATE is an open-source project and is distributed with a [GPLv3 license](LICENCE.md).
