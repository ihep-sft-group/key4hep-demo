# key4hep-demo

TODO: create a package for key4hep demo.

## Quick start (at IHEP lxslc7)

Define an envvar for the work directory:
```
$ export KEY4HEP=/junofs/users/lint/key4hep-dev
```

Setup the LCG env:
```
$ source /cvmfs/sft.cern.ch/lcg/views/LCG_96b/x86_64-centos7-gcc9-opt/setup.sh
```

Install podio:
```
$ cd $KEY4HEP
$ git clone https://github.com/AIDASoft/podio.git
$ cd podio/
$ source init.sh
$ mkdir build && cd build
$ cmake ..
$ make
$ make install DESTDIR=$KEY4HEP
```

After that, the podio will be installed under `$KEY4HEP/usr/local/lib64/`.
In order to let cmake find the library, setup following envvar:
```
$ export CMAKE_PREFIX_PATH=$KEY4HEP/usr/local:$CMAKE_PREFIX_PATH
```

Install edm4hep:
```
$ cd $KEY4HEP
$ git clone https://github.com/HSF/EDM4hep
$ cd EDM4HEP
$ mkdir build && cd build
$ cmake ..
$ make
$ make install DESTDIR=$KEY4HEP
```

Install Gaudi if not installed:
```
$ git clone https://gitlab.cern.ch/gaudi/Gaudi.git
$ git checkout v32r2 # switch to a specific version
$ mkdir build && cd build
$ cmake ..
$ make
```





