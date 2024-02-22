# DKIM Registry CASA scanning framework

## Setup

### Install Docker

See https://docs.docker.com/engine/install/

### Clone the repository

```bash
git@github.com:foolo/dkimreg_casa.git
cd dkimreg_casa
git submodule init
git submodule update
cd ..
```

### Build the Docker image

```bash
docker build -t casascan dkimreg_casa
```

### Run the scan

```bash
cd dkimreg_casa
docker run --name casacontainer --volume .:/fluidscan fluidattacks/cli:amd64 skims scan /fluidscan/fluidconfig.yaml
```

### Obtain the output

Copy the results file to the host machine, where it can be viewed

```bash
docker cp casacontainer:/src/fluid_attacks_results.csv .
```
