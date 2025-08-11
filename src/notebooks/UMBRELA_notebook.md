**Objective**: Set up UMBRELA using Colab notebook (w/ GPT & HuggingFace Open-Source Models for eval)

Steps:

1.   Install Anserini
2.   Install Pyserini
3.   Install UMBRELA



**Anserini:** Need Java 21 and Maven 3.9+

Get JDK 21


```python
!apt-get install openjdk-21-jdk
```

    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    The following additional packages will be installed:
      fonts-dejavu-core fonts-dejavu-extra libatk-wrapper-java
      libatk-wrapper-java-jni libxt-dev libxtst6 libxxf86dga1
      openjdk-21-jdk-headless openjdk-21-jre openjdk-21-jre-headless x11-utils
    Suggested packages:
      libxt-doc openjdk-21-demo openjdk-21-source visualvm libnss-mdns
      fonts-ipafont-gothic fonts-ipafont-mincho fonts-wqy-microhei
      | fonts-wqy-zenhei fonts-indic mesa-utils
    The following NEW packages will be installed:
      fonts-dejavu-core fonts-dejavu-extra libatk-wrapper-java
      libatk-wrapper-java-jni libxt-dev libxtst6 libxxf86dga1 openjdk-21-jdk
      openjdk-21-jdk-headless openjdk-21-jre openjdk-21-jre-headless x11-utils
    0 upgraded, 12 newly installed, 0 to remove and 35 not upgraded.
    Need to get 135 MB of archives.
    After this operation, 314 MB of additional disk space will be used.
    Get:1 http://archive.ubuntu.com/ubuntu jammy/main amd64 fonts-dejavu-core all 2.37-2build1 [1,041 kB]
    Get:2 http://archive.ubuntu.com/ubuntu jammy/main amd64 fonts-dejavu-extra all 2.37-2build1 [2,041 kB]
    Get:3 http://archive.ubuntu.com/ubuntu jammy/main amd64 libxtst6 amd64 2:1.2.3-1build4 [13.4 kB]
    Get:4 http://archive.ubuntu.com/ubuntu jammy/main amd64 libxxf86dga1 amd64 2:1.1.5-0ubuntu3 [12.6 kB]
    Get:5 http://archive.ubuntu.com/ubuntu jammy/main amd64 x11-utils amd64 7.7+5build2 [206 kB]
    Get:6 http://archive.ubuntu.com/ubuntu jammy/main amd64 libatk-wrapper-java all 0.38.0-5build1 [53.1 kB]
    Get:7 http://archive.ubuntu.com/ubuntu jammy/main amd64 libatk-wrapper-java-jni amd64 0.38.0-5build1 [49.0 kB]
    Get:8 http://archive.ubuntu.com/ubuntu jammy/main amd64 libxt-dev amd64 1:1.2.1-1 [396 kB]
    Get:9 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-21-jre-headless amd64 21.0.8+9~us1-0ubuntu1~22.04.1 [46.8 MB]
    Get:10 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-21-jre amd64 21.0.8+9~us1-0ubuntu1~22.04.1 [234 kB]
    Get:11 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-21-jdk-headless amd64 21.0.8+9~us1-0ubuntu1~22.04.1 [82.7 MB]
    Get:12 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 openjdk-21-jdk amd64 21.0.8+9~us1-0ubuntu1~22.04.1 [1,651 kB]
    Fetched 135 MB in 4s (34.1 MB/s)
    Selecting previously unselected package fonts-dejavu-core.
    (Reading database ... 126284 files and directories currently installed.)
    Preparing to unpack .../00-fonts-dejavu-core_2.37-2build1_all.deb ...
    Unpacking fonts-dejavu-core (2.37-2build1) ...
    Selecting previously unselected package fonts-dejavu-extra.
    Preparing to unpack .../01-fonts-dejavu-extra_2.37-2build1_all.deb ...
    Unpacking fonts-dejavu-extra (2.37-2build1) ...
    Selecting previously unselected package libxtst6:amd64.
    Preparing to unpack .../02-libxtst6_2%3a1.2.3-1build4_amd64.deb ...
    Unpacking libxtst6:amd64 (2:1.2.3-1build4) ...
    Selecting previously unselected package libxxf86dga1:amd64.
    Preparing to unpack .../03-libxxf86dga1_2%3a1.1.5-0ubuntu3_amd64.deb ...
    Unpacking libxxf86dga1:amd64 (2:1.1.5-0ubuntu3) ...
    Selecting previously unselected package x11-utils.
    Preparing to unpack .../04-x11-utils_7.7+5build2_amd64.deb ...
    Unpacking x11-utils (7.7+5build2) ...
    Selecting previously unselected package libatk-wrapper-java.
    Preparing to unpack .../05-libatk-wrapper-java_0.38.0-5build1_all.deb ...
    Unpacking libatk-wrapper-java (0.38.0-5build1) ...
    Selecting previously unselected package libatk-wrapper-java-jni:amd64.
    Preparing to unpack .../06-libatk-wrapper-java-jni_0.38.0-5build1_amd64.deb ...
    Unpacking libatk-wrapper-java-jni:amd64 (0.38.0-5build1) ...
    Selecting previously unselected package libxt-dev:amd64.
    Preparing to unpack .../07-libxt-dev_1%3a1.2.1-1_amd64.deb ...
    Unpacking libxt-dev:amd64 (1:1.2.1-1) ...
    Selecting previously unselected package openjdk-21-jre-headless:amd64.
    Preparing to unpack .../08-openjdk-21-jre-headless_21.0.8+9~us1-0ubuntu1~22.04.1_amd64.deb ...
    Unpacking openjdk-21-jre-headless:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    Selecting previously unselected package openjdk-21-jre:amd64.
    Preparing to unpack .../09-openjdk-21-jre_21.0.8+9~us1-0ubuntu1~22.04.1_amd64.deb ...
    Unpacking openjdk-21-jre:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    Selecting previously unselected package openjdk-21-jdk-headless:amd64.
    Preparing to unpack .../10-openjdk-21-jdk-headless_21.0.8+9~us1-0ubuntu1~22.04.1_amd64.deb ...
    Unpacking openjdk-21-jdk-headless:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    Selecting previously unselected package openjdk-21-jdk:amd64.
    Preparing to unpack .../11-openjdk-21-jdk_21.0.8+9~us1-0ubuntu1~22.04.1_amd64.deb ...
    Unpacking openjdk-21-jdk:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    Setting up openjdk-21-jre-headless:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/java to provide /usr/bin/java (java) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jpackage to provide /usr/bin/jpackage (jpackage) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode
    Setting up libxtst6:amd64 (2:1.2.3-1build4) ...
    Setting up libxxf86dga1:amd64 (2:1.1.5-0ubuntu3) ...
    Setting up openjdk-21-jre:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    Setting up libxt-dev:amd64 (1:1.2.1-1) ...
    Setting up fonts-dejavu-core (2.37-2build1) ...
    Setting up fonts-dejavu-extra (2.37-2build1) ...
    Setting up x11-utils (7.7+5build2) ...
    Setting up libatk-wrapper-java (0.38.0-5build1) ...
    Setting up openjdk-21-jdk-headless:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jar to provide /usr/bin/jar (jar) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/javac to provide /usr/bin/javac (javac) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/javap to provide /usr/bin/javap (javap) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jcmd to provide /usr/bin/jcmd (jcmd) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jdeprscan to provide /usr/bin/jdeprscan (jdeprscan) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jdeps to provide /usr/bin/jdeps (jdeps) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jfr to provide /usr/bin/jfr (jfr) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jimage to provide /usr/bin/jimage (jimage) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jlink to provide /usr/bin/jlink (jlink) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jmod to provide /usr/bin/jmod (jmod) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jps to provide /usr/bin/jps (jps) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jshell to provide /usr/bin/jshell (jshell) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jwebserver to provide /usr/bin/jwebserver (jwebserver) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jhsdb to provide /usr/bin/jhsdb (jhsdb) in auto mode
    Setting up libatk-wrapper-java-jni:amd64 (0.38.0-5build1) ...
    Setting up openjdk-21-jdk:amd64 (21.0.8+9~us1-0ubuntu1~22.04.1) ...
    update-alternatives: using /usr/lib/jvm/java-21-openjdk-amd64/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode
    Processing triggers for fontconfig (2.13.1-4.2ubuntu5) ...
    Processing triggers for hicolor-icon-theme (0.17-2) ...
    Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
    /sbin/ldconfig.real: /usr/local/lib/libtbbbind.so.3 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libur_adapter_level_zero.so.0 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libumf.so.0 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libur_adapter_level_zero_v2.so.0 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libtbbmalloc.so.2 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libtcm_debug.so.1 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libtbbbind_2_0.so.3 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libhwloc.so.15 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libtcm.so.1 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libtbb.so.12 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libtbbmalloc_proxy.so.2 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libur_adapter_opencl.so.0 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libur_loader.so.0 is not a symbolic link
    
    /sbin/ldconfig.real: /usr/local/lib/libtbbbind_2_5.so.3 is not a symbolic link
    
    Processing triggers for man-db (2.10.2-1) ...
    Processing triggers for mailcap (3.70+nmu1ubuntu1) ...



```python
import os
os.environ['JAVA_HOME'] = '/usr/lib/jvm/java-21-openjdk-amd64'
os.environ['PATH'] = os.environ['PATH'] + ':' + os.environ['JAVA_HOME'] + '/bin'
```

Confirm Java Version


```python
!java -version
```

    openjdk version "21.0.8" 2025-07-15
    OpenJDK Runtime Environment (build 21.0.8+9-Ubuntu-0ubuntu122.04.1)
    OpenJDK 64-Bit Server VM (build 21.0.8+9-Ubuntu-0ubuntu122.04.1, mixed mode, sharing)


Get Maven (Latest)


```python
!wget https://dlcdn.apache.org/maven/maven-3/3.9.11/binaries/apache-maven-3.9.11-bin.tar.gz
```

    --2025-08-11 17:11:28--  https://dlcdn.apache.org/maven/maven-3/3.9.11/binaries/apache-maven-3.9.11-bin.tar.gz
    Resolving dlcdn.apache.org (dlcdn.apache.org)... 151.101.2.132, 2a04:4e42::644
    Connecting to dlcdn.apache.org (dlcdn.apache.org)|151.101.2.132|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 9160848 (8.7M) [application/x-gzip]
    Saving to: ‘apache-maven-3.9.11-bin.tar.gz’
    
    apache-maven-3.9.11 100%[===================>]   8.74M  --.-KB/s    in 0.06s   
    
    2025-08-11 17:11:28 (140 MB/s) - ‘apache-maven-3.9.11-bin.tar.gz’ saved [9160848/9160848]
    



```python
!tar -xvzf apache-maven-3.9.11-bin.tar.gz
```

    apache-maven-3.9.11/README.txt
    apache-maven-3.9.11/LICENSE
    apache-maven-3.9.11/NOTICE
    apache-maven-3.9.11/lib/
    apache-maven-3.9.11/lib/aopalliance.license
    apache-maven-3.9.11/lib/asm.license
    apache-maven-3.9.11/lib/commons-cli.license
    apache-maven-3.9.11/lib/commons-codec.license
    apache-maven-3.9.11/lib/error_prone_annotations.license
    apache-maven-3.9.11/lib/failureaccess.license
    apache-maven-3.9.11/lib/gson.license
    apache-maven-3.9.11/lib/guava.license
    apache-maven-3.9.11/lib/guice.license
    apache-maven-3.9.11/lib/httpclient.license
    apache-maven-3.9.11/lib/httpcore.license
    apache-maven-3.9.11/lib/jansi.license
    apache-maven-3.9.11/lib/javax.annotation-api.license
    apache-maven-3.9.11/lib/javax.inject.license
    apache-maven-3.9.11/lib/jcl-over-slf4j.license
    apache-maven-3.9.11/lib/jspecify.license
    apache-maven-3.9.11/lib/org.eclipse.sisu.inject.license
    apache-maven-3.9.11/lib/org.eclipse.sisu.plexus.license
    apache-maven-3.9.11/lib/plexus-cipher.license
    apache-maven-3.9.11/lib/plexus-component-annotations.license
    apache-maven-3.9.11/lib/plexus-interpolation.license
    apache-maven-3.9.11/lib/plexus-sec-dispatcher.license
    apache-maven-3.9.11/lib/plexus-utils.license
    apache-maven-3.9.11/lib/slf4j-api.license
    apache-maven-3.9.11/boot/
    apache-maven-3.9.11/boot/plexus-classworlds.license
    apache-maven-3.9.11/lib/jansi-native/
    apache-maven-3.9.11/lib/jansi-native/Windows/
    apache-maven-3.9.11/lib/jansi-native/Windows/arm64/
    apache-maven-3.9.11/lib/jansi-native/Windows/x86/
    apache-maven-3.9.11/lib/jansi-native/Windows/x86_64/
    apache-maven-3.9.11/lib/jansi-native/Windows/arm64/jansi.dll
    apache-maven-3.9.11/lib/jansi-native/Windows/x86/jansi.dll
    apache-maven-3.9.11/lib/jansi-native/Windows/x86_64/jansi.dll
    apache-maven-3.9.11/bin/m2.conf
    apache-maven-3.9.11/bin/mvn.cmd
    apache-maven-3.9.11/bin/mvnDebug.cmd
    apache-maven-3.9.11/bin/mvn
    apache-maven-3.9.11/bin/mvnDebug
    apache-maven-3.9.11/bin/mvnyjp
    apache-maven-3.9.11/conf/
    apache-maven-3.9.11/conf/logging/
    apache-maven-3.9.11/conf/logging/simplelogger.properties
    apache-maven-3.9.11/conf/settings.xml
    apache-maven-3.9.11/conf/toolchains.xml
    apache-maven-3.9.11/lib/ext/
    apache-maven-3.9.11/lib/ext/hazelcast/
    apache-maven-3.9.11/lib/ext/redisson/
    apache-maven-3.9.11/lib/jansi-native/
    apache-maven-3.9.11/lib/ext/README.txt
    apache-maven-3.9.11/lib/ext/hazelcast/README.txt
    apache-maven-3.9.11/lib/ext/redisson/README.txt
    apache-maven-3.9.11/lib/jansi-native/README.txt
    apache-maven-3.9.11/boot/plexus-classworlds-2.9.0.jar
    apache-maven-3.9.11/lib/jcl-over-slf4j-1.7.36.jar
    apache-maven-3.9.11/lib/aopalliance-1.0.jar
    apache-maven-3.9.11/lib/maven-resolver-connector-basic-1.9.24.jar
    apache-maven-3.9.11/lib/maven-settings-builder-3.9.11.jar
    apache-maven-3.9.11/lib/maven-artifact-3.9.11.jar
    apache-maven-3.9.11/lib/maven-compat-3.9.11.jar
    apache-maven-3.9.11/lib/slf4j-api-1.7.36.jar
    apache-maven-3.9.11/lib/org.eclipse.sisu.inject-0.9.0.M4.jar
    apache-maven-3.9.11/lib/jspecify-1.0.0.jar
    apache-maven-3.9.11/lib/wagon-provider-api-3.5.3.jar
    apache-maven-3.9.11/lib/guice-5.1.0-classes.jar
    apache-maven-3.9.11/lib/maven-slf4j-provider-3.9.11.jar
    apache-maven-3.9.11/lib/maven-resolver-named-locks-1.9.24.jar
    apache-maven-3.9.11/lib/javax.annotation-api-1.3.2.jar
    apache-maven-3.9.11/lib/commons-codec-1.18.0.jar
    apache-maven-3.9.11/lib/maven-resolver-transport-http-1.9.24.jar
    apache-maven-3.9.11/lib/maven-resolver-spi-1.9.24.jar
    apache-maven-3.9.11/lib/httpcore-4.4.16.jar
    apache-maven-3.9.11/lib/wagon-http-3.5.3.jar
    apache-maven-3.9.11/lib/org.eclipse.sisu.plexus-0.9.0.M4.jar
    apache-maven-3.9.11/lib/jansi-2.4.2.jar
    apache-maven-3.9.11/lib/maven-resolver-transport-file-1.9.24.jar
    apache-maven-3.9.11/lib/maven-plugin-api-3.9.11.jar
    apache-maven-3.9.11/lib/plexus-interpolation-1.28.jar
    apache-maven-3.9.11/lib/maven-resolver-transport-wagon-1.9.24.jar
    apache-maven-3.9.11/lib/plexus-utils-3.6.0.jar
    apache-maven-3.9.11/lib/plexus-cipher-2.0.jar
    apache-maven-3.9.11/lib/plexus-sec-dispatcher-2.0.jar
    apache-maven-3.9.11/lib/maven-resolver-provider-3.9.11.jar
    apache-maven-3.9.11/lib/maven-shared-utils-3.4.2.jar
    apache-maven-3.9.11/lib/wagon-file-3.5.3.jar
    apache-maven-3.9.11/lib/guava-33.4.8-jre.jar
    apache-maven-3.9.11/lib/gson-2.13.1.jar
    apache-maven-3.9.11/lib/asm-9.8.jar
    apache-maven-3.9.11/lib/maven-resolver-api-1.9.24.jar
    apache-maven-3.9.11/lib/maven-resolver-util-1.9.24.jar
    apache-maven-3.9.11/lib/maven-embedder-3.9.11.jar
    apache-maven-3.9.11/lib/maven-settings-3.9.11.jar
    apache-maven-3.9.11/lib/error_prone_annotations-2.38.0.jar
    apache-maven-3.9.11/lib/plexus-component-annotations-2.2.0.jar
    apache-maven-3.9.11/lib/javax.inject-1.jar
    apache-maven-3.9.11/lib/maven-model-3.9.11.jar
    apache-maven-3.9.11/lib/failureaccess-1.0.3.jar
    apache-maven-3.9.11/lib/maven-builder-support-3.9.11.jar
    apache-maven-3.9.11/lib/maven-repository-metadata-3.9.11.jar
    apache-maven-3.9.11/lib/maven-resolver-impl-1.9.24.jar
    apache-maven-3.9.11/lib/wagon-http-shared-3.5.3.jar
    apache-maven-3.9.11/lib/httpclient-4.5.14.jar
    apache-maven-3.9.11/lib/maven-core-3.9.11.jar
    apache-maven-3.9.11/lib/commons-cli-1.9.0.jar
    apache-maven-3.9.11/lib/maven-model-builder-3.9.11.jar



```python
!sudo mv apache-maven-3.9.11 /opt/maven
```


```python
import os
os.environ['MAVEN_HOME'] = '/opt/maven'
os.environ['PATH'] = os.environ['MAVEN_HOME'] + '/bin:' + os.environ['PATH']
```

Confirm Maven is present


