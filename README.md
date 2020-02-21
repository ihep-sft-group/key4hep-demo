# key4hep-demo

TODO: create a package for key4hep demo.

## Environment variables
```
export CMAKE_PREFIX_PATH=/cvmfs/sft.cern.ch/lcg/releases:$CMAKE_PREFIX_PATH
export BINARY_TAG=x86_64-centos7-gcc9-opt

source /cvmfs/sft.cern.ch/lcg/views/LCG_96b/x86_64-centos7-gcc9-opt/setup.sh

export KEY4HEP=/junofs/users/lint/key4hep-dev
export CMAKE_PREFIX_PATH=$KEY4HEP/usr/local:$CMAKE_PREFIX_PATH

```

## Quick start (at IHEP lxslc7)

Define an envvar for the work directory:
```
$ export KEY4HEP=/junofs/users/lint/key4hep-dev
```

Setup the LCG env:
```
$ export CMAKE_PREFIX_PATH=/cvmfs/sft.cern.ch/lcg/releases:$CMAKE_PREFIX_PATH
$ export BINARY_TAG=x86_64-centos7-gcc9-opt
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
$ cd $KEY4HEP
$ git clone https://gitlab.cern.ch/gaudi/Gaudi.git Gaudi-v32r2
$ cd Gaudi-v32r2 && git checkout v32r2 && cd .. # switch to a specific version
$ mkdir Gaudi-v32r2-build && cd Gaudi-v32r2-build
$ cmake ../Gaudi-v32r2 -DBoost_NO_BOOST_CMAKE=ON
$ make
$ make install
```

Note: during build Gaudi, set `Boost_NO_BOOST_CMAKE` to force using FindBoost.cmake.

Setup envvar for Gaudi:
```
$ export CMAKE_PREFIX_PATH=$KEY4HEP/Gaudi-v32r2/InstallArea:$CMAKE_PREFIX_PATH
```

Install K4FWCore:
```
$ cd $KEY4HEP
$ git clone https://github.com/key4hep/K4FWCore.git
$ cd K4FWCore
$ mkdir build && cd build
$ cmake ..
$ make
$ make install
```

If no `CMAKE_INSTALL_PREFIX` specified, the libraries will be installed under `InstallArea`.