```python
!mvn --version
```

    [1mApache Maven 3.9.11 (3e54c93a704957b63ee3494413a2b544fd3d825b)[m
    Maven home: /opt/maven
    Java version: 21.0.8, vendor: Ubuntu, runtime: /usr/lib/jvm/java-21-openjdk-amd64
    Default locale: en_US, platform encoding: UTF-8
    OS name: "linux", version: "6.1.123+", arch: "amd64", family: "unix"
    [0m[0m

Clone Anserini


```python
!git clone https://github.com/castorini/anserini.git --recurse-submodules
```

    Cloning into 'anserini'...
    remote: Enumerating objects: 49844, done.[K
    remote: Counting objects: 100% (1429/1429), done.[K
    remote: Compressing objects: 100% (230/230), done.[K
    remote: Total 49844 (delta 1289), reused 1210 (delta 1190), pack-reused 48415 (from 4)[K
    Receiving objects: 100% (49844/49844), 94.61 MiB | 14.54 MiB/s, done.
    Resolving deltas: 100% (37899/37899), done.
    Submodule 'tools' (https://github.com/castorini/anserini-tools.git) registered for path 'tools'
    Cloning into '/content/anserini/tools'...
    remote: Enumerating objects: 1118, done.        
    remote: Counting objects: 100% (81/81), done.        
    remote: Compressing objects: 100% (27/27), done.        
    remote: Total 1118 (delta 67), reused 55 (delta 54), pack-reused 1037 (from 3)        
    Receiving objects: 100% (1118/1118), 781.49 MiB | 37.78 MiB/s, done.
    Resolving deltas: 100% (252/252), done.
    Submodule path 'tools': checked out '064d1f4013b18ff0bccfd32db40be2a578c6d35a'


Follow along the Anserini official repo installation process


```python
%cd anserini/
```

    /content/anserini



```python
!git submodule update --init --recursive
```


```python
!mvn clean package -DskipTests
```

    [[1;34mINFO[m] Scanning for projects...
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/central/central-publishing-maven-plugin/0.8.0/central-publishing-maven-plugin-0.8.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/central/central-publishing-maven-plugin/0.8.0/central-publishing-maven-plugin-0.8.0.pom[90m (17 kB at 22 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/buildsupport/buildsupport/32/buildsupport-32.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/buildsupport/buildsupport/32/buildsupport-32.pom[90m (36 kB at 524 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.5.1/plexus-utils-3.5.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.5.1/plexus-utils-3.5.1.pom[90m (8.8 kB at 302 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/10/plexus-10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/10/plexus-10.pom[90m (25 kB at 941 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/package-url/packageurl-java/1.4.1/packageurl-java-1.4.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/package-url/packageurl-java/1.4.1/packageurl-java-1.4.1.pom[90m (12 kB at 782 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/32.1.0-jre/guava-32.1.0-jre.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/32.1.0-jre/guava-32.1.0-jre.pom[90m (13 kB at 800 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/32.1.0-jre/guava-parent-32.1.0-jre.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/32.1.0-jre/guava-parent-32.1.0-jre.pom[90m (22 kB at 1.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.1/failureaccess-1.0.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.1/failureaccess-1.0.1.pom[90m (2.4 kB at 201 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/26.0-android/guava-parent-26.0-android.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/26.0-android/guava-parent-26.0-android.pom[90m (10 kB at 636 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/oss/oss-parent/9/oss-parent-9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/oss/oss-parent/9/oss-parent-9.pom[90m (6.6 kB at 411 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/listenablefuture/9999.0-empty-to-avoid-conflict-with-guava/listenablefuture-9999.0-empty-to-avoid-conflict-with-guava.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/listenablefuture/9999.0-empty-to-avoid-conflict-with-guava/listenablefuture-9999.0-empty-to-avoid-conflict-with-guava.pom[90m (2.3 kB at 152 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/3.0.2/jsr305-3.0.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/3.0.2/jsr305-3.0.2.pom[90m (4.3 kB at 390 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/oss/oss-parent/7/oss-parent-7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/oss/oss-parent/7/oss-parent-7.pom[90m (4.8 kB at 402 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/checkerframework/checker-qual/3.33.0/checker-qual-3.33.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/checkerframework/checker-qual/3.33.0/checker-qual-3.33.0.pom[90m (2.1 kB at 161 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.18.0/error_prone_annotations-2.18.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.18.0/error_prone_annotations-2.18.0.pom[90m (2.2 kB at 135 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_parent/2.18.0/error_prone_parent-2.18.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_parent/2.18.0/error_prone_parent-2.18.0.pom[90m (11 kB at 923 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/2.8/j2objc-annotations-2.8.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/2.8/j2objc-annotations-2.8.pom[90m (2.9 kB at 146 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.15.1/commons-io-2.15.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.15.1/commons-io-2.15.1.pom[90m (20 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/65/commons-parent-65.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/65/commons-parent-65.pom[90m (78 kB at 3.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/31/apache-31.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/31/apache-31.pom[90m (24 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.10.1/junit-bom-5.10.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.10.1/junit-bom-5.10.1.pom[90m (5.6 kB at 565 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.12.0/commons-lang3-3.12.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.12.0/commons-lang3-3.12.0.pom[90m (31 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/52/commons-parent-52.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/52/commons-parent-52.pom[90m (79 kB at 3.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/23/apache-23.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/23/apache-23.pom[90m (18 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.7.1/junit-bom-5.7.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.7.1/junit-bom-5.7.1.pom[90m (5.1 kB at 392 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.1/jackson-databind-2.16.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.1/jackson-databind-2.16.1.pom[90m (21 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-base/2.16.1/jackson-base-2.16.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-base/2.16.1/jackson-base-2.16.1.pom[90m (11 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-bom/2.16.1/jackson-bom-2.16.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-bom/2.16.1/jackson-bom-2.16.1.pom[90m (18 kB at 1.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-parent/2.16/jackson-parent-2.16.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-parent/2.16/jackson-parent-2.16.pom[90m (6.5 kB at 652 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/oss-parent/56/oss-parent-56.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/oss-parent/56/oss-parent-56.pom[90m (24 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.9.2/junit-bom-5.9.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.9.2/junit-bom-5.9.2.pom[90m (5.6 kB at 626 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.1/jackson-annotations-2.16.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.1/jackson-annotations-2.16.1.pom[90m (7.1 kB at 588 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.1/jackson-core-2.16.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.1/jackson-core-2.16.1.pom[90m (9.9 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.9.3/junit-bom-5.9.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.9.3/junit-bom-5.9.3.pom[90m (5.6 kB at 704 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/client5/httpclient5/5.3.1/httpclient5-5.3.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/client5/httpclient5/5.3.1/httpclient5-5.3.1.pom[90m (6.0 kB at 662 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/client5/httpclient5-parent/5.3.1/httpclient5-parent-5.3.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/client5/httpclient5-parent/5.3.1/httpclient5-parent-5.3.1.pom[90m (17 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-parent/13/httpcomponents-parent-13.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-parent/13/httpcomponents-parent-13.pom[90m (30 kB at 2.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/27/apache-27.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/27/apache-27.pom[90m (20 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5/5.2.4/httpcore5-5.2.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5/5.2.4/httpcore5-5.2.4.pom[90m (3.9 kB at 395 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5-parent/5.2.4/httpcore5-parent-5.2.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5-parent/5.2.4/httpcore5-parent-5.2.4.pom[90m (14 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5-h2/5.2.4/httpcore5-h2-5.2.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5-h2/5.2.4/httpcore5-h2-5.2.4.pom[90m (3.6 kB at 362 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.36/slf4j-api-1.7.36.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.36/slf4j-api-1.7.36.pom[90m (2.7 kB at 249 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/1.7.36/slf4j-parent-1.7.36.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/1.7.36/slf4j-parent-1.7.36.pom[90m (14 kB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/central/central-publishing-maven-plugin/0.8.0/central-publishing-maven-plugin-0.8.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/central/central-publishing-maven-plugin/0.8.0/central-publishing-maven-plugin-0.8.0.jar[90m (111 kB at 5.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.5.1/plexus-utils-3.5.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/package-url/packageurl-java/1.4.1/packageurl-java-1.4.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/32.1.0-jre/guava-32.1.0-jre.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.1/failureaccess-1.0.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/listenablefuture/9999.0-empty-to-avoid-conflict-with-guava/listenablefuture-9999.0-empty-to-avoid-conflict-with-guava.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/package-url/packageurl-java/1.4.1/packageurl-java-1.4.1.jar[90m (16 kB at 400 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/3.0.2/jsr305-3.0.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.1/failureaccess-1.0.1.jar[90m (4.6 kB at 69 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/checkerframework/checker-qual/3.33.0/checker-qual-3.33.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.5.1/plexus-utils-3.5.1.jar[90m (269 kB at 3.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.18.0/error_prone_annotations-2.18.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/listenablefuture/9999.0-empty-to-avoid-conflict-with-guava/listenablefuture-9999.0-empty-to-avoid-conflict-with-guava.jar[90m (2.2 kB at 22 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/3.0.2/jsr305-3.0.2.jar[90m (20 kB at 237 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/2.8/j2objc-annotations-2.8.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.15.1/commons-io-2.15.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.18.0/error_prone_annotations-2.18.0.jar[90m (16 kB at 169 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.12.0/commons-lang3-3.12.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/2.8/j2objc-annotations-2.8.jar[90m (9.3 kB at 95 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.1/jackson-databind-2.16.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/checkerframework/checker-qual/3.33.0/checker-qual-3.33.0.jar[90m (224 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.1/jackson-annotations-2.16.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.1/jackson-annotations-2.16.1.jar[90m (78 kB at 695 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.1/jackson-core-2.16.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.1/jackson-core-2.16.1.jar[90m (578 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/client5/httpclient5/5.3.1/httpclient5-5.3.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.15.1/commons-io-2.15.1.jar[90m (501 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5/5.2.4/httpcore5-5.2.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.12.0/commons-lang3-3.12.0.jar[90m (587 kB at 2.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5-h2/5.2.4/httpcore5-h2-5.2.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5-h2/5.2.4/httpcore5-h2-5.2.4.jar[90m (237 kB at 919 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.36/slf4j-api-1.7.36.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.36/slf4j-api-1.7.36.jar[90m (41 kB at 158 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/client5/httpclient5/5.3.1/httpclient5-5.3.1.jar[90m (862 kB at 3.0 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.1/jackson-databind-2.16.1.jar[90m (1.6 MB at 5.6 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/core5/httpcore5/5.2.4/httpcore5-5.2.4.jar[90m (855 kB at 2.9 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/32.1.0-jre/guava-32.1.0-jre.jar[90m (3.0 MB at 8.4 MB/s)[0m
    [[1;34mINFO[m] Inspecting build with total of 1 modules
    [[1;34mINFO[m] Installing Central Publishing features
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m------------------------< [0;36mio.anserini:anserini[0;1m >------------------------[m
    [[1;34mINFO[m] [1mBuilding Anserini 1.1.2-SNAPSHOT[m
    [[1;34mINFO[m]   from pom.xml
    [[1;34mINFO[m] [1m--------------------------------[ jar ]---------------------------------[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-source-plugin/3.3.0/maven-source-plugin-3.3.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-source-plugin/3.3.0/maven-source-plugin-3.3.0.pom[90m (6.7 kB at 562 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/39/maven-plugins-39.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/39/maven-plugins-39.pom[90m (8.1 kB at 506 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/39/maven-parent-39.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/39/maven-parent-39.pom[90m (48 kB at 3.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/29/apache-29.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/29/apache-29.pom[90m (21 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-source-plugin/3.3.0/maven-source-plugin-3.3.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-source-plugin/3.3.0/maven-source-plugin-3.3.0.jar[90m (32 kB at 2.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-javadoc-plugin/3.6.3/maven-javadoc-plugin-3.6.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-javadoc-plugin/3.6.3/maven-javadoc-plugin-3.6.3.pom[90m (22 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/41/maven-plugins-41.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/41/maven-plugins-41.pom[90m (7.4 kB at 919 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/41/maven-parent-41.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/41/maven-parent-41.pom[90m (50 kB at 5.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-javadoc-plugin/3.6.3/maven-javadoc-plugin-3.6.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-javadoc-plugin/3.6.3/maven-javadoc-plugin-3.6.3.jar[90m (510 kB at 18 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/jacoco-maven-plugin/0.8.11/jacoco-maven-plugin-0.8.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/jacoco-maven-plugin/0.8.11/jacoco-maven-plugin-0.8.11.pom[90m (4.2 kB at 529 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.build/0.8.11/org.jacoco.build-0.8.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.build/0.8.11/org.jacoco.build-0.8.11.pom[90m (44 kB at 4.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-bom/9.6/asm-bom-9.6.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-bom/9.6/asm-bom-9.6.pom[90m (3.2 kB at 293 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/ow2/1.5.1/ow2-1.5.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/ow2/1.5.1/ow2-1.5.1.pom[90m (11 kB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/jacoco-maven-plugin/0.8.11/jacoco-maven-plugin-0.8.11.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/jacoco-maven-plugin/0.8.11/jacoco-maven-plugin-0.8.11.jar[90m (57 kB at 6.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-clean-plugin/3.2.0/maven-clean-plugin-3.2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-clean-plugin/3.2.0/maven-clean-plugin-3.2.0.pom[90m (5.3 kB at 354 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/35/maven-plugins-35.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/35/maven-plugins-35.pom[90m (9.9 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/35/maven-parent-35.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/35/maven-parent-35.pom[90m (45 kB at 3.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/25/apache-25.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/25/apache-25.pom[90m (21 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-clean-plugin/3.2.0/maven-clean-plugin-3.2.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-clean-plugin/3.2.0/maven-clean-plugin-3.2.0.jar[90m (36 kB at 4.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-resources-plugin/3.3.1/maven-resources-plugin-3.3.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-resources-plugin/3.3.1/maven-resources-plugin-3.3.1.pom[90m (8.2 kB at 680 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-resources-plugin/3.3.1/maven-resources-plugin-3.3.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-resources-plugin/3.3.1/maven-resources-plugin-3.3.1.jar[90m (31 kB at 3.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-compiler-plugin/3.12.1/maven-compiler-plugin-3.12.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-compiler-plugin/3.12.1/maven-compiler-plugin-3.12.1.pom[90m (9.7 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-compiler-plugin/3.12.1/maven-compiler-plugin-3.12.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-compiler-plugin/3.12.1/maven-compiler-plugin-3.12.1.jar[90m (76 kB at 9.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-surefire-plugin/3.1.0/maven-surefire-plugin-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-surefire-plugin/3.1.0/maven-surefire-plugin-3.1.0.pom[90m (6.1 kB at 382 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire/3.1.0/surefire-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire/3.1.0/surefire-3.1.0.pom[90m (22 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-surefire-plugin/3.1.0/maven-surefire-plugin-3.1.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-surefire-plugin/3.1.0/maven-surefire-plugin-3.1.0.jar[90m (43 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-jar-plugin/3.3.0/maven-jar-plugin-3.3.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-jar-plugin/3.3.0/maven-jar-plugin-3.3.0.pom[90m (6.8 kB at 966 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/37/maven-plugins-37.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/37/maven-plugins-37.pom[90m (9.9 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/37/maven-parent-37.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/37/maven-parent-37.pom[90m (46 kB at 5.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-jar-plugin/3.3.0/maven-jar-plugin-3.3.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-jar-plugin/3.3.0/maven-jar-plugin-3.3.0.jar[90m (27 kB at 3.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-shade-plugin/3.5.3/maven-shade-plugin-3.5.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-shade-plugin/3.5.3/maven-shade-plugin-3.5.3.pom[90m (13 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/42/maven-plugins-42.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-plugins/42/maven-plugins-42.pom[90m (7.7 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/42/maven-parent-42.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/42/maven-parent-42.pom[90m (50 kB at 6.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/32/apache-32.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/32/apache-32.pom[90m (24 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.10.2/junit-bom-5.10.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.10.2/junit-bom-5.10.2.pom[90m (5.6 kB at 807 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-shade-plugin/3.5.3/maven-shade-plugin-3.5.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/plugins/maven-shade-plugin/3.5.3/maven-shade-plugin-3.5.3.jar[90m (148 kB at 9.2 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-core/9.9.1/lucene-core-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-core/9.9.1/lucene-core-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-core/9.9.1/lucene-core-9.9.1.pom[90m (2.1 kB at 239 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-codecs/9.9.1/lucene-codecs-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-codecs/9.9.1/lucene-codecs-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-codecs/9.9.1/lucene-codecs-9.9.1.pom[90m (2.4 kB at 25 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-backward-codecs/9.9.1/lucene-backward-codecs-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-backward-codecs/9.9.1/lucene-backward-codecs-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-backward-codecs/9.9.1/lucene-backward-codecs-9.9.1.pom[90m (2.4 kB at 300 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-queries/9.9.1/lucene-queries-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queries/9.9.1/lucene-queries-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queries/9.9.1/lucene-queries-9.9.1.pom[90m (2.4 kB at 264 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-queryparser/9.9.1/lucene-queryparser-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queryparser/9.9.1/lucene-queryparser-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queryparser/9.9.1/lucene-queryparser-9.9.1.pom[90m (2.8 kB at 344 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-sandbox/9.9.1/lucene-sandbox-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-sandbox/9.9.1/lucene-sandbox-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-sandbox/9.9.1/lucene-sandbox-9.9.1.pom[90m (2.6 kB at 366 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-analysis-common/9.9.1/lucene-analysis-common-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-common/9.9.1/lucene-analysis-common-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-common/9.9.1/lucene-analysis-common-9.9.1.pom[90m (2.4 kB at 340 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-analysis-kuromoji/9.9.1/lucene-analysis-kuromoji-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-kuromoji/9.9.1/lucene-analysis-kuromoji-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-kuromoji/9.9.1/lucene-analysis-kuromoji-9.9.1.pom[90m (2.6 kB at 27 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-analysis-morfologik/9.9.1/lucene-analysis-morfologik-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-morfologik/9.9.1/lucene-analysis-morfologik-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-morfologik/9.9.1/lucene-analysis-morfologik-9.9.1.pom[90m (3.1 kB at 33 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/carrot2/morfologik-stemming/2.1.9/morfologik-stemming-2.1.9.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-stemming/2.1.9/morfologik-stemming-2.1.9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-stemming/2.1.9/morfologik-stemming-2.1.9.pom[90m (1.4 kB at 160 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/carrot2/morfologik-parent/2.1.9/morfologik-parent-2.1.9.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-parent/2.1.9/morfologik-parent-2.1.9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-parent/2.1.9/morfologik-parent-2.1.9.pom[90m (26 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/carrot2/morfologik-fsa/2.1.9/morfologik-fsa-2.1.9.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-fsa/2.1.9/morfologik-fsa-2.1.9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-fsa/2.1.9/morfologik-fsa-2.1.9.pom[90m (1.3 kB at 179 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/carrot2/morfologik-polish/2.1.9/morfologik-polish-2.1.9.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-polish/2.1.9/morfologik-polish-2.1.9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-polish/2.1.9/morfologik-polish-2.1.9.pom[90m (1.5 kB at 185 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mua/net/nlp/morfologik-ukrainian-search/4.9.1/morfologik-ukrainian-search-4.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mua/net/nlp/morfologik-ukrainian-search/4.9.1/morfologik-ukrainian-search-4.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mua/net/nlp/morfologik-ukrainian-search/4.9.1/morfologik-ukrainian-search-4.9.1.pom[90m (1.0 kB at 113 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-test-framework/9.9.1/lucene-test-framework-9.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-test-framework/9.9.1/lucene-test-framework-9.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-test-framework/9.9.1/lucene-test-framework-9.9.1.pom[90m (3.4 kB at 39 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-runner/2.8.1/randomizedtesting-runner-2.8.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-runner/2.8.1/randomizedtesting-runner-2.8.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-runner/2.8.1/randomizedtesting-runner-2.8.1.pom[90m (2.7 kB at 299 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-parent/2.8.1/randomizedtesting-parent-2.8.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-parent/2.8.1/randomizedtesting-parent-2.8.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-parent/2.8.1/randomizedtesting-parent-2.8.1.pom[90m (24 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mjunit/junit/4.13.1/junit-4.13.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/4.13.1/junit-4.13.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/4.13.1/junit-4.13.1.pom[90m (25 kB at 3.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/hamcrest/hamcrest/2.2/hamcrest-2.2.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest/2.2/hamcrest-2.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest/2.2/hamcrest-2.2.pom[90m (1.1 kB at 161 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mjunit/junit/4.13.2/junit-4.13.2.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/4.13.2/junit-4.13.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/4.13.2/junit-4.13.2.pom[90m (27 kB at 3.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.pom[90m (766 B at 109 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/hamcrest/hamcrest-parent/1.3/hamcrest-parent-1.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest-parent/1.3/hamcrest-parent-1.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest-parent/1.3/hamcrest-parent-1.3.pom[90m (2.0 kB at 246 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/tukaani/xz/1.9/xz-1.9.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/tukaani/xz/1.9/xz-1.9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/tukaani/xz/1.9/xz-1.9.pom[90m (2.0 kB at 205 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-core/2.16.0/jackson-core-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.0/jackson-core-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.0/jackson-core-2.16.0.pom[90m (9.9 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/jackson-base/2.16.0/jackson-base-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-base/2.16.0/jackson-base-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-base/2.16.0/jackson-base-2.16.0.pom[90m (11 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/jackson-bom/2.16.0/jackson-bom-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-bom/2.16.0/jackson-bom-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-bom/2.16.0/jackson-bom-2.16.0.pom[90m (18 kB at 2.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.0/jackson-databind-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.0/jackson-databind-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.0/jackson-databind-2.16.0.pom[90m (21 kB at 2.7 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.0/jackson-annotations-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.0/jackson-annotations-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.0/jackson-annotations-2.16.0.pom[90m (7.1 kB at 784 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.16.0/jackson-datatype-jdk8-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.16.0/jackson-datatype-jdk8-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.16.0/jackson-datatype-jdk8-2.16.0.pom[90m (2.6 kB at 368 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/module/jackson-modules-java8/2.16.0/jackson-modules-java8-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/module/jackson-modules-java8/2.16.0/jackson-modules-java8-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/module/jackson-modules-java8/2.16.0/jackson-modules-java8-2.16.0.pom[90m (3.1 kB at 310 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/dataformat/jackson-dataformat-yaml/2.16.0/jackson-dataformat-yaml-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/dataformat/jackson-dataformat-yaml/2.16.0/jackson-dataformat-yaml-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/dataformat/jackson-dataformat-yaml/2.16.0/jackson-dataformat-yaml-2.16.0.pom[90m (2.6 kB at 329 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/dataformat/jackson-dataformats-text/2.16.0/jackson-dataformats-text-2.16.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/dataformat/jackson-dataformats-text/2.16.0/jackson-dataformats-text-2.16.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/dataformat/jackson-dataformats-text/2.16.0/jackson-dataformats-text-2.16.0.pom[90m (3.5 kB at 497 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/yaml/snakeyaml/2.2/snakeyaml-2.2.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/yaml/snakeyaml/2.2/snakeyaml-2.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/yaml/snakeyaml/2.2/snakeyaml-2.2.pom[90m (21 kB at 3.5 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jsoup/jsoup/1.15.3/jsoup-1.15.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jsoup/jsoup/1.15.3/jsoup-1.15.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jsoup/jsoup/1.15.3/jsoup-1.15.3.pom[90m (13 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0margs4j/args4j/2.33/args4j-2.33.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0margs4j/args4j/2.33/args4j-2.33.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0margs4j/args4j/2.33/args4j-2.33.pom[90m (1.3 kB at 129 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0margs4j/args4j-site/2.33/args4j-site-2.33.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0margs4j/args4j-site/2.33/args4j-site-2.33.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0margs4j/args4j-site/2.33/args4j-site-2.33.pom[90m (4.4 kB at 555 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/kohsuke/pom/14/pom-14.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/kohsuke/pom/14/pom-14.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/kohsuke/pom/14/pom-14.pom[90m (5.5 kB at 685 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/logging/log4j/log4j-api/2.23.1/log4j-api-2.23.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-api/2.23.1/log4j-api-2.23.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-api/2.23.1/log4j-api-2.23.1.pom[90m (3.8 kB at 639 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/logging/log4j/log4j/2.23.1/log4j-2.23.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j/2.23.1/log4j-2.23.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j/2.23.1/log4j-2.23.1.pom[90m (37 kB at 5.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/logging/log4j/log4j-bom/2.23.1/log4j-bom-2.23.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-bom/2.23.1/log4j-bom-2.23.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-bom/2.23.1/log4j-bom-2.23.1.pom[90m (12 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/logging/logging-parent/10.6.0/logging-parent-10.6.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/logging-parent/10.6.0/logging-parent-10.6.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/logging-parent/10.6.0/logging-parent-10.6.0.pom[90m (54 kB at 6.8 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/codehaus/groovy/groovy-bom/3.0.21/groovy-bom-3.0.21.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/groovy/groovy-bom/3.0.21/groovy-bom-3.0.21.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/groovy/groovy-bom/3.0.21/groovy-bom-3.0.21.pom[90m (26 kB at 3.8 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mjakarta/platform/jakarta.jakartaee-bom/9.1.0/jakarta.jakartaee-bom-9.1.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjakarta/platform/jakarta.jakartaee-bom/9.1.0/jakarta.jakartaee-bom-9.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjakarta/platform/jakarta.jakartaee-bom/9.1.0/jakarta.jakartaee-bom-9.1.0.pom[90m (9.6 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mjakarta/platform/jakartaee-api-parent/9.1.0/jakartaee-api-parent-9.1.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjakarta/platform/jakartaee-api-parent/9.1.0/jakartaee-api-parent-9.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjakarta/platform/jakartaee-api-parent/9.1.0/jakartaee-api-parent-9.1.0.pom[90m (15 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/eclipse/ee4j/project/1.0.7/project-1.0.7.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/ee4j/project/1.0.7/project-1.0.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/ee4j/project/1.0.7/project-1.0.7.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/eclipse/jetty/jetty-bom/9.4.54.v20240208/jetty-bom-9.4.54.v20240208.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/jetty/jetty-bom/9.4.54.v20240208/jetty-bom-9.4.54.v20240208.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/jetty/jetty-bom/9.4.54.v20240208/jetty-bom-9.4.54.v20240208.pom[90m (18 kB at 2.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mio/fabric8/kubernetes-client-bom/5.12.4/kubernetes-client-bom-5.12.4.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mio/fabric8/kubernetes-client-bom/5.12.4/kubernetes-client-bom-5.12.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mio/fabric8/kubernetes-client-bom/5.12.4/kubernetes-client-bom-5.12.4.pom[90m (26 kB at 3.2 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/mockito/mockito-bom/4.11.0/mockito-bom-4.11.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/mockito/mockito-bom/4.11.0/mockito-bom-4.11.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/mockito/mockito-bom/4.11.0/mockito-bom-4.11.0.pom[90m (3.2 kB at 450 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mio/netty/netty-bom/4.1.107.Final/netty-bom-4.1.107.Final.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mio/netty/netty-bom/4.1.107.Final/netty-bom-4.1.107.Final.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mio/netty/netty-bom/4.1.107.Final/netty-bom-4.1.107.Final.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/springframework/spring-framework-bom/5.3.32/spring-framework-bom-5.3.32.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/springframework/spring-framework-bom/5.3.32/spring-framework-bom-5.3.32.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/springframework/spring-framework-bom/5.3.32/spring-framework-bom-5.3.32.pom[90m (5.7 kB at 943 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/logging/log4j/log4j-core/2.23.1/log4j-core-2.23.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-core/2.23.1/log4j-core-2.23.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-core/2.23.1/log4j-core-2.23.1.pom[90m (9.7 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-simple/1.7.32/slf4j-simple-1.7.32.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-simple/1.7.32/slf4j-simple-1.7.32.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-simple/1.7.32/slf4j-simple-1.7.32.pom[90m (1.0 kB at 128 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-parent/1.7.32/slf4j-parent-1.7.32.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/1.7.32/slf4j-parent-1.7.32.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/1.7.32/slf4j-parent-1.7.32.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-api/1.7.32/slf4j-api-1.7.32.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.32/slf4j-api-1.7.32.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.32/slf4j-api-1.7.32.pom[90m (3.8 kB at 548 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mit/unimi/dsi/fastutil/8.5.8/fastutil-8.5.8.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mit/unimi/dsi/fastutil/8.5.8/fastutil-8.5.8.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mit/unimi/dsi/fastutil/8.5.8/fastutil-8.5.8.pom[90m (1.6 kB at 198 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/wikiclean/wikiclean/1.1/wikiclean-1.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/wikiclean/wikiclean/1.1/wikiclean-1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/wikiclean/wikiclean/1.1/wikiclean-1.1.pom[90m (4.4 kB at 48 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant/1.10.1/ant-1.10.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant/1.10.1/ant-1.10.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant/1.10.1/ant-1.10.1.pom[90m (9.8 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant-parent/1.10.1/ant-parent-1.10.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-parent/1.10.1/ant-parent-1.10.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-parent/1.10.1/ant-parent-1.10.1.pom[90m (5.6 kB at 704 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant-launcher/1.10.1/ant-launcher-1.10.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-launcher/1.10.1/ant-launcher-1.10.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-launcher/1.10.1/ant-launcher-1.10.1.pom[90m (2.3 kB at 292 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcommons-io/commons-io/2.5/commons-io-2.5.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.5/commons-io-2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.5/commons-io-2.5.pom[90m (13 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/39/commons-parent-39.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/39/commons-parent-39.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/39/commons-parent-39.pom[90m (62 kB at 8.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/apache/16/apache-16.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/16/apache-16.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/16/apache-16.pom[90m (15 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-lang3/3.5/commons-lang3-3.5.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.5/commons-lang3-3.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.5/commons-lang3-3.5.pom[90m (23 kB at 2.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/41/commons-parent-41.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/41/commons-parent-41.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/41/commons-parent-41.pom[90m (65 kB at 8.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/apache/18/apache-18.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/18/apache-18.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/18/apache-18.pom[90m (16 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant/1.10.11/ant-1.10.11.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant/1.10.11/ant-1.10.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant/1.10.11/ant-1.10.11.pom[90m (17 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant-parent/1.10.11/ant-parent-1.10.11.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-parent/1.10.11/ant-parent-1.10.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-parent/1.10.11/ant-parent-1.10.11.pom[90m (6.5 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant-launcher/1.10.11/ant-launcher-1.10.11.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-launcher/1.10.11/ant-launcher-1.10.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-launcher/1.10.11/ant-launcher-1.10.11.pom[90m (3.2 kB at 352 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/twitter/twittertext/twitter-text/2.0.10/twitter-text-2.0.10.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/twitter/twittertext/twitter-text/2.0.10/twitter-text-2.0.10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/twitter/twittertext/twitter-text/2.0.10/twitter-text-2.0.10.pom[90m (8.2 kB at 84 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-databind/2.8.7/jackson-databind-2.8.7.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.8.7/jackson-databind-2.8.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.8.7/jackson-databind-2.8.7.pom[90m (5.4 kB at 678 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/jackson-parent/2.8/jackson-parent-2.8.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-parent/2.8/jackson-parent-2.8.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/jackson-parent/2.8/jackson-parent-2.8.pom[90m (8.0 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/oss-parent/27/oss-parent-27.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/oss-parent/27/oss-parent-27.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/oss-parent/27/oss-parent-27.pom[90m (20 kB at 2.8 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-annotations/2.8.0/jackson-annotations-2.8.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.8.0/jackson-annotations-2.8.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.8.0/jackson-annotations-2.8.0.pom[90m (1.8 kB at 231 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-core/2.8.7/jackson-core-2.8.7.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.8.7/jackson-core-2.8.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.8.7/jackson-core-2.8.7.pom[90m (5.4 kB at 677 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.pom[90m (965 B at 138 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/github/TREMA-UNH/trec-car-tools-java/19/trec-car-tools-java-19.pom
    Downloaded[90m from [0mjitpack.io[90m: https://jitpack.io/[0mcom/github/TREMA-UNH/trec-car-tools-java/19/trec-car-tools-java-19.pom[90m (3.1 kB at 13 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mco/nstant/in/cbor/0.8/cbor-0.8.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mco/nstant/in/cbor/0.8/cbor-0.8.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mco/nstant/in/cbor/0.8/cbor-0.8.pom[90m (7.7 kB at 962 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-lang3/3.3.2/commons-lang3-3.3.2.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.3.2/commons-lang3-3.3.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.3.2/commons-lang3-3.3.2.pom[90m (20 kB at 2.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/33/commons-parent-33.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/33/commons-parent-33.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/33/commons-parent-33.pom[90m (53 kB at 7.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/apache/13/apache-13.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/13/apache-13.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/13/apache-13.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jetbrains/annotations-java5/maven-metadata.xml
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jetbrains/annotations-java5/maven-metadata.xml
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jetbrains/annotations-java5/maven-metadata.xml[90m (850 B at 121 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jetbrains/annotations-java5/24.1.0/annotations-java5-24.1.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jetbrains/annotations-java5/24.1.0/annotations-java5-24.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jetbrains/annotations-java5/24.1.0/annotations-java5-24.1.0.pom[90m (1.3 kB at 148 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcommons-io/commons-io/2.16.1/commons-io-2.16.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.16.1/commons-io-2.16.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.16.1/commons-io-2.16.1.pom[90m (20 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/69/commons-parent-69.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/69/commons-parent-69.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/69/commons-parent-69.pom[90m (77 kB at 9.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-compress/1.26.2/commons-compress-1.26.2.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.2/commons-compress-1.26.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.2/commons-compress-1.26.2.pom[90m (23 kB at 3.8 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcommons-codec/commons-codec/1.17.0/commons-codec-1.17.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.17.0/commons-codec-1.17.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.17.0/commons-codec-1.17.0.pom[90m (18 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-lang3/3.14.0/commons-lang3-3.14.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.14.0/commons-lang3-3.14.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.14.0/commons-lang3-3.14.0.pom[90m (31 kB at 3.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/64/commons-parent-64.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/64/commons-parent-64.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/64/commons-parent-64.pom[90m (78 kB at 7.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/apache/30/apache-30.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/30/apache-30.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/30/apache-30.pom[90m (23 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/junit/junit-bom/5.10.0/junit-bom-5.10.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.10.0/junit-bom-5.10.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.10.0/junit-bom-5.10.0.pom[90m (5.6 kB at 706 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-csv/1.8/commons-csv-1.8.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-csv/1.8/commons-csv-1.8.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-csv/1.8/commons-csv-1.8.pom[90m (20 kB at 2.5 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/50/commons-parent-50.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/50/commons-parent-50.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/50/commons-parent-50.pom[90m (76 kB at 7.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/apache/21/apache-21.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/21/apache-21.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/21/apache-21.pom[90m (17 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-text/1.10.0/commons-text-1.10.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.10.0/commons-text-1.10.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.10.0/commons-text-1.10.0.pom[90m (21 kB at 2.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/54/commons-parent-54.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/54/commons-parent-54.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/54/commons-parent-54.pom[90m (82 kB at 10 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/junit/junit-bom/5.9.1/junit-bom-5.9.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.9.1/junit-bom-5.9.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.9.1/junit-bom-5.9.1.pom[90m (5.6 kB at 938 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/mockito/mockito-all/1.10.19/mockito-all-1.10.19.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/mockito/mockito-all/1.10.19/mockito-all-1.10.19.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/mockito/mockito-all/1.10.19/mockito-all-1.10.19.pom[90m (930 B at 133 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jbibtex/jbibtex/1.0.19/jbibtex-1.0.19.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jbibtex/jbibtex/1.0.19/jbibtex-1.0.19.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jbibtex/jbibtex/1.0.19/jbibtex-1.0.19.pom[90m (4.7 kB at 51 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/guava/guava/33.4.8-jre/guava-33.4.8-jre.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/33.4.8-jre/guava-33.4.8-jre.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/33.4.8-jre/guava-33.4.8-jre.pom[90m (9.6 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/guava/guava-parent/33.4.8-jre/guava-parent-33.4.8-jre.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/33.4.8-jre/guava-parent-33.4.8-jre.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/33.4.8-jre/guava-parent-33.4.8-jre.pom[90m (25 kB at 3.5 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/guava/failureaccess/1.0.3/failureaccess-1.0.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.3/failureaccess-1.0.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.3/failureaccess-1.0.3.pom[90m (5.6 kB at 794 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/guava/guava-parent/33.4.0-android/guava-parent-33.4.0-android.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/33.4.0-android/guava-parent-33.4.0-android.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/33.4.0-android/guava-parent-33.4.0-android.pom[90m (22 kB at 3.1 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jspecify/jspecify/1.0.0/jspecify-1.0.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jspecify/jspecify/1.0.0/jspecify-1.0.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jspecify/jspecify/1.0.0/jspecify-1.0.0.pom[90m (1.5 kB at 252 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/errorprone/error_prone_annotations/2.36.0/error_prone_annotations-2.36.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.36.0/error_prone_annotations-2.36.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.36.0/error_prone_annotations-2.36.0.pom[90m (4.3 kB at 607 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/errorprone/error_prone_parent/2.36.0/error_prone_parent-2.36.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_parent/2.36.0/error_prone_parent-2.36.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_parent/2.36.0/error_prone_parent-2.36.0.pom[90m (16 kB at 2.7 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/j2objc/j2objc-annotations/3.0.0/j2objc-annotations-3.0.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/3.0.0/j2objc-annotations-3.0.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/3.0.0/j2objc-annotations-3.0.0.pom[90m (5.1 kB at 843 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/microsoft/onnxruntime/onnxruntime/1.17.0/onnxruntime-1.17.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/microsoft/onnxruntime/onnxruntime/1.17.0/onnxruntime-1.17.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/microsoft/onnxruntime/onnxruntime/1.17.0/onnxruntime-1.17.0.pom[90m (1.7 kB at 187 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mai/djl/huggingface/tokenizers/0.33.0/tokenizers-0.33.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/huggingface/tokenizers/0.33.0/tokenizers-0.33.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/huggingface/tokenizers/0.33.0/tokenizers-0.33.0.pom[90m (1.5 kB at 208 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mai/djl/api/0.33.0/api-0.33.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/api/0.33.0/api-0.33.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/api/0.33.0/api-0.33.0.pom[90m (2.1 kB at 260 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/code/gson/gson/2.13.1/gson-2.13.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/gson/gson/2.13.1/gson-2.13.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/gson/gson/2.13.1/gson-2.13.1.pom[90m (13 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/code/gson/gson-parent/2.13.1/gson-parent-2.13.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/gson/gson-parent/2.13.1/gson-parent-2.13.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/gson/gson-parent/2.13.1/gson-parent-2.13.1.pom[90m (27 kB at 3.4 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/errorprone/error_prone_annotations/2.38.0/error_prone_annotations-2.38.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.38.0/error_prone_annotations-2.38.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.38.0/error_prone_annotations-2.38.0.pom[90m (4.3 kB at 607 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/errorprone/error_prone_parent/2.38.0/error_prone_parent-2.38.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_parent/2.38.0/error_prone_parent-2.38.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_parent/2.38.0/error_prone_parent-2.38.0.pom[90m (16 kB at 2.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mnet/java/dev/jna/jna/5.14.0/jna-5.14.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mnet/java/dev/jna/jna/5.14.0/jna-5.14.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mnet/java/dev/jna/jna/5.14.0/jna-5.14.0.pom[90m (2.0 kB at 290 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-compress/1.27.1/commons-compress-1.27.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.27.1/commons-compress-1.27.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.27.1/commons-compress-1.27.1.pom[90m (23 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/72/commons-parent-72.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/72/commons-parent-72.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/72/commons-parent-72.pom[90m (78 kB at 9.7 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/apache/33/apache-33.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/33/apache-33.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/33/apache-33.pom[90m (24 kB at 3.5 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/junit/junit-bom/5.11.0-M2/junit-bom-5.11.0-M2.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.11.0-M2/junit-bom-5.11.0-M2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.11.0-M2/junit-bom-5.11.0-M2.pom[90m (5.7 kB at 80 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcommons-codec/commons-codec/1.17.1/commons-codec-1.17.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.17.1/commons-codec-1.17.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.17.1/commons-codec-1.17.1.pom[90m (18 kB at 1.5 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-parent/71/commons-parent-71.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/71/commons-parent-71.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/71/commons-parent-71.pom[90m (78 kB at 9.7 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-api/2.0.17/slf4j-api-2.0.17.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/2.0.17/slf4j-api-2.0.17.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/2.0.17/slf4j-api-2.0.17.pom[90m (2.8 kB at 353 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-parent/2.0.17/slf4j-parent-2.0.17.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/2.0.17/slf4j-parent-2.0.17.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/2.0.17/slf4j-parent-2.0.17.pom[90m (13 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-bom/2.0.17/slf4j-bom-2.0.17.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-bom/2.0.17/slf4j-bom-2.0.17.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-bom/2.0.17/slf4j-bom-2.0.17.pom[90m (7.3 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mme/tongfei/progressbar/0.10.1/progressbar-0.10.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mme/tongfei/progressbar/0.10.1/progressbar-0.10.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mme/tongfei/progressbar/0.10.1/progressbar-0.10.1.pom[90m (9.9 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jline/jline-terminal/3.24.1/jline-terminal-3.24.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-terminal/3.24.1/jline-terminal-3.24.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-terminal/3.24.1/jline-terminal-3.24.1.pom[90m (2.0 kB at 290 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jline/jline-parent/3.24.1/jline-parent-3.24.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-parent/3.24.1/jline-parent-3.24.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-parent/3.24.1/jline-parent-3.24.1.pom[90m (32 kB at 4.6 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jline/jline-native/3.24.1/jline-native-3.24.1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-native/3.24.1/jline-native-3.24.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-native/3.24.1/jline-native-3.24.1.pom[90m (4.2 kB at 605 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcommons-codec/commons-codec/1.15/commons-codec-1.15.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.15/commons-codec-1.15.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.15/commons-codec-1.15.pom[90m (15 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mblue/strategic/parquet/parquet-floor/1.36/parquet-floor-1.36.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mblue/strategic/parquet/parquet-floor/1.36/parquet-floor-1.36.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mblue/strategic/parquet/parquet-floor/1.36/parquet-floor-1.36.pom[90m (4.9 kB at 705 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-column/1.12.3/parquet-column-1.12.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-column/1.12.3/parquet-column-1.12.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-column/1.12.3/parquet-column-1.12.3.pom[90m (6.0 kB at 850 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet/1.12.3/parquet-1.12.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet/1.12.3/parquet-1.12.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet/1.12.3/parquet-1.12.3.pom[90m (23 kB at 2.5 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-common/1.12.3/parquet-common-1.12.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-common/1.12.3/parquet-common-1.12.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-common/1.12.3/parquet-common-1.12.3.pom[90m (3.4 kB at 428 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-format-structures/1.12.3/parquet-format-structures-1.12.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-format-structures/1.12.3/parquet-format-structures-1.12.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-format-structures/1.12.3/parquet-format-structures-1.12.3.pom[90m (6.7 kB at 836 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-api/1.7.22/slf4j-api-1.7.22.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.22/slf4j-api-1.7.22.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.22/slf4j-api-1.7.22.pom[90m (2.8 kB at 396 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-parent/1.7.22/slf4j-parent-1.7.22.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/1.7.22/slf4j-parent-1.7.22.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-parent/1.7.22/slf4j-parent-1.7.22.pom[90m (14 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-encoding/1.12.3/parquet-encoding-1.12.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-encoding/1.12.3/parquet-encoding-1.12.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-encoding/1.12.3/parquet-encoding-1.12.3.pom[90m (3.2 kB at 405 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/yetus/audience-annotations/0.13.0/audience-annotations-0.13.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/yetus/audience-annotations/0.13.0/audience-annotations-0.13.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/yetus/audience-annotations/0.13.0/audience-annotations-0.13.0.pom[90m (2.8 kB at 468 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/yetus/yetus-project/0.13.0/yetus-project-0.13.0.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/yetus/yetus-project/0.13.0/yetus-project-0.13.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/yetus/yetus-project/0.13.0/yetus-project-0.13.0.pom[90m (11 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-hadoop/1.12.3/parquet-hadoop-1.12.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-hadoop/1.12.3/parquet-hadoop-1.12.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-hadoop/1.12.3/parquet-hadoop-1.12.3.pom[90m (15 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-jackson/1.12.3/parquet-jackson-1.12.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-jackson/1.12.3/parquet-jackson-1.12.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-jackson/1.12.3/parquet-jackson-1.12.3.pom[90m (3.3 kB at 407 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/xerial/snappy/snappy-java/1.1.8.3/snappy-java-1.1.8.3.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/xerial/snappy/snappy-java/1.1.8.3/snappy-java-1.1.8.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/xerial/snappy/snappy-java/1.1.8.3/snappy-java-1.1.8.3.pom[90m (3.5 kB at 391 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/github/luben/zstd-jni/1.5.0-1/zstd-jni-1.5.0-1.pom
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.0-1/zstd-jni-1.5.0-1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.0-1/zstd-jni-1.5.0-1.pom[90m (1.9 kB at 272 kB/s)[0m
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-core/9.9.1/lucene-core-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-codecs/9.9.1/lucene-codecs-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-backward-codecs/9.9.1/lucene-backward-codecs-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-queries/9.9.1/lucene-queries-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-queryparser/9.9.1/lucene-queryparser-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-sandbox/9.9.1/lucene-sandbox-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-analysis-common/9.9.1/lucene-analysis-common-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-analysis-kuromoji/9.9.1/lucene-analysis-kuromoji-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-analysis-morfologik/9.9.1/lucene-analysis-morfologik-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/carrot2/morfologik-stemming/2.1.9/morfologik-stemming-2.1.9.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/carrot2/morfologik-fsa/2.1.9/morfologik-fsa-2.1.9.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/carrot2/morfologik-polish/2.1.9/morfologik-polish-2.1.9.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mua/net/nlp/morfologik-ukrainian-search/4.9.1/morfologik-ukrainian-search-4.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/lucene/lucene-test-framework/9.9.1/lucene-test-framework-9.9.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-runner/2.8.1/randomizedtesting-runner-2.8.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/hamcrest/hamcrest/2.2/hamcrest-2.2.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mjunit/junit/4.13.2/junit-4.13.2.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/tukaani/xz/1.9/xz-1.9.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-core/2.16.0/jackson-core-2.16.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.0/jackson-databind-2.16.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.0/jackson-annotations-2.16.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.16.0/jackson-datatype-jdk8-2.16.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/fasterxml/jackson/dataformat/jackson-dataformat-yaml/2.16.0/jackson-dataformat-yaml-2.16.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/yaml/snakeyaml/2.2/snakeyaml-2.2.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jsoup/jsoup/1.15.3/jsoup-1.15.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0margs4j/args4j/2.33/args4j-2.33.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/logging/log4j/log4j-api/2.23.1/log4j-api-2.23.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/logging/log4j/log4j-core/2.23.1/log4j-core-2.23.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-simple/1.7.32/slf4j-simple-1.7.32.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/slf4j/slf4j-api/1.7.32/slf4j-api-1.7.32.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mit/unimi/dsi/fastutil/8.5.8/fastutil-8.5.8.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/wikiclean/wikiclean/1.1/wikiclean-1.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-lang3/3.5/commons-lang3-3.5.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant/1.10.11/ant-1.10.11.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/ant/ant-launcher/1.10.11/ant-launcher-1.10.11.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/twitter/twittertext/twitter-text/2.0.10/twitter-text-2.0.10.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/github/TREMA-UNH/trec-car-tools-java/19/trec-car-tools-java-19.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mco/nstant/in/cbor/0.8/cbor-0.8.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcommons-io/commons-io/2.16.1/commons-io-2.16.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-compress/1.26.2/commons-compress-1.26.2.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-csv/1.8/commons-csv-1.8.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/commons/commons-text/1.10.0/commons-text-1.10.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/mockito/mockito-all/1.10.19/mockito-all-1.10.19.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jbibtex/jbibtex/1.0.19/jbibtex-1.0.19.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/guava/guava/33.4.8-jre/guava-33.4.8-jre.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/guava/failureaccess/1.0.3/failureaccess-1.0.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jspecify/jspecify/1.0.0/jspecify-1.0.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/errorprone/error_prone_annotations/2.36.0/error_prone_annotations-2.36.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/google/j2objc/j2objc-annotations/3.0.0/j2objc-annotations-3.0.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/microsoft/onnxruntime/onnxruntime/1.17.0/onnxruntime-1.17.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mai/djl/huggingface/tokenizers/0.33.0/tokenizers-0.33.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mai/djl/api/0.33.0/api-0.33.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mme/tongfei/progressbar/0.10.1/progressbar-0.10.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jline/jline-terminal/3.24.1/jline-terminal-3.24.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/jline/jline-native/3.24.1/jline-native-3.24.1.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcommons-codec/commons-codec/1.15/commons-codec-1.15.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mblue/strategic/parquet/parquet-floor/1.36/parquet-floor-1.36.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-column/1.12.3/parquet-column-1.12.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-common/1.12.3/parquet-common-1.12.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-encoding/1.12.3/parquet-encoding-1.12.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/yetus/audience-annotations/0.13.0/audience-annotations-0.13.0.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-hadoop/1.12.3/parquet-hadoop-1.12.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-format-structures/1.12.3/parquet-format-structures-1.12.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/apache/parquet/parquet-jackson/1.12.3/parquet-jackson-1.12.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0morg/xerial/snappy/snappy-java/1.1.8.3/snappy-java-1.1.8.3.jar
    [90mDownloading from [0mjitpack.io[90m: https://jitpack.io/[0mcom/github/luben/zstd-jni/1.5.0-1/zstd-jni-1.5.0-1.jar
    Downloaded[90m from [0mjitpack.io[90m: https://jitpack.io/[0mcom/github/TREMA-UNH/trec-car-tools-java/19/trec-car-tools-java-19.jar[90m (69 kB at 90 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-core/9.9.1/lucene-core-9.9.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-core/9.9.1/lucene-core-9.9.1.jar[90m (4.0 MB at 24 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-codecs/9.9.1/lucene-codecs-9.9.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-backward-codecs/9.9.1/lucene-backward-codecs-9.9.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queries/9.9.1/lucene-queries-9.9.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queryparser/9.9.1/lucene-queryparser-9.9.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-sandbox/9.9.1/lucene-sandbox-9.9.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-backward-codecs/9.9.1/lucene-backward-codecs-9.9.1.jar[90m (700 kB at 12 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-sandbox/9.9.1/lucene-sandbox-9.9.1.jar[90m (236 kB at 4.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-common/9.9.1/lucene-analysis-common-9.9.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queries/9.9.1/lucene-queries-9.9.1.jar[90m (519 kB at 8.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-kuromoji/9.9.1/lucene-analysis-kuromoji-9.9.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-morfologik/9.9.1/lucene-analysis-morfologik-9.9.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-queryparser/9.9.1/lucene-queryparser-9.9.1.jar[90m (426 kB at 6.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-stemming/2.1.9/morfologik-stemming-2.1.9.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-stemming/2.1.9/morfologik-stemming-2.1.9.jar[90m (52 kB at 636 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-fsa/2.1.9/morfologik-fsa-2.1.9.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-fsa/2.1.9/morfologik-fsa-2.1.9.jar[90m (19 kB at 210 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-polish/2.1.9/morfologik-polish-2.1.9.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-codecs/9.9.1/lucene-codecs-9.9.1.jar[90m (465 kB at 3.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mua/net/nlp/morfologik-ukrainian-search/4.9.1/morfologik-ukrainian-search-4.9.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-morfologik/9.9.1/lucene-analysis-morfologik-9.9.1.jar[90m (30 kB at 213 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-test-framework/9.9.1/lucene-test-framework-9.9.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-common/9.9.1/lucene-analysis-common-9.9.1.jar[90m (1.7 MB at 9.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-runner/2.8.1/randomizedtesting-runner-2.8.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/carrotsearch/randomizedtesting/randomizedtesting-runner/2.8.1/randomizedtesting-runner-2.8.1.jar[90m (251 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest/2.2/hamcrest-2.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/carrot2/morfologik-polish/2.1.9/morfologik-polish-2.1.9.jar[90m (1.9 MB at 8.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/4.13.2/junit-4.13.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest/2.2/hamcrest-2.2.jar[90m (123 kB at 506 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar[90m (45 kB at 179 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/tukaani/xz/1.9/xz-1.9.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/tukaani/xz/1.9/xz-1.9.jar[90m (116 kB at 431 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.0/jackson-core-2.16.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/4.13.2/junit-4.13.2.jar[90m (385 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.0/jackson-databind-2.16.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-core/2.16.0/jackson-core-2.16.0.jar[90m (579 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.0/jackson-annotations-2.16.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-annotations/2.16.0/jackson-annotations-2.16.0.jar[90m (78 kB at 214 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.16.0/jackson-datatype-jdk8-2.16.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.16.0/jackson-datatype-jdk8-2.16.0.jar[90m (36 kB at 95 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/dataformat/jackson-dataformat-yaml/2.16.0/jackson-dataformat-yaml-2.16.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/dataformat/jackson-dataformat-yaml/2.16.0/jackson-dataformat-yaml-2.16.0.jar[90m (55 kB at 141 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/yaml/snakeyaml/2.2/snakeyaml-2.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/fasterxml/jackson/core/jackson-databind/2.16.0/jackson-databind-2.16.0.jar[90m (1.6 MB at 3.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jsoup/jsoup/1.15.3/jsoup-1.15.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/yaml/snakeyaml/2.2/snakeyaml-2.2.jar[90m (334 kB at 751 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0margs4j/args4j/2.33/args4j-2.33.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0margs4j/args4j/2.33/args4j-2.33.jar[90m (155 kB at 331 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jsoup/jsoup/1.15.3/jsoup-1.15.3.jar[90m (438 kB at 926 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-api/2.23.1/log4j-api-2.23.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-core/2.23.1/log4j-core-2.23.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-api/2.23.1/log4j-api-2.23.1.jar[90m (343 kB at 678 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-simple/1.7.32/slf4j-simple-1.7.32.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-simple/1.7.32/slf4j-simple-1.7.32.jar[90m (15 kB at 29 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.32/slf4j-api-1.7.32.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mua/net/nlp/morfologik-ukrainian-search/4.9.1/morfologik-ukrainian-search-4.9.1.jar[90m (4.1 MB at 7.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mit/unimi/dsi/fastutil/8.5.8/fastutil-8.5.8.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/slf4j/slf4j-api/1.7.32/slf4j-api-1.7.32.jar[90m (42 kB at 77 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/wikiclean/wikiclean/1.1/wikiclean-1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/logging/log4j/log4j-core/2.23.1/log4j-core-2.23.1.jar[90m (1.9 MB at 3.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.5/commons-lang3-3.5.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/wikiclean/wikiclean/1.1/wikiclean-1.1.jar[90m (27 kB at 43 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant/1.10.11/ant-1.10.11.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.5/commons-lang3-3.5.jar[90m (480 kB at 705 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-launcher/1.10.11/ant-launcher-1.10.11.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant-launcher/1.10.11/ant-launcher-1.10.11.jar[90m (19 kB at 27 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/twitter/twittertext/twitter-text/2.0.10/twitter-text-2.0.10.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-analysis-kuromoji/9.9.1/lucene-analysis-kuromoji-9.9.1.jar[90m (4.7 MB at 6.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/code/findbugs/jsr305/2.0.1/jsr305-2.0.1.jar[90m (32 kB at 43 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mco/nstant/in/cbor/0.8/cbor-0.8.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mco/nstant/in/cbor/0.8/cbor-0.8.jar[90m (71 kB at 94 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jetbrains/annotations-java5/24.1.0/annotations-java5-24.1.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jetbrains/annotations-java5/24.1.0/annotations-java5-24.1.0.jar[90m (28 kB at 36 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.16.1/commons-io-2.16.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/ant/ant/1.10.11/ant-1.10.11.jar[90m (2.3 MB at 3.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.2/commons-compress-1.26.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/twitter/twittertext/twitter-text/2.0.10/twitter-text-2.0.10.jar[90m (99 kB at 125 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-csv/1.8/commons-csv-1.8.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-csv/1.8/commons-csv-1.8.jar[90m (49 kB at 62 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.10.0/commons-text-1.10.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.10.0/commons-text-1.10.0.jar[90m (238 kB at 290 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/mockito/mockito-all/1.10.19/mockito-all-1.10.19.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.16.1/commons-io-2.16.1.jar[90m (509 kB at 613 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jbibtex/jbibtex/1.0.19/jbibtex-1.0.19.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jbibtex/jbibtex/1.0.19/jbibtex-1.0.19.jar[90m (75 kB at 89 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/33.4.8-jre/guava-33.4.8-jre.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.2/commons-compress-1.26.2.jar[90m (1.1 MB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.3/failureaccess-1.0.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/failureaccess/1.0.3/failureaccess-1.0.3.jar[90m (11 kB at 12 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jspecify/jspecify/1.0.0/jspecify-1.0.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jspecify/jspecify/1.0.0/jspecify-1.0.0.jar[90m (3.8 kB at 4.2 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.36.0/error_prone_annotations-2.36.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/errorprone/error_prone_annotations/2.36.0/error_prone_annotations-2.36.0.jar[90m (19 kB at 22 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/3.0.0/j2objc-annotations-3.0.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/j2objc/j2objc-annotations/3.0.0/j2objc-annotations-3.0.0.jar[90m (12 kB at 14 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/microsoft/onnxruntime/onnxruntime/1.17.0/onnxruntime-1.17.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/mockito/mockito-all/1.10.19/mockito-all-1.10.19.jar[90m (1.2 MB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/huggingface/tokenizers/0.33.0/tokenizers-0.33.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/33.4.8-jre/guava-33.4.8-jre.jar[90m (3.0 MB at 2.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/api/0.33.0/api-0.33.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/api/0.33.0/api-0.33.0.jar[90m (973 kB at 800 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mme/tongfei/progressbar/0.10.1/progressbar-0.10.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mme/tongfei/progressbar/0.10.1/progressbar-0.10.1.jar[90m (38 kB at 31 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-terminal/3.24.1/jline-terminal-3.24.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-terminal/3.24.1/jline-terminal-3.24.1.jar[90m (259 kB at 209 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-native/3.24.1/jline-native-3.24.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jline/jline-native/3.24.1/jline-native-3.24.1.jar[90m (188 kB at 149 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.15/commons-codec-1.15.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.15/commons-codec-1.15.jar[90m (354 kB at 268 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mblue/strategic/parquet/parquet-floor/1.36/parquet-floor-1.36.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mblue/strategic/parquet/parquet-floor/1.36/parquet-floor-1.36.jar[90m (40 kB at 30 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-column/1.12.3/parquet-column-1.12.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-column/1.12.3/parquet-column-1.12.3.jar[90m (2.0 MB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-common/1.12.3/parquet-common-1.12.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-common/1.12.3/parquet-common-1.12.3.jar[90m (96 kB at 63 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-encoding/1.12.3/parquet-encoding-1.12.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/lucene/lucene-test-framework/9.9.1/lucene-test-framework-9.9.1.jar[90m (11 MB at 7.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/yetus/audience-annotations/0.13.0/audience-annotations-0.13.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/yetus/audience-annotations/0.13.0/audience-annotations-0.13.0.jar[90m (21 kB at 13 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-hadoop/1.12.3/parquet-hadoop-1.12.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-encoding/1.12.3/parquet-encoding-1.12.3.jar[90m (848 kB at 518 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-format-structures/1.12.3/parquet-format-structures-1.12.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-hadoop/1.12.3/parquet-hadoop-1.12.3.jar[90m (991 kB at 570 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-jackson/1.12.3/parquet-jackson-1.12.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-format-structures/1.12.3/parquet-format-structures-1.12.3.jar[90m (726 kB at 417 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/xerial/snappy/snappy-java/1.1.8.3/snappy-java-1.1.8.3.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/parquet/parquet-jackson/1.12.3/parquet-jackson-1.12.3.jar[90m (2.0 MB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.0-1/zstd-jni-1.5.0-1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/xerial/snappy/snappy-java/1.1.8.3/snappy-java-1.1.8.3.jar[90m (2.0 MB at 1.0 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mit/unimi/dsi/fastutil/8.5.8/fastutil-8.5.8.jar[90m (23 MB at 9.7 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.0-1/zstd-jni-1.5.0-1.jar[90m (6.7 MB at 2.8 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mai/djl/huggingface/tokenizers/0.33.0/tokenizers-0.33.0.jar[90m (19 MB at 7.5 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/microsoft/onnxruntime/onnxruntime/1.17.0/onnxruntime-1.17.0.jar[90m (88 MB at 25 MB/s)[0m
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mclean:3.2.0:clean[m [1m(default-clean)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.3.4/maven-shared-utils-3.3.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.3.4/maven-shared-utils-3.3.4.pom[90m (5.8 kB at 530 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/34/maven-shared-components-34.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/34/maven-shared-components-34.pom[90m (5.1 kB at 637 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/34/maven-parent-34.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/34/maven-parent-34.pom[90m (43 kB at 5.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.6/commons-io-2.6.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.6/commons-io-2.6.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/42/commons-parent-42.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/42/commons-parent-42.pom[90m (68 kB at 8.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.3.4/maven-shared-utils-3.3.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.3.4/maven-shared-utils-3.3.4.jar[90m (153 kB at 17 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.6/commons-io-2.6.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.6/commons-io-2.6.jar[90m (215 kB at 17 MB/s)[0m
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mjacoco:0.8.11:prepare-agent[m [1m(default)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.0.24/plexus-utils-3.0.24.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.0.24/plexus-utils-3.0.24.pom[90m (4.1 kB at 516 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/4.0/plexus-4.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/4.0/plexus-4.0.pom[90m (22 kB at 2.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/10/forge-parent-10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/10/forge-parent-10.pom[90m (14 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/file-management/3.1.0/file-management-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/file-management/3.1.0/file-management-3.1.0.pom[90m (4.5 kB at 641 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/36/maven-shared-components-36.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/36/maven-shared-components-36.pom[90m (4.9 kB at 699 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/36/maven-parent-36.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/36/maven-parent-36.pom[90m (45 kB at 6.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/26/apache-26.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/26/apache-26.pom[90m (21 kB at 2.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.4.2/plexus-utils-3.4.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.4.2/plexus-utils-3.4.2.pom[90m (8.2 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/8/plexus-8.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/8/plexus-8.pom[90m (25 kB at 3.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.11.0/commons-io-2.11.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.11.0/commons-io-2.11.0.pom[90m (20 kB at 2.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.7.2/junit-bom-5.7.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/junit/junit-bom/5.7.2/junit-bom-5.7.2.pom[90m (5.1 kB at 728 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.0/maven-reporting-api-3.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.0/maven-reporting-api-3.0.pom[90m (2.4 kB at 339 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/15/maven-shared-components-15.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/15/maven-shared-components-15.pom[90m (9.3 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/16/maven-parent-16.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/16/maven-parent-16.pom[90m (23 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/7/apache-7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/7/apache-7.pom[90m (14 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.0/doxia-sink-api-1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.0/doxia-sink-api-1.0.pom[90m (1.4 kB at 198 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia/1.0/doxia-1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia/1.0/doxia-1.0.pom[90m (9.6 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/10/maven-parent-10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/10/maven-parent-10.pom[90m (32 kB at 4.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/4/apache-4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/4/apache-4.pom[90m (4.5 kB at 409 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.agent/0.8.11/org.jacoco.agent-0.8.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.agent/0.8.11/org.jacoco.agent-0.8.11.pom[90m (3.5 kB at 584 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.core/0.8.11/org.jacoco.core-0.8.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.core/0.8.11/org.jacoco.core-0.8.11.pom[90m (2.1 kB at 348 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.6/asm-9.6.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.6/asm-9.6.pom[90m (2.4 kB at 339 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.6/asm-commons-9.6.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.6/asm-commons-9.6.pom[90m (2.8 kB at 398 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.6/asm-tree-9.6.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.6/asm-tree-9.6.pom[90m (2.6 kB at 199 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.report/0.8.11/org.jacoco.report-0.8.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.report/0.8.11/org.jacoco.report-0.8.11.pom[90m (1.9 kB at 269 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.0.24/plexus-utils-3.0.24.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.0.24/plexus-utils-3.0.24.jar[90m (247 kB at 19 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/file-management/3.1.0/file-management-3.1.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.11.0/commons-io-2.11.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.0/maven-reporting-api-3.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.0/doxia-sink-api-1.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.agent/0.8.11/org.jacoco.agent-0.8.11-runtime.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/file-management/3.1.0/file-management-3.1.0.jar[90m (36 kB at 3.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.core/0.8.11/org.jacoco.core-0.8.11.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.0/maven-reporting-api-3.0.jar[90m (11 kB at 995 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.6/asm-9.6.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.0/doxia-sink-api-1.0.jar[90m (10 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.6/asm-commons-9.6.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.11.0/commons-io-2.11.0.jar[90m (327 kB at 23 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.6/asm-tree-9.6.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.6/asm-commons-9.6.jar[90m (72 kB at 4.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.report/0.8.11/org.jacoco.report-0.8.11.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.6/asm-9.6.jar[90m (124 kB at 6.5 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.6/asm-tree-9.6.jar[90m (52 kB at 2.7 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.core/0.8.11/org.jacoco.core-0.8.11.jar[90m (210 kB at 10 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.agent/0.8.11/org.jacoco.agent-0.8.11-runtime.jar[90m (301 kB at 12 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jacoco/org.jacoco.report/0.8.11/org.jacoco.report-0.8.11.jar[90m (131 kB at 4.5 MB/s)[0m
    [[1;34mINFO[m] argLine set to -javaagent:/root/.m2/repository/org/jacoco/org.jacoco.agent/0.8.11/org.jacoco.agent-0.8.11-runtime.jar=destfile=/content/anserini/target/jacoco.exec
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mresources:3.3.1:resources[m [1m(default-resources)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.26/plexus-interpolation-1.26.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.26/plexus-interpolation-1.26.pom[90m (2.7 kB at 379 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/5.1/plexus-5.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/5.1/plexus-5.1.pom[90m (23 kB at 3.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-filtering/3.3.1/maven-filtering-3.3.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-filtering/3.3.1/maven-filtering-3.3.1.pom[90m (6.0 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/39/maven-shared-components-39.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/39/maven-shared-components-39.pom[90m (3.2 kB at 537 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/inject/javax.inject/1/javax.inject-1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/inject/javax.inject/1/javax.inject-1.pom[90m (612 B at 41 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-build-api/0.0.7/plexus-build-api-0.0.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-build-api/0.0.7/plexus-build-api-0.0.7.pom[90m (3.2 kB at 458 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/spice/spice-parent/15/spice-parent-15.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/spice/spice-parent/15/spice-parent-15.pom[90m (8.4 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/5/forge-parent-5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/5/forge-parent-5.pom[90m (8.4 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.5.0/plexus-utils-3.5.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.5.0/plexus-utils-3.5.0.pom[90m (8.0 kB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.26/plexus-interpolation-1.26.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.26/plexus-interpolation-1.26.jar[90m (85 kB at 12 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-filtering/3.3.1/maven-filtering-3.3.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/inject/javax.inject/1/javax.inject-1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-build-api/0.0.7/plexus-build-api-0.0.7.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-filtering/3.3.1/maven-filtering-3.3.1.jar[90m (55 kB at 6.9 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/inject/javax.inject/1/javax.inject-1.jar[90m (2.5 kB at 312 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-build-api/0.0.7/plexus-build-api-0.0.7.jar[90m (8.5 kB at 1.1 MB/s)[0m
    [[1;34mINFO[m] Copying 1769 resources from src/main/resources to target/classes
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mcompiler:3.12.1:compile[m [1m(default-compile)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.4.2/maven-shared-utils-3.4.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.4.2/maven-shared-utils-3.4.2.pom[90m (5.9 kB at 100 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.pom[90m (4.7 kB at 339 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/19/maven-shared-components-19.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/19/maven-shared-components-19.pom[90m (6.4 kB at 908 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/23/maven-parent-23.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/23/maven-parent-23.pom[90m (33 kB at 4.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.pom[90m (815 B at 116 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/1.5.5/plexus-containers-1.5.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/1.5.5/plexus-containers-1.5.5.pom[90m (4.2 kB at 707 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/2.0.7/plexus-2.0.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/2.0.7/plexus-2.0.7.pom[90m (17 kB at 2.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.2.0/plexus-java-1.2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.2.0/plexus-java-1.2.0.pom[90m (4.3 kB at 534 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-languages/1.2.0/plexus-languages-1.2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-languages/1.2.0/plexus-languages-1.2.0.pom[90m (3.2 kB at 532 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/15/plexus-15.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/15/plexus-15.pom[90m (28 kB at 4.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/thoughtworks/qdox/qdox/2.0.3/qdox-2.0.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/thoughtworks/qdox/qdox/2.0.3/qdox-2.0.3.pom[90m (17 kB at 2.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-api/2.14.2/plexus-compiler-api-2.14.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-api/2.14.2/plexus-compiler-api-2.14.2.pom[90m (1.4 kB at 195 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler/2.14.2/plexus-compiler-2.14.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler/2.14.2/plexus-compiler-2.14.2.pom[90m (8.1 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/16/plexus-16.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/16/plexus-16.pom[90m (28 kB at 3.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.0/plexus-utils-4.0.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.0/plexus-utils-4.0.0.pom[90m (8.7 kB at 962 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/13/plexus-13.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/13/plexus-13.pom[90m (27 kB at 3.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-manager/2.14.2/plexus-compiler-manager-2.14.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-manager/2.14.2/plexus-compiler-manager-2.14.2.pom[90m (1.2 kB at 177 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-xml/3.0.0/plexus-xml-3.0.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-xml/3.0.0/plexus-xml-3.0.0.pom[90m (3.7 kB at 623 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-javac/2.14.2/plexus-compiler-javac-2.14.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-javac/2.14.2/plexus-compiler-javac-2.14.2.pom[90m (1.3 kB at 190 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compilers/2.14.2/plexus-compilers-2.14.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compilers/2.14.2/plexus-compilers-2.14.2.pom[90m (1.3 kB at 160 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.4.2/maven-shared-utils-3.4.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.4.2/maven-shared-utils-3.4.2.jar[90m (151 kB at 15 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/thoughtworks/qdox/qdox/2.0.3/qdox-2.0.3.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.2.0/plexus-java-1.2.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-api/2.14.2/plexus-compiler-api-2.14.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-incremental/1.1/maven-shared-incremental-1.1.jar[90m (14 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-manager/2.14.2/plexus-compiler-manager-2.14.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.2.0/plexus-java-1.2.0.jar[90m (58 kB at 6.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-xml/3.0.0/plexus-xml-3.0.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-api/2.14.2/plexus-compiler-api-2.14.2.jar[90m (29 kB at 2.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-javac/2.14.2/plexus-compiler-javac-2.14.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-manager/2.14.2/plexus-compiler-manager-2.14.2.jar[90m (4.4 kB at 341 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.0/plexus-utils-4.0.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/1.5.5/plexus-component-annotations-1.5.5.jar[90m (4.2 kB at 281 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-xml/3.0.0/plexus-xml-3.0.0.jar[90m (93 kB at 5.2 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-compiler-javac/2.14.2/plexus-compiler-javac-2.14.2.jar[90m (23 kB at 1.3 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.0/plexus-utils-4.0.0.jar[90m (192 kB at 8.7 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/thoughtworks/qdox/qdox/2.0.3/qdox-2.0.3.jar[90m (334 kB at 15 MB/s)[0m
    [[1;34mINFO[m] Recompiling the module because of [1mchanged source code[m.
    [[1;34mINFO[m] Compiling 189 source files with javac [debug deprecation target 21] to target/classes
    [[1;34mINFO[m] Annotation processing is enabled because one or more processors were found
      on the class path. A future release of javac may disable annotation processing
      unless at least one processor is specified by name (-processor), or a search
      path is specified (--processor-path, --processor-module-path), or annotation
      processing is enabled explicitly (-proc:only, -proc:full).
      Use -Xlint:-options to suppress this message.
      Use -proc:none to disable annotation processing.
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/util/PrebuiltIndexHandler.java:[160,9] org.apache.commons.io.input.CountingInputStream in org.apache.commons.io.input has been deprecated
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/util/PrebuiltIndexHandler.java:[160,39] org.apache.commons.io.input.CountingInputStream in org.apache.commons.io.input has been deprecated
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/HtmlCollection.java:[78,47] ReaderInputStream(java.io.Reader,java.nio.charset.Charset) in org.apache.commons.io.input.ReaderInputStream has been deprecated
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/rerank/GenerateRerankerRequests.java:[104,54] unchecked conversion
      required: java.util.Map<java.lang.String,java.lang.Object>
      found:    java.util.Map
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/rerank/GenerateRerankerRequests.java:[147,28] unchecked cast
      required: K
      found:    java.lang.String
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/rerank/GenerateRerankerRequests.java:[155,22] unchecked cast
      required: K
      found:    java.lang.String
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/RunOutputWriter.java:[73,58] unchecked conversion
      required: java.util.Map<java.lang.String,java.lang.Object>
      found:    java.util.Map
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/CarCollection.java:[75,16] ReaderInputStream(java.io.Reader,java.nio.charset.Charset) in org.apache.commons.io.input.ReaderInputStream has been deprecated
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mresources:3.3.1:testResources[m [1m(default-testResources)[m @ [36manserini[0;1m ---[m
    [[1;34mINFO[m] Copying 254 resources from src/test/resources to target/test-classes
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mcompiler:3.12.1:testCompile[m [1m(default-testCompile)[m @ [36manserini[0;1m ---[m
    [[1;34mINFO[m] Recompiling the module because of [1mchanged dependency[m.
    [[1;34mINFO[m] Compiling 191 source files with javac [debug deprecation target 21] to target/test-classes
    [[1;34mINFO[m] Annotation processing is enabled because one or more processors were found
      on the class path. A future release of javac may disable annotation processing
      unless at least one processor is specified by name (-processor), or a search
      path is specified (--processor-path, --processor-module-path), or annotation
      processing is enabled explicitly (-proc:only, -proc:full).
      Use -Xlint:-options to suppress this message.
      Use -proc:none to disable annotation processing.
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32msurefire:3.1.0:test[m [1m(default-test)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/maven-surefire-common/3.1.0/maven-surefire-common-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/maven-surefire-common/3.1.0/maven-surefire-common-3.1.0.pom[90m (6.1 kB at 469 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-api/3.1.0/surefire-api-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-api/3.1.0/surefire-api-3.1.0.pom[90m (3.5 kB at 442 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-logger-api/3.1.0/surefire-logger-api-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-logger-api/3.1.0/surefire-logger-api-3.1.0.pom[90m (3.3 kB at 466 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-shared-utils/3.1.0/surefire-shared-utils-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-shared-utils/3.1.0/surefire-shared-utils-3.1.0.pom[90m (4.1 kB at 580 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-api/3.1.0/surefire-extensions-api-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-api/3.1.0/surefire-extensions-api-3.1.0.pom[90m (3.3 kB at 368 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-booter/3.1.0/surefire-booter-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-booter/3.1.0/surefire-booter-3.1.0.pom[90m (4.5 kB at 557 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-spi/3.1.0/surefire-extensions-spi-3.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-spi/3.1.0/surefire-extensions-spi-3.1.0.pom[90m (1.8 kB at 196 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-util/1.0.0.v20140518/aether-util-1.0.0.v20140518.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-util/1.0.0.v20140518/aether-util-1.0.0.v20140518.pom[90m (2.2 kB at 313 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether/1.0.0.v20140518/aether-1.0.0.v20140518.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether/1.0.0.v20140518/aether-1.0.0.v20140518.pom[90m (30 kB at 4.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-api/1.0.0.v20140518/aether-api-1.0.0.v20140518.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-api/1.0.0.v20140518/aether-api-1.0.0.v20140518.pom[90m (1.9 kB at 271 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.1.1/maven-common-artifact-filters-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.1.1/maven-common-artifact-filters-3.1.1.pom[90m (5.8 kB at 828 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.2.5/maven-artifact-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.2.5/maven-artifact-3.2.5.pom[90m (2.3 kB at 335 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven/3.2.5/maven-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven/3.2.5/maven-3.2.5.pom[90m (22 kB at 3.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/25/maven-parent-25.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/25/maven-parent-25.pom[90m (37 kB at 4.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/15/apache-15.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/15/apache-15.pom[90m (15 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-core/3.2.5/maven-core-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-core/3.2.5/maven-core-3.2.5.pom[90m (8.1 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings/3.2.5/maven-settings-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings/3.2.5/maven-settings-3.2.5.pom[90m (2.2 kB at 362 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings-builder/3.2.5/maven-settings-builder-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings-builder/3.2.5/maven-settings-builder-3.2.5.pom[90m (2.6 kB at 371 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.21/plexus-interpolation-1.21.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.21/plexus-interpolation-1.21.pom[90m (1.5 kB at 220 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/1.3.1/plexus-components-1.3.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/1.3.1/plexus-components-1.3.1.pom[90m (3.1 kB at 511 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/3.3.1/plexus-3.3.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/3.3.1/plexus-3.3.1.pom[90m (20 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/spice/spice-parent/17/spice-parent-17.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/spice/spice-parent/17/spice-parent-17.pom[90m (6.8 kB at 966 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-sec-dispatcher/1.3/plexus-sec-dispatcher-1.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-sec-dispatcher/1.3/plexus-sec-dispatcher-1.3.pom[90m (3.0 kB at 423 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/spice/spice-parent/12/spice-parent-12.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/spice/spice-parent/12/spice-parent-12.pom[90m (6.8 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/4/forge-parent-4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/4/forge-parent-4.pom[90m (8.4 kB at 1.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-cipher/1.4/plexus-cipher-1.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-cipher/1.4/plexus-cipher-1.4.pom[90m (2.1 kB at 206 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-repository-metadata/3.2.5/maven-repository-metadata-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-repository-metadata/3.2.5/maven-repository-metadata-3.2.5.pom[90m (2.2 kB at 279 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-plugin-api/3.2.5/maven-plugin-api-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-plugin-api/3.2.5/maven-plugin-api-3.2.5.pom[90m (3.0 kB at 432 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.plexus/0.3.5/org.eclipse.sisu.plexus-0.3.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.plexus/0.3.5/org.eclipse.sisu.plexus-0.3.5.pom[90m (4.3 kB at 714 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-plexus/0.3.5/sisu-plexus-0.3.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-plexus/0.3.5/sisu-plexus-0.3.5.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/annotation/javax.annotation-api/1.2/javax.annotation-api-1.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/annotation/javax.annotation-api/1.2/javax.annotation-api-1.2.pom[90m (13 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mnet/java/jvnet-parent/3/jvnet-parent-3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mnet/java/jvnet-parent/3/jvnet-parent-3.pom[90m (4.8 kB at 684 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/enterprise/cdi-api/1.2/cdi-api-1.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/enterprise/cdi-api/1.2/cdi-api-1.2.pom[90m (6.3 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jboss/weld/weld-parent/26/weld-parent-26.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jboss/weld/weld-parent/26/weld-parent-26.pom[90m (32 kB at 4.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.inject/0.3.5/org.eclipse.sisu.inject-0.3.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.inject/0.3.5/org.eclipse.sisu.inject-0.3.5.pom[90m (2.6 kB at 328 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-inject/0.3.5/sisu-inject-0.3.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-inject/0.3.5/sisu-inject-0.3.5.pom[90m (14 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.5.2/plexus-classworlds-2.5.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.5.2/plexus-classworlds-2.5.2.pom[90m (7.3 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model-builder/3.2.5/maven-model-builder-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model-builder/3.2.5/maven-model-builder-3.2.5.pom[90m (3.0 kB at 499 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-aether-provider/3.2.5/maven-aether-provider-3.2.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-aether-provider/3.2.5/maven-aether-provider-3.2.5.pom[90m (4.2 kB at 708 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-spi/1.0.0.v20140518/aether-spi-1.0.0.v20140518.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-spi/1.0.0.v20140518/aether-spi-1.0.0.v20140518.pom[90m (2.1 kB at 293 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-impl/1.0.0.v20140518/aether-impl-1.0.0.v20140518.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-impl/1.0.0.v20140518/aether-impl-1.0.0.v20140518.pom[90m (3.5 kB at 496 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/sisu/sisu-guice/3.2.3/sisu-guice-3.2.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/sisu/sisu-guice/3.2.3/sisu-guice-3.2.3.pom[90m (11 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/sisu/inject/guice-parent/3.2.3/guice-parent-3.2.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/sisu/inject/guice-parent/3.2.3/guice-parent-3.2.3.pom[90m (13 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/38/forge-parent-38.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/forge/forge-parent/38/forge-parent-38.pom[90m (19 kB at 3.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0maopalliance/aopalliance/1.0/aopalliance-1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0maopalliance/aopalliance/1.0/aopalliance-1.0.pom[90m (363 B at 52 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/16.0.1/guava-16.0.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava/16.0.1/guava-16.0.1.pom[90m (6.1 kB at 872 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/16.0.1/guava-parent-16.0.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/guava/guava-parent/16.0.1/guava-parent-16.0.1.pom[90m (7.3 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.1.2/plexus-java-1.1.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.1.2/plexus-java-1.1.2.pom[90m (5.0 kB at 710 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-languages/1.1.2/plexus-languages-1.1.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-languages/1.1.2/plexus-languages-1.1.2.pom[90m (4.1 kB at 592 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.4/asm-9.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.4/asm-9.4.pom[90m (2.4 kB at 296 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/maven-surefire-common/3.1.0/maven-surefire-common-3.1.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/maven-surefire-common/3.1.0/maven-surefire-common-3.1.0.jar[90m (306 kB at 19 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-api/3.1.0/surefire-api-3.1.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-logger-api/3.1.0/surefire-logger-api-3.1.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-api/3.1.0/surefire-extensions-api-3.1.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-booter/3.1.0/surefire-booter-3.1.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-spi/3.1.0/surefire-extensions-spi-3.1.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-logger-api/3.1.0/surefire-logger-api-3.1.0.jar[90m (14 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-util/1.0.0.v20140518/aether-util-1.0.0.v20140518.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-api/3.1.0/surefire-api-3.1.0.jar[90m (170 kB at 12 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-api/1.0.0.v20140518/aether-api-1.0.0.v20140518.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-booter/3.1.0/surefire-booter-3.1.0.jar[90m (118 kB at 7.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.1.1/maven-common-artifact-filters-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-util/1.0.0.v20140518/aether-util-1.0.0.v20140518.jar[90m (146 kB at 8.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.1.2/plexus-java-1.1.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-api/1.0.0.v20140518/aether-api-1.0.0.v20140518.jar[90m (136 kB at 5.5 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-spi/3.1.0/surefire-extensions-spi-3.1.0.jar[90m (8.2 kB at 302 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-extensions-api/3.1.0/surefire-extensions-api-3.1.0.jar[90m (26 kB at 891 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.4/asm-9.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-java/1.1.2/plexus-java-1.1.2.jar[90m (55 kB at 2.0 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.1.1/maven-common-artifact-filters-3.1.1.jar[90m (61 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-shared-utils/3.1.0/surefire-shared-utils-3.1.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.4/asm-9.4.jar[90m (122 kB at 3.5 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/surefire/surefire-shared-utils/3.1.0/surefire-shared-utils-3.1.0.jar[90m (2.1 MB at 28 MB/s)[0m
    [[1;34mINFO[m] Tests are skipped.
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mjacoco:0.8.11:report[m [1m(report)[m @ [36manserini[0;1m ---[m
    [[1;34mINFO[m] Skipping JaCoCo execution due to missing execution data file.
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mjar:3.3.0:jar[m [1m(default-jar)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.3.0/plexus-utils-3.3.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.3.0/plexus-utils-3.3.0.pom[90m (5.2 kB at 518 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.0/maven-archiver-3.6.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.0/maven-archiver-3.6.0.pom[90m (3.9 kB at 653 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.0/plexus-io-3.4.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.0/plexus-io-3.4.0.pom[90m (6.0 kB at 752 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.4.0/plexus-archiver-4.4.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.4.0/plexus-archiver-4.4.0.pom[90m (6.3 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.21/commons-compress-1.21.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.21/commons-compress-1.21.pom[90m (20 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/iq80/snappy/snappy/0.4/snappy-0.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/iq80/snappy/snappy/0.4/snappy-0.4.pom[90m (15 kB at 2.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.0/maven-archiver-3.6.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.0/maven-archiver-3.6.0.jar[90m (26 kB at 3.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.0/plexus-io-3.4.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.4.0/plexus-archiver-4.4.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.21/commons-compress-1.21.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/iq80/snappy/snappy/0.4/snappy-0.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.0/plexus-io-3.4.0.jar[90m (79 kB at 7.2 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/iq80/snappy/snappy/0.4/snappy-0.4.jar[90m (58 kB at 3.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.4.2/plexus-utils-3.4.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.4.0/plexus-archiver-4.4.0.jar[90m (211 kB at 6.4 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/3.4.2/plexus-utils-3.4.2.jar[90m (267 kB at 8.9 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.21/commons-compress-1.21.jar[90m (1.0 MB at 23 MB/s)[0m
    [[1;34mINFO[m] Building jar: /content/anserini/target/anserini-1.1.2-SNAPSHOT.jar
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m>>> [0;32msource:3.3.0:jar[m [1m(attach-sources)[0;1m > [0;1mgenerate-sources[m @ [36manserini[0;1m >>>[m
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mjacoco:0.8.11:prepare-agent[m [1m(default)[m @ [36manserini[0;1m ---[m
    [[1;34mINFO[m] argLine set to -javaagent:/root/.m2/repository/org/jacoco/org.jacoco.agent/0.8.11/org.jacoco.agent-0.8.11-runtime.jar=destfile=/content/anserini/target/jacoco.exec
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m<<< [0;32msource:3.3.0:jar[m [1m(attach-sources)[0;1m < [0;1mgenerate-sources[m @ [36manserini[0;1m <<<[m
    [[1;34mINFO[m] 
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32msource:3.3.0:jar[m [1m(attach-sources)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.7.1/plexus-archiver-4.7.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.7.1/plexus-archiver-4.7.1.pom[90m (6.5 kB at 816 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.1/plexus-io-3.4.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.1/plexus-io-3.4.1.pom[90m (6.0 kB at 859 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.23.0/commons-compress-1.23.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.23.0/commons-compress-1.23.0.pom[90m (22 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/56/commons-parent-56.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/56/commons-parent-56.pom[90m (82 kB at 9.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-2/zstd-jni-1.5.5-2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-2/zstd-jni-1.5.5-2.pom[90m (1.9 kB at 213 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.7.1/plexus-archiver-4.7.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.7.1/plexus-archiver-4.7.1.jar[90m (221 kB at 18 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.23.0/commons-compress-1.23.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-2/zstd-jni-1.5.5-2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.23.0/commons-compress-1.23.0.jar[90m (1.1 MB at 23 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-2/zstd-jni-1.5.5-2.jar[90m (5.9 MB at 39 MB/s)[0m
    [[1;34mINFO[m] Building jar: /content/anserini/target/anserini-1.1.2-SNAPSHOT-sources.jar
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mjavadoc:3.6.3:jar[m [1m(attach-javadocs)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.1.1/maven-reporting-api-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.1.1/maven-reporting-api-3.1.1.pom[90m (3.8 kB at 538 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.11.1/doxia-sink-api-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.11.1/doxia-sink-api-1.11.1.pom[90m (1.6 kB at 225 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia/1.11.1/doxia-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia/1.11.1/doxia-1.11.1.pom[90m (18 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-logging-api/1.11.1/doxia-logging-api-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-logging-api/1.11.1/doxia-logging-api-1.11.1.pom[90m (1.6 kB at 198 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.1/maven-archiver-3.6.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.1/maven-archiver-3.6.1.pom[90m (4.1 kB at 579 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/40/maven-shared-components-40.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/40/maven-shared-components-40.pom[90m (3.2 kB at 460 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/40/maven-parent-40.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/40/maven-parent-40.pom[90m (49 kB at 6.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.8.0/plexus-archiver-4.8.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.8.0/plexus-archiver-4.8.0.pom[90m (6.1 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/14/plexus-14.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/14/plexus-14.pom[90m (28 kB at 4.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.13.0/commons-io-2.13.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.13.0/commons-io-2.13.0.pom[90m (20 kB at 2.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/58/commons-parent-58.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/58/commons-parent-58.pom[90m (83 kB at 9.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-5/zstd-jni-1.5.5-5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-5/zstd-jni-1.5.5-5.pom[90m (1.9 kB at 274 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-invoker/3.2.0/maven-invoker-3.2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-invoker/3.2.0/maven-invoker-3.2.0.pom[90m (5.2 kB at 740 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/35/maven-shared-components-35.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/35/maven-shared-components-35.pom[90m (4.9 kB at 699 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.2.0/maven-common-artifact-filters-3.2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.2.0/maven-common-artifact-filters-3.2.0.pom[90m (6.9 kB at 992 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.1.1/maven-artifact-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.1.1/maven-artifact-3.1.1.pom[90m (2.0 kB at 281 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven/3.1.1/maven-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven/3.1.1/maven-3.1.1.pom[90m (22 kB at 2.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model/3.1.1/maven-model-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model/3.1.1/maven-model-3.1.1.pom[90m (4.1 kB at 592 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-core/3.1.1/maven-core-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-core/3.1.1/maven-core-3.1.1.pom[90m (7.3 kB at 909 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings/3.1.1/maven-settings-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings/3.1.1/maven-settings-3.1.1.pom[90m (2.2 kB at 197 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings-builder/3.1.1/maven-settings-builder-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings-builder/3.1.1/maven-settings-builder-3.1.1.pom[90m (2.6 kB at 324 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.19/plexus-interpolation-1.19.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interpolation/1.19/plexus-interpolation-1.19.pom[90m (1.0 kB at 129 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-repository-metadata/3.1.1/maven-repository-metadata-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-repository-metadata/3.1.1/maven-repository-metadata-3.1.1.pom[90m (2.2 kB at 248 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-plugin-api/3.1.1/maven-plugin-api-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-plugin-api/3.1.1/maven-plugin-api-3.1.1.pom[90m (3.4 kB at 483 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.plexus/0.9.0.M2/org.eclipse.sisu.plexus-0.9.0.M2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.plexus/0.9.0.M2/org.eclipse.sisu.plexus-0.9.0.M2.pom[90m (15 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-plexus/0.9.0.M2/sisu-plexus-0.9.0.M2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-plexus/0.9.0.M2/sisu-plexus-0.9.0.M2.pom[90m (15 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.inject/0.9.0.M2/org.eclipse.sisu.inject-0.9.0.M2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.inject/0.9.0.M2/org.eclipse.sisu.inject-0.9.0.M2.pom[90m (17 kB at 2.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-inject/0.9.0.M2/sisu-inject-0.9.0.M2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/sisu-inject/0.9.0.M2/sisu-inject-0.9.0.M2.pom[90m (15 kB at 1.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/2.1.0/plexus-component-annotations-2.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/2.1.0/plexus-component-annotations-2.1.0.pom[90m (750 B at 75 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/2.1.0/plexus-containers-2.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/2.1.0/plexus-containers-2.1.0.pom[90m (4.8 kB at 601 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.6.0/plexus-classworlds-2.6.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.6.0/plexus-classworlds-2.6.0.pom[90m (7.9 kB at 719 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model-builder/3.1.1/maven-model-builder-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model-builder/3.1.1/maven-model-builder-3.1.1.pom[90m (2.8 kB at 234 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-aether-provider/3.1.1/maven-aether-provider-3.1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-aether-provider/3.1.1/maven-aether-provider-3.1.1.pom[90m (4.1 kB at 409 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-spi/0.9.0.M2/aether-spi-0.9.0.M2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-spi/0.9.0.M2/aether-spi-0.9.0.M2.pom[90m (1.8 kB at 220 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether/0.9.0.M2/aether-0.9.0.M2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether/0.9.0.M2/aether-0.9.0.M2.pom[90m (28 kB at 3.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.5.1/plexus-classworlds-2.5.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.5.1/plexus-classworlds-2.5.1.pom[90m (5.0 kB at 501 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.3.3/maven-shared-utils-3.3.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-utils/3.3.3/maven-shared-utils-3.3.3.pom[90m (5.8 kB at 722 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/2.1.0/plexus-container-default-2.1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/2.1.0/plexus-container-default-2.1.0.pom[90m (3.0 kB at 329 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/xbean/xbean-reflect/3.7/xbean-reflect-3.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/xbean/xbean-reflect/3.7/xbean-reflect-3.7.pom[90m (5.1 kB at 566 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/xbean/xbean/3.7/xbean-3.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/xbean/xbean/3.7/xbean-3.7.pom[90m (15 kB at 1.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/geronimo/genesis/genesis-java5-flava/2.0/genesis-java5-flava-2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/geronimo/genesis/genesis-java5-flava/2.0/genesis-java5-flava-2.0.pom[90m (5.5 kB at 685 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/geronimo/genesis/genesis-default-flava/2.0/genesis-default-flava-2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/geronimo/genesis/genesis-default-flava/2.0/genesis-default-flava-2.0.pom[90m (18 kB at 2.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/geronimo/genesis/genesis/2.0/genesis-2.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/geronimo/genesis/genesis/2.0/genesis-2.0.pom[90m (18 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/6/apache-6.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/6/apache-6.pom[90m (13 kB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/collections/google-collections/1.0/google-collections-1.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/collections/google-collections/1.0/google-collections-1.0.pom[90m (2.5 kB at 413 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/google/1/google-1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/google/google/1/google-1.pom[90m (1.6 kB at 111 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-site-renderer/1.11.1/doxia-site-renderer-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-site-renderer/1.11.1/doxia-site-renderer-1.11.1.pom[90m (7.7 kB at 962 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sitetools/1.11.1/doxia-sitetools-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sitetools/1.11.1/doxia-sitetools-1.11.1.pom[90m (14 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.0/maven-artifact-3.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.0/maven-artifact-3.0.pom[90m (1.9 kB at 161 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven/3.0/maven-3.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven/3.0/maven-3.0.pom[90m (22 kB at 2.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/15/maven-parent-15.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-parent/15/maven-parent-15.pom[90m (24 kB at 3.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-core/1.11.1/doxia-core-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-core/1.11.1/doxia-core-1.11.1.pom[90m (4.5 kB at 503 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.8.1/commons-lang3-3.8.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.8.1/commons-lang3-3.8.1.pom[90m (28 kB at 4.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/47/commons-parent-47.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/47/commons-parent-47.pom[90m (78 kB at 9.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/19/apache-19.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/apache/19/apache-19.pom[90m (15 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.3/commons-text-1.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.3/commons-text-1.3.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/45/commons-parent-45.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/45/commons-parent-45.pom[90m (73 kB at 7.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.7/commons-lang3-3.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.7/commons-lang3-3.7.pom[90m (28 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpclient/4.5.13/httpclient-4.5.13.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpclient/4.5.13/httpclient-4.5.13.pom[90m (6.6 kB at 734 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-client/4.5.13/httpcomponents-client-4.5.13.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-client/4.5.13/httpcomponents-client-4.5.13.pom[90m (16 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-parent/11/httpcomponents-parent-11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-parent/11/httpcomponents-parent-11.pom[90m (35 kB at 4.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.13/httpcore-4.4.13.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.13/httpcore-4.4.13.pom[90m (5.0 kB at 382 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-core/4.4.13/httpcomponents-core-4.4.13.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-core/4.4.13/httpcomponents-core-4.4.13.pom[90m (13 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-logging/commons-logging/1.2/commons-logging-1.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-logging/commons-logging/1.2/commons-logging-1.2.pom[90m (19 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/34/commons-parent-34.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/34/commons-parent-34.pom[90m (56 kB at 8.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.11/commons-codec-1.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.11/commons-codec-1.11.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.14/httpcore-4.4.14.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.14/httpcore-4.4.14.pom[90m (5.0 kB at 552 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-core/4.4.14/httpcomponents-core-4.4.14.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-core/4.4.14/httpcomponents-core-4.4.14.pom[90m (13 kB at 1.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-decoration-model/1.11.1/doxia-decoration-model-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-decoration-model/1.11.1/doxia-decoration-model-1.11.1.pom[90m (3.4 kB at 284 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/2.0.0/plexus-component-annotations-2.0.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/2.0.0/plexus-component-annotations-2.0.0.pom[90m (750 B at 68 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/2.0.0/plexus-containers-2.0.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/2.0.0/plexus-containers-2.0.0.pom[90m (4.8 kB at 801 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-skin-model/1.11.1/doxia-skin-model-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-skin-model/1.11.1/doxia-skin-model-1.11.1.pom[90m (3.0 kB at 276 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml/1.11.1/doxia-module-xhtml-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml/1.11.1/doxia-module-xhtml-1.11.1.pom[90m (2.0 kB at 247 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-modules/1.11.1/doxia-modules-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-modules/1.11.1/doxia-modules-1.11.1.pom[90m (2.7 kB at 457 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml5/1.11.1/doxia-module-xhtml5-1.11.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml5/1.11.1/doxia-module-xhtml5-1.11.1.pom[90m (2.0 kB at 283 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-i18n/1.0-beta-10/plexus-i18n-1.0-beta-10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-i18n/1.0-beta-10/plexus-i18n-1.0-beta-10.pom[90m (2.1 kB at 296 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/1.1.12/plexus-components-1.1.12.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/1.1.12/plexus-components-1.1.12.pom[90m (3.0 kB at 429 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/1.0.10/plexus-1.0.10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/1.0.10/plexus-1.0.10.pom[90m (8.2 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/1.0-alpha-30/plexus-container-default-1.0-alpha-30.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/1.0-alpha-30/plexus-container-default-1.0-alpha-30.pom[90m (3.5 kB at 497 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/1.0-alpha-30/plexus-containers-1.0-alpha-30.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/1.0-alpha-30/plexus-containers-1.0-alpha-30.pom[90m (1.9 kB at 271 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/1.0.11/plexus-1.0.11.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/1.0.11/plexus-1.0.11.pom[90m (9.0 kB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/1.2-alpha-9/plexus-classworlds-1.2-alpha-9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/1.2-alpha-9/plexus-classworlds-1.2-alpha-9.pom[90m (3.2 kB at 293 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/3.8.1/junit-3.8.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/3.8.1/junit-3.8.1.pom[90m (998 B at 125 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-velocity/1.2/plexus-velocity-1.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-velocity/1.2/plexus-velocity-1.2.pom[90m (2.8 kB at 313 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/4.0/plexus-components-4.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/4.0/plexus-components-4.0.pom[90m (2.7 kB at 156 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/1.0-alpha-9-stable-1/plexus-container-default-1.0-alpha-9-stable-1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/1.0-alpha-9-stable-1/plexus-container-default-1.0-alpha-9-stable-1.pom[90m (3.9 kB at 564 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/1.0.3/plexus-containers-1.0.3.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-containers/1.0.3/plexus-containers-1.0.3.pom[90m (492 B at 62 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/1.0.4/plexus-1.0.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/1.0.4/plexus-1.0.4.pom[90m (5.7 kB at 820 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mclassworlds/classworlds/1.1-alpha-2/classworlds-1.1-alpha-2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mclassworlds/classworlds/1.1-alpha-2/classworlds-1.1-alpha-2.pom[90m (3.1 kB at 447 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.1/commons-collections-3.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.1/commons-collections-3.1.pom[90m (6.1 kB at 869 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/velocity/velocity/1.7/velocity-1.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/velocity/velocity/1.7/velocity-1.7.pom[90m (11 kB at 1.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.2.1/commons-collections-3.2.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.2.1/commons-collections-3.2.1.pom[90m (13 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/9/commons-parent-9.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/9/commons-parent-9.pom[90m (22 kB at 3.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-lang/commons-lang/2.4/commons-lang-2.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-lang/commons-lang/2.4/commons-lang-2.4.pom[90m (14 kB at 2.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.2.2/commons-collections-3.2.2.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.2.2/commons-collections-3.2.2.pom[90m (12 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/wagon/wagon-provider-api/2.4/wagon-provider-api-2.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/wagon/wagon-provider-api/2.4/wagon-provider-api-2.4.pom[90m (1.7 kB at 247 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/wagon/wagon/2.4/wagon-2.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/wagon/wagon/2.4/wagon-2.4.pom[90m (20 kB at 2.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.11.0/commons-text-1.11.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.11.0/commons-text-1.11.0.pom[90m (19 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.13.0/commons-lang3-3.13.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.13.0/commons-lang3-3.13.0.pom[90m (31 kB at 4.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpclient/4.5.14/httpclient-4.5.14.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpclient/4.5.14/httpclient-4.5.14.pom[90m (6.6 kB at 946 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-client/4.5.14/httpcomponents-client-4.5.14.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-client/4.5.14/httpcomponents-client-4.5.14.pom[90m (15 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.16/httpcore-4.4.16.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.16/httpcore-4.4.16.pom[90m (5.0 kB at 414 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-core/4.4.16/httpcomponents-core-4.4.16.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcomponents-core/4.4.16/httpcomponents-core-4.4.16.pom[90m (12 kB at 1.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.9.0/plexus-archiver-4.9.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.9.0/plexus-archiver-4.9.0.pom[90m (5.8 kB at 579 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.15.0/commons-io-2.15.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.15.0/commons-io-2.15.0.pom[90m (22 kB at 2.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.24.0/commons-compress-1.24.0.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.24.0/commons-compress-1.24.0.pom[90m (22 kB at 2.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/61/commons-parent-61.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/61/commons-parent-61.pom[90m (81 kB at 10 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-10/zstd-jni-1.5.5-10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-10/zstd-jni-1.5.5-10.pom[90m (2.0 kB at 287 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interactivity-api/1.1/plexus-interactivity-api-1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interactivity-api/1.1/plexus-interactivity-api-1.1.pom[90m (823 B at 118 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interactivity/1.1/plexus-interactivity-1.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interactivity/1.1/plexus-interactivity-1.1.pom[90m (1.7 kB at 247 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/6.5/plexus-components-6.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-components/6.5/plexus-components-6.5.pom[90m (2.7 kB at 385 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/6.5/plexus-6.5.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/6.5/plexus-6.5.pom[90m (26 kB at 3.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.1.1/maven-reporting-api-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/reporting/maven-reporting-api/3.1.1/maven-reporting-api-3.1.1.jar[90m (11 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.1/maven-archiver-3.6.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.2.0/maven-common-artifact-filters-3.2.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-invoker/3.2.0/maven-invoker-3.2.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-archiver/3.6.1/maven-archiver-3.6.1.jar[90m (27 kB at 3.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.1.1/maven-artifact-3.1.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model/3.1.1/maven-model-3.1.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-core/3.1.1/maven-core-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-common-artifact-filters/3.2.0/maven-common-artifact-filters-3.2.0.jar[90m (61 kB at 6.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings/3.1.1/maven-settings-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-invoker/3.2.0/maven-invoker-3.2.0.jar[90m (33 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings-builder/3.1.1/maven-settings-builder-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-artifact/3.1.1/maven-artifact-3.1.1.jar[90m (52 kB at 3.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-repository-metadata/3.1.1/maven-repository-metadata-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings/3.1.1/maven-settings-3.1.1.jar[90m (42 kB at 2.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model-builder/3.1.1/maven-model-builder-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-settings-builder/3.1.1/maven-settings-builder-3.1.1.jar[90m (42 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-aether-provider/3.1.1/maven-aether-provider-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-repository-metadata/3.1.1/maven-repository-metadata-3.1.1.jar[90m (25 kB at 933 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-spi/0.9.0.M2/aether-spi-0.9.0.M2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-aether-provider/3.1.1/maven-aether-provider-3.1.1.jar[90m (60 kB at 1.7 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-impl/1.0.0.v20140518/aether-impl-1.0.0.v20140518.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-spi/0.9.0.M2/aether-spi-0.9.0.M2.jar[90m (18 kB at 506 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.5.1/plexus-classworlds-2.5.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/aether/aether-impl/1.0.0.v20140518/aether-impl-1.0.0.v20140518.jar[90m (172 kB at 3.8 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-classworlds/2.5.1/plexus-classworlds-2.5.1.jar[90m (50 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-sec-dispatcher/1.3/plexus-sec-dispatcher-1.3.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-cipher/1.4/plexus-cipher-1.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-core/3.1.1/maven-core-3.1.1.jar[90m (557 kB at 12 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-plugin-api/3.1.1/maven-plugin-api-3.1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model-builder/3.1.1/maven-model-builder-3.1.1.jar[90m (160 kB at 3.5 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.plexus/0.9.0.M2/org.eclipse.sisu.plexus-0.9.0.M2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-model/3.1.1/maven-model-3.1.1.jar[90m (154 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/annotation/javax.annotation-api/1.2/javax.annotation-api-1.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-cipher/1.4/plexus-cipher-1.4.jar[90m (13 kB at 270 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/enterprise/cdi-api/1.2/cdi-api-1.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/sonatype/plexus/plexus-sec-dispatcher/1.3/plexus-sec-dispatcher-1.3.jar[90m (29 kB at 571 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.inject/0.9.0.M2/org.eclipse.sisu.inject-0.9.0.M2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/maven-plugin-api/3.1.1/maven-plugin-api-3.1.1.jar[90m (45 kB at 863 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.11.1/doxia-sink-api-1.11.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/annotation/javax.annotation-api/1.2/javax.annotation-api-1.2.jar[90m (26 kB at 488 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-logging-api/1.11.1/doxia-logging-api-1.11.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjavax/enterprise/cdi-api/1.2/cdi-api-1.2.jar[90m (71 kB at 1.1 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-site-renderer/1.11.1/doxia-site-renderer-1.11.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-sink-api/1.11.1/doxia-sink-api-1.11.1.jar[90m (12 kB at 179 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.plexus/0.9.0.M2/org.eclipse.sisu.plexus-0.9.0.M2.jar[90m (210 kB at 3.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-core/1.11.1/doxia-core-1.11.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-decoration-model/1.11.1/doxia-decoration-model-1.11.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-logging-api/1.11.1/doxia-logging-api-1.11.1.jar[90m (12 kB at 163 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-skin-model/1.11.1/doxia-skin-model-1.11.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-site-renderer/1.11.1/doxia-site-renderer-1.11.1.jar[90m (65 kB at 795 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-decoration-model/1.11.1/doxia-decoration-model-1.11.1.jar[90m (60 kB at 729 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml/1.11.1/doxia-module-xhtml-1.11.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml5/1.11.1/doxia-module-xhtml5-1.11.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/eclipse/sisu/org.eclipse.sisu.inject/0.9.0.M2/org.eclipse.sisu.inject-0.9.0.M2.jar[90m (425 kB at 5.2 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml/1.11.1/doxia-module-xhtml-1.11.1.jar[90m (17 kB at 209 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-skin-model/1.11.1/doxia-skin-model-1.11.1.jar[90m (16 kB at 194 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/2.0.0/plexus-component-annotations-2.0.0.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-i18n/1.0-beta-10/plexus-i18n-1.0-beta-10.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-module-xhtml5/1.11.1/doxia-module-xhtml5-1.11.1.jar[90m (18 kB at 210 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/1.0-alpha-30/plexus-container-default-1.0-alpha-30.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/3.8.1/junit-3.8.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-i18n/1.0-beta-10/plexus-i18n-1.0-beta-10.jar[90m (12 kB at 130 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-velocity/1.2/plexus-velocity-1.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-component-annotations/2.0.0/plexus-component-annotations-2.0.0.jar[90m (4.2 kB at 44 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/velocity/velocity/1.7/velocity-1.7.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mjunit/junit/3.8.1/junit-3.8.1.jar[90m (121 kB at 1.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-lang/commons-lang/2.4/commons-lang-2.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/doxia/doxia-core/1.11.1/doxia-core-1.11.1.jar[90m (218 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.2.2/commons-collections-3.2.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-velocity/1.2/plexus-velocity-1.2.jar[90m (8.1 kB at 81 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/wagon/wagon-provider-api/2.4/wagon-provider-api-2.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-container-default/1.0-alpha-30/plexus-container-default-1.0-alpha-30.jar[90m (237 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.14.0/commons-lang3-3.14.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/wagon/wagon-provider-api/2.4/wagon-provider-api-2.4.jar[90m (52 kB at 481 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.11.0/commons-text-1.11.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-lang/commons-lang/2.4/commons-lang-2.4.jar[90m (262 kB at 2.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpclient/4.5.14/httpclient-4.5.14.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-text/1.11.0/commons-text-1.11.0.jar[90m (247 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-logging/commons-logging/1.2/commons-logging-1.2.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-logging/commons-logging/1.2/commons-logging-1.2.jar[90m (62 kB at 468 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.11/commons-codec-1.11.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/velocity/velocity/1.7/velocity-1.7.jar[90m (450 kB at 2.9 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.16/httpcore-4.4.16.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-lang3/3.14.0/commons-lang3-3.14.0.jar[90m (658 kB at 4.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.1/plexus-io-3.4.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-collections/commons-collections/3.2.2/commons-collections-3.2.2.jar[90m (588 kB at 3.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.9.0/plexus-archiver-4.9.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.11/commons-codec-1.11.jar[90m (335 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.24.0/commons-compress-1.24.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-io/3.4.1/plexus-io-3.4.1.jar[90m (79 kB at 478 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-10/zstd-jni-1.5.5-10.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpcore/4.4.16/httpcore-4.4.16.jar[90m (328 kB at 1.8 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interactivity-api/1.1/plexus-interactivity-api-1.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-archiver/4.9.0/plexus-archiver-4.9.0.jar[90m (225 kB at 1.2 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-interactivity-api/1.1/plexus-interactivity-api-1.1.jar[90m (9.4 kB at 48 kB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/httpcomponents/httpclient/4.5.14/httpclient-4.5.14.jar[90m (786 kB at 4.0 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.24.0/commons-compress-1.24.0.jar[90m (1.1 MB at 4.7 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcom/github/luben/zstd-jni/1.5.5-10/zstd-jni-1.5.5-10.jar[90m (6.7 MB at 17 MB/s)[0m
    [[1;34mINFO[m] No previous run data found, generating javadoc.
    [[1;33mWARNING[m] Javadoc Warnings
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/DocumentCollection.java:71: warning: no @param for <T>
    [[1;33mWARNING[m] public abstract class DocumentCollection<T extends SourceDocument> implements Iterable<FileSegment<T>> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/JsonCollection.java:102: warning: no @param for <T>
    [[1;33mWARNING[m] public static class Segment<T extends Document> extends FileSegment<T> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/FileSegment.java:39: warning: no @param for <T>
    [[1;33mWARNING[m] public abstract class FileSegment<T extends SourceDocument> implements Iterable<T>, Closeable {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/MsMarcoV2DocCollection.java:66: warning: no @param for <T>
    [[1;33mWARNING[m] public static class Segment<T extends Document> extends FileSegment<T> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/MrTyDiCollection.java:66: warning: no @param for <T>
    [[1;33mWARNING[m] public static class Segment<T extends Document> extends FileSegment<T> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/NeuClirCollection.java:69: warning: no @param for <T>
    [[1;33mWARNING[m] public static class Segment<T extends Document> extends FileSegment<T> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/MsMarcoV2PassageCollection.java:65: warning: no @param for <T>
    [[1;33mWARNING[m] public static class Segment<T extends Document> extends FileSegment<T> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/SearchCollection.java:120: warning: no @param for <K>
    [[1;33mWARNING[m] public final class SearchCollection<K extends Comparable<K>> implements Runnable, Closeable {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/SearchShardedHnswDenseVectors.java:39: warning: no @param for <K>
    [[1;33mWARNING[m] public final class SearchShardedHnswDenseVectors<K extends Comparable<K>> implements Runnable, Closeable {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/SearchFlatDenseVectors.java:46: warning: no @param for <K>
    [[1;33mWARNING[m] public final class SearchFlatDenseVectors<K extends Comparable<K>> implements Runnable, Closeable {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/SearchHnswDenseVectors.java:45: warning: no @param for <K>
    [[1;33mWARNING[m] public final class SearchHnswDenseVectors<K extends Comparable<K>> implements Runnable, AutoCloseable {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/SearchInvertedDenseVectors.java:45: warning: no @param for <K>
    [[1;33mWARNING[m] public final class SearchInvertedDenseVectors<K extends Comparable<K>> implements Runnable, Closeable {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:48: warning: no comment
    [[1;33mWARNING[m] public abstract class AbstractIndexer implements Runnable {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:51: warning: no comment
    [[1;33mWARNING[m] public static class Args {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:91: warning: no comment
    [[1;33mWARNING[m] public class IndexerThread extends Thread {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:184: warning: no comment
    [[1;33mWARNING[m] protected final Args args;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:187: warning: no comment
    [[1;33mWARNING[m] protected DocumentCollection<? extends SourceDocument> collection;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:186: warning: no comment
    [[1;33mWARNING[m] protected Path collectionPath;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:185: warning: no comment
    [[1;33mWARNING[m] protected Counters counters = new Counters();
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:188: warning: no comment
    [[1;33mWARNING[m] protected Class<LuceneDocumentGenerator<? extends SourceDocument>> generatorClass;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:189: warning: no comment
    [[1;33mWARNING[m] protected IndexWriter writer;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:192: warning: no comment
    [[1;33mWARNING[m] public AbstractIndexer(Args args) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:365: warning: no comment
    [[1;33mWARNING[m] public Counters getCounters() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:302: warning: no comment
    [[1;33mWARNING[m] protected void processSegments(ThreadPoolExecutor executor, List<Path> segmentPaths) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:317: warning: no comment
    [[1;33mWARNING[m] protected void processSegments(List<Path> segmentPaths, AtomicInteger completedTaskCount) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:53: warning: no comment
    [[1;33mWARNING[m] public String collectionClass;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:59: warning: no comment
    [[1;33mWARNING[m] public String index;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:56: warning: no comment
    [[1;33mWARNING[m] public String input;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:68: warning: no comment
    [[1;33mWARNING[m] public int memoryBuffer = 4096;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:65: warning: no comment
    [[1;33mWARNING[m] public boolean optimize = false;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:80: warning: no comment
    [[1;33mWARNING[m] public Boolean options = false;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:77: warning: no comment
    [[1;33mWARNING[m] public boolean quiet = false;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:84: warning: no comment
    [[1;33mWARNING[m] public int shardCount = -1;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:88: warning: no comment
    [[1;33mWARNING[m] public int shardCurrent = -1;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:71: warning: no comment
    [[1;33mWARNING[m] public int threads = 4;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:62: warning: no comment
    [[1;33mWARNING[m] public boolean uniqueDocid = false;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:74: warning: no comment
    [[1;33mWARNING[m] public boolean verbose = false;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:51: warning: use of default constructor, which does not provide a comment
    [[1;33mWARNING[m] public static class Args {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:96: warning: no comment
    [[1;33mWARNING[m] public IndexerThread(Path inputFile, LuceneDocumentGenerator<SourceDocument> generator) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/AbstractIndexer.java:100: warning: no comment
    [[1;33mWARNING[m] public IndexerThread(Path inputFile, LuceneDocumentGenerator<SourceDocument> generator, Set<String> docids) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/similarity/AccurateBM25Similarity.java:29: warning: no comment
    [[1;33mWARNING[m] public class AccurateBM25Similarity extends Similarity {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/similarity/AccurateBM25Similarity.java:44: warning: no comment
    [[1;33mWARNING[m] public AccurateBM25Similarity() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/similarity/AccurateBM25Similarity.java:33: warning: no comment
    [[1;33mWARNING[m] public AccurateBM25Similarity(float k1, float b) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/similarity/AccurateBM25Similarity.java:104: warning: no comment
    [[1;33mWARNING[m] public final float getB() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/similarity/AccurateBM25Similarity.java:100: warning: no comment
    [[1;33mWARNING[m] public final float getK1() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/search/similarity/AccurateBM25Similarity.java:48: warning: no comment
    [[1;33mWARNING[m] protected float idf(long docFreq, long docCount) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:50: warning: no comment
    [[1;33mWARNING[m] public AclAnthology() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:53: warning: no comment
    [[1;33mWARNING[m] public AclAnthology(Path path) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:177: warning: no comment
    [[1;33mWARNING[m] public Document(String rawContent) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:150: warning: no comment
    [[1;33mWARNING[m] public Document(Map.Entry<String, JsonNode> jsonEntry) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:218: warning: no comment
    [[1;33mWARNING[m] public List<String> authors() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:210: warning: no comment
    [[1;33mWARNING[m] public JsonNode paper() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:226: warning: no comment
    [[1;33mWARNING[m] public List<String> sigs() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:222: warning: no comment
    [[1;33mWARNING[m] public List<String> venues() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:214: warning: no comment
    [[1;33mWARNING[m] public JsonNode volume() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:113: warning: no comment
    [[1;33mWARNING[m] public Segment(BufferedReader bufferedReader) throws IOException {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AclAnthology.java:90: warning: no comment
    [[1;33mWARNING[m] public Segment(Path path) throws IOException {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/generator/AclAnthologyGenerator.java:81: warning: no comment
    [[1;33mWARNING[m] public static final List<String> FIELDS_WITHOUT_STEMMING = List.of(
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/generator/AclAnthologyGenerator.java:78: warning: no comment
    [[1;33mWARNING[m] public static final List<String> NUMERIC_FIELD_NAMES = List.of(
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/generator/AclAnthologyGenerator.java:70: warning: no comment
    [[1;33mWARNING[m] public static final List<String> STRING_FIELD_NAMES = List.of(
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/generator/AclAnthologyGenerator.java:88: warning: no comment
    [[1;33mWARNING[m] public AclAnthologyGenerator(IndexCollection.Args args) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/generator/LuceneDocumentGenerator.java:28: warning: no comment
    [[1;33mWARNING[m] Document createDocument(T src) throws GeneratorException;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:41: warning: no comment
    [[1;33mWARNING[m] public class AfribertaCollection extends DocumentCollection<AfribertaCollection.Document> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:65: warning: no comment
    [[1;33mWARNING[m] public static class Segment<T extends Document> extends FileSegment<T> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:44: warning: no comment
    [[1;33mWARNING[m] public AfribertaCollection() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:47: warning: no comment
    [[1;33mWARNING[m] public AfribertaCollection(Path path) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:159: warning: no comment
    [[1;33mWARNING[m] public Document(JsonNode json) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:89: warning: no comment
    [[1;33mWARNING[m] public Segment(BufferedReader bufferedReader) throws IOException {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:70: warning: no comment
    [[1;33mWARNING[m] public Segment(Path path) throws IOException {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/collection/AfribertaCollection.java:145: warning: no comment
    [[1;33mWARNING[m] protected AfribertaCollection.Document createNewDocument(JsonNode node) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerMap.java:27: warning: no comment
    [[1;33mWARNING[m] public class AnalyzerMap {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerMap.java:30: warning: no comment
    [[1;33mWARNING[m] public static final Map<String, String> analyzerMap = new HashMap<>() {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerMap.java:27: warning: use of default constructor, which does not provide a comment
    [[1;33mWARNING[m] public class AnalyzerMap {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerMap.java:60: warning: no comment
    [[1;33mWARNING[m] public static Analyzer getLanguageSpecificAnalyzer(String language) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerUtils.java:36: warning: no comment
    [[1;33mWARNING[m] public class AnalyzerUtils {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerUtils.java:36: warning: use of default constructor, which does not provide a comment
    [[1;33mWARNING[m] public class AnalyzerUtils {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerUtils.java:38: warning: no comment
    [[1;33mWARNING[m] public static List<String> analyze(String s) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerUtils.java:42: warning: no comment
    [[1;33mWARNING[m] public static List<String> analyze(Analyzer analyzer, String s) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerUtils.java:87: warning: no comment
    [[1;33mWARNING[m] public static Map<String, Long> computeDocumentVector(Analyzer analyzer, Class parser, String s) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AnalyzerUtils.java:64: warning: no comment
    [[1;33mWARNING[m] public static Map<String, Long> computeDocumentVector(Analyzer analyzer, String s) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99FlatVectorFormat.java:41: warning: no comment
    [[1;33mWARNING[m] public class AnseriniLucene99FlatVectorFormat extends KnnVectorsFormat {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99FlatVectorFormat.java:104: warning: no comment
    [[1;33mWARNING[m] public static class AnseriniLucene99FlatVectorReader extends KnnVectorsReader {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99FlatVectorFormat.java:64: warning: no comment
    [[1;33mWARNING[m] public static class AnseriniLucene99FlatVectorWriter extends KnnVectorsWriter {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99FlatVectorFormat.java:108: warning: no comment
    [[1;33mWARNING[m] public AnseriniLucene99FlatVectorReader(FlatVectorsReader reader) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99FlatVectorFormat.java:68: warning: no comment
    [[1;33mWARNING[m] public AnseriniLucene99FlatVectorWriter(FlatVectorsWriter writer) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99ScalarQuantizedVectorsFormat.java:41: warning: no comment
    [[1;33mWARNING[m] public class AnseriniLucene99ScalarQuantizedVectorsFormat extends KnnVectorsFormat {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99ScalarQuantizedVectorsFormat.java:104: warning: no comment
    [[1;33mWARNING[m] public static class AnseriniLucene99ScalarQuantizedVectorReader extends KnnVectorsReader {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99ScalarQuantizedVectorsFormat.java:64: warning: no comment
    [[1;33mWARNING[m] public static class AnseriniLucene99ScalarQuantizedVectorWriter extends KnnVectorsWriter {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99ScalarQuantizedVectorsFormat.java:108: warning: no comment
    [[1;33mWARNING[m] public AnseriniLucene99ScalarQuantizedVectorReader(FlatVectorsReader reader) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/index/codecs/AnseriniLucene99ScalarQuantizedVectorsFormat.java:68: warning: no comment
    [[1;33mWARNING[m] public AnseriniLucene99ScalarQuantizedVectorWriter(FlatVectorsWriter writer) {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/encoder/dense/ArcticEmbedLEncoder.java:32: warning: no comment
    [[1;33mWARNING[m] public class ArcticEmbedLEncoder extends DenseEncoder {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/encoder/dense/ArcticEmbedLEncoder.java:48: warning: no comment
    [[1;33mWARNING[m] public ArcticEmbedLEncoder() throws IOException, OrtException, URISyntaxException {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/encoder/OnnxEncoder.java:127: warning: no comment
    [[1;33mWARNING[m] public abstract T encode(@NotNull String query) throws OrtException;
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AutoCompositeAnalyzer.java:28: warning: no comment
    [[1;33mWARNING[m] public class AutoCompositeAnalyzer {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AutoCompositeAnalyzer.java:28: warning: use of default constructor, which does not provide a comment
    [[1;33mWARNING[m] public class AutoCompositeAnalyzer {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AutoCompositeAnalyzer.java:50: warning: no comment
    [[1;33mWARNING[m] public static Analyzer getAnalyzer(String language) throws IOException {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/analysis/AutoCompositeAnalyzer.java:54: warning: no comment
    [[1;33mWARNING[m] public static Analyzer getAnalyzer(String language, String analyzeWithHuggingFaceTokenizer) throws IOException {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/rerank/lib/AxiomReranker.java:108: warning: no comment
    [[1;33mWARNING[m] public class AxiomReranker<T> implements Reranker<T> {
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/rerank/lib/AxiomReranker.java:121: warning: no comment
    [[1;33mWARNING[m] public static List<String> externalDocidsCache; // When enabling the deterministic reranking we can opt to read sorted docids
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] /content/anserini/src/main/java/io/anserini/rerank/lib/AxiomReranker.java:119: warning: no comment
    [[1;33mWARNING[m] public static ScoreDoc[] internalDocidsCache; // When enabling the deterministic reranking we could cache all the
    [[1;33mWARNING[m] ^
    [[1;33mWARNING[m] 100 warnings
    [[1;34mINFO[m] Building jar: /content/anserini/target/anserini-1.1.2-SNAPSHOT-javadoc.jar
    [[1;34mINFO[m] 
    [[1;34mINFO[m] [1m--- [0;32mshade:3.5.3:shade[m [1m(shade-jar-with-dependencies)[m @ [36manserini[0;1m ---[m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.1/plexus-utils-4.0.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.1/plexus-utils-4.0.1.pom[90m (7.8 kB at 870 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/17/plexus-17.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus/17/plexus-17.pom[90m (28 kB at 4.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.7/asm-9.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.7/asm-9.7.pom[90m (2.4 kB at 395 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.7/asm-commons-9.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.7/asm-commons-9.7.pom[90m (2.8 kB at 398 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.7/asm-tree-9.7.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.7/asm-tree-9.7.pom[90m (2.6 kB at 370 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jdom/jdom2/2.0.6.1/jdom2-2.0.6.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jdom/jdom2/2.0.6.1/jdom2-2.0.6.1.pom[90m (4.6 kB at 575 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-dependency-tree/3.2.1/maven-dependency-tree-3.2.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-dependency-tree/3.2.1/maven-dependency-tree-3.2.1.pom[90m (6.2 kB at 891 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/37/maven-shared-components-37.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-shared-components/37/maven-shared-components-37.pom[90m (4.9 kB at 816 kB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/vafer/jdependency/2.10/jdependency-2.10.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/vafer/jdependency/2.10/jdependency-2.10.pom[90m (14 kB at 2.0 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-collections4/4.4/commons-collections4-4.4.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-collections4/4.4/commons-collections4-4.4.pom[90m (24 kB at 3.4 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/48/commons-parent-48.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/48/commons-parent-48.pom[90m (72 kB at 10 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.1/commons-compress-1.26.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.1/commons-compress-1.26.1.pom[90m (22 kB at 2.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/66/commons-parent-66.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-parent/66/commons-parent-66.pom[90m (77 kB at 11 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.16.1/commons-codec-1.16.1.pom
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.16.1/commons-codec-1.16.1.pom[90m (16 kB at 2.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.1/plexus-utils-4.0.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/codehaus/plexus/plexus-utils/4.0.1/plexus-utils-4.0.1.jar[90m (193 kB at 18 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.7/asm-9.7.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.7/asm-commons-9.7.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.7/asm-tree-9.7.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jdom/jdom2/2.0.6.1/jdom2-2.0.6.1.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-dependency-tree/3.2.1/maven-dependency-tree-3.2.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm/9.7/asm-9.7.jar[90m (125 kB at 11 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-tree/9.7/asm-tree-9.7.jar[90m (52 kB at 5.2 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.13.0/commons-io-2.13.0.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/ow2/asm/asm-commons/9.7/asm-commons-9.7.jar[90m (73 kB at 5.6 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/vafer/jdependency/2.10/jdependency-2.10.jar
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-collections4/4.4/commons-collections4-4.4.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/maven/shared/maven-dependency-tree/3.2.1/maven-dependency-tree-3.2.1.jar[90m (43 kB at 3.3 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.1/commons-compress-1.26.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/jdom/jdom2/2.0.6.1/jdom2-2.0.6.1.jar[90m (328 kB at 11 MB/s)[0m
    [90mDownloading from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.16.1/commons-codec-1.16.1.jar
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-io/commons-io/2.13.0/commons-io-2.13.0.jar[90m (484 kB at 14 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0mcommons-codec/commons-codec/1.16.1/commons-codec-1.16.1.jar[90m (365 kB at 7.8 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-compress/1.26.1/commons-compress-1.26.1.jar[90m (1.1 MB at 22 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/apache/commons/commons-collections4/4.4/commons-collections4-4.4.jar[90m (752 kB at 16 MB/s)[0m
    Downloaded[90m from [0mcentral[90m: https://repo.maven.apache.org/maven2/[0morg/vafer/jdependency/2.10/jdependency-2.10.jar[90m (416 kB at 3.9 MB/s)[0m
    [[1;34mINFO[m] Including org.apache.lucene:lucene-core:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-codecs:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-backward-codecs:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-queries:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-queryparser:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-sandbox:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-analysis-common:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-analysis-kuromoji:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.lucene:lucene-analysis-morfologik:jar:9.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.carrot2:morfologik-stemming:jar:2.1.9 in the shaded jar.
    [[1;34mINFO[m] Including org.carrot2:morfologik-fsa:jar:2.1.9 in the shaded jar.
    [[1;34mINFO[m] Including org.carrot2:morfologik-polish:jar:2.1.9 in the shaded jar.
    [[1;34mINFO[m] Including ua.net.nlp:morfologik-ukrainian-search:jar:4.9.1 in the shaded jar.
    [[1;34mINFO[m] Including org.tukaani:xz:jar:1.9 in the shaded jar.
    [[1;34mINFO[m] Including com.fasterxml.jackson.core:jackson-core:jar:2.16.0 in the shaded jar.
    [[1;34mINFO[m] Including com.fasterxml.jackson.core:jackson-databind:jar:2.16.0 in the shaded jar.
    [[1;34mINFO[m] Including com.fasterxml.jackson.core:jackson-annotations:jar:2.16.0 in the shaded jar.
    [[1;34mINFO[m] Including com.fasterxml.jackson.datatype:jackson-datatype-jdk8:jar:2.16.0 in the shaded jar.
    [[1;34mINFO[m] Including com.fasterxml.jackson.dataformat:jackson-dataformat-yaml:jar:2.16.0 in the shaded jar.
    [[1;34mINFO[m] Including org.yaml:snakeyaml:jar:2.2 in the shaded jar.
    [[1;34mINFO[m] Including org.jsoup:jsoup:jar:1.15.3 in the shaded jar.
    [[1;34mINFO[m] Including args4j:args4j:jar:2.33 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.logging.log4j:log4j-api:jar:2.23.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.logging.log4j:log4j-core:jar:2.23.1 in the shaded jar.
    [[1;34mINFO[m] Including org.slf4j:slf4j-simple:jar:1.7.32 in the shaded jar.
    [[1;34mINFO[m] Including org.slf4j:slf4j-api:jar:1.7.32 in the shaded jar.
    [[1;34mINFO[m] Including it.unimi.dsi:fastutil:jar:8.5.8 in the shaded jar.
    [[1;34mINFO[m] Including org.wikiclean:wikiclean:jar:1.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.commons:commons-lang3:jar:3.5 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.ant:ant:jar:1.10.11 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.ant:ant-launcher:jar:1.10.11 in the shaded jar.
    [[1;34mINFO[m] Including com.twitter.twittertext:twitter-text:jar:2.0.10 in the shaded jar.
    [[1;34mINFO[m] Including com.google.code.findbugs:jsr305:jar:2.0.1 in the shaded jar.
    [[1;34mINFO[m] Including com.github.TREMA-UNH:trec-car-tools-java:jar:19 in the shaded jar.
    [[1;34mINFO[m] Including co.nstant.in:cbor:jar:0.8 in the shaded jar.
    [[1;34mINFO[m] Including org.jetbrains:annotations-java5:jar:24.1.0 in the shaded jar.
    [[1;34mINFO[m] Including commons-io:commons-io:jar:2.16.1 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.commons:commons-compress:jar:1.26.2 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.commons:commons-csv:jar:1.8 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.commons:commons-text:jar:1.10.0 in the shaded jar.
    [[1;34mINFO[m] Including org.mockito:mockito-all:jar:1.10.19 in the shaded jar.
    [[1;34mINFO[m] Including org.jbibtex:jbibtex:jar:1.0.19 in the shaded jar.
    [[1;34mINFO[m] Including com.google.guava:guava:jar:33.4.8-jre in the shaded jar.
    [[1;34mINFO[m] Including com.google.guava:failureaccess:jar:1.0.3 in the shaded jar.
    [[1;34mINFO[m] Including com.google.guava:listenablefuture:jar:9999.0-empty-to-avoid-conflict-with-guava in the shaded jar.
    [[1;34mINFO[m] Including org.jspecify:jspecify:jar:1.0.0 in the shaded jar.
    [[1;34mINFO[m] Including com.google.errorprone:error_prone_annotations:jar:2.36.0 in the shaded jar.
    [[1;34mINFO[m] Including com.google.j2objc:j2objc-annotations:jar:3.0.0 in the shaded jar.
    [[1;34mINFO[m] Including com.microsoft.onnxruntime:onnxruntime:jar:1.17.0 in the shaded jar.
    [[1;34mINFO[m] Including ai.djl.huggingface:tokenizers:jar:0.33.0 in the shaded jar.
    [[1;34mINFO[m] Including ai.djl:api:jar:0.33.0 in the shaded jar.
    [[1;34mINFO[m] Including me.tongfei:progressbar:jar:0.10.1 in the shaded jar.
    [[1;34mINFO[m] Including org.jline:jline-terminal:jar:3.24.1 in the shaded jar.
    [[1;34mINFO[m] Including org.jline:jline-native:jar:3.24.1 in the shaded jar.
    [[1;34mINFO[m] Including commons-codec:commons-codec:jar:1.15 in the shaded jar.
    [[1;34mINFO[m] Including blue.strategic.parquet:parquet-floor:jar:1.36 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.parquet:parquet-column:jar:1.12.3 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.parquet:parquet-common:jar:1.12.3 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.parquet:parquet-encoding:jar:1.12.3 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.yetus:audience-annotations:jar:0.13.0 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.parquet:parquet-hadoop:jar:1.12.3 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.parquet:parquet-format-structures:jar:1.12.3 in the shaded jar.
    [[1;34mINFO[m] Including org.apache.parquet:parquet-jackson:jar:1.12.3 in the shaded jar.
    [[1;34mINFO[m] Including org.xerial.snappy:snappy-java:jar:1.1.8.3 in the shaded jar.
    [[1;34mINFO[m] Including com.github.luben:zstd-jni:jar:1.5.0-1 in the shaded jar.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] Discovered module-info.class. Shading will break its strong encapsulation.
    [[1;33mWARNING[m] args4j-2.33.jar, mockito-all-1.10.19.jar define 1 overlapping resource: 
    [[1;33mWARNING[m]   - LICENSE
    [[1;33mWARNING[m] audience-annotations-0.13.0.jar, log4j-api-2.23.1.jar, log4j-core-2.23.1.jar define 1 overlapping resource: 
    [[1;33mWARNING[m]   - META-INF/DEPENDENCIES
    [[1;33mWARNING[m] annotations-java5-24.1.0.jar, commons-compress-1.26.2.jar, commons-io-2.16.1.jar, error_prone_annotations-2.36.0.jar, failureaccess-1.0.3.jar, guava-33.4.8-jre.jar, j2objc-annotations-3.0.0.jar, jackson-core-2.16.0.jar, jackson-databind-2.16.0.jar, jackson-dataformat-yaml-2.16.0.jar, jackson-datatype-jdk8-2.16.0.jar, jspecify-1.0.0.jar, parquet-jackson-1.12.3.jar, snakeyaml-2.2.jar, xz-1.9.jar define 1 overlapping classes: 
    [[1;33mWARNING[m]   - META-INF.versions.9.module-info
    [[1;33mWARNING[m] jackson-databind-2.16.0.jar, parquet-jackson-1.12.3.jar define 2 overlapping resources: 
    [[1;33mWARNING[m]   - META-INF/maven/com.fasterxml.jackson.core/jackson-databind/pom.properties
    [[1;33mWARNING[m]   - META-INF/maven/com.fasterxml.jackson.core/jackson-databind/pom.xml
    [[1;33mWARNING[m] parquet-column-1.12.3.jar, parquet-hadoop-1.12.3.jar define 206 overlapping classes: 
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.Arrays
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.Arrays$ForkJoinGenericQuickSort
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.BidirectionalIterator
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.BigArrays
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.BigSwapper
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.Hash
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.Hash$Strategy
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.SafeMath
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.Stack
    [[1;33mWARNING[m]   - shaded.parquet.it.unimi.dsi.fastutil.Swapper
    [[1;33mWARNING[m]   - 196 more...
    [[1;33mWARNING[m] audience-annotations-0.13.0.jar, jackson-annotations-2.16.0.jar, jackson-core-2.16.0.jar, jackson-databind-2.16.0.jar, jackson-dataformat-yaml-2.16.0.jar, jackson-datatype-jdk8-2.16.0.jar, log4j-api-2.23.1.jar, log4j-core-2.23.1.jar, mockito-all-1.10.19.jar, parquet-jackson-1.12.3.jar define 1 overlapping resource: 
    [[1;33mWARNING[m]   - META-INF/NOTICE
    [[1;33mWARNING[m] audience-annotations-0.13.0.jar, failureaccess-1.0.3.jar, guava-33.4.8-jre.jar, jackson-annotations-2.16.0.jar, jackson-core-2.16.0.jar, jackson-databind-2.16.0.jar, jackson-dataformat-yaml-2.16.0.jar, jackson-datatype-jdk8-2.16.0.jar, jsoup-1.15.3.jar, log4j-api-2.23.1.jar, log4j-core-2.23.1.jar, mockito-all-1.10.19.jar, parquet-column-1.12.3.jar, parquet-encoding-1.12.3.jar, parquet-hadoop-1.12.3.jar, parquet-jackson-1.12.3.jar define 1 overlapping resource: 
    [[1;33mWARNING[m]   - META-INF/LICENSE
    [[1;33mWARNING[m] ant-1.10.11.jar, ant-launcher-1.10.11.jar, commons-codec-1.15.jar, commons-compress-1.26.2.jar, commons-csv-1.8.jar, commons-io-2.16.1.jar, commons-lang3-3.5.jar, commons-text-1.10.0.jar, lucene-analysis-common-9.9.1.jar, lucene-analysis-kuromoji-9.9.1.jar, lucene-analysis-morfologik-9.9.1.jar, lucene-backward-codecs-9.9.1.jar, lucene-codecs-9.9.1.jar, lucene-core-9.9.1.jar, lucene-queries-9.9.1.jar, lucene-queryparser-9.9.1.jar, lucene-sandbox-9.9.1.jar define 2 overlapping resources: 
    [[1;33mWARNING[m]   - META-INF/LICENSE.txt
    [[1;33mWARNING[m]   - META-INF/NOTICE.txt
    [[1;33mWARNING[m] jackson-annotations-2.16.0.jar, parquet-jackson-1.12.3.jar define 2 overlapping resources: 
    [[1;33mWARNING[m]   - META-INF/maven/com.fasterxml.jackson.core/jackson-annotations/pom.properties
    [[1;33mWARNING[m]   - META-INF/maven/com.fasterxml.jackson.core/jackson-annotations/pom.xml
    [[1;33mWARNING[m] jackson-core-2.16.0.jar, parquet-jackson-1.12.3.jar define 2 overlapping resources: 
    [[1;33mWARNING[m]   - META-INF/maven/com.fasterxml.jackson.core/jackson-core/pom.properties
    [[1;33mWARNING[m]   - META-INF/maven/com.fasterxml.jackson.core/jackson-core/pom.xml
    [[1;33mWARNING[m] annotations-java5-24.1.0.jar, anserini-1.1.2-SNAPSHOT.jar, ant-1.10.11.jar, ant-launcher-1.10.11.jar, api-0.33.0.jar, args4j-2.33.jar, audience-annotations-0.13.0.jar, cbor-0.8.jar, commons-codec-1.15.jar, commons-compress-1.26.2.jar, commons-csv-1.8.jar, commons-io-2.16.1.jar, commons-lang3-3.5.jar, commons-text-1.10.0.jar, error_prone_annotations-2.36.0.jar, failureaccess-1.0.3.jar, fastutil-8.5.8.jar, guava-33.4.8-jre.jar, j2objc-annotations-3.0.0.jar, jackson-annotations-2.16.0.jar, jackson-core-2.16.0.jar, jackson-databind-2.16.0.jar, jackson-dataformat-yaml-2.16.0.jar, jackson-datatype-jdk8-2.16.0.jar, jbibtex-1.0.19.jar, jline-native-3.24.1.jar, jline-terminal-3.24.1.jar, jsoup-1.15.3.jar, jspecify-1.0.0.jar, jsr305-2.0.1.jar, listenablefuture-9999.0-empty-to-avoid-conflict-with-guava.jar, log4j-api-2.23.1.jar, log4j-core-2.23.1.jar, lucene-analysis-common-9.9.1.jar, lucene-analysis-kuromoji-9.9.1.jar, lucene-analysis-morfologik-9.9.1.jar, lucene-backward-codecs-9.9.1.jar, lucene-codecs-9.9.1.jar, lucene-core-9.9.1.jar, lucene-queries-9.9.1.jar, lucene-queryparser-9.9.1.jar, lucene-sandbox-9.9.1.jar, mockito-all-1.10.19.jar, morfologik-fsa-2.1.9.jar, morfologik-polish-2.1.9.jar, morfologik-stemming-2.1.9.jar, morfologik-ukrainian-search-4.9.1.jar, onnxruntime-1.17.0.jar, parquet-column-1.12.3.jar, parquet-common-1.12.3.jar, parquet-encoding-1.12.3.jar, parquet-floor-1.36.jar, parquet-format-structures-1.12.3.jar, parquet-hadoop-1.12.3.jar, parquet-jackson-1.12.3.jar, progressbar-0.10.1.jar, slf4j-api-1.7.32.jar, slf4j-simple-1.7.32.jar, snakeyaml-2.2.jar, snappy-java-1.1.8.3.jar, tokenizers-0.33.0.jar, trec-car-tools-java-19.jar, twitter-text-2.0.10.jar, wikiclean-1.1.jar, xz-1.9.jar, zstd-jni-1.5.0-1.jar define 1 overlapping resource: 
    [[1;33mWARNING[m]   - META-INF/MANIFEST.MF
    [[1;33mWARNING[m] maven-shade-plugin has detected that some files are
    [[1;33mWARNING[m] present in two or more JARs. When this happens, only one
    [[1;33mWARNING[m] single version of the file is copied to the uber jar.
    [[1;33mWARNING[m] Usually this is not harmful and you can skip these warnings,
    [[1;33mWARNING[m] otherwise try to manually exclude artifacts based on
    [[1;33mWARNING[m] mvn dependency:tree -Ddetail=true and the above output.
    [[1;33mWARNING[m] See https://maven.apache.org/plugins/maven-shade-plugin/
    [[1;34mINFO[m] Attaching shaded artifact.
    [[1;34mINFO[m] [1m------------------------------------------------------------------------[m
    [[1;34mINFO[m] [1;32mBUILD SUCCESS[m
    [[1;34mINFO[m] [1m------------------------------------------------------------------------[m
    [[1;34mINFO[m] Total time:  01:24 min
    [[1;34mINFO[m] Finished at: 2025-08-11T17:13:39Z
    [[1;34mINFO[m] [1m------------------------------------------------------------------------[m
    [0m[0m


```python
!cd tools/eval && tar xvfz trec_eval.9.0.4.tar.gz && cd trec_eval.9.0.4 && make && cd ../../..
```

    trec_eval.9.0.4/
    trec_eval.9.0.4/m_prefs_pair.c
    trec_eval.9.0.4/m_ndcg_p.c
    trec_eval.9.0.4/m_infap.c
    trec_eval.9.0.4/m_num_q.c
    trec_eval.9.0.4/m_iprec_at_recall.c
    trec_eval.9.0.4/form_prefs_counts.c
    trec_eval.9.0.4/m_prefs_num_prefs_ful_ret.c
    trec_eval.9.0.4/utility_pool.c
    trec_eval.9.0.4/m_binG.c
    trec_eval.9.0.4/meas_avg.c
    trec_eval.9.0.4/m_gm_bpref.c
    trec_eval.9.0.4/m_runid.c
    trec_eval.9.0.4/m_bpref.c
    trec_eval.9.0.4/m_gm_map.c
    trec_eval.9.0.4/trec_eval.h
    trec_eval.9.0.4/m_yaap.c
    trec_eval.9.0.4/m_relstring.c
    trec_eval.9.0.4/m_Rprec.c
    trec_eval.9.0.4/m_prefs_avgjg.c
    trec_eval.9.0.4/m_success.c
    trec_eval.9.0.4/m_ndcg.c
    trec_eval.9.0.4/functions.h
    trec_eval.9.0.4/m_P_avgjg.c
    trec_eval.9.0.4/test/
    trec_eval.9.0.4/test/qrels.rel_level
    trec_eval.9.0.4/test/results.test
    trec_eval.9.0.4/test/qrels.test
    trec_eval.9.0.4/test/out.test.qrels_jg
    trec_eval.9.0.4/test/out.test.meas_params
    trec_eval.9.0.4/test/out.test.a
    trec_eval.9.0.4/test/out.test.prefs
    trec_eval.9.0.4/test/out.test.aqcM
    trec_eval.9.0.4/test/out.test.aql
    trec_eval.9.0.4/test/prefs.test
    trec_eval.9.0.4/test/out.test
    trec_eval.9.0.4/test/out.test.aq
    trec_eval.9.0.4/test/out.test.aqc
    trec_eval.9.0.4/test/out.test.qrels_prefs
    trec_eval.9.0.4/test/zscores_file
    trec_eval.9.0.4/test/qrels.123
    trec_eval.9.0.4/test/out.test.aqZ
    trec_eval.9.0.4/test/results.trunc
    trec_eval.9.0.4/test/prefs.results.test
    trec_eval.9.0.4/test/prefs.rank20
    trec_eval.9.0.4/m_11pt_avg.c
    trec_eval.9.0.4/m_G.c
    trec_eval.9.0.4/m_num_rel.c
    trec_eval.9.0.4/m_map_cut.c
    trec_eval.9.0.4/m_prefs_avgjg_ret.c
    trec_eval.9.0.4/m_Rprec_mult.c
    trec_eval.9.0.4/Makefile
    trec_eval.9.0.4/m_map_avgjg.c
    trec_eval.9.0.4/get_qrels_prefs.c
    trec_eval.9.0.4/README
    trec_eval.9.0.4/m_set_rel_P.c
    trec_eval.9.0.4/sysfunc.h
    trec_eval.9.0.4/m_prefs_pair_ret.c
    trec_eval.9.0.4/convert_zscores.c
    trec_eval.9.0.4/m_ndcg_cut.c
    trec_eval.9.0.4/m_prefs_pair_imp.c
    trec_eval.9.0.4/meas_print_single.c
    trec_eval.9.0.4/meas_print_final.c
    trec_eval.9.0.4/trec_eval.c
    trec_eval.9.0.4/m_num_ret.c
    trec_eval.9.0.4/get_prefs.c
    trec_eval.9.0.4/m_P.c
    trec_eval.9.0.4/get_qrels_jg.c
    trec_eval.9.0.4/m_rel_P.c
    trec_eval.9.0.4/meas_acc.c
    trec_eval.9.0.4/m_prefs_simp.c
    trec_eval.9.0.4/m_recall.c
    trec_eval.9.0.4/trec_format.h
    trec_eval.9.0.4/m_ndcg_rel.c
    trec_eval.9.0.4/m_num_nonrel_judged_ret.c
    trec_eval.9.0.4/formats.c
    trec_eval.9.0.4/bpref_bug
    trec_eval.9.0.4/README.windows.md
    trec_eval.9.0.4/m_prefs_num_prefs_ful.c
    trec_eval.9.0.4/m_set_map.c
    trec_eval.9.0.4/get_qrels.c
    trec_eval.9.0.4/m_set_F.c
    trec_eval.9.0.4/measures.c
    trec_eval.9.0.4/common.h
    trec_eval.9.0.4/meas_init.c
    trec_eval.9.0.4/m_recip_rank.c
    trec_eval.9.0.4/m_set_recall.c
    trec_eval.9.0.4/get_trec_results.c
    trec_eval.9.0.4/m_prefs_simp_ret.c
    trec_eval.9.0.4/m_num_rel_ret.c
    trec_eval.9.0.4/m_map.c
    trec_eval.9.0.4/m_utility.c
    trec_eval.9.0.4/form_res_rels.c
    trec_eval.9.0.4/form_res_rels_jg.c
    trec_eval.9.0.4/m_prefs_simp_imp.c
    trec_eval.9.0.4/m_prefs_num_prefs_poss.c
    trec_eval.9.0.4/m_prefs_avgjg_Rnonrel.c
    trec_eval.9.0.4/m_prefs_avgjg_Rnonrel_ret.c
    trec_eval.9.0.4/m_set_P.c
    trec_eval.9.0.4/m_prefs_avgjg_imp.c
    trec_eval.9.0.4/m_Rndcg.c
    trec_eval.9.0.4/CHANGELOG
    trec_eval.9.0.4/m_Rprec_mult_avgjg.c
    trec_eval.9.0.4/get_zscores.c
    gcc -g -I.  -Wall -DVERSIONID=\"9.0.4\"  -o trec_eval trec_eval.c formats.c meas_init.c meas_acc.c meas_avg.c meas_print_single.c meas_print_final.c get_qrels.c get_trec_results.c get_prefs.c get_qrels_prefs.c get_qrels_jg.c form_res_rels.c form_res_rels_jg.c form_prefs_counts.c utility_pool.c get_zscores.c convert_zscores.c measures.c  m_map.c m_P.c m_num_q.c m_num_ret.c m_num_rel.c m_num_rel_ret.c m_gm_map.c m_Rprec.c m_recip_rank.c m_bpref.c m_iprec_at_recall.c m_recall.c m_Rprec_mult.c m_utility.c m_11pt_avg.c m_ndcg.c m_ndcg_cut.c m_Rndcg.c m_ndcg_rel.c m_binG.c m_G.c m_rel_P.c m_success.c m_infap.c m_map_cut.c m_gm_bpref.c m_runid.c m_relstring.c m_set_P.c m_set_recall.c m_set_rel_P.c m_set_map.c m_set_F.c m_num_nonrel_judged_ret.c m_prefs_num_prefs_poss.c m_prefs_num_prefs_ful.c m_prefs_num_prefs_ful_ret.c m_prefs_simp.c m_prefs_pair.c m_prefs_avgjg.c m_prefs_avgjg_Rnonrel.c m_prefs_simp_ret.c m_prefs_pair_ret.c m_prefs_avgjg_ret.c m_prefs_avgjg_Rnonrel_ret.c m_prefs_simp_imp.c m_prefs_pair_imp.c m_prefs_avgjg_imp.c m_map_avgjg.c m_Rprec_mult_avgjg.c m_P_avgjg.c m_yaap.c -lm



```python
!cd tools/eval/ndeval && make && cd ../../..
```

    gcc -o ndeval ndeval.c -lm
    [01m[Kndeval.c:[m[K In function ‘[01m[Kmain[m[K’:
    [01m[Kndeval.c:1435:9:[m[K [01;35m[Kwarning: [m[Kformat not a string literal and no format arguments [[01;35m[K]8;;https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html#index-Wformat-security-Wformat-security]8;;[m[K]
     1435 |         [01;35m[Kprintf[m[K (helpText);
          |         [01;35m[K^~~~~~[m[K



```python
%cd ../
```

    /content


**Pyserini**

Follow development installation instructions


```python
!git clone https://github.com/castorini/pyserini.git --recurse-submodules
```

    Cloning into 'pyserini'...
    remote: Enumerating objects: 11248, done.[K
    remote: Counting objects: 100% (83/83), done.[K
    remote: Compressing objects: 100% (56/56), done.[K
    remote: Total 11248 (delta 50), reused 27 (delta 27), pack-reused 11165 (from 2)[K
    Receiving objects: 100% (11248/11248), 8.51 MiB | 29.42 MiB/s, done.
    Resolving deltas: 100% (8461/8461), done.
    Submodule 'pyserini/encode/mbeir/uniir/_uniir_vendor' (https://github.com/TIGER-AI-Lab/UniIR) registered for path 'pyserini/encode/mbeir/uniir/_uniir_vendor'
    Submodule 'tools' (https://github.com/castorini/anserini-tools.git) registered for path 'tools'
    Cloning into '/content/pyserini/pyserini/encode/mbeir/uniir/_uniir_vendor'...
    remote: Enumerating objects: 906, done.        
    remote: Counting objects: 100% (353/353), done.        
    remote: Compressing objects: 100% (195/195), done.        
    remote: Total 906 (delta 186), reused 270 (delta 142), pack-reused 553 (from 1)        
    Receiving objects: 100% (906/906), 54.91 MiB | 38.59 MiB/s, done.
    Resolving deltas: 100% (448/448), done.
    Cloning into '/content/pyserini/tools'...
    remote: Enumerating objects: 1118, done.        
    remote: Counting objects: 100% (81/81), done.        
    remote: Compressing objects: 100% (27/27), done.        
    remote: Total 1118 (delta 67), reused 55 (delta 54), pack-reused 1037 (from 3)        
    Receiving objects: 100% (1118/1118), 781.49 MiB | 37.08 MiB/s, done.
    Resolving deltas: 100% (252/252), done.
    Submodule path 'pyserini/encode/mbeir/uniir/_uniir_vendor': checked out '98dc570c2645fec8e1fd42c7d4ac9853f46051fd'
    Submodule path 'tools': checked out '444a982f2cf24940c8f7f941dd9659eb36a0debd'



```python
%cd pyserini/
```

    /content/pyserini



```python
!cd tools/eval && tar xvfz trec_eval.9.0.4.tar.gz && cd trec_eval.9.0.4 && make && cd ../../..
```

    trec_eval.9.0.4/
    trec_eval.9.0.4/m_prefs_pair.c
    trec_eval.9.0.4/m_ndcg_p.c
    trec_eval.9.0.4/m_infap.c
    trec_eval.9.0.4/m_num_q.c
    trec_eval.9.0.4/m_iprec_at_recall.c
    trec_eval.9.0.4/form_prefs_counts.c
    trec_eval.9.0.4/m_prefs_num_prefs_ful_ret.c
    trec_eval.9.0.4/utility_pool.c
    trec_eval.9.0.4/m_binG.c
    trec_eval.9.0.4/meas_avg.c
    trec_eval.9.0.4/m_gm_bpref.c
    trec_eval.9.0.4/m_runid.c
    trec_eval.9.0.4/m_bpref.c
    trec_eval.9.0.4/m_gm_map.c
    trec_eval.9.0.4/trec_eval.h
    trec_eval.9.0.4/m_yaap.c
    trec_eval.9.0.4/m_relstring.c
    trec_eval.9.0.4/m_Rprec.c
    trec_eval.9.0.4/m_prefs_avgjg.c
    trec_eval.9.0.4/m_success.c
    trec_eval.9.0.4/m_ndcg.c
    trec_eval.9.0.4/functions.h
    trec_eval.9.0.4/m_P_avgjg.c
    trec_eval.9.0.4/test/
    trec_eval.9.0.4/test/qrels.rel_level
    trec_eval.9.0.4/test/results.test
    trec_eval.9.0.4/test/qrels.test
    trec_eval.9.0.4/test/out.test.qrels_jg
    trec_eval.9.0.4/test/out.test.meas_params
    trec_eval.9.0.4/test/out.test.a
    trec_eval.9.0.4/test/out.test.prefs
    trec_eval.9.0.4/test/out.test.aqcM
    trec_eval.9.0.4/test/out.test.aql
    trec_eval.9.0.4/test/prefs.test
    trec_eval.9.0.4/test/out.test
    trec_eval.9.0.4/test/out.test.aq
    trec_eval.9.0.4/test/out.test.aqc
    trec_eval.9.0.4/test/out.test.qrels_prefs
    trec_eval.9.0.4/test/zscores_file
    trec_eval.9.0.4/test/qrels.123
    trec_eval.9.0.4/test/out.test.aqZ
    trec_eval.9.0.4/test/results.trunc
    trec_eval.9.0.4/test/prefs.results.test
    trec_eval.9.0.4/test/prefs.rank20
    trec_eval.9.0.4/m_11pt_avg.c
    trec_eval.9.0.4/m_G.c
    trec_eval.9.0.4/m_num_rel.c
    trec_eval.9.0.4/m_map_cut.c
    trec_eval.9.0.4/m_prefs_avgjg_ret.c
    trec_eval.9.0.4/m_Rprec_mult.c
    trec_eval.9.0.4/Makefile
    trec_eval.9.0.4/m_map_avgjg.c
    trec_eval.9.0.4/get_qrels_prefs.c
    trec_eval.9.0.4/README
    trec_eval.9.0.4/m_set_rel_P.c
    trec_eval.9.0.4/sysfunc.h
    trec_eval.9.0.4/m_prefs_pair_ret.c
    trec_eval.9.0.4/convert_zscores.c
    trec_eval.9.0.4/m_ndcg_cut.c
    trec_eval.9.0.4/m_prefs_pair_imp.c
    trec_eval.9.0.4/meas_print_single.c
    trec_eval.9.0.4/meas_print_final.c
    trec_eval.9.0.4/trec_eval.c
    trec_eval.9.0.4/m_num_ret.c
    trec_eval.9.0.4/get_prefs.c
    trec_eval.9.0.4/m_P.c
    trec_eval.9.0.4/get_qrels_jg.c
    trec_eval.9.0.4/m_rel_P.c
    trec_eval.9.0.4/meas_acc.c
    trec_eval.9.0.4/m_prefs_simp.c
    trec_eval.9.0.4/m_recall.c
    trec_eval.9.0.4/trec_format.h
    trec_eval.9.0.4/m_ndcg_rel.c
    trec_eval.9.0.4/m_num_nonrel_judged_ret.c
    trec_eval.9.0.4/formats.c
    trec_eval.9.0.4/bpref_bug
    trec_eval.9.0.4/README.windows.md
    trec_eval.9.0.4/m_prefs_num_prefs_ful.c
    trec_eval.9.0.4/m_set_map.c
    trec_eval.9.0.4/get_qrels.c
    trec_eval.9.0.4/m_set_F.c
    trec_eval.9.0.4/measures.c
    trec_eval.9.0.4/common.h
    trec_eval.9.0.4/meas_init.c
    trec_eval.9.0.4/m_recip_rank.c
    trec_eval.9.0.4/m_set_recall.c
    trec_eval.9.0.4/get_trec_results.c
    trec_eval.9.0.4/m_prefs_simp_ret.c
    trec_eval.9.0.4/m_num_rel_ret.c
    trec_eval.9.0.4/m_map.c
    trec_eval.9.0.4/m_utility.c
    trec_eval.9.0.4/form_res_rels.c
    trec_eval.9.0.4/form_res_rels_jg.c
    trec_eval.9.0.4/m_prefs_simp_imp.c
    trec_eval.9.0.4/m_prefs_num_prefs_poss.c
    trec_eval.9.0.4/m_prefs_avgjg_Rnonrel.c
    trec_eval.9.0.4/m_prefs_avgjg_Rnonrel_ret.c
    trec_eval.9.0.4/m_set_P.c
    trec_eval.9.0.4/m_prefs_avgjg_imp.c
    trec_eval.9.0.4/m_Rndcg.c
    trec_eval.9.0.4/CHANGELOG
    trec_eval.9.0.4/m_Rprec_mult_avgjg.c
    trec_eval.9.0.4/get_zscores.c
    gcc -g -I.  -Wall -DVERSIONID=\"9.0.4\"  -o trec_eval trec_eval.c formats.c meas_init.c meas_acc.c meas_avg.c meas_print_single.c meas_print_final.c get_qrels.c get_trec_results.c get_prefs.c get_qrels_prefs.c get_qrels_jg.c form_res_rels.c form_res_rels_jg.c form_prefs_counts.c utility_pool.c get_zscores.c convert_zscores.c measures.c  m_map.c m_P.c m_num_q.c m_num_ret.c m_num_rel.c m_num_rel_ret.c m_gm_map.c m_Rprec.c m_recip_rank.c m_bpref.c m_iprec_at_recall.c m_recall.c m_Rprec_mult.c m_utility.c m_11pt_avg.c m_ndcg.c m_ndcg_cut.c m_Rndcg.c m_ndcg_rel.c m_binG.c m_G.c m_rel_P.c m_success.c m_infap.c m_map_cut.c m_gm_bpref.c m_runid.c m_relstring.c m_set_P.c m_set_recall.c m_set_rel_P.c m_set_map.c m_set_F.c m_num_nonrel_judged_ret.c m_prefs_num_prefs_poss.c m_prefs_num_prefs_ful.c m_prefs_num_prefs_ful_ret.c m_prefs_simp.c m_prefs_pair.c m_prefs_avgjg.c m_prefs_avgjg_Rnonrel.c m_prefs_simp_ret.c m_prefs_pair_ret.c m_prefs_avgjg_ret.c m_prefs_avgjg_Rnonrel_ret.c m_prefs_simp_imp.c m_prefs_pair_imp.c m_prefs_avgjg_imp.c m_map_avgjg.c m_Rprec_mult_avgjg.c m_P_avgjg.c m_yaap.c -lm



```python
!cd tools/eval/ndeval && make && cd ../../..
```

    gcc -o ndeval ndeval.c -lm
    [01m[Kndeval.c:[m[K In function ‘[01m[Kmain[m[K’:
    [01m[Kndeval.c:1435:9:[m[K [01;35m[Kwarning: [m[Kformat not a string literal and no format arguments [[01;35m[K]8;;https://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html#index-Wformat-security-Wformat-security]8;;[m[K]
     1435 |         [01;35m[Kprintf[m[K (helpText);
          |         [01;35m[K^~~~~~[m[K



```python
!pip install -e .
```

    Obtaining file:///content/pyserini
      Installing build dependencies ... [?25l[?25hdone
      Checking if build backend supports build_editable ... [?25l[?25hdone
      Getting requirements to build editable ... [?25l[?25hdone
      Preparing editable metadata (pyproject.toml) ... [?25l[?25hdone
    Requirement already satisfied: tqdm in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (4.67.1)
    Requirement already satisfied: pyyaml in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (6.0.2)
    Requirement already satisfied: requests in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (2.32.3)
    Requirement already satisfied: Cython>=0.29.21 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (3.0.12)
    Requirement already satisfied: numpy>=1.18.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (2.0.2)
    Requirement already satisfied: pandas>=1.4.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (2.2.2)
    Collecting pyjnius>=1.6.0 (from pyserini==1.2.0)
      Downloading pyjnius-1.6.1-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (10 kB)
    Requirement already satisfied: scikit-learn>=0.22.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (1.6.1)
    Requirement already satisfied: scipy>=1.4.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (1.16.1)
    Requirement already satisfied: transformers>=4.6.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (4.55.0)
    Requirement already satisfied: torch>=2.4.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (2.6.0+cu124)
    Collecting onnxruntime>=1.8.1 (from pyserini==1.2.0)
      Downloading onnxruntime-1.22.1-cp311-cp311-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl.metadata (4.6 kB)
    Requirement already satisfied: openai>=1.0.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (1.99.1)
    Requirement already satisfied: sentencepiece>=0.2 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (0.2.0)
    Requirement already satisfied: tiktoken>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (0.10.0)
    Requirement already satisfied: flask>3.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (3.1.1)
    Requirement already satisfied: pillow>=10.2.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (11.3.0)
    Requirement already satisfied: fastapi>=0.70.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (0.116.1)
    Requirement already satisfied: uvicorn>=0.13.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0) (0.35.0)
    Collecting fastmcp>=2.10.4 (from pyserini==1.2.0)
      Downloading fastmcp-2.11.2-py3-none-any.whl.metadata (17 kB)
    Requirement already satisfied: starlette<0.48.0,>=0.40.0 in /usr/local/lib/python3.11/dist-packages (from fastapi>=0.70.0->pyserini==1.2.0) (0.47.2)
    Requirement already satisfied: pydantic!=1.8,!=1.8.1,!=2.0.0,!=2.0.1,!=2.1.0,<3.0.0,>=1.7.4 in /usr/local/lib/python3.11/dist-packages (from fastapi>=0.70.0->pyserini==1.2.0) (2.11.7)
    Requirement already satisfied: typing-extensions>=4.8.0 in /usr/local/lib/python3.11/dist-packages (from fastapi>=0.70.0->pyserini==1.2.0) (4.14.1)
    Collecting authlib>=1.5.2 (from fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading authlib-1.6.1-py2.py3-none-any.whl.metadata (1.6 kB)
    Collecting cyclopts>=3.0.0 (from fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading cyclopts-3.22.5-py3-none-any.whl.metadata (11 kB)
    Collecting exceptiongroup>=1.2.2 (from fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading exceptiongroup-1.3.0-py3-none-any.whl.metadata (6.7 kB)
    Requirement already satisfied: httpx>=0.28.1 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0) (0.28.1)
    Collecting mcp>=1.10.0 (from fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading mcp-1.12.4-py3-none-any.whl.metadata (68 kB)
    [2K     [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m68.2/68.2 kB[0m [31m4.3 MB/s[0m eta [36m0:00:00[0m
    [?25hCollecting openapi-core>=0.19.5 (from fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading openapi_core-0.19.5-py3-none-any.whl.metadata (6.6 kB)
    Collecting openapi-pydantic>=0.5.1 (from fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading openapi_pydantic-0.5.1-py3-none-any.whl.metadata (10 kB)
    Requirement already satisfied: pyperclip>=1.9.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0) (1.9.0)
    Collecting python-dotenv>=1.1.0 (from fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading python_dotenv-1.1.1-py3-none-any.whl.metadata (24 kB)
    Requirement already satisfied: rich>=13.9.4 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0) (13.9.4)
    Requirement already satisfied: blinker>=1.9.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0) (1.9.0)
    Requirement already satisfied: click>=8.1.3 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0) (8.2.1)
    Requirement already satisfied: itsdangerous>=2.2.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0) (2.2.0)
    Requirement already satisfied: jinja2>=3.1.2 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0) (3.1.6)
    Requirement already satisfied: markupsafe>=2.1.1 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0) (3.0.2)
    Requirement already satisfied: werkzeug>=3.1.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0) (3.1.3)
    Collecting coloredlogs (from onnxruntime>=1.8.1->pyserini==1.2.0)
      Downloading coloredlogs-15.0.1-py2.py3-none-any.whl.metadata (12 kB)
    Requirement already satisfied: flatbuffers in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0) (25.2.10)
    Requirement already satisfied: packaging in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0) (25.0)
    Requirement already satisfied: protobuf in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0) (5.29.5)
    Requirement already satisfied: sympy in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0) (1.13.1)
    Requirement already satisfied: anyio<5,>=3.5.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.0.0->pyserini==1.2.0) (4.10.0)
    Requirement already satisfied: distro<2,>=1.7.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.0.0->pyserini==1.2.0) (1.9.0)
    Requirement already satisfied: jiter<1,>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.0.0->pyserini==1.2.0) (0.10.0)
    Requirement already satisfied: sniffio in /usr/local/lib/python3.11/dist-packages (from openai>=1.0.0->pyserini==1.2.0) (1.3.1)
    Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0) (2025.2)
    Requirement already satisfied: tzdata>=2022.7 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0) (2025.2)
    Requirement already satisfied: joblib>=1.2.0 in /usr/local/lib/python3.11/dist-packages (from scikit-learn>=0.22.1->pyserini==1.2.0) (1.5.1)
    Requirement already satisfied: threadpoolctl>=3.1.0 in /usr/local/lib/python3.11/dist-packages (from scikit-learn>=0.22.1->pyserini==1.2.0) (3.6.0)
    Requirement already satisfied: regex>=2022.1.18 in /usr/local/lib/python3.11/dist-packages (from tiktoken>=0.4.0->pyserini==1.2.0) (2024.11.6)
    Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0) (3.4.2)
    Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0) (3.10)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0) (2.5.0)
    Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0) (2025.8.3)
    Requirement already satisfied: filelock in /usr/local/lib/python3.11/dist-packages (from torch>=2.4.0->pyserini==1.2.0) (3.18.0)
    Requirement already satisfied: networkx in /usr/local/lib/python3.11/dist-packages (from torch>=2.4.0->pyserini==1.2.0) (3.5)
    Requirement already satisfied: fsspec in /usr/local/lib/python3.11/dist-packages (from torch>=2.4.0->pyserini==1.2.0) (2025.3.0)
    Collecting nvidia-cuda-nvrtc-cu12==12.4.127 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cuda_nvrtc_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl.metadata (1.5 kB)
    Collecting nvidia-cuda-runtime-cu12==12.4.127 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cuda_runtime_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl.metadata (1.5 kB)
    Collecting nvidia-cuda-cupti-cu12==12.4.127 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cuda_cupti_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl.metadata (1.6 kB)
    Collecting nvidia-cudnn-cu12==9.1.0.70 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cudnn_cu12-9.1.0.70-py3-none-manylinux2014_x86_64.whl.metadata (1.6 kB)
    Collecting nvidia-cublas-cu12==12.4.5.8 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cublas_cu12-12.4.5.8-py3-none-manylinux2014_x86_64.whl.metadata (1.5 kB)
    Collecting nvidia-cufft-cu12==11.2.1.3 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cufft_cu12-11.2.1.3-py3-none-manylinux2014_x86_64.whl.metadata (1.5 kB)
    Collecting nvidia-curand-cu12==10.3.5.147 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_curand_cu12-10.3.5.147-py3-none-manylinux2014_x86_64.whl.metadata (1.5 kB)
    Collecting nvidia-cusolver-cu12==11.6.1.9 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cusolver_cu12-11.6.1.9-py3-none-manylinux2014_x86_64.whl.metadata (1.6 kB)
    Collecting nvidia-cusparse-cu12==12.3.1.170 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_cusparse_cu12-12.3.1.170-py3-none-manylinux2014_x86_64.whl.metadata (1.6 kB)
    Requirement already satisfied: nvidia-cusparselt-cu12==0.6.2 in /usr/local/lib/python3.11/dist-packages (from torch>=2.4.0->pyserini==1.2.0) (0.6.2)
    Collecting nvidia-nccl-cu12==2.21.5 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_nccl_cu12-2.21.5-py3-none-manylinux2014_x86_64.whl.metadata (1.8 kB)
    Requirement already satisfied: nvidia-nvtx-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.4.0->pyserini==1.2.0) (12.4.127)
    Collecting nvidia-nvjitlink-cu12==12.4.127 (from torch>=2.4.0->pyserini==1.2.0)
      Downloading nvidia_nvjitlink_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl.metadata (1.5 kB)
    Requirement already satisfied: triton==3.2.0 in /usr/local/lib/python3.11/dist-packages (from torch>=2.4.0->pyserini==1.2.0) (3.2.0)
    Requirement already satisfied: mpmath<1.4,>=1.1.0 in /usr/local/lib/python3.11/dist-packages (from sympy->onnxruntime>=1.8.1->pyserini==1.2.0) (1.3.0)
    Requirement already satisfied: huggingface-hub<1.0,>=0.34.0 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.6.0->pyserini==1.2.0) (0.34.3)
    Requirement already satisfied: tokenizers<0.22,>=0.21 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.6.0->pyserini==1.2.0) (0.21.4)
    Requirement already satisfied: safetensors>=0.4.3 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.6.0->pyserini==1.2.0) (0.6.1)
    Requirement already satisfied: h11>=0.8 in /usr/local/lib/python3.11/dist-packages (from uvicorn>=0.13.0->pyserini==1.2.0) (0.16.0)
    Requirement already satisfied: cryptography in /usr/local/lib/python3.11/dist-packages (from authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0) (43.0.3)
    Requirement already satisfied: attrs>=23.1.0 in /usr/local/lib/python3.11/dist-packages (from cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0) (25.3.0)
    Requirement already satisfied: docstring-parser>=0.15 in /usr/local/lib/python3.11/dist-packages (from cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0) (0.17.0)
    Collecting rich-rst<2.0.0,>=1.3.1 (from cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading rich_rst-1.3.1-py3-none-any.whl.metadata (6.0 kB)
    Requirement already satisfied: httpcore==1.* in /usr/local/lib/python3.11/dist-packages (from httpx>=0.28.1->fastmcp>=2.10.4->pyserini==1.2.0) (1.0.9)
    Requirement already satisfied: hf-xet<2.0.0,>=1.1.3 in /usr/local/lib/python3.11/dist-packages (from huggingface-hub<1.0,>=0.34.0->transformers>=4.6.0->pyserini==1.2.0) (1.1.7)
    Collecting httpx-sse>=0.4 (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading httpx_sse-0.4.1-py3-none-any.whl.metadata (9.4 kB)
    Requirement already satisfied: jsonschema>=4.20.0 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0) (4.25.0)
    Collecting pydantic-settings>=2.5.2 (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading pydantic_settings-2.10.1-py3-none-any.whl.metadata (3.4 kB)
    Requirement already satisfied: python-multipart>=0.0.9 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0) (0.0.20)
    Collecting sse-starlette>=1.6.1 (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading sse_starlette-3.0.2-py3-none-any.whl.metadata (11 kB)
    Collecting isodate (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading isodate-0.7.2-py3-none-any.whl.metadata (11 kB)
    Collecting jsonschema-path<0.4.0,>=0.3.1 (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading jsonschema_path-0.3.4-py3-none-any.whl.metadata (4.3 kB)
    Requirement already satisfied: more-itertools in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0) (10.7.0)
    Collecting openapi-schema-validator<0.7.0,>=0.6.0 (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading openapi_schema_validator-0.6.3-py3-none-any.whl.metadata (5.4 kB)
    Collecting openapi-spec-validator<0.8.0,>=0.7.1 (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading openapi_spec_validator-0.7.2-py3-none-any.whl.metadata (5.7 kB)
    Collecting parse (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading parse-1.20.2-py2.py3-none-any.whl.metadata (22 kB)
    Collecting werkzeug>=3.1.0 (from flask>3.0->pyserini==1.2.0)
      Downloading werkzeug-3.1.1-py3-none-any.whl.metadata (3.7 kB)
    Requirement already satisfied: annotated-types>=0.6.0 in /usr/local/lib/python3.11/dist-packages (from pydantic!=1.8,!=1.8.1,!=2.0.0,!=2.0.1,!=2.1.0,<3.0.0,>=1.7.4->fastapi>=0.70.0->pyserini==1.2.0) (0.7.0)
    Requirement already satisfied: pydantic-core==2.33.2 in /usr/local/lib/python3.11/dist-packages (from pydantic!=1.8,!=1.8.1,!=2.0.0,!=2.0.1,!=2.1.0,<3.0.0,>=1.7.4->fastapi>=0.70.0->pyserini==1.2.0) (2.33.2)
    Requirement already satisfied: typing-inspection>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from pydantic!=1.8,!=1.8.1,!=2.0.0,!=2.0.1,!=2.1.0,<3.0.0,>=1.7.4->fastapi>=0.70.0->pyserini==1.2.0) (0.4.1)
    Collecting email-validator>=2.0.0 (from pydantic[email]>=2.11.7->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading email_validator-2.2.0-py3-none-any.whl.metadata (25 kB)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.11/dist-packages (from python-dateutil>=2.8.2->pandas>=1.4.0->pyserini==1.2.0) (1.17.0)
    Requirement already satisfied: markdown-it-py>=2.2.0 in /usr/local/lib/python3.11/dist-packages (from rich>=13.9.4->fastmcp>=2.10.4->pyserini==1.2.0) (3.0.0)
    Requirement already satisfied: pygments<3.0.0,>=2.13.0 in /usr/local/lib/python3.11/dist-packages (from rich>=13.9.4->fastmcp>=2.10.4->pyserini==1.2.0) (2.19.2)
    Collecting humanfriendly>=9.1 (from coloredlogs->onnxruntime>=1.8.1->pyserini==1.2.0)
      Downloading humanfriendly-10.0-py2.py3-none-any.whl.metadata (9.2 kB)
    Collecting dnspython>=2.0.0 (from email-validator>=2.0.0->pydantic[email]>=2.11.7->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading dnspython-2.7.0-py3-none-any.whl.metadata (5.8 kB)
    Requirement already satisfied: jsonschema-specifications>=2023.03.6 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0) (2025.4.1)
    Requirement already satisfied: referencing>=0.28.4 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0) (0.36.2)
    Requirement already satisfied: rpds-py>=0.7.1 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0) (0.26.0)
    Collecting pathable<0.5.0,>=0.4.1 (from jsonschema-path<0.4.0,>=0.3.1->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading pathable-0.4.4-py3-none-any.whl.metadata (1.8 kB)
    Requirement already satisfied: mdurl~=0.1 in /usr/local/lib/python3.11/dist-packages (from markdown-it-py>=2.2.0->rich>=13.9.4->fastmcp>=2.10.4->pyserini==1.2.0) (0.1.2)
    Collecting rfc3339-validator (from openapi-schema-validator<0.7.0,>=0.6.0->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading rfc3339_validator-0.1.4-py2.py3-none-any.whl.metadata (1.5 kB)
    Collecting lazy-object-proxy<2.0.0,>=1.7.1 (from openapi-spec-validator<0.8.0,>=0.7.1->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0)
      Downloading lazy_object_proxy-1.11.0-py3-none-any.whl.metadata (8.2 kB)
    Requirement already satisfied: docutils in /usr/local/lib/python3.11/dist-packages (from rich-rst<2.0.0,>=1.3.1->cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0) (0.21.2)
    Requirement already satisfied: cffi>=1.12 in /usr/local/lib/python3.11/dist-packages (from cryptography->authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0) (1.17.1)
    Requirement already satisfied: pycparser in /usr/local/lib/python3.11/dist-packages (from cffi>=1.12->cryptography->authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0) (2.22)
    Downloading fastmcp-2.11.2-py3-none-any.whl (257 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m257.1/257.1 kB[0m [31m17.9 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading onnxruntime-1.22.1-cp311-cp311-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl (16.5 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m16.5/16.5 MB[0m [31m77.3 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading pyjnius-1.6.1-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (1.6 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m1.6/1.6 MB[0m [31m59.6 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cublas_cu12-12.4.5.8-py3-none-manylinux2014_x86_64.whl (363.4 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m363.4/363.4 MB[0m [31m4.1 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cuda_cupti_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl (13.8 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m13.8/13.8 MB[0m [31m119.3 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cuda_nvrtc_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl (24.6 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m24.6/24.6 MB[0m [31m95.5 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cuda_runtime_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl (883 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m883.7/883.7 kB[0m [31m56.2 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cudnn_cu12-9.1.0.70-py3-none-manylinux2014_x86_64.whl (664.8 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m664.8/664.8 MB[0m [31m3.0 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cufft_cu12-11.2.1.3-py3-none-manylinux2014_x86_64.whl (211.5 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m211.5/211.5 MB[0m [31m5.7 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_curand_cu12-10.3.5.147-py3-none-manylinux2014_x86_64.whl (56.3 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m56.3/56.3 MB[0m [31m16.1 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cusolver_cu12-11.6.1.9-py3-none-manylinux2014_x86_64.whl (127.9 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m127.9/127.9 MB[0m [31m7.8 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_cusparse_cu12-12.3.1.170-py3-none-manylinux2014_x86_64.whl (207.5 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m207.5/207.5 MB[0m [31m5.9 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_nccl_cu12-2.21.5-py3-none-manylinux2014_x86_64.whl (188.7 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m188.7/188.7 MB[0m [31m6.3 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nvidia_nvjitlink_cu12-12.4.127-py3-none-manylinux2014_x86_64.whl (21.1 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m21.1/21.1 MB[0m [31m101.9 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading authlib-1.6.1-py2.py3-none-any.whl (239 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m239.3/239.3 kB[0m [31m22.0 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading cyclopts-3.22.5-py3-none-any.whl (84 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m85.0/85.0 kB[0m [31m9.2 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading exceptiongroup-1.3.0-py3-none-any.whl (16 kB)
    Downloading mcp-1.12.4-py3-none-any.whl (160 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m160.1/160.1 kB[0m [31m16.8 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading openapi_core-0.19.5-py3-none-any.whl (106 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m106.6/106.6 kB[0m [31m11.1 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading openapi_pydantic-0.5.1-py3-none-any.whl (96 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m96.4/96.4 kB[0m [31m9.8 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading python_dotenv-1.1.1-py3-none-any.whl (20 kB)
    Downloading werkzeug-3.1.1-py3-none-any.whl (224 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m224.4/224.4 kB[0m [31m23.3 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading coloredlogs-15.0.1-py2.py3-none-any.whl (46 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m46.0/46.0 kB[0m [31m4.4 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading email_validator-2.2.0-py3-none-any.whl (33 kB)
    Downloading httpx_sse-0.4.1-py3-none-any.whl (8.1 kB)
    Downloading humanfriendly-10.0-py2.py3-none-any.whl (86 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m86.8/86.8 kB[0m [31m9.6 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading jsonschema_path-0.3.4-py3-none-any.whl (14 kB)
    Downloading openapi_schema_validator-0.6.3-py3-none-any.whl (8.8 kB)
    Downloading openapi_spec_validator-0.7.2-py3-none-any.whl (39 kB)
    Downloading pydantic_settings-2.10.1-py3-none-any.whl (45 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m45.2/45.2 kB[0m [31m4.6 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading rich_rst-1.3.1-py3-none-any.whl (11 kB)
    Downloading sse_starlette-3.0.2-py3-none-any.whl (11 kB)
    Downloading isodate-0.7.2-py3-none-any.whl (22 kB)
    Downloading parse-1.20.2-py2.py3-none-any.whl (20 kB)
    Downloading dnspython-2.7.0-py3-none-any.whl (313 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m313.6/313.6 kB[0m [31m31.8 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading lazy_object_proxy-1.11.0-py3-none-any.whl (16 kB)
    Downloading pathable-0.4.4-py3-none-any.whl (9.6 kB)
    Downloading rfc3339_validator-0.1.4-py2.py3-none-any.whl (3.5 kB)
    Building wheels for collected packages: pyserini
      Building editable for pyserini (pyproject.toml) ... [?25l[?25hdone
      Created wheel for pyserini: filename=pyserini-1.2.0-0.editable-py3-none-any.whl size=9994 sha256=283874c8fd072289cc775ac98e5c21c1f0e53bd42e19300cefdcc070da33057d
      Stored in directory: /tmp/pip-ephem-wheel-cache-2kplucrw/wheels/05/4b/3b/8bdb2cb4987e0f276b3732b00d6512134fa8708c17afc7be29
    Successfully built pyserini
    Installing collected packages: pyjnius, parse, werkzeug, rfc3339-validator, python-dotenv, pathable, nvidia-nvjitlink-cu12, nvidia-nccl-cu12, nvidia-curand-cu12, nvidia-cufft-cu12, nvidia-cuda-runtime-cu12, nvidia-cuda-nvrtc-cu12, nvidia-cuda-cupti-cu12, nvidia-cublas-cu12, lazy-object-proxy, isodate, humanfriendly, httpx-sse, exceptiongroup, dnspython, sse-starlette, nvidia-cusparse-cu12, nvidia-cudnn-cu12, jsonschema-path, email-validator, coloredlogs, rich-rst, pydantic-settings, openapi-pydantic, onnxruntime, nvidia-cusolver-cu12, authlib, openapi-schema-validator, mcp, cyclopts, openapi-spec-validator, openapi-core, fastmcp, pyserini
      Attempting uninstall: werkzeug
        Found existing installation: Werkzeug 3.1.3
        Uninstalling Werkzeug-3.1.3:
          Successfully uninstalled Werkzeug-3.1.3
      Attempting uninstall: nvidia-nvjitlink-cu12
        Found existing installation: nvidia-nvjitlink-cu12 12.5.82
        Uninstalling nvidia-nvjitlink-cu12-12.5.82:
          Successfully uninstalled nvidia-nvjitlink-cu12-12.5.82
      Attempting uninstall: nvidia-nccl-cu12
        Found existing installation: nvidia-nccl-cu12 2.23.4
        Uninstalling nvidia-nccl-cu12-2.23.4:
          Successfully uninstalled nvidia-nccl-cu12-2.23.4
      Attempting uninstall: nvidia-curand-cu12
        Found existing installation: nvidia-curand-cu12 10.3.6.82
        Uninstalling nvidia-curand-cu12-10.3.6.82:
          Successfully uninstalled nvidia-curand-cu12-10.3.6.82
      Attempting uninstall: nvidia-cufft-cu12
        Found existing installation: nvidia-cufft-cu12 11.2.3.61
        Uninstalling nvidia-cufft-cu12-11.2.3.61:
          Successfully uninstalled nvidia-cufft-cu12-11.2.3.61
      Attempting uninstall: nvidia-cuda-runtime-cu12
        Found existing installation: nvidia-cuda-runtime-cu12 12.5.82
        Uninstalling nvidia-cuda-runtime-cu12-12.5.82:
          Successfully uninstalled nvidia-cuda-runtime-cu12-12.5.82
      Attempting uninstall: nvidia-cuda-nvrtc-cu12
        Found existing installation: nvidia-cuda-nvrtc-cu12 12.5.82
        Uninstalling nvidia-cuda-nvrtc-cu12-12.5.82:
          Successfully uninstalled nvidia-cuda-nvrtc-cu12-12.5.82
      Attempting uninstall: nvidia-cuda-cupti-cu12
        Found existing installation: nvidia-cuda-cupti-cu12 12.5.82
        Uninstalling nvidia-cuda-cupti-cu12-12.5.82:
          Successfully uninstalled nvidia-cuda-cupti-cu12-12.5.82
      Attempting uninstall: nvidia-cublas-cu12
        Found existing installation: nvidia-cublas-cu12 12.5.3.2
        Uninstalling nvidia-cublas-cu12-12.5.3.2:
          Successfully uninstalled nvidia-cublas-cu12-12.5.3.2
      Attempting uninstall: nvidia-cusparse-cu12
        Found existing installation: nvidia-cusparse-cu12 12.5.1.3
        Uninstalling nvidia-cusparse-cu12-12.5.1.3:
          Successfully uninstalled nvidia-cusparse-cu12-12.5.1.3
      Attempting uninstall: nvidia-cudnn-cu12
        Found existing installation: nvidia-cudnn-cu12 9.3.0.75
        Uninstalling nvidia-cudnn-cu12-9.3.0.75:
          Successfully uninstalled nvidia-cudnn-cu12-9.3.0.75
      Attempting uninstall: nvidia-cusolver-cu12
        Found existing installation: nvidia-cusolver-cu12 11.6.3.83
        Uninstalling nvidia-cusolver-cu12-11.6.3.83:
          Successfully uninstalled nvidia-cusolver-cu12-11.6.3.83
    Successfully installed authlib-1.6.1 coloredlogs-15.0.1 cyclopts-3.22.5 dnspython-2.7.0 email-validator-2.2.0 exceptiongroup-1.3.0 fastmcp-2.11.2 httpx-sse-0.4.1 humanfriendly-10.0 isodate-0.7.2 jsonschema-path-0.3.4 lazy-object-proxy-1.11.0 mcp-1.12.4 nvidia-cublas-cu12-12.4.5.8 nvidia-cuda-cupti-cu12-12.4.127 nvidia-cuda-nvrtc-cu12-12.4.127 nvidia-cuda-runtime-cu12-12.4.127 nvidia-cudnn-cu12-9.1.0.70 nvidia-cufft-cu12-11.2.1.3 nvidia-curand-cu12-10.3.5.147 nvidia-cusolver-cu12-11.6.1.9 nvidia-cusparse-cu12-12.3.1.170 nvidia-nccl-cu12-2.21.5 nvidia-nvjitlink-cu12-12.4.127 onnxruntime-1.22.1 openapi-core-0.19.5 openapi-pydantic-0.5.1 openapi-schema-validator-0.6.3 openapi-spec-validator-0.7.2 parse-1.20.2 pathable-0.4.4 pydantic-settings-2.10.1 pyjnius-1.6.1 pyserini-1.2.0 python-dotenv-1.1.1 rfc3339-validator-0.1.4 rich-rst-1.3.1 sse-starlette-3.0.2 werkzeug-3.1.1



```python
%cd ../
```

    /content



```python
%cd anserini/target/
```

    /content/anserini/target



```python
!ls -l
```

    total 188452
    -rw-r--r--  1 root root 184855426 Aug 11 17:13 anserini-1.1.2-SNAPSHOT-fatjar.jar
    -rw-r--r--  1 root root   3226128 Aug 11 17:12 anserini-1.1.2-SNAPSHOT.jar
    -rw-r--r--  1 root root   1947109 Aug 11 17:13 anserini-1.1.2-SNAPSHOT-javadoc.jar
    -rw-r--r--  1 root root   2888968 Aug 11 17:12 anserini-1.1.2-SNAPSHOT-sources.jar
    drwxr-xr-x  7 root root      4096 Aug 11 17:13 apidocs
    drwxr-xr-x 13 root root      4096 Aug 11 17:12 classes
    drwxr-xr-x  3 root root      4096 Aug 11 17:12 generated-sources
    drwxr-xr-x  3 root root      4096 Aug 11 17:12 generated-test-sources
    drwxr-xr-x  2 root root      4096 Aug 11 17:12 javadoc-bundle-options
    drwxr-xr-x  2 root root      4096 Aug 11 17:12 maven-archiver
    -rw-r--r--  1 root root     14355 Aug 11 17:13 maven-javadoc-plugin-stale-data.txt
    drwxr-xr-x  3 root root      4096 Aug 11 17:12 maven-status
    drwxr-xr-x  8 root root      4096 Aug 11 17:12 test-classes



```python
!mv anserini-1.1.2-SNAPSHOT-fatjar.jar /content/pyserini/pyserini/resources/jars/
```


```python
%cd ../../
```

    /content



```python
%cd pyserini/
```

    /content/pyserini



```python
#!python -m unittest
```


```python
%cd ../
```

    /content


Set up UMBRELA


```python
!git clone https://github.com/castorini/umbrela.git
```

    Cloning into 'umbrela'...
    remote: Enumerating objects: 264, done.[K
    remote: Counting objects: 100% (25/25), done.[K
    remote: Compressing objects: 100% (19/19), done.[K
    remote: Total 264 (delta 9), reused 7 (delta 6), pack-reused 239 (from 1)[K
    Receiving objects: 100% (264/264), 105.56 KiB | 6.21 MiB/s, done.
    Resolving deltas: 100% (139/139), done.



```python
!pip install faiss-cpu torch
```

    Collecting faiss-cpu
      Downloading faiss_cpu-1.11.0.post1-cp311-cp311-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl.metadata (5.0 kB)
    Requirement already satisfied: torch in /usr/local/lib/python3.11/dist-packages (2.6.0+cu124)
    Requirement already satisfied: numpy<3.0,>=1.25.0 in /usr/local/lib/python3.11/dist-packages (from faiss-cpu) (2.0.2)
    Requirement already satisfied: packaging in /usr/local/lib/python3.11/dist-packages (from faiss-cpu) (25.0)
    Requirement already satisfied: filelock in /usr/local/lib/python3.11/dist-packages (from torch) (3.18.0)
    Requirement already satisfied: typing-extensions>=4.10.0 in /usr/local/lib/python3.11/dist-packages (from torch) (4.14.1)
    Requirement already satisfied: networkx in /usr/local/lib/python3.11/dist-packages (from torch) (3.5)
    Requirement already satisfied: jinja2 in /usr/local/lib/python3.11/dist-packages (from torch) (3.1.6)
    Requirement already satisfied: fsspec in /usr/local/lib/python3.11/dist-packages (from torch) (2025.3.0)
    Requirement already satisfied: nvidia-cuda-nvrtc-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch) (12.4.127)
    Requirement already satisfied: nvidia-cuda-runtime-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch) (12.4.127)
    Requirement already satisfied: nvidia-cuda-cupti-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch) (12.4.127)
    Requirement already satisfied: nvidia-cudnn-cu12==9.1.0.70 in /usr/local/lib/python3.11/dist-packages (from torch) (9.1.0.70)
    Requirement already satisfied: nvidia-cublas-cu12==12.4.5.8 in /usr/local/lib/python3.11/dist-packages (from torch) (12.4.5.8)
    Requirement already satisfied: nvidia-cufft-cu12==11.2.1.3 in /usr/local/lib/python3.11/dist-packages (from torch) (11.2.1.3)
    Requirement already satisfied: nvidia-curand-cu12==10.3.5.147 in /usr/local/lib/python3.11/dist-packages (from torch) (10.3.5.147)
    Requirement already satisfied: nvidia-cusolver-cu12==11.6.1.9 in /usr/local/lib/python3.11/dist-packages (from torch) (11.6.1.9)
    Requirement already satisfied: nvidia-cusparse-cu12==12.3.1.170 in /usr/local/lib/python3.11/dist-packages (from torch) (12.3.1.170)
    Requirement already satisfied: nvidia-cusparselt-cu12==0.6.2 in /usr/local/lib/python3.11/dist-packages (from torch) (0.6.2)
    Requirement already satisfied: nvidia-nccl-cu12==2.21.5 in /usr/local/lib/python3.11/dist-packages (from torch) (2.21.5)
    Requirement already satisfied: nvidia-nvtx-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch) (12.4.127)
    Requirement already satisfied: nvidia-nvjitlink-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch) (12.4.127)
    Requirement already satisfied: triton==3.2.0 in /usr/local/lib/python3.11/dist-packages (from torch) (3.2.0)
    Requirement already satisfied: sympy==1.13.1 in /usr/local/lib/python3.11/dist-packages (from torch) (1.13.1)
    Requirement already satisfied: mpmath<1.4,>=1.1.0 in /usr/local/lib/python3.11/dist-packages (from sympy==1.13.1->torch) (1.3.0)
    Requirement already satisfied: MarkupSafe>=2.0 in /usr/local/lib/python3.11/dist-packages (from jinja2->torch) (3.0.2)
    Downloading faiss_cpu-1.11.0.post1-cp311-cp311-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl (31.3 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m31.3/31.3 MB[0m [31m21.3 MB/s[0m eta [36m0:00:00[0m
    [?25hInstalling collected packages: faiss-cpu
    Successfully installed faiss-cpu-1.11.0.post1



```python
%cd /content/umbrela
```

    /content/umbrela



```python
!pip install -r requirements.txt
```

    Requirement already satisfied: datasets>=2.19.0 in /usr/local/lib/python3.11/dist-packages (from -r requirements.txt (line 1)) (4.0.0)
    Collecting fschat>=0.2.36 (from -r requirements.txt (line 2))
      Downloading fschat-0.2.36-py3-none-any.whl.metadata (20 kB)
    Requirement already satisfied: openai>=1.24.1 in /usr/local/lib/python3.11/dist-packages (from -r requirements.txt (line 3)) (1.99.1)
    Requirement already satisfied: pyserini==1.2.0 in /usr/local/lib/python3.11/dist-packages (from -r requirements.txt (line 4)) (1.2.0)
    Requirement already satisfied: torch>=2.2.2 in /usr/local/lib/python3.11/dist-packages (from -r requirements.txt (line 5)) (2.6.0+cu124)
    Requirement already satisfied: tqdm>=4.66.2 in /usr/local/lib/python3.11/dist-packages (from -r requirements.txt (line 6)) (4.67.1)
    Requirement already satisfied: transformers>=4.40.1 in /usr/local/lib/python3.11/dist-packages (from -r requirements.txt (line 7)) (4.55.0)
    Requirement already satisfied: pyyaml in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (6.0.2)
    Requirement already satisfied: requests in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (2.32.3)
    Requirement already satisfied: Cython>=0.29.21 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (3.0.12)
    Requirement already satisfied: numpy>=1.18.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (2.0.2)
    Requirement already satisfied: pandas>=1.4.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (2.2.2)
    Requirement already satisfied: pyjnius>=1.6.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (1.6.1)
    Requirement already satisfied: scikit-learn>=0.22.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (1.6.1)
    Requirement already satisfied: scipy>=1.4.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (1.16.1)
    Requirement already satisfied: onnxruntime>=1.8.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (1.22.1)
    Requirement already satisfied: sentencepiece>=0.2 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (0.2.0)
    Requirement already satisfied: tiktoken>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (0.10.0)
    Requirement already satisfied: flask>3.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (3.1.1)
    Requirement already satisfied: pillow>=10.2.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (11.3.0)
    Requirement already satisfied: fastapi>=0.70.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (0.116.1)
    Requirement already satisfied: uvicorn>=0.13.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (0.35.0)
    Requirement already satisfied: fastmcp>=2.10.4 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->-r requirements.txt (line 4)) (2.11.2)
    Requirement already satisfied: filelock in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->-r requirements.txt (line 1)) (3.18.0)
    Requirement already satisfied: pyarrow>=15.0.0 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->-r requirements.txt (line 1)) (18.1.0)
    Requirement already satisfied: dill<0.3.9,>=0.3.0 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->-r requirements.txt (line 1)) (0.3.8)
    Requirement already satisfied: xxhash in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->-r requirements.txt (line 1)) (3.5.0)
    Requirement already satisfied: multiprocess<0.70.17 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->-r requirements.txt (line 1)) (0.70.16)
    Requirement already satisfied: fsspec<=2025.3.0,>=2023.1.0 in /usr/local/lib/python3.11/dist-packages (from fsspec[http]<=2025.3.0,>=2023.1.0->datasets>=2.19.0->-r requirements.txt (line 1)) (2025.3.0)
    Requirement already satisfied: huggingface-hub>=0.24.0 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->-r requirements.txt (line 1)) (0.34.3)
    Requirement already satisfied: packaging in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->-r requirements.txt (line 1)) (25.0)
    Requirement already satisfied: aiohttp in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->-r requirements.txt (line 2)) (3.12.15)
    Requirement already satisfied: httpx in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->-r requirements.txt (line 2)) (0.28.1)
    Collecting markdown2[all] (from fschat>=0.2.36->-r requirements.txt (line 2))
      Downloading markdown2-2.5.4-py3-none-any.whl.metadata (2.1 kB)
    Collecting nh3 (from fschat>=0.2.36->-r requirements.txt (line 2))
      Downloading nh3-0.3.0-cp38-abi3-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (2.0 kB)
    Requirement already satisfied: prompt-toolkit>=3.0.0 in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->-r requirements.txt (line 2)) (3.0.51)
    Requirement already satisfied: pydantic in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->-r requirements.txt (line 2)) (2.11.7)
    Requirement already satisfied: rich>=10.0.0 in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->-r requirements.txt (line 2)) (13.9.4)
    Collecting shortuuid (from fschat>=0.2.36->-r requirements.txt (line 2))
      Downloading shortuuid-1.0.13-py3-none-any.whl.metadata (5.8 kB)
    Requirement already satisfied: anyio<5,>=3.5.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->-r requirements.txt (line 3)) (4.10.0)
    Requirement already satisfied: distro<2,>=1.7.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->-r requirements.txt (line 3)) (1.9.0)
    Requirement already satisfied: jiter<1,>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->-r requirements.txt (line 3)) (0.10.0)
    Requirement already satisfied: sniffio in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->-r requirements.txt (line 3)) (1.3.1)
    Requirement already satisfied: typing-extensions<5,>=4.11 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->-r requirements.txt (line 3)) (4.14.1)
    Requirement already satisfied: networkx in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (3.5)
    Requirement already satisfied: jinja2 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (3.1.6)
    Requirement already satisfied: nvidia-cuda-nvrtc-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (12.4.127)
    Requirement already satisfied: nvidia-cuda-runtime-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (12.4.127)
    Requirement already satisfied: nvidia-cuda-cupti-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (12.4.127)
    Requirement already satisfied: nvidia-cudnn-cu12==9.1.0.70 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (9.1.0.70)
    Requirement already satisfied: nvidia-cublas-cu12==12.4.5.8 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (12.4.5.8)
    Requirement already satisfied: nvidia-cufft-cu12==11.2.1.3 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (11.2.1.3)
    Requirement already satisfied: nvidia-curand-cu12==10.3.5.147 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (10.3.5.147)
    Requirement already satisfied: nvidia-cusolver-cu12==11.6.1.9 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (11.6.1.9)
    Requirement already satisfied: nvidia-cusparse-cu12==12.3.1.170 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (12.3.1.170)
    Requirement already satisfied: nvidia-cusparselt-cu12==0.6.2 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (0.6.2)
    Requirement already satisfied: nvidia-nccl-cu12==2.21.5 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (2.21.5)
    Requirement already satisfied: nvidia-nvtx-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (12.4.127)
    Requirement already satisfied: nvidia-nvjitlink-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (12.4.127)
    Requirement already satisfied: triton==3.2.0 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (3.2.0)
    Requirement already satisfied: sympy==1.13.1 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->-r requirements.txt (line 5)) (1.13.1)
    Requirement already satisfied: mpmath<1.4,>=1.1.0 in /usr/local/lib/python3.11/dist-packages (from sympy==1.13.1->torch>=2.2.2->-r requirements.txt (line 5)) (1.3.0)
    Requirement already satisfied: regex!=2019.12.17 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.40.1->-r requirements.txt (line 7)) (2024.11.6)
    Requirement already satisfied: tokenizers<0.22,>=0.21 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.40.1->-r requirements.txt (line 7)) (0.21.4)
    Requirement already satisfied: safetensors>=0.4.3 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.40.1->-r requirements.txt (line 7)) (0.6.1)
    Requirement already satisfied: idna>=2.8 in /usr/local/lib/python3.11/dist-packages (from anyio<5,>=3.5.0->openai>=1.24.1->-r requirements.txt (line 3)) (3.10)
    Requirement already satisfied: starlette<0.48.0,>=0.40.0 in /usr/local/lib/python3.11/dist-packages (from fastapi>=0.70.0->pyserini==1.2.0->-r requirements.txt (line 4)) (0.47.2)
    Requirement already satisfied: authlib>=1.5.2 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.6.1)
    Requirement already satisfied: cyclopts>=3.0.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (3.22.5)
    Requirement already satisfied: exceptiongroup>=1.2.2 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.3.0)
    Requirement already satisfied: mcp>=1.10.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.12.4)
    Requirement already satisfied: openapi-core>=0.19.5 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.19.5)
    Requirement already satisfied: openapi-pydantic>=0.5.1 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.5.1)
    Requirement already satisfied: pyperclip>=1.9.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.9.0)
    Requirement already satisfied: python-dotenv>=1.1.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.1.1)
    Requirement already satisfied: blinker>=1.9.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->-r requirements.txt (line 4)) (1.9.0)
    Requirement already satisfied: click>=8.1.3 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->-r requirements.txt (line 4)) (8.2.1)
    Requirement already satisfied: itsdangerous>=2.2.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->-r requirements.txt (line 4)) (2.2.0)
    Requirement already satisfied: markupsafe>=2.1.1 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->-r requirements.txt (line 4)) (3.0.2)
    Requirement already satisfied: werkzeug>=3.1.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->-r requirements.txt (line 4)) (3.1.1)
    Requirement already satisfied: aiohappyeyeballs>=2.5.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->-r requirements.txt (line 2)) (2.6.1)
    Requirement already satisfied: aiosignal>=1.4.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->-r requirements.txt (line 2)) (1.4.0)
    Requirement already satisfied: attrs>=17.3.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->-r requirements.txt (line 2)) (25.3.0)
    Requirement already satisfied: frozenlist>=1.1.1 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->-r requirements.txt (line 2)) (1.7.0)
    Requirement already satisfied: multidict<7.0,>=4.5 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->-r requirements.txt (line 2)) (6.6.3)
    Requirement already satisfied: propcache>=0.2.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->-r requirements.txt (line 2)) (0.3.2)
    Requirement already satisfied: yarl<2.0,>=1.17.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->-r requirements.txt (line 2)) (1.20.1)
    Requirement already satisfied: certifi in /usr/local/lib/python3.11/dist-packages (from httpx->fschat>=0.2.36->-r requirements.txt (line 2)) (2025.8.3)
    Requirement already satisfied: httpcore==1.* in /usr/local/lib/python3.11/dist-packages (from httpx->fschat>=0.2.36->-r requirements.txt (line 2)) (1.0.9)
    Requirement already satisfied: h11>=0.16 in /usr/local/lib/python3.11/dist-packages (from httpcore==1.*->httpx->fschat>=0.2.36->-r requirements.txt (line 2)) (0.16.0)
    Requirement already satisfied: hf-xet<2.0.0,>=1.1.3 in /usr/local/lib/python3.11/dist-packages (from huggingface-hub>=0.24.0->datasets>=2.19.0->-r requirements.txt (line 1)) (1.1.7)
    Requirement already satisfied: coloredlogs in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0->-r requirements.txt (line 4)) (15.0.1)
    Requirement already satisfied: flatbuffers in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0->-r requirements.txt (line 4)) (25.2.10)
    Requirement already satisfied: protobuf in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0->-r requirements.txt (line 4)) (5.29.5)
    Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0->-r requirements.txt (line 4)) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0->-r requirements.txt (line 4)) (2025.2)
    Requirement already satisfied: tzdata>=2022.7 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0->-r requirements.txt (line 4)) (2025.2)
    Requirement already satisfied: wcwidth in /usr/local/lib/python3.11/dist-packages (from prompt-toolkit>=3.0.0->fschat>=0.2.36->-r requirements.txt (line 2)) (0.2.13)
    Requirement already satisfied: annotated-types>=0.6.0 in /usr/local/lib/python3.11/dist-packages (from pydantic->fschat>=0.2.36->-r requirements.txt (line 2)) (0.7.0)
    Requirement already satisfied: pydantic-core==2.33.2 in /usr/local/lib/python3.11/dist-packages (from pydantic->fschat>=0.2.36->-r requirements.txt (line 2)) (2.33.2)
    Requirement already satisfied: typing-inspection>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from pydantic->fschat>=0.2.36->-r requirements.txt (line 2)) (0.4.1)
    Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0->-r requirements.txt (line 4)) (3.4.2)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0->-r requirements.txt (line 4)) (2.5.0)
    Requirement already satisfied: markdown-it-py>=2.2.0 in /usr/local/lib/python3.11/dist-packages (from rich>=10.0.0->fschat>=0.2.36->-r requirements.txt (line 2)) (3.0.0)
    Requirement already satisfied: pygments<3.0.0,>=2.13.0 in /usr/local/lib/python3.11/dist-packages (from rich>=10.0.0->fschat>=0.2.36->-r requirements.txt (line 2)) (2.19.2)
    Requirement already satisfied: joblib>=1.2.0 in /usr/local/lib/python3.11/dist-packages (from scikit-learn>=0.22.1->pyserini==1.2.0->-r requirements.txt (line 4)) (1.5.1)
    Requirement already satisfied: threadpoolctl>=3.1.0 in /usr/local/lib/python3.11/dist-packages (from scikit-learn>=0.22.1->pyserini==1.2.0->-r requirements.txt (line 4)) (3.6.0)
    Collecting wavedrom (from markdown2[all]->fschat>=0.2.36->-r requirements.txt (line 2))
      Downloading wavedrom-2.0.3.post3.tar.gz (137 kB)
    [2K     [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m137.7/137.7 kB[0m [31m13.3 MB/s[0m eta [36m0:00:00[0m
    [?25h  Preparing metadata (setup.py) ... [?25l[?25hdone
    Collecting latex2mathml (from markdown2[all]->fschat>=0.2.36->-r requirements.txt (line 2))
      Downloading latex2mathml-3.78.0-py3-none-any.whl.metadata (14 kB)
    Requirement already satisfied: cryptography in /usr/local/lib/python3.11/dist-packages (from authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (43.0.3)
    Requirement already satisfied: docstring-parser>=0.15 in /usr/local/lib/python3.11/dist-packages (from cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.17.0)
    Requirement already satisfied: rich-rst<2.0.0,>=1.3.1 in /usr/local/lib/python3.11/dist-packages (from cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.3.1)
    Requirement already satisfied: mdurl~=0.1 in /usr/local/lib/python3.11/dist-packages (from markdown-it-py>=2.2.0->rich>=10.0.0->fschat>=0.2.36->-r requirements.txt (line 2)) (0.1.2)
    Requirement already satisfied: httpx-sse>=0.4 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.4.1)
    Requirement already satisfied: jsonschema>=4.20.0 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (4.25.0)
    Requirement already satisfied: pydantic-settings>=2.5.2 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (2.10.1)
    Requirement already satisfied: python-multipart>=0.0.9 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.0.20)
    Requirement already satisfied: sse-starlette>=1.6.1 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (3.0.2)
    Requirement already satisfied: isodate in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.7.2)
    Requirement already satisfied: jsonschema-path<0.4.0,>=0.3.1 in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.3.4)
    Requirement already satisfied: more-itertools in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (10.7.0)
    Requirement already satisfied: openapi-schema-validator<0.7.0,>=0.6.0 in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.6.3)
    Requirement already satisfied: openapi-spec-validator<0.8.0,>=0.7.1 in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.7.2)
    Requirement already satisfied: parse in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.20.2)
    Requirement already satisfied: email-validator>=2.0.0 in /usr/local/lib/python3.11/dist-packages (from pydantic[email]>=2.11.7->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (2.2.0)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.11/dist-packages (from python-dateutil>=2.8.2->pandas>=1.4.0->pyserini==1.2.0->-r requirements.txt (line 4)) (1.17.0)
    Requirement already satisfied: humanfriendly>=9.1 in /usr/local/lib/python3.11/dist-packages (from coloredlogs->onnxruntime>=1.8.1->pyserini==1.2.0->-r requirements.txt (line 4)) (10.0)
    Collecting svgwrite (from wavedrom->markdown2[all]->fschat>=0.2.36->-r requirements.txt (line 2))
      Downloading svgwrite-1.4.3-py3-none-any.whl.metadata (8.8 kB)
    Requirement already satisfied: dnspython>=2.0.0 in /usr/local/lib/python3.11/dist-packages (from email-validator>=2.0.0->pydantic[email]>=2.11.7->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (2.7.0)
    Requirement already satisfied: jsonschema-specifications>=2023.03.6 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (2025.4.1)
    Requirement already satisfied: referencing>=0.28.4 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.36.2)
    Requirement already satisfied: rpds-py>=0.7.1 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.26.0)
    Requirement already satisfied: pathable<0.5.0,>=0.4.1 in /usr/local/lib/python3.11/dist-packages (from jsonschema-path<0.4.0,>=0.3.1->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.4.4)
    Requirement already satisfied: rfc3339-validator in /usr/local/lib/python3.11/dist-packages (from openapi-schema-validator<0.7.0,>=0.6.0->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.1.4)
    Requirement already satisfied: lazy-object-proxy<2.0.0,>=1.7.1 in /usr/local/lib/python3.11/dist-packages (from openapi-spec-validator<0.8.0,>=0.7.1->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.11.0)
    Requirement already satisfied: docutils in /usr/local/lib/python3.11/dist-packages (from rich-rst<2.0.0,>=1.3.1->cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (0.21.2)
    Requirement already satisfied: cffi>=1.12 in /usr/local/lib/python3.11/dist-packages (from cryptography->authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (1.17.1)
    Requirement already satisfied: pycparser in /usr/local/lib/python3.11/dist-packages (from cffi>=1.12->cryptography->authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0->-r requirements.txt (line 4)) (2.22)
    Downloading fschat-0.2.36-py3-none-any.whl (256 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m256.9/256.9 kB[0m [31m16.4 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading nh3-0.3.0-cp38-abi3-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (803 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m804.0/804.0 kB[0m [31m46.7 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading shortuuid-1.0.13-py3-none-any.whl (10 kB)
    Downloading latex2mathml-3.78.0-py3-none-any.whl (73 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m73.7/73.7 kB[0m [31m5.5 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading markdown2-2.5.4-py3-none-any.whl (49 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m50.0/50.0 kB[0m [31m2.6 MB/s[0m eta [36m0:00:00[0m
    [?25hDownloading svgwrite-1.4.3-py3-none-any.whl (67 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m67.1/67.1 kB[0m [31m6.8 MB/s[0m eta [36m0:00:00[0m
    [?25hBuilding wheels for collected packages: wavedrom
      Building wheel for wavedrom (setup.py) ... [?25l[?25hdone
      Created wheel for wavedrom: filename=wavedrom-2.0.3.post3-py2.py3-none-any.whl size=30142 sha256=2d01c9397a792ce339702731ed9bc811fa2abd69e4c5bad0e3cae47c30539c45
      Stored in directory: /root/.cache/pip/wheels/23/cf/3b/4dcf6b22fa41c5ece715fa5f4e05afd683e7b0ce0f2fcc7bb6
    Successfully built wavedrom
    Installing collected packages: svgwrite, shortuuid, nh3, markdown2, latex2mathml, wavedrom, fschat
    Successfully installed fschat-0.2.36 latex2mathml-3.78.0 markdown2-2.5.4 nh3-0.3.0 shortuuid-1.0.13 svgwrite-1.4.3 wavedrom-2.0.3.post3



```python
!pip install -e .
```

    Obtaining file:///content/umbrela
      Installing build dependencies ... [?25l[?25hdone
      Checking if build backend supports build_editable ... [?25l[?25hdone
      Getting requirements to build editable ... [?25l[?25hdone
      Preparing editable metadata (pyproject.toml) ... [?25l[?25hdone
    Requirement already satisfied: datasets>=2.19.0 in /usr/local/lib/python3.11/dist-packages (from umbrela==0.0.7) (4.0.0)
    Requirement already satisfied: fschat>=0.2.36 in /usr/local/lib/python3.11/dist-packages (from umbrela==0.0.7) (0.2.36)
    Requirement already satisfied: openai>=1.24.1 in /usr/local/lib/python3.11/dist-packages (from umbrela==0.0.7) (1.99.1)
    Requirement already satisfied: pyserini==1.2.0 in /usr/local/lib/python3.11/dist-packages (from umbrela==0.0.7) (1.2.0)
    Requirement already satisfied: torch>=2.2.2 in /usr/local/lib/python3.11/dist-packages (from umbrela==0.0.7) (2.6.0+cu124)
    Requirement already satisfied: tqdm>=4.66.2 in /usr/local/lib/python3.11/dist-packages (from umbrela==0.0.7) (4.67.1)
    Requirement already satisfied: transformers>=4.40.1 in /usr/local/lib/python3.11/dist-packages (from umbrela==0.0.7) (4.55.0)
    Requirement already satisfied: pyyaml in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (6.0.2)
    Requirement already satisfied: requests in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (2.32.3)
    Requirement already satisfied: Cython>=0.29.21 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (3.0.12)
    Requirement already satisfied: numpy>=1.18.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (2.0.2)
    Requirement already satisfied: pandas>=1.4.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (2.2.2)
    Requirement already satisfied: pyjnius>=1.6.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (1.6.1)
    Requirement already satisfied: scikit-learn>=0.22.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (1.6.1)
    Requirement already satisfied: scipy>=1.4.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (1.16.1)
    Requirement already satisfied: onnxruntime>=1.8.1 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (1.22.1)
    Requirement already satisfied: sentencepiece>=0.2 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (0.2.0)
    Requirement already satisfied: tiktoken>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (0.10.0)
    Requirement already satisfied: flask>3.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (3.1.1)
    Requirement already satisfied: pillow>=10.2.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (11.3.0)
    Requirement already satisfied: fastapi>=0.70.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (0.116.1)
    Requirement already satisfied: uvicorn>=0.13.0 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (0.35.0)
    Requirement already satisfied: fastmcp>=2.10.4 in /usr/local/lib/python3.11/dist-packages (from pyserini==1.2.0->umbrela==0.0.7) (2.11.2)
    Requirement already satisfied: filelock in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->umbrela==0.0.7) (3.18.0)
    Requirement already satisfied: pyarrow>=15.0.0 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->umbrela==0.0.7) (18.1.0)
    Requirement already satisfied: dill<0.3.9,>=0.3.0 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->umbrela==0.0.7) (0.3.8)
    Requirement already satisfied: xxhash in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->umbrela==0.0.7) (3.5.0)
    Requirement already satisfied: multiprocess<0.70.17 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->umbrela==0.0.7) (0.70.16)
    Requirement already satisfied: fsspec<=2025.3.0,>=2023.1.0 in /usr/local/lib/python3.11/dist-packages (from fsspec[http]<=2025.3.0,>=2023.1.0->datasets>=2.19.0->umbrela==0.0.7) (2025.3.0)
    Requirement already satisfied: huggingface-hub>=0.24.0 in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->umbrela==0.0.7) (0.34.3)
    Requirement already satisfied: packaging in /usr/local/lib/python3.11/dist-packages (from datasets>=2.19.0->umbrela==0.0.7) (25.0)
    Requirement already satisfied: aiohttp in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (3.12.15)
    Requirement already satisfied: httpx in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (0.28.1)
    Requirement already satisfied: markdown2[all] in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (2.5.4)
    Requirement already satisfied: nh3 in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (0.3.0)
    Requirement already satisfied: prompt-toolkit>=3.0.0 in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (3.0.51)
    Requirement already satisfied: pydantic in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (2.11.7)
    Requirement already satisfied: rich>=10.0.0 in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (13.9.4)
    Requirement already satisfied: shortuuid in /usr/local/lib/python3.11/dist-packages (from fschat>=0.2.36->umbrela==0.0.7) (1.0.13)
    Requirement already satisfied: anyio<5,>=3.5.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->umbrela==0.0.7) (4.10.0)
    Requirement already satisfied: distro<2,>=1.7.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->umbrela==0.0.7) (1.9.0)
    Requirement already satisfied: jiter<1,>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->umbrela==0.0.7) (0.10.0)
    Requirement already satisfied: sniffio in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->umbrela==0.0.7) (1.3.1)
    Requirement already satisfied: typing-extensions<5,>=4.11 in /usr/local/lib/python3.11/dist-packages (from openai>=1.24.1->umbrela==0.0.7) (4.14.1)
    Requirement already satisfied: networkx in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (3.5)
    Requirement already satisfied: jinja2 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (3.1.6)
    Requirement already satisfied: nvidia-cuda-nvrtc-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (12.4.127)
    Requirement already satisfied: nvidia-cuda-runtime-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (12.4.127)
    Requirement already satisfied: nvidia-cuda-cupti-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (12.4.127)
    Requirement already satisfied: nvidia-cudnn-cu12==9.1.0.70 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (9.1.0.70)
    Requirement already satisfied: nvidia-cublas-cu12==12.4.5.8 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (12.4.5.8)
    Requirement already satisfied: nvidia-cufft-cu12==11.2.1.3 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (11.2.1.3)
    Requirement already satisfied: nvidia-curand-cu12==10.3.5.147 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (10.3.5.147)
    Requirement already satisfied: nvidia-cusolver-cu12==11.6.1.9 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (11.6.1.9)
    Requirement already satisfied: nvidia-cusparse-cu12==12.3.1.170 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (12.3.1.170)
    Requirement already satisfied: nvidia-cusparselt-cu12==0.6.2 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (0.6.2)
    Requirement already satisfied: nvidia-nccl-cu12==2.21.5 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (2.21.5)
    Requirement already satisfied: nvidia-nvtx-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (12.4.127)
    Requirement already satisfied: nvidia-nvjitlink-cu12==12.4.127 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (12.4.127)
    Requirement already satisfied: triton==3.2.0 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (3.2.0)
    Requirement already satisfied: sympy==1.13.1 in /usr/local/lib/python3.11/dist-packages (from torch>=2.2.2->umbrela==0.0.7) (1.13.1)
    Requirement already satisfied: mpmath<1.4,>=1.1.0 in /usr/local/lib/python3.11/dist-packages (from sympy==1.13.1->torch>=2.2.2->umbrela==0.0.7) (1.3.0)
    Requirement already satisfied: regex!=2019.12.17 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.40.1->umbrela==0.0.7) (2024.11.6)
    Requirement already satisfied: tokenizers<0.22,>=0.21 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.40.1->umbrela==0.0.7) (0.21.4)
    Requirement already satisfied: safetensors>=0.4.3 in /usr/local/lib/python3.11/dist-packages (from transformers>=4.40.1->umbrela==0.0.7) (0.6.1)
    Requirement already satisfied: idna>=2.8 in /usr/local/lib/python3.11/dist-packages (from anyio<5,>=3.5.0->openai>=1.24.1->umbrela==0.0.7) (3.10)
    Requirement already satisfied: starlette<0.48.0,>=0.40.0 in /usr/local/lib/python3.11/dist-packages (from fastapi>=0.70.0->pyserini==1.2.0->umbrela==0.0.7) (0.47.2)
    Requirement already satisfied: authlib>=1.5.2 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.6.1)
    Requirement already satisfied: cyclopts>=3.0.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (3.22.5)
    Requirement already satisfied: exceptiongroup>=1.2.2 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.3.0)
    Requirement already satisfied: mcp>=1.10.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.12.4)
    Requirement already satisfied: openapi-core>=0.19.5 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.19.5)
    Requirement already satisfied: openapi-pydantic>=0.5.1 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.5.1)
    Requirement already satisfied: pyperclip>=1.9.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.9.0)
    Requirement already satisfied: python-dotenv>=1.1.0 in /usr/local/lib/python3.11/dist-packages (from fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.1.1)
    Requirement already satisfied: blinker>=1.9.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->umbrela==0.0.7) (1.9.0)
    Requirement already satisfied: click>=8.1.3 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->umbrela==0.0.7) (8.2.1)
    Requirement already satisfied: itsdangerous>=2.2.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->umbrela==0.0.7) (2.2.0)
    Requirement already satisfied: markupsafe>=2.1.1 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->umbrela==0.0.7) (3.0.2)
    Requirement already satisfied: werkzeug>=3.1.0 in /usr/local/lib/python3.11/dist-packages (from flask>3.0->pyserini==1.2.0->umbrela==0.0.7) (3.1.1)
    Requirement already satisfied: aiohappyeyeballs>=2.5.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->umbrela==0.0.7) (2.6.1)
    Requirement already satisfied: aiosignal>=1.4.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->umbrela==0.0.7) (1.4.0)
    Requirement already satisfied: attrs>=17.3.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->umbrela==0.0.7) (25.3.0)
    Requirement already satisfied: frozenlist>=1.1.1 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->umbrela==0.0.7) (1.7.0)
    Requirement already satisfied: multidict<7.0,>=4.5 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->umbrela==0.0.7) (6.6.3)
    Requirement already satisfied: propcache>=0.2.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->umbrela==0.0.7) (0.3.2)
    Requirement already satisfied: yarl<2.0,>=1.17.0 in /usr/local/lib/python3.11/dist-packages (from aiohttp->fschat>=0.2.36->umbrela==0.0.7) (1.20.1)
    Requirement already satisfied: certifi in /usr/local/lib/python3.11/dist-packages (from httpx->fschat>=0.2.36->umbrela==0.0.7) (2025.8.3)
    Requirement already satisfied: httpcore==1.* in /usr/local/lib/python3.11/dist-packages (from httpx->fschat>=0.2.36->umbrela==0.0.7) (1.0.9)
    Requirement already satisfied: h11>=0.16 in /usr/local/lib/python3.11/dist-packages (from httpcore==1.*->httpx->fschat>=0.2.36->umbrela==0.0.7) (0.16.0)
    Requirement already satisfied: hf-xet<2.0.0,>=1.1.3 in /usr/local/lib/python3.11/dist-packages (from huggingface-hub>=0.24.0->datasets>=2.19.0->umbrela==0.0.7) (1.1.7)
    Requirement already satisfied: coloredlogs in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0->umbrela==0.0.7) (15.0.1)
    Requirement already satisfied: flatbuffers in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0->umbrela==0.0.7) (25.2.10)
    Requirement already satisfied: protobuf in /usr/local/lib/python3.11/dist-packages (from onnxruntime>=1.8.1->pyserini==1.2.0->umbrela==0.0.7) (5.29.5)
    Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0->umbrela==0.0.7) (2.9.0.post0)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0->umbrela==0.0.7) (2025.2)
    Requirement already satisfied: tzdata>=2022.7 in /usr/local/lib/python3.11/dist-packages (from pandas>=1.4.0->pyserini==1.2.0->umbrela==0.0.7) (2025.2)
    Requirement already satisfied: wcwidth in /usr/local/lib/python3.11/dist-packages (from prompt-toolkit>=3.0.0->fschat>=0.2.36->umbrela==0.0.7) (0.2.13)
    Requirement already satisfied: annotated-types>=0.6.0 in /usr/local/lib/python3.11/dist-packages (from pydantic->fschat>=0.2.36->umbrela==0.0.7) (0.7.0)
    Requirement already satisfied: pydantic-core==2.33.2 in /usr/local/lib/python3.11/dist-packages (from pydantic->fschat>=0.2.36->umbrela==0.0.7) (2.33.2)
    Requirement already satisfied: typing-inspection>=0.4.0 in /usr/local/lib/python3.11/dist-packages (from pydantic->fschat>=0.2.36->umbrela==0.0.7) (0.4.1)
    Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0->umbrela==0.0.7) (3.4.2)
    Requirement already satisfied: urllib3<3,>=1.21.1 in /usr/local/lib/python3.11/dist-packages (from requests->pyserini==1.2.0->umbrela==0.0.7) (2.5.0)
    Requirement already satisfied: markdown-it-py>=2.2.0 in /usr/local/lib/python3.11/dist-packages (from rich>=10.0.0->fschat>=0.2.36->umbrela==0.0.7) (3.0.0)
    Requirement already satisfied: pygments<3.0.0,>=2.13.0 in /usr/local/lib/python3.11/dist-packages (from rich>=10.0.0->fschat>=0.2.36->umbrela==0.0.7) (2.19.2)
    Requirement already satisfied: joblib>=1.2.0 in /usr/local/lib/python3.11/dist-packages (from scikit-learn>=0.22.1->pyserini==1.2.0->umbrela==0.0.7) (1.5.1)
    Requirement already satisfied: threadpoolctl>=3.1.0 in /usr/local/lib/python3.11/dist-packages (from scikit-learn>=0.22.1->pyserini==1.2.0->umbrela==0.0.7) (3.6.0)
    Requirement already satisfied: wavedrom in /usr/local/lib/python3.11/dist-packages (from markdown2[all]->fschat>=0.2.36->umbrela==0.0.7) (2.0.3.post3)
    Requirement already satisfied: latex2mathml in /usr/local/lib/python3.11/dist-packages (from markdown2[all]->fschat>=0.2.36->umbrela==0.0.7) (3.78.0)
    Requirement already satisfied: cryptography in /usr/local/lib/python3.11/dist-packages (from authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (43.0.3)
    Requirement already satisfied: docstring-parser>=0.15 in /usr/local/lib/python3.11/dist-packages (from cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.17.0)
    Requirement already satisfied: rich-rst<2.0.0,>=1.3.1 in /usr/local/lib/python3.11/dist-packages (from cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.3.1)
    Requirement already satisfied: mdurl~=0.1 in /usr/local/lib/python3.11/dist-packages (from markdown-it-py>=2.2.0->rich>=10.0.0->fschat>=0.2.36->umbrela==0.0.7) (0.1.2)
    Requirement already satisfied: httpx-sse>=0.4 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.4.1)
    Requirement already satisfied: jsonschema>=4.20.0 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (4.25.0)
    Requirement already satisfied: pydantic-settings>=2.5.2 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (2.10.1)
    Requirement already satisfied: python-multipart>=0.0.9 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.0.20)
    Requirement already satisfied: sse-starlette>=1.6.1 in /usr/local/lib/python3.11/dist-packages (from mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (3.0.2)
    Requirement already satisfied: isodate in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.7.2)
    Requirement already satisfied: jsonschema-path<0.4.0,>=0.3.1 in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.3.4)
    Requirement already satisfied: more-itertools in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (10.7.0)
    Requirement already satisfied: openapi-schema-validator<0.7.0,>=0.6.0 in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.6.3)
    Requirement already satisfied: openapi-spec-validator<0.8.0,>=0.7.1 in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.7.2)
    Requirement already satisfied: parse in /usr/local/lib/python3.11/dist-packages (from openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.20.2)
    Requirement already satisfied: email-validator>=2.0.0 in /usr/local/lib/python3.11/dist-packages (from pydantic[email]>=2.11.7->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (2.2.0)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.11/dist-packages (from python-dateutil>=2.8.2->pandas>=1.4.0->pyserini==1.2.0->umbrela==0.0.7) (1.17.0)
    Requirement already satisfied: humanfriendly>=9.1 in /usr/local/lib/python3.11/dist-packages (from coloredlogs->onnxruntime>=1.8.1->pyserini==1.2.0->umbrela==0.0.7) (10.0)
    Requirement already satisfied: svgwrite in /usr/local/lib/python3.11/dist-packages (from wavedrom->markdown2[all]->fschat>=0.2.36->umbrela==0.0.7) (1.4.3)
    Requirement already satisfied: dnspython>=2.0.0 in /usr/local/lib/python3.11/dist-packages (from email-validator>=2.0.0->pydantic[email]>=2.11.7->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (2.7.0)
    Requirement already satisfied: jsonschema-specifications>=2023.03.6 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (2025.4.1)
    Requirement already satisfied: referencing>=0.28.4 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.36.2)
    Requirement already satisfied: rpds-py>=0.7.1 in /usr/local/lib/python3.11/dist-packages (from jsonschema>=4.20.0->mcp>=1.10.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.26.0)
    Requirement already satisfied: pathable<0.5.0,>=0.4.1 in /usr/local/lib/python3.11/dist-packages (from jsonschema-path<0.4.0,>=0.3.1->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.4.4)
    Requirement already satisfied: rfc3339-validator in /usr/local/lib/python3.11/dist-packages (from openapi-schema-validator<0.7.0,>=0.6.0->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.1.4)
    Requirement already satisfied: lazy-object-proxy<2.0.0,>=1.7.1 in /usr/local/lib/python3.11/dist-packages (from openapi-spec-validator<0.8.0,>=0.7.1->openapi-core>=0.19.5->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.11.0)
    Requirement already satisfied: docutils in /usr/local/lib/python3.11/dist-packages (from rich-rst<2.0.0,>=1.3.1->cyclopts>=3.0.0->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (0.21.2)
    Requirement already satisfied: cffi>=1.12 in /usr/local/lib/python3.11/dist-packages (from cryptography->authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (1.17.1)
    Requirement already satisfied: pycparser in /usr/local/lib/python3.11/dist-packages (from cffi>=1.12->cryptography->authlib>=1.5.2->fastmcp>=2.10.4->pyserini==1.2.0->umbrela==0.0.7) (2.22)
    Building wheels for collected packages: umbrela
      Building editable for umbrela (pyproject.toml) ... [?25l[?25hdone
      Created wheel for umbrela: filename=umbrela-0.0.7-0.editable-py3-none-any.whl size=10285 sha256=4f634c548de938670f8698f77c2bb48705113316e9102728d315e8869848e5c4
      Stored in directory: /tmp/pip-ephem-wheel-cache-9us2naa2/wheels/04/ba/66/03dae92461612d1035b0d9aa64c03a854460a4b110b1ac0db4
    Successfully built umbrela
    Installing collected packages: umbrela
    Successfully installed umbrela-0.0.7


Now, there are a dependency that need to be installed for the eval command to run


```python
!pip install retry
```

    Collecting retry
      Downloading retry-0.9.2-py2.py3-none-any.whl.metadata (5.8 kB)
    Requirement already satisfied: decorator>=3.4.2 in /usr/local/lib/python3.11/dist-packages (from retry) (4.4.2)
    Collecting py<2.0.0,>=1.4.26 (from retry)
      Downloading py-1.11.0-py2.py3-none-any.whl.metadata (2.8 kB)
    Downloading retry-0.9.2-py2.py3-none-any.whl (8.0 kB)
    Downloading py-1.11.0-py2.py3-none-any.whl (98 kB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m98.7/98.7 kB[0m [31m6.8 MB/s[0m eta [36m0:00:00[0m
    [?25hInstalling collected packages: py, retry
    Successfully installed py-1.11.0 retry-0.9.2


# **FOR CHATGPT**



```python
%cd src/
```

    /content/umbrela/src



```python
%%writefile chatgptrun.py
from umbrela.gpt_judge import GPTJudge
from dotenv import load_dotenv

load_dotenv()

judge_gpt = GPTJudge(qrel="dl19-passage", prompt_type="bing", model_name="gpt-4o")

input_dict = {
    "query": {"text": "how long is life cycle of flea", "qid": "264014"},
    "candidates": [
        {
            "doc": {
                "segment": "The life cycle of a flea can last anywhere from 20 days to an entire year. It depends on how long the flea remains in the dormant stage (eggs, larvae, pupa). Outside influences, such as weather, affect the flea cycle. A female flea can lay around 20 to 25 eggs in one day."
            },
            "docid": "4834547",
        },
    ]
}

judgments = judge_gpt.judge(request_dict=input_dict)
print(judgments)

```

    Writing chatgptrun.py



```python
import os
os.environ['OPEN_AI_API_KEY'] = 'sk-dummy-key-for-testing'
os.environ['AZURE_OPENAI_ENDPOINT'] = 'https://dummy.openai.azure.com/'
os.environ['AZURE_OPENAI_API_VERSION'] = '2024-02-15-preview'
os.environ['AZURE_OPENAI_API_KEY'] = 'dummy-key-for-testing'
os.environ['AZURE_OPENAI_API_BASE'] = 'https://dummy.openai.azure.com/'
os.environ['DEPLOYMENT_NAME'] = 'gpt-4o'
```


```python
!python chatgptrun.py
```

    WARNING: Using incubator modules: jdk.incubator.vector
    Warning!! Prompt file expects input fields namely: (examples, query, passage).
      0% 0/1 [00:00<?, ?it/s]
    2025-08-11 17:17:37,367 - retry.api - WARNING - Connection error., retrying in 0.1 seconds...
    
    2025-08-11 17:17:38,828 - retry.api - WARNING - Connection error., retrying in 0.1 seconds...
    Traceback (most recent call last):
      File "/usr/local/lib/python3.11/dist-packages/httpx/_transports/default.py", line 101, in map_httpcore_exceptions
        yield
      File "/usr/local/lib/python3.11/dist-packages/httpx/_transports/default.py", line 250, in handle_request
        resp = self._pool.handle_request(req)
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpcore/_sync/connection_pool.py", line 256, in handle_request
        raise exc from None
      File "/usr/local/lib/python3.11/dist-packages/httpcore/_sync/connection_pool.py", line 236, in handle_request
        response = connection.handle_request(
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpcore/_sync/connection.py", line 101, in handle_request
        raise exc
      File "/usr/local/lib/python3.11/dist-packages/httpcore/_sync/connection.py", line 78, in handle_request
        stream = self._connect(request)
                 ^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpcore/_sync/connection.py", line 124, in _connect
        stream = self._network_backend.connect_tcp(**kwargs)
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpcore/_backends/sync.py", line 207, in connect_tcp
        with map_exceptions(exc_map):
      File "/usr/lib/python3.11/contextlib.py", line 158, in __exit__
        self.gen.throw(typ, value, traceback)
      File "/usr/local/lib/python3.11/dist-packages/httpcore/_exceptions.py", line 14, in map_exceptions
        raise to_exc(exc) from exc
    httpcore.ConnectError: [Errno -2] Name or service not known
    
    The above exception was the direct cause of the following exception:
    
    Traceback (most recent call last):
      File "/usr/local/lib/python3.11/dist-packages/openai/_base_client.py", line 982, in request
        response = self._client.send(
                   ^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpx/_client.py", line 914, in send
        response = self._send_handling_auth(
                   ^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpx/_client.py", line 942, in _send_handling_auth
        response = self._send_handling_redirects(
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpx/_client.py", line 979, in _send_handling_redirects
        response = self._send_single_request(request)
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpx/_client.py", line 1014, in _send_single_request
        response = transport.handle_request(request)
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/httpx/_transports/default.py", line 249, in handle_request
        with map_httpcore_exceptions():
      File "/usr/lib/python3.11/contextlib.py", line 158, in __exit__
        self.gen.throw(typ, value, traceback)
      File "/usr/local/lib/python3.11/dist-packages/httpx/_transports/default.py", line 118, in map_httpcore_exceptions
        raise mapped_exc(message) from exc
    httpx.ConnectError: [Errno -2] Name or service not known
    
    The above exception was the direct cause of the following exception:
    
    Traceback (most recent call last):
      File "/content/umbrela/src/chatgptrun.py", line 20, in <module>
        judgments = judge_gpt.judge(request_dict=input_dict)
                    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/content/umbrela/src/umbrela/gpt_judge.py", line 94, in judge
        outputs = self.predict_with_llm(request_dict, max_new_tokens, prepocess)
                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/content/umbrela/src/umbrela/gpt_judge.py", line 88, in predict_with_llm
        outputs = [
                  ^
      File "/content/umbrela/src/umbrela/gpt_judge.py", line 89, in <listcomp>
        self.run_gpt(prompt, max_new_tokens) for prompt in tqdm(self.prompts)
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "<decorator-gen-2>", line 2, in run_gpt
      File "/usr/local/lib/python3.11/dist-packages/retry/api.py", line 73, in retry_decorator
        return __retry_internal(partial(f, *args, **kwargs), exceptions, tries, delay, max_delay, backoff, jitter,
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/retry/api.py", line 33, in __retry_internal
        return f()
               ^^^
      File "/content/umbrela/src/umbrela/gpt_judge.py", line 55, in run_gpt
        response = self.client.chat.completions.create(
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/openai/_utils/_utils.py", line 287, in wrapper
        return func(*args, **kwargs)
               ^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/openai/resources/chat/completions/completions.py", line 1135, in create
        return self._post(
               ^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/openai/_base_client.py", line 1259, in post
        return cast(ResponseT, self.request(cast_to, opts, stream=stream, stream_cls=stream_cls))
                               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
      File "/usr/local/lib/python3.11/dist-packages/openai/_base_client.py", line 1014, in request
        raise APIConnectionError(request=request) from err
    openai.APIConnectionError: Connection error.
      0% 0/1 [00:05<?, ?it/s]


Error, as expected, since I did not use valid values for the env variables. However, generally, it would work otherwise.

# **FOR HUGGING FACE OPEN-SOURCE MODELS**

Below is a Claude-generated prompt to test small, medium, large open-source models on Hugging Face with judgement snippets


```python
import os
os.environ["HF_TOKEN"] = "................."
os.environ["HF_CACHE_DIR"] = "/content/hf_cache"
```


```python
%%writefile huggingfacerun.py
"""
UMBRELA 30-Minute Benchmark for Colab Pro Decision
Optimized to test real TREC evaluation performance in minimal time
"""

import torch
import gc
import time
import json
import psutil
import subprocess
import os
import re # Import regex for parsing model output
from datetime import datetime
from transformers import AutoTokenizer, AutoModelForCausalLM, T5ForConditionalGeneration, T5Tokenizer
import warnings
warnings.filterwarnings("ignore")

class QuickUmbrelaBenchmark:
    def __init__(self):
        self.results = []

        # Real TREC DL 2019 samples (from UMBRELA paper)
        self.trec_samples = [
            {
                "query": "how long is life cycle of flea",
                "passage": "The life cycle of a flea can last anywhere from 20 days to an entire year. It depends on how long the flea remains in the dormant stage (eggs, larvae, pupa). Outside influences, such as weather, affect the flea cycle. A female flea can lay around 20 to 25 eggs in one day.",
                "expected_relevance": 3  # From UMBRELA paper
            },
            {
                "query": "medicare's definition of mechanical ventilation",
                "passage": "Continuous Positive Airway Pressure (CPAP) Continuous positive airway pressure – also called CPAP – is a treatment in which a mask is worn over the nose and/or mouth while you sleep. The mask is hooked up to a machine that delivers a continuous flow of air into the nose.",
                "expected_relevance": 1
            },
            {
                "query": "what is the daily life of thai people",
                "passage": "Thai Flag Meaning: The red stripes represent the blood spilt to maintain Thailand's independence. The white stands for purity and is the color of Buddhism which is the country's main religion. The flag of Thailand consists of five horizontal stripes.",
                "expected_relevance": 0
            },
            {
                "query": "define visceral pleura",
                "passage": "The visceral pleura is the thin membrane that covers the surface of the lungs. It is continuous with the parietal pleura, which lines the chest cavity. The pleural space between these two membranes contains pleural fluid.",
                "expected_relevance": 3
            },
            {
                "query": "causes of air pollution",
                "passage": "Air pollution is caused by various factors including vehicle emissions, industrial activities, burning of fossil fuels, deforestation, and agricultural practices. These activities release harmful substances into the atmosphere.",
                "expected_relevance": 2
            }
        ]

        # Models to test with approximate parameter counts (M = million, B = billion)
        self.test_models = [
            {
                "name": "google/flan-t5-small",
                "type": "t5",
                "size": "Small",
                "params_m": 80,
                "description": "Smallest T5, instruction-tuned"
            },
            {
                "name": "google/flan-t5-base",
                "type": "t5",
                "size": "Base",
                "params_m": 250,
                "description": "Mid-range T5"
            },
            {
                "name": "google/flan-t5-large",
                "type": "t5",
                "size": "Large",
                "params_m": 780,
                "description": "Larger T5"
            },
            {
                "name": "google/flan-t5-xl",
                "type": "t5",
                "size": "Extra Large",
                "params_b": 3, # 3 Billion
                "description": "Significant T5 model for better judgments"
            },
            {
                "name": "microsoft/DialoGPT-medium",
                "type": "gpt",
                "size": "Medium",
                "params_m": 345, # From previous info
                "description": "Alternative GPT model"
            },
            {
                "name": "microsoft/Phi-3-mini-4k-instruct",
                "type": "gpt", # Phi-3 models are decoder-only, like GPT
                "size": "Mini (Instruct)",
                "params_b": 3.8, # 3.8 Billion parameters
                "description": "Microsoft's small, capable instruct model"
            },
            {
                "name": "google/gemma-2-9b",
                "type": "gpt", # Gemma models are decoder-only
                "size": "9B",
                "params_b": 9,
                "description": "Gemma 9 Billion instruction-tuned"
            },
            {
                "name": "Qwen/Qwen2-7B-Instruct",
                "type": "gpt", # Qwen models are decoder-only (causal LM)
                "size": "7B (Instruct)",
                "params_b": 7,
                "description": "Qwen 7 Billion instruction-tuned"
            },
            {
                "name": "HuggingFaceM4/idefics-9b-instruct",
                "type": "gpt", # IDEFICS is decoder-only, with multimodal capabilities
                "size": "9B (Instruct, Multi)",
                "params_b": 9,
                "description": "IDEFICS 9 Billion instruction-tuned, multimodal"
            },
            {
                "name": "utter-project/EuroLLM-9B-Instruct",
                "type": "gpt", # EuroLLM is decoder-only
                "size": "9B (Instruct, Multi-lingual)",
                "params_b": 9,
                "description": "EuroLLM 9 Billion instruction-tuned"
            },
            {
                "name": "01-ai/Yi-1.5-9B-Chat",
                "type": "gpt", # Yi models are decoder-only (chat variant)
                "size": "9B (Chat)",
                "params_b": 9,
                "description": "Yi 9 Billion chat model"
            },
            {
                "name": "meta-llama/Meta-Llama-3-8B-Instruct",
                "type": "gpt", # Llama models are decoder-only
                "size": "8B (Instruct)",
                "params_b": 8,
                "description": "Meta Llama 3 8 Billion instruction-tuned"
            }
        ]

    def check_system_resources(self):
        """Check available system resources and determine Colab tier"""
        print("\n" + "="*70)
        print("🔍 SYSTEM RESOURCES & COLAB TIER DETECTION")
        print("="*70)

        # RAM
        ram = psutil.virtual_memory()
        print(f"💾 RAM: {ram.available/1024**3:.1f}GB available / {ram.total/1024**3:.1f}GB total")

        # GPU Detection
        if torch.cuda.is_available():
            gpu_name = torch.cuda.get_device_name()
            gpu_memory = torch.cuda.get_device_properties(0).total_memory/1024**3
            gpu_available = (torch.cuda.get_device_properties(0).total_memory - torch.cuda.memory_allocated())/1024**3

            print(f"🚀 GPU: {gpu_name}")
            print(f"📊 GPU Memory: {gpu_memory:.1f}GB total, {gpu_available:.1f}GB available")

            # Determine Colab tier (updated for typical Colab GPU memory ranges)
            if "T4" in gpu_name and gpu_memory < 16:
                tier = "🆓 Colab FREE (T4, ~15GB)"
            elif "V100" in gpu_name or (gpu_memory > 20 and gpu_memory < 35):
                tier = "💰 Colab PRO (V100, ~32GB)"
            elif "A100" in gpu_name or gpu_memory >= 35:
                tier = "💎 Colab PRO+ (A100, ~40GB)"
            else:
                tier = f"❓ Unknown ({gpu_name}, {gpu_memory:.1f}GB)"

            print(f"🏷️  Detected: {tier}")
        else:
            gpu_name = "CPU Only"
            gpu_memory = 0
            print("❌ GPU: Not available (CPU mode)")
            tier = "CPU Only"

        print("="*70)
        return {"name": gpu_name, "memory": gpu_memory, "tier": tier}

    def create_umbrela_prompt(self, query, passage):
        """
        Create UMBRELA-style prompt based on Figure 1 of the paper,
        tailored to encourage numerical output in the specified format.
        """
        prompt_template = """Given a query and a passage, you must provide a score on an integer scale of 0 to 3 with the following meanings:
0 = Irrelevant: The passage has nothing to do with the query.
1 = Related: The passage seems related to the query but does not answer it.
2 = Highly relevant: The passage has some answer for the query, but the answer may be a bit unclear, or hidden amongst extraneous information.
3 = Perfectly relevant: The passage is dedicated to the query and contains the exact answer.

Important Instruction: Assign category 1 if the passage is somewhat related to the topic but not completely, category 2 if passage presents something very important related to the entire topic and also has some extra information and category 3 if the passage only and entirely refers to the topic. If none of the above satisfies give it category 0.

Query: {query}
Passage: {passage}

Do not provide any code in result. Provide each score in the format of: ##final score: score without providing any reasoning.
##final score: """

        prompt = prompt_template.format(query=query, passage=passage)
        return prompt

    def test_model_performance(self, model_info, num_samples=80): # Default samples set to 80
        """Test a specific model with timing and memory benchmarks and check judgment accuracy"""
        model_name = model_info["name"]
        model_type = model_info["type"]

        print(f"\n{'='*70}")
        print(f"🧪 TESTING: {model_name}")
        print(f"📋 Type: {model_type.upper()} | Size: {model_info['size']}")
        print("="*70)

        try:
            # Memory before loading
            if torch.cuda.is_available():
                torch.cuda.empty_cache()
                mem_before = torch.cuda.memory_allocated() / 1024**3
            else:
                mem_before = 0

            # Load model
            print("⏳ Loading model...")
            start_time = time.time()

            # Use AutoModelForSeq2SeqLM for T5 models (encoder-decoder)
            # Use AutoModelForCausalLM for GPT-style models (decoder-only)
            if model_type == "t5":
                tokenizer = T5Tokenizer.from_pretrained(model_name)
                model = T5ForConditionalGeneration.from_pretrained(
                    model_name,
                    torch_dtype=torch.float16 if torch.cuda.is_available() else torch.float32,
                    device_map="auto" if torch.cuda.is_available() else None
                )
            else:  # GPT-style
                tokenizer = AutoTokenizer.from_pretrained(model_name)
                # Specific models that might require trust_remote_code=True
                if any(m in model_name for m in ["Phi-3", "Qwen", "idefics", "EuroLLM", "Yi"]):
                    model = AutoModelForCausalLM.from_pretrained(
                        model_name,
                        torch_dtype=torch.float16 if torch.cuda.is_available() else torch.float32,
                        device_map="auto" if torch.cuda.is_available() else None,
                        trust_remote_code=True
                    )
                else:
                    model = AutoModelForCausalLM.from_pretrained(
                        model_name,
                        torch_dtype=torch.float16 if torch.cuda.is_available() else torch.float32,
                        device_map="auto" if torch.cuda.is_available() else None
                    )
                if tokenizer.pad_token is None:
                    tokenizer.pad_token = tokenizer.eos_token # Ensure pad token is set for generation

            load_time = time.time() - start_time

            # Memory after loading
            if torch.cuda.is_available():
                mem_after = torch.cuda.memory_allocated() / 1024**3
                memory_used = mem_after - mem_before
            else:
                memory_used = 0

            print(f"✅ Loaded in {load_time:.1f}s | Memory: {memory_used:.2f}GB")

            # Benchmark evaluations
            print(f"🔄 Running {num_samples} evaluations...")

            eval_times = []
            correct_judgments_count = 0
            sample_outputs = []

            for i in range(num_samples):
                # Cycle through our TREC samples
                sample = self.trec_samples[i % len(self.trec_samples)]
                query = sample["query"]
                passage = sample["passage"]

                eval_start = time.time()

                try:
                    prompt = self.create_umbrela_prompt(query, passage) # Prompt is now generic

                    inputs = tokenizer.encode(prompt, return_tensors='pt', max_length=512, truncation=True)
                    if torch.cuda.is_available():
                        inputs = inputs.to(model.device)

                    with torch.no_grad():
                        outputs = model.generate(
                            inputs,
                            max_new_tokens=20, # Increased from 3/5 to allow more generation
                            temperature=0.1,  # Keep responses deterministic
                            do_sample=False,
                            pad_token_id=tokenizer.pad_token_id if tokenizer.pad_token_id is not None else tokenizer.eos_token_id
                        )

                    full_response = tokenizer.decode(outputs[0], skip_special_tokens=True)

                    # Attempt to parse the expected format "##final score: X"
                    parsed_response = None
                    match = re.search(r'##final score:\s*(\d+)', full_response)
                    if match:
                        try:
                            parsed_response = int(match.group(1).strip())
                        except ValueError:
                            pass # Not a valid integer

                    # Prepare response for display
                    display_response = str(parsed_response) if parsed_response is not None else full_response[len(tokenizer.decode(inputs[0], skip_special_tokens=True)):].strip()
                    display_response = display_response[:20] if len(display_response) > 20 else display_response # Truncate if too long

                    is_correct = (parsed_response == sample["expected_relevance"])
                    if is_correct:
                        correct_judgments_count += 1

                    eval_time = time.time() - eval_start
                    eval_times.append(eval_time)

                    if i < 3: # Store first few examples for detailed output
                        sample_outputs.append({
                            "query": query[:50] + "...",
                            "response": display_response,
                            "time": eval_time,
                            "expected": sample["expected_relevance"],
                            "correct": is_correct
                        })

                except Exception as e:
                    print(f"  ⚠️ Evaluation {i+1} failed: {str(e)[:50]}...") # Truncate error message
                    eval_times.append(float('inf')) # Record as infinite time for failed eval

            # Filter out infinite times for avg calculation, but keep for success rate context
            valid_eval_times = [t for t in eval_times if t != float('inf')]
            avg_eval_time = sum(valid_eval_times) / max(len(valid_eval_times), 1)

            # The 'success rate' now reflects the rate of judgments being parsed correctly and compared
            # to expected. Not just execution success.
            # A correct judgment rate is more meaningful than just successful execution.
            correct_judgment_rate = (correct_judgments_count / num_samples) * 100 if num_samples > 0 else 0

            # Project to full TREC dataset (9260 evaluations)
            full_trec_evals = 9260
            projected_hours = (avg_eval_time * full_trec_evals) / 3600
            projected_minutes = ((avg_eval_time * full_trec_evals) % 3600) / 60

            # Determine Colab recommendation
            # NOTE: These thresholds are estimates. Actual performance varies.
            if memory_used > 12: # Over 12GB VRAM often requires A100 (Pro+)
                colab_rec = "PRO+ Required"
                colab_reason = f"Memory ({memory_used:.1f}GB) too high for Free/Pro"
            elif memory_used > 8: # Over 8GB VRAM often benefits from V100 (Pro)
                colab_rec = "PRO Recommended"
                colab_reason = f"Memory ({memory_used:.1f}GB) ideal for Pro"
            elif projected_hours > 24:
                colab_rec = "PRO Recommended"
                colab_reason = f"Time ({projected_hours:.1f}h) > 24 hours (Colab max lifetime)"
            elif projected_hours > 12:
                colab_rec = "PRO Helpful"
                colab_reason = f"Time ({projected_hours:.1f}h) > 12 hours (Colab max lifetime)"
            else:
                colab_rec = "FREE OK"
                colab_reason = "Within limits"

            # Print results
            print(f"\n📊 PERFORMANCE METRICS:")
            print(f"  ⚡ Avg evaluation: {avg_eval_time:.3f}s")
            print(f"  ✅ Correct Judgment Rate: {correct_judgment_rate}/{num_samples} ({correct_judgment_rate:.1f}%)")
            print(f"  💾 Memory used: {memory_used:.2f}GB")
            print(f"  🕐 Full TREC est: {projected_hours:.1f}h {projected_minutes:.0f}m")
            print(f"  🎯 Colab rec: {colab_rec} ({colab_reason})")
            print(f"Total model test completion: {(time.time() - start_time):.1f}s") # Time for this model's test

            # Show sample outputs
            if sample_outputs:
                print(f"\n🔍 SAMPLE OUTPUTS:")
                for i, sample_out in enumerate(sample_outputs):
                    correct_str = "✔️ Correct" if sample_out['correct'] else "❌ Incorrect"
                    print(f"  {i+1}. Query: {sample_out['query']}")
                    print(f"       Response: '{sample_out['response']}' (expected: {sample_out['expected']}) - {sample_out['time']:.3f}s [{correct_str}]")

            result = {
                "model_name": model_name,
                "model_type": model_type,
                "model_size": model_info["size"],
                "params_m": model_info.get("params_m"), # Use .get to handle missing key for XL (params_b)
                "params_b": model_info.get("params_b"),
                "load_time": load_time,
                "memory_used_gb": memory_used,
                "avg_eval_time": avg_eval_time,
                "correct_judgment_rate": correct_judgment_rate, # Updated field
                "projected_hours": projected_hours,
                "colab_recommendation": colab_rec,
                "colab_reason": colab_reason
            }

            self.results.append(result)

            # Cleanup
            del model
            del tokenizer
            if torch.cuda.is_available():
                torch.cuda.empty_cache()
            gc.collect()

            return result

        except Exception as e:
            # Enhanced error handling for model loading failures
            print(f"❌ FAILED to test {model_name}: {str(e)[:100]}...") # Truncate long error messages
            print("  This often means the model is too large for the available memory or the model name/type is incorrect.")

            # Add a partial result for failed models to the report
            self.results.append({
                "model_name": model_name,
                "model_type": model_type,
                "model_size": model_info["size"],
                "params_m": model_info.get("params_m"),
                "params_b": model_info.get("params_b"),
                "load_time": float('inf'), # Indicate failure for load time
                "memory_used_gb": float('inf'), # Indicate unknown/exceeded memory
                "avg_eval_time": float('inf'), # Indicate failure for eval time
                "correct_judgment_rate": 0.0, # No correct judgments if failed
                "projected_hours": float('inf'),
                "colab_recommendation": "FAIL: Check Memory/Model Name",
                "colab_reason": str(e)[:50]
            })
            return None

    def run_quick_benchmark(self):
        """Run the optimized 30-minute benchmark"""
        print("🚀 QUICK UMBRELA BENCHMARK FOR COLAB PRO DECISION")
        print("🎯 Target: Evaluate TREC relevance assessment for multiple models")
        print("="*70)

        # System check
        system_info = self.check_system_resources()

        # Determine sample size to keep total time around 15-16 minutes
        # Sum of avg_eval_times for current models (estimated with XL) is ~11.071s
        # (11.071s * num_samples) / 60s/min = ~15 minutes => num_samples = 900 / 11.071 = ~81
        # With 11 models, 80 samples each: (roughly 45s per model test run) * 11 models / 60s/min = ~8.25 min
        sample_size = 80 # Aim for 80 samples per model to keep total time within reasonable limits

        print(f"\n🧪 Testing {len(self.test_models)} models with {sample_size} evaluations each")
        # Estimate based on a typical average run time for a model test, adjusted for number of models
        estimated_total_time_minutes = (len(self.test_models) * 45) / 60 # Rough average of 45 seconds per model test
        print(f"⏱️  Estimated total benchmark time: ~{estimated_total_time_minutes:.1f} minutes")

        start_benchmark = time.time()

        # Test each model
        for i, model_info in enumerate(self.test_models, 1):
            print(f"\n[{i}/{len(self.test_models)}] Testing {model_info['name']}")

            model_start = time.time()
            result = self.test_model_performance(model_info, sample_size)
            model_time = time.time() - model_start

            if result:
                print(f"✅ Model test completed in {model_time:.1f}s")
            else:
                print(f"❌ Model test failed after {model_time:.1f}s")

            # Brief cooldown to avoid immediate resource issues
            time.sleep(2) # Increased cooldown slightly

        total_time = time.time() - start_benchmark

        # Generate report
        self.generate_quick_report(system_info, total_time)

    def generate_quick_report(self, system_info, total_time):
        """Generate focused report for Colab Pro decision, including parameter counts"""
        print("\n" + "="*80)
        print("📊 COLAB PRO DECISION REPORT")
        print("="*80)

        if not self.results:
            print("❌ No results to analyze")
            return

        print(f"⏱️  Benchmark completed in {total_time/60:.1f} minutes")
        print(f"🖥️  System: {system_info['tier']}")
        print(f"📅 Timestamp: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}")

        # Sort by performance (fastest avg_eval_time first, handle inf values)
        sorted_results = sorted(self.results, key=lambda x: x["avg_eval_time"] if x["avg_eval_time"] != float('inf') else float('inf'))

        print(f"\n{'MODEL PERFORMANCE RANKING':^80}")
        print("-" * 80)
        print(f"{'Rank':<5} {'Model':<25} {'Parameters':<12} {'Speed':<8} {'Mem Used':<10} {'Full TREC Est':<15} {'Judgements %':<15} {'Colab Rec':<15}")
        print("-" * 80)

        for i, result in enumerate(sorted_results, 1):
            model_short = result["model_name"].split("/")[-1][:20]
            params_str = ""
            if result.get("params_m") is not None:
                params_str = f"{result['params_m']}M"
            elif result.get("params_b") is not None:
                params_str = f"{result['params_b']}B"

            mem_used_str = f"{result['memory_used_gb']:.1f}GB" if result['memory_used_gb'] != float('inf') else "N/A"
            avg_eval_time_str = f"{result['avg_eval_time']:.3f}s" if result['avg_eval_time'] != float('inf') else "N/A"
            projected_time_str = f"{result['projected_hours']:.1f}h" if result['projected_hours'] != float('inf') else "N/A"

            # Corrected f-string for the 'Judgements %' column
            correct_judgment_rate_val = result['correct_judgment_rate']
            correct_judgment_rate_display = f"{correct_judgment_rate_val:.1f}"
            if correct_judgment_rate_val == 0.0:
                suffix_for_display = ""
            elif correct_judgment_rate_val < 100.0:
                suffix_for_display = "%"
            else: # For 100.0%
                suffix_for_display = " " # Add a space for 100% to maintain alignment as per original intent

            # Ensure the padding aligns with the full string for Judgments %
            # The padding is applied to the combined string.
            formatted_judgement_percent_col = f"{correct_judgment_rate_display}{suffix_for_display:<14}"

            print(f"{i:<5} {model_short:<25} {params_str:<12} {avg_eval_time_str:<8} {mem_used_str:<10} {projected_time_str:<15} {formatted_judgement_percent_col} {result['colab_recommendation']:<15}")

        # Decision matrix
        print(f"\n{'DECISION MATRIX':^80}")
        print("-" * 80)

        free_ok_models = [r for r in sorted_results if "FREE" in r["colab_recommendation"] and r["projected_hours"] != float('inf')]
        pro_helpful = [r for r in sorted_results if "Helpful" in r["colab_recommendation"] and r["projected_hours"] != float('inf')]
        pro_recommended = [r for r in sorted_results if "Recommended" in r["colab_recommendation"] and r["projected_hours"] != float('inf')]
        pro_required = [r for r in sorted_results if "Required" in r["colab_recommendation"] and r["projected_hours"] != float('inf')]
        failed_models = [r for r in self.results if r["load_time"] == float('inf')] # Use self.results to get all including failed ones

        if free_ok_models:
            best_free = free_ok_models[0]
            print(f"✅ COLAB FREE is sufficient:")
            print(f"   • Best model: {best_free['model_name'].split('/')[-1]} ({best_free.get('params_m', '')}M{best_free.get('params_b', '')}B parameters)")
            print(f"   • Estimated time: {best_free['projected_hours']:.1f} hours")
            print(f"   • Memory usage: {best_free['memory_used_gb']:.1f}GB")
            print(f"   • Correct Judgment Rate: {best_free['correct_judgment_rate']:.1f}%")
            print(f"   • 💰 Cost: $0/month")

        if pro_recommended or pro_helpful:
            relevant_models = pro_recommended + pro_helpful
            # Filter out models that failed or are too slow for realistic Pro benefit
            relevant_models = [m for m in relevant_models if m["projected_hours"] < 24] # Only show if it's under 24 hours
            if relevant_models:
                best_pro = min(relevant_models, key=lambda x: x["projected_hours"])
                print(f"\n⚡ COLAB PRO would provide:")
                print(f"   • Better model options: {len(relevant_models)} models")
                print(f"   • Potentially faster completion: {best_pro['projected_hours']:.1f} hours with {best_pro['model_name'].split('/')[-1]} ({best_pro.get('params_m', '')}M{best_pro.get('params_b', '')}B parameters)")
                print(f"   • More reliable performance for larger models")
                print(f"   • 💸 Cost: $10/month")

        if pro_required:
            print(f"\n🔴 COLAB PRO+ needed for (memory-intensive models):")
            for model in pro_required:
                print(f"   • {model['model_name'].split('/')[-1]} ({model.get('params_m', '')}M{model.get('params_b', '')}B parameters): {model['colab_reason']}")

        if failed_models:
            print(f"\n❌ FAILED TO RUN (Likely memory issues or invalid model name):")
            for model in failed_models:
                print(f"   • {model['model_name'].split('/')[-1]} ({model.get('params_m', '')}M{model.get('params_b', '')}B parameters): {model['colab_reason']}")

        # Final recommendation
        print(f"\n{'🎯 FINAL RECOMMENDATION':^80}")
        print("=" * 80)

        if free_ok_models:
            fastest_free = free_ok_models[0]
            if fastest_free["projected_hours"] < 12:
                print("💡 VERDICT: Colab FREE is perfectly adequate for your current needs.")
                print(f"   ✅ You can complete a full TREC evaluation in {fastest_free['projected_hours']:.1f} hours using {fastest_free['model_name'].split('/')[-1]}.")
                print(f"   ✅ It achieves a correct judgment rate of {fastest_free['correct_judgment_rate']:.1f}%.")
                print(f"   💰 Save $10/month - use the free tier!")
            else:
                print("💡 VERDICT: Colab PRO recommended but not strictly required.")
                print(f"   ⚠️  Free tier will take {fastest_free['projected_hours']:.1f} hours with {fastest_free['model_name'].split('/')[-1]}, exceeding typical session limits.")
                print(f"   ⚡ Pro tier could significantly reduce this time and provide more stable performance.")
                print(f"   💸 Consider Pro if your time and consistent access are more valuable than $10/month.")
        else:
            print("💡 VERDICT: Colab PRO is necessary for any of the tested models.")
            print("   ❌ Free tier cannot handle the memory requirements of these models for benchmarking.")
            print("   ✅ A Pro tier ($10/month) is required for reasonable performance and to even run some models.")
            print("   💸 This investment is justified for these tasks.")

        # Command for your specific use case
        if free_ok_models:
            best_model_for_command = free_ok_models[0]["model_name"]
            print(f"\n📝 FOR YOUR UMBRELA COMMAND (using the best FREE tier compatible model):")
            print("-" * 70)
            print(f"# Your command for efficient testing on Colab Free:")
            print(f"!python running.py \\") # Changed to running.py as this is the current script name
            print(f"  --qrel dl19-passage \\") # These args would need to be parsed by running.py if you want to use them
            print(f"  --result_file output.txt \\")
            print(f"  --prompt_type bing \\")
            print(f"  --model {best_model_for_command} \\")
            print(f"  --few_shot_count 0 \\")
            print(f"  --device cuda \\")
            print(f"  --num_sample 1")
            print(f"# Estimated completion for full TREC evaluation with this model: {free_ok_models[0]['projected_hours']:.1f} hours")

        print("=" * 80)


# Run the quick benchmark
if __name__ == "__main__":
    benchmark = QuickUmbrelaBenchmark()
    benchmark.run_quick_benchmark()

```

    Writing huggingfacerun.py



```python
!python huggingfacerun.py
```

    2025-08-11 17:18:06.595150: E external/local_xla/xla/stream_executor/cuda/cuda_fft.cc:467] Unable to register cuFFT factory: Attempting to register factory for plugin cuFFT when one has already been registered
    WARNING: All log messages before absl::InitializeLog() is called are written to STDERR
    E0000 00:00:1754932686.909125    6639 cuda_dnn.cc:8579] Unable to register cuDNN factory: Attempting to register factory for plugin cuDNN when one has already been registered
    E0000 00:00:1754932686.992573    6639 cuda_blas.cc:1407] Unable to register cuBLAS factory: Attempting to register factory for plugin cuBLAS when one has already been registered
    W0000 00:00:1754932687.629234    6639 computation_placer.cc:177] computation placer already registered. Please check linkage and avoid linking the same target more than once.
    W0000 00:00:1754932687.629281    6639 computation_placer.cc:177] computation placer already registered. Please check linkage and avoid linking the same target more than once.
    W0000 00:00:1754932687.629287    6639 computation_placer.cc:177] computation placer already registered. Please check linkage and avoid linking the same target more than once.
    W0000 00:00:1754932687.629293    6639 computation_placer.cc:177] computation placer already registered. Please check linkage and avoid linking the same target more than once.
    2025-08-11 17:18:07.692638: I tensorflow/core/platform/cpu_feature_guard.cc:210] This TensorFlow binary is optimized to use available CPU instructions in performance-critical operations.
    To enable the following instructions: AVX2 AVX512F FMA, in other operations, rebuild TensorFlow with the appropriate compiler flags.
    🚀 QUICK UMBRELA BENCHMARK FOR COLAB PRO DECISION
    🎯 Target: Evaluate TREC relevance assessment for multiple models
    ======================================================================
    
    ======================================================================
    🔍 SYSTEM RESOURCES & COLAB TIER DETECTION
    ======================================================================
    💾 RAM: 9.3GB available / 12.7GB total
    🚀 GPU: Tesla T4
    📊 GPU Memory: 14.7GB total, 14.7GB available
    🏷️  Detected: 🆓 Colab FREE (T4, ~15GB)
    ======================================================================
    
    🧪 Testing 12 models with 80 evaluations each
    ⏱️  Estimated total benchmark time: ~9.0 minutes
    
    [1/12] Testing google/flan-t5-small
    
    ======================================================================
    🧪 TESTING: google/flan-t5-small
    📋 Type: T5 | Size: Small
    ======================================================================
    ⏳ Loading model...
    tokenizer_config.json: 2.54kB [00:00, 5.12MB/s]
    spiece.model: 100% 792k/792k [00:00<00:00, 1.06MB/s]
    special_tokens_map.json: 2.20kB [00:00, 8.71MB/s]
    tokenizer.json: 2.42MB [00:00, 57.5MB/s]
    You are using the default legacy behaviour of the <class 'transformers.models.t5.tokenization_t5.T5Tokenizer'>. This is expected, and simply means that the `legacy` (previous) behavior will be used so nothing changes for you. If you want to use the new behaviour, set `legacy=False`. This should only be set if you understand what it means, and thoroughly read the reason why this was added as explained in https://github.com/huggingface/transformers/pull/24565
    config.json: 1.40kB [00:00, 6.46MB/s]
    model.safetensors: 100% 308M/308M [00:03<00:00, 77.8MB/s]
    generation_config.json: 100% 147/147 [00:00<00:00, 957kB/s]
    ✅ Loaded in 9.7s | Memory: 0.16GB
    🔄 Running 80 evaluations...
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    
    📊 PERFORMANCE METRICS:
      ⚡ Avg evaluation: 0.092s
      ✅ Correct Judgment Rate: 0.0/80 (0.0%)
      💾 Memory used: 0.16GB
      🕐 Full TREC est: 0.2h 14m
      🎯 Colab rec: FREE OK (Within limits)
    Total model test completion: 17.1s
    
    🔍 SAMPLE OUTPUTS:
      1. Query: how long is life cycle of flea...
           Response: '' (expected: 3) - 1.422s [❌ Incorrect]
      2. Query: medicare's definition of mechanical ventilation...
           Response: '' (expected: 1) - 0.076s [❌ Incorrect]
      3. Query: what is the daily life of thai people...
           Response: '' (expected: 0) - 0.070s [❌ Incorrect]
    ✅ Model test completed in 17.4s
    
    [2/12] Testing google/flan-t5-base
    
    ======================================================================
    🧪 TESTING: google/flan-t5-base
    📋 Type: T5 | Size: Base
    ======================================================================
    ⏳ Loading model...
    tokenizer_config.json: 2.54kB [00:00, 12.8MB/s]
    spiece.model: 100% 792k/792k [00:00<00:00, 1.44MB/s]
    special_tokens_map.json: 2.20kB [00:00, 10.7MB/s]
    tokenizer.json: 2.42MB [00:00, 16.7MB/s]
    config.json: 1.40kB [00:00, 6.09MB/s]
    model.safetensors: 100% 990M/990M [00:24<00:00, 41.1MB/s]
    generation_config.json: 100% 147/147 [00:00<00:00, 1.28MB/s]
    ✅ Loaded in 28.6s | Memory: 0.53GB
    🔄 Running 80 evaluations...
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    
    📊 PERFORMANCE METRICS:
      ⚡ Avg evaluation: 0.093s
      ✅ Correct Judgment Rate: 0.0/80 (0.0%)
      💾 Memory used: 0.53GB
      🕐 Full TREC est: 0.2h 14m
      🎯 Colab rec: FREE OK (Within limits)
    Total model test completion: 36.0s
    
    🔍 SAMPLE OUTPUTS:
      1. Query: how long is life cycle of flea...
           Response: '' (expected: 3) - 0.116s [❌ Incorrect]
      2. Query: medicare's definition of mechanical ventilation...
           Response: '' (expected: 1) - 0.093s [❌ Incorrect]
      3. Query: what is the daily life of thai people...
           Response: '' (expected: 0) - 0.090s [❌ Incorrect]
    ✅ Model test completed in 36.3s
    
    [3/12] Testing google/flan-t5-large
    
    ======================================================================
    🧪 TESTING: google/flan-t5-large
    📋 Type: T5 | Size: Large
    ======================================================================
    ⏳ Loading model...
    tokenizer_config.json: 2.54kB [00:00, 12.0MB/s]
    spiece.model: 100% 792k/792k [00:00<00:00, 1.10MB/s]
    special_tokens_map.json: 2.20kB [00:00, 10.1MB/s]
    tokenizer.json: 2.42MB [00:00, 22.9MB/s]
    config.json: 100% 662/662 [00:00<00:00, 6.06MB/s]
    model.safetensors: 100% 3.13G/3.13G [01:21<00:00, 38.5MB/s]
    generation_config.json: 100% 147/147 [00:00<00:00, 1.08MB/s]
    ✅ Loaded in 97.9s | Memory: 1.72GB
    🔄 Running 80 evaluations...
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    The following generation flags are not valid and may be ignored: ['temperature']. Set `TRANSFORMERS_VERBOSITY=info` for more details.
    
    📊 PERFORMANCE METRICS:
      ⚡ Avg evaluation: 0.173s
      ✅ Correct Judgment Rate: 0.0/80 (0.0%)
      💾 Memory used: 1.72GB
      🕐 Full TREC est: 0.4h 27m
      🎯 Colab rec: FREE OK (Within limits)
    Total model test completion: 111.8s
    
    🔍 SAMPLE OUTPUTS:
      1. Query: how long is life cycle of flea...
           Response: '' (expected: 3) - 0.265s [❌ Incorrect]
      2. Query: medicare's definition of mechanical ventilation...
           Response: '' (expected: 1) - 0.216s [❌ Incorrect]
      3. Query: what is the daily life of thai people...
           Response: '' (expected: 0) - 0.289s [❌ Incorrect]
    ✅ Model test completed in 112.1s
    
    [4/12] Testing google/flan-t5-xl
    
    ======================================================================
    🧪 TESTING: google/flan-t5-xl
    📋 Type: T5 | Size: Extra Large
    ======================================================================
    ⏳ Loading model...
    tokenizer_config.json: 2.54kB [00:00, 10.7MB/s]
    spiece.model: 100% 792k/792k [00:00<00:00, 1.37MB/s]
    special_tokens_map.json: 2.20kB [00:00, 11.9MB/s]
    tokenizer.json: 2.42MB [00:00, 199MB/s]
    config.json: 1.44kB [00:00, 6.27MB/s]
    model.safetensors.index.json: 53.0kB [00:00, 25.0MB/s]
    Fetching 2 files:   0% 0/2 [00:00<?, ?it/s]
    model-00001-of-00002.safetensors:   0% 0.00/9.45G [00:00<?, ?B/s][A
    
    model-00002-of-00002.safetensors:   0% 0.00/1.95G [00:00<?, ?B/s][A[A
    model-00001-of-00002.safetensors:   0% 16.6k/9.45G [00:01<232:02:49, 11.3kB/s][A
    model-00001-of-00002.safetensors:   0% 4.43M/9.45G [00:01<40:39, 3.87MB/s]    [A
    model-00001-of-00002.safetensors:   0% 7.64M/9.45G [00:01<22:41, 6.94MB/s][A
    
    model-00002-of-00002.safetensors:   0% 1.07M/1.95G [00:01<49:23, 657kB/s][A[A
    model-00001-of-00002.safetensors:   0% 11.4M/9.45G [00:09<2:33:51, 1.02MB/s][A
    
    model-00002-of-00002.safetensors:   0% 1.07M/1.95G [00:14<49:23, 657kB/s][A[A
    
    model-00002-of-00002.safetensors:   2% 33.5M/1.95G [00:22<21:11, 1.51MB/s][A[A
    model-00001-of-00002.safetensors:   1% 78.3M/9.45G [00:24<2:32:45, 1.02MB/s][A
    
    model-00002-of-00002.safetensors:   2% 33.5M/1.95G [00:34<21:11, 1.51MB/s][A[A
    model-00001-of-00002.safetensors:   2% 145M/9.45G [00:55<58:14, 2.66MB/s]   [A
    
    model-00002-of-00002.safetensors:   5% 101M/1.95G [01:03<19:24, 1.59MB/s] [A[A
    model-00001-of-00002.safetensors:   3% 273M/9.45G [01:04<30:26, 5.02MB/s][A
    model-00001-of-00002.safetensors:   4% 340M/9.45G [01:10<25:20, 5.99MB/s][A
    
    model-00002-of-00002.safetensors:   9% 168M/1.95G [01:10<10:35, 2.80MB/s][A[A
    model-00001-of-00002.safetensors:   4% 407M/9.45G [01:22<25:48, 5.84MB/s][A
    
    model-00002-of-00002.safetensors:   9% 168M/1.95G [01:24<10:35, 2.80MB/s][A[A
    model-00001-of-00002.safetensors:   5% 474M/9.45G [01:34<26:10, 5.72MB/s][A
    model-00001-of-00002.safetensors:   6% 541M/9.45G [01:44<25:58, 5.72MB/s][A
    model-00001-of-00002.safetensors:   6% 608M/9.45G [01:46<20:05, 7.34MB/s][A
    model-00001-of-00002.safetensors:   8% 742M/9.45G [01:50<13:37, 10.6MB/s][A
    model-00001-of-00002.safetensors:   9% 810M/9.45G [02:03<16:23, 8.78MB/s][A
    
    model-00002-of-00002.safetensors:  12% 235M/1.95G [02:09<16:28, 1.73MB/s][A[A
    model-00001-of-00002.safetensors:   9% 877M/9.45G [02:14<16:16, 8.78MB/s][A
    model-00001-of-00002.safetensors:  10% 944M/9.45G [02:15<14:58, 9.47MB/s][A
    
    model-00002-of-00002.safetensors:  12% 235M/1.95G [02:24<16:28, 1.73MB/s][A[A
    
    model-00002-of-00002.safetensors:  15% 302M/1.95G [02:28<12:52, 2.13MB/s][A[A
    model-00001-of-00002.safetensors:  10% 944M/9.45G [02:34<14:58, 9.47MB/s][A
    model-00001-of-00002.safetensors:  11% 1.01G/9.45G [02:34<20:21, 6.91MB/s][A
    
    model-00002-of-00002.safetensors:  15% 302M/1.95G [02:44<12:52, 2.13MB/s][A[A
    model-00001-of-00002.safetensors:  11% 1.08G/9.45G [02:54<20:11, 6.91MB/s][A
    model-00001-of-00002.safetensors:  12% 1.14G/9.45G [03:13<27:39, 5.01MB/s][A
    
    model-00002-of-00002.safetensors:  19% 369M/1.95G [03:23<15:32, 1.70MB/s][A[A
    model-00001-of-00002.safetensors:  13% 1.21G/9.45G [03:23<26:08, 5.25MB/s][A
    
    model-00002-of-00002.safetensors:  22% 436M/1.95G [03:23<09:59, 2.53MB/s][A[A
    model-00001-of-00002.safetensors:  14% 1.28G/9.45G [03:31<23:32, 5.79MB/s][A
    
    model-00002-of-00002.safetensors:  26% 503M/1.95G [03:31<07:18, 3.30MB/s][A[A
    
    model-00002-of-00002.safetensors:  29% 570M/1.95G [03:36<05:19, 4.32MB/s][A[A
    
    model-00002-of-00002.safetensors:  29% 574M/1.95G [03:37<05:18, 4.32MB/s][A[A
    model-00001-of-00002.safetensors:  14% 1.34G/9.45G [03:37<20:40, 6.53MB/s][A
    model-00001-of-00002.safetensors:  15% 1.41G/9.45G [03:49<21:30, 6.23MB/s][A
    
    model-00002-of-00002.safetensors:  33% 641M/1.95G [03:49<04:39, 4.68MB/s][A[A
    model-00001-of-00002.safetensors:  16% 1.48G/9.45G [03:56<18:53, 7.03MB/s][A
    model-00001-of-00002.safetensors:  16% 1.55G/9.45G [03:56<13:30, 9.76MB/s][A
    
    model-00002-of-00002.safetensors:  33% 641M/1.95G [04:04<04:39, 4.68MB/s][A[A
    model-00001-of-00002.safetensors:  16% 1.55G/9.45G [04:14<13:30, 9.76MB/s][A
    
    model-00002-of-00002.safetensors:  36% 708M/1.95G [04:30<07:17, 2.84MB/s][A[A
    
    model-00002-of-00002.safetensors:  40% 775M/1.95G [04:30<04:36, 4.25MB/s][A[A
    
    model-00002-of-00002.safetensors:  43% 842M/1.95G [04:36<03:29, 5.29MB/s][A[A
    model-00001-of-00002.safetensors:  16% 1.55G/9.45G [04:36<45:31, 2.89MB/s][A
    
    model-00002-of-00002.safetensors:  47% 909M/1.95G [04:42<02:44, 6.33MB/s][A[A
    model-00001-of-00002.safetensors:  17% 1.61G/9.45G [04:49<37:21, 3.50MB/s][A
    model-00001-of-00002.safetensors:  18% 1.68G/9.45G [04:49<24:31, 5.28MB/s][A
    
    model-00002-of-00002.safetensors:  47% 909M/1.95G [04:54<02:44, 6.33MB/s][A[A
    
    model-00002-of-00002.safetensors:  50% 977M/1.95G [05:01<03:09, 5.12MB/s][A[A
    model-00001-of-00002.safetensors:  18% 1.75G/9.45G [05:01<23:58, 5.35MB/s][A
    model-00001-of-00002.safetensors:  19% 1.81G/9.45G [05:13<23:32, 5.40MB/s][A
    model-00001-of-00002.safetensors:  19% 1.82G/9.45G [05:13<23:33, 5.40MB/s][A
    
    model-00002-of-00002.safetensors:  54% 1.04G/1.95G [05:14<02:54, 5.19MB/s][A[A
    
    model-00002-of-00002.safetensors:  54% 1.04G/1.95G [05:41<02:54, 5.19MB/s][A[A
    model-00001-of-00002.safetensors:  19% 1.82G/9.45G [05:41<23:33, 5.40MB/s][A
    
    model-00002-of-00002.safetensors:  57% 1.11G/1.95G [05:41<03:36, 3.88MB/s][A[A
    model-00001-of-00002.safetensors:  20% 1.88G/9.45G [05:41<34:16, 3.68MB/s][A
    model-00001-of-00002.safetensors:  21% 1.95G/9.45G [05:46<25:21, 4.93MB/s][A
    model-00001-of-00002.safetensors:  21% 2.02G/9.45G [05:47<16:47, 7.37MB/s][A
    
    model-00002-of-00002.safetensors:  60% 1.18G/1.95G [05:47<02:40, 4.81MB/s][A[A
    
    model-00002-of-00002.safetensors:  64% 1.24G/1.95G [05:55<02:06, 5.59MB/s][A[A
    model-00001-of-00002.safetensors:  22% 2.09G/9.45G [05:55<15:30, 7.91MB/s][A
    model-00001-of-00002.safetensors:  23% 2.17G/9.45G [05:57<11:39, 10.4MB/s][A
    
    model-00002-of-00002.safetensors:  67% 1.31G/1.95G [05:59<01:31, 6.99MB/s][A[A
    
    model-00002-of-00002.safetensors:  69% 1.35G/1.95G [05:59<01:12, 8.32MB/s][A[A
    model-00001-of-00002.safetensors:  24% 2.23G/9.45G [06:05<11:57, 10.1MB/s][A
    
    model-00002-of-00002.safetensors:  73% 1.41G/1.95G [06:05<00:58, 9.21MB/s][A[A
    model-00001-of-00002.safetensors:  24% 2.30G/9.45G [06:07<09:35, 12.4MB/s][A
    model-00001-of-00002.safetensors:  25% 2.37G/9.45G [06:11<08:40, 13.6MB/s][A
    model-00001-of-00002.safetensors:  26% 2.44G/9.45G [06:11<06:08, 19.0MB/s][A
    model-00001-of-00002.safetensors:  26% 2.48G/9.45G [06:12<04:56, 23.5MB/s][A
    model-00001-of-00002.safetensors:  27% 2.55G/9.45G [06:12<03:47, 30.4MB/s][A
    
    model-00002-of-00002.safetensors:  76% 1.48G/1.95G [06:16<00:58, 7.94MB/s][A[A
    model-00001-of-00002.safetensors:  28% 2.62G/9.45G [06:17<05:11, 21.9MB/s][A
    
    model-00002-of-00002.safetensors:  76% 1.48G/1.95G [06:31<00:58, 7.94MB/s][A[A
    model-00001-of-00002.safetensors:  28% 2.62G/9.45G [06:31<05:11, 21.9MB/s][A
    
    model-00002-of-00002.safetensors:  79% 1.55G/1.95G [06:54<01:46, 3.78MB/s][A[A
    model-00001-of-00002.safetensors:  28% 2.68G/9.45G [06:54<22:35, 4.99MB/s][A
    model-00001-of-00002.safetensors:  28% 2.69G/9.45G [06:54<22:37, 4.98MB/s][A
    
    model-00002-of-00002.safetensors:  83% 1.62G/1.95G [07:06<01:20, 4.15MB/s][A[A
    model-00001-of-00002.safetensors:  28% 2.69G/9.45G [07:11<22:37, 4.98MB/s][A
    
    model-00002-of-00002.safetensors:  86% 1.68G/1.95G [07:15<00:55, 4.80MB/s][A[A
    model-00001-of-00002.safetensors:  28% 2.69G/9.45G [07:20<49:44, 2.27MB/s][A
    model-00001-of-00002.safetensors:  31% 2.89G/9.45G [07:20<13:11, 8.29MB/s][A
    model-00001-of-00002.safetensors:  31% 2.96G/9.45G [07:21<09:47, 11.0MB/s][A
    model-00001-of-00002.safetensors:  32% 3.03G/9.45G [07:27<09:29, 11.3MB/s][A
    
    model-00002-of-00002.safetensors:  86% 1.68G/1.95G [07:31<00:55, 4.80MB/s][A[A
    
    model-00002-of-00002.safetensors:  90% 1.75G/1.95G [07:33<00:44, 4.47MB/s][A[A
    model-00001-of-00002.safetensors:  33% 3.12G/9.45G [07:39<11:07, 9.49MB/s][A
    model-00001-of-00002.safetensors:  33% 3.12G/9.45G [07:39<10:52, 9.70MB/s][A
    
    model-00002-of-00002.safetensors:  93% 1.82G/1.95G [07:43<00:27, 4.93MB/s][A[A
    model-00001-of-00002.safetensors:  34% 3.19G/9.45G [07:43<09:21, 11.1MB/s][A
    model-00001-of-00002.safetensors:  34% 3.26G/9.45G [07:51<09:45, 10.6MB/s][A
    model-00001-of-00002.safetensors:  35% 3.32G/9.45G [07:55<08:55, 11.4MB/s][A
    
    model-00002-of-00002.safetensors:  93% 1.82G/1.95G [08:01<00:27, 4.93MB/s][A[A
    model-00001-of-00002.safetensors:  36% 3.39G/9.45G [08:07<11:26, 8.83MB/s][A
    model-00001-of-00002.safetensors:  36% 3.39G/9.45G [08:07<11:29, 8.78MB/s][A
    model-00001-of-00002.safetensors:  37% 3.46G/9.45G [08:07<07:04, 14.1MB/s][A
    
    model-00002-of-00002.safetensors:  97% 1.88G/1.95G [08:08<00:17, 3.94MB/s][A[A
    
    model-00002-of-00002.safetensors:  97% 1.88G/1.95G [08:21<00:17, 3.94MB/s][A[A
    model-00001-of-00002.safetensors:  37% 3.46G/9.45G [08:21<07:04, 14.1MB/s][A
    model-00001-of-00002.safetensors:  37% 3.53G/9.45G [08:24<13:20, 7.40MB/s][A
    model-00001-of-00002.safetensors:  38% 3.60G/9.45G [08:24<08:51, 11.0MB/s][A
    model-00001-of-00002.safetensors:  39% 3.66G/9.45G [08:30<08:34, 11.2MB/s][A
    model-00001-of-00002.safetensors:  39% 3.73G/9.45G [08:36<08:28, 11.3MB/s][A
    model-00001-of-00002.safetensors:  39% 3.73G/9.45G [08:51<08:28, 11.3MB/s][A
    model-00001-of-00002.safetensors:  40% 3.80G/9.45G [09:07<19:17, 4.88MB/s][A
    model-00001-of-00002.safetensors:  41% 3.87G/9.45G [09:08<13:23, 6.95MB/s][A
    model-00001-of-00002.safetensors:  42% 3.93G/9.45G [09:15<12:12, 7.53MB/s][A
    model-00001-of-00002.safetensors:  42% 4.00G/9.45G [09:21<10:44, 8.45MB/s][A
    model-00001-of-00002.safetensors:  43% 4.07G/9.45G [09:21<07:37, 11.8MB/s][A
    model-00001-of-00002.safetensors:  44% 4.14G/9.45G [09:27<07:26, 11.9MB/s][A
    model-00001-of-00002.safetensors:  44% 4.20G/9.45G [09:27<05:15, 16.6MB/s][A
    
    model-00002-of-00002.safetensors: 100% 1.95G/1.95G [09:28<00:00, 3.43MB/s]
    
    model-00001-of-00002.safetensors:  45% 4.28G/9.45G [09:29<04:05, 21.1MB/s][A
    model-00001-of-00002.safetensors:  45% 4.29G/9.45G [09:29<04:02, 21.3MB/s][A
    model-00001-of-00002.safetensors:  46% 4.36G/9.45G [09:36<05:44, 14.8MB/s][A
    model-00001-of-00002.safetensors:  46% 4.36G/9.45G [09:51<05:44, 14.8MB/s][A
    model-00001-of-00002.safetensors:  47% 4.42G/9.45G [10:07<16:26, 5.09MB/s][A
    model-00001-of-00002.safetensors:  48% 4.49G/9.45G [10:07<11:03, 7.48MB/s][A
    model-00001-of-00002.safetensors:  48% 4.52G/9.45G [10:08<09:43, 8.45MB/s][A
    model-00001-of-00002.safetensors:  48% 4.58G/9.45G [10:15<09:28, 8.57MB/s][A
    model-00001-of-00002.safetensors:  49% 4.65G/9.45G [10:21<08:27, 9.46MB/s][A
    model-00001-of-00002.safetensors:  50% 4.72G/9.45G [10:27<07:55, 9.94MB/s][A
    model-00001-of-00002.safetensors:  50% 4.73G/9.45G [10:27<07:31, 10.5MB/s][A
    model-00001-of-00002.safetensors:  51% 4.79G/9.45G [10:33<07:14, 10.7MB/s][A
    model-00001-of-00002.safetensors:  51% 4.86G/9.45G [10:33<04:41, 16.3MB/s][A
    model-00001-of-00002.safetensors:  52% 4.93G/9.45G [10:40<05:44, 13.1MB/s][A
    model-00001-of-00002.safetensors:  52% 4.93G/9.45G [10:51<05:44, 13.1MB/s][A
    model-00001-of-00002.safetensors:  53% 4.98G/9.45G [11:06<13:52, 5.37MB/s][A
    model-00001-of-00002.safetensors:  53% 4.99G/9.45G [11:06<13:10, 5.64MB/s][A
    model-00001-of-00002.safetensors:  54% 5.06G/9.45G [11:08<08:19, 8.78MB/s][A
    model-00001-of-00002.safetensors:  54% 5.13G/9.45G [11:08<05:17, 13.6MB/s][A
    model-00001-of-00002.safetensors:  55% 5.20G/9.45G [11:15<05:30, 12.8MB/s][A
    model-00001-of-00002.safetensors:  56% 5.27G/9.45G [11:20<05:35, 12.5MB/s][A
    model-00001-of-00002.safetensors:  57% 5.36G/9.45G [11:26<05:18, 12.9MB/s][A
    model-00001-of-00002.safetensors:  57% 5.42G/9.45G [11:34<05:48, 11.5MB/s][A
    model-00001-of-00002.safetensors:  57% 5.43G/9.45G [11:51<05:48, 11.5MB/s][A
    model-00001-of-00002.safetensors:  57% 5.43G/9.45G [11:52<13:07, 5.11MB/s][A
    model-00001-of-00002.safetensors:  57% 5.43G/9.45G [11:55<14:54, 4.50MB/s][A
    model-00001-of-00002.safetensors:  58% 5.49G/9.45G [12:07<13:10, 5.00MB/s][A
    model-00001-of-00002.safetensors:  59% 5.56G/9.45G [12:07<08:04, 8.03MB/s][A
    model-00001-of-00002.safetensors:  60% 5.63G/9.45G [12:08<05:12, 12.2MB/s][A
    model-00001-of-00002.safetensors:  60% 5.70G/9.45G [12:20<07:05, 8.81MB/s][A
    model-00001-of-00002.safetensors:  61% 5.76G/9.45G [12:20<04:58, 12.3MB/s][A
    model-00001-of-00002.safetensors:  61% 5.76G/9.45G [12:31<04:58, 12.3MB/s][A
    model-00001-of-00002.safetensors:  62% 5.82G/9.45G [12:44<10:18, 5.86MB/s][A
    model-00001-of-00002.safetensors:  62% 5.89G/9.45G [12:45<07:17, 8.14MB/s][A
    model-00001-of-00002.safetensors:  63% 5.96G/9.45G [12:47<05:23, 10.8MB/s][A
    model-00001-of-00002.safetensors:  64% 6.03G/9.45G [12:52<05:05, 11.2MB/s][A
    model-00001-of-00002.safetensors:  64% 6.09G/9.45G [12:53<03:32, 15.8MB/s][A
    model-00001-of-00002.safetensors:  65% 6.16G/9.45G [12:59<03:53, 14.1MB/s][A
    model-00001-of-00002.safetensors:  66% 6.23G/9.45G [13:05<04:09, 12.9MB/s][A
    model-00001-of-00002.safetensors:  67% 6.29G/9.45G [13:10<04:00, 13.1MB/s][A
    model-00001-of-00002.safetensors:  67% 6.36G/9.45G [13:11<02:57, 17.4MB/s][A
    model-00001-of-00002.safetensors:  68% 6.43G/9.45G [13:11<02:06, 23.9MB/s][A
    model-00001-of-00002.safetensors:  69% 6.50G/9.45G [13:17<02:44, 17.9MB/s][A
    model-00001-of-00002.safetensors:  69% 6.57G/9.45G [13:23<03:10, 15.1MB/s][A
    model-00001-of-00002.safetensors:  70% 6.63G/9.45G [13:29<03:28, 13.5MB/s][A
    model-00001-of-00002.safetensors:  71% 6.70G/9.45G [13:35<03:36, 12.7MB/s][A
    model-00001-of-00002.safetensors:  72% 6.77G/9.45G [13:42<03:41, 12.1MB/s][A
    model-00001-of-00002.safetensors:  72% 6.83G/9.45G [13:43<02:42, 16.1MB/s][A
    model-00001-of-00002.safetensors:  73% 6.90G/9.45G [13:54<04:00, 10.6MB/s][A
    model-00001-of-00002.safetensors:  74% 6.97G/9.45G [13:54<02:46, 14.9MB/s][A
    model-00001-of-00002.safetensors:  74% 6.97G/9.45G [14:11<02:46, 14.9MB/s][A
    model-00001-of-00002.safetensors:  74% 7.04G/9.45G [14:21<06:45, 5.96MB/s][A
    model-00001-of-00002.safetensors:  75% 7.10G/9.45G [14:27<05:32, 7.07MB/s][A

Now, eval for complete judgement using hugging face open-source models


```python
%%writefile output.txt
#test
```


```python
!nvidia-smi

```


```python
!python umbrela/hgfllm_judge.py --qrel dl19-passage --result_file output.txt --prompt_type bing --model Qwen/Qwen2-7B-Instruct --few_shot_count 0 --device cuda --num_sample 1
```
