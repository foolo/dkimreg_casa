# DKIM Registry CASA scanning framework

## Prerequisites

Install Docker if it is not already installed. See https://docs.docker.com/engine/install/

## Usage

Clone the repository

```bash
git clone --recurse-submodules git@github.com:foolo/dkimreg_casa.git
```

Build the Docker image

```bash
docker build --tag casascan dkimreg_casa/
```

Run the scan

```bash
cd dkimreg_casa
docker run --name casacontainer --volume .:/fluidscan fluidattacks/cli:amd64 skims scan /fluidscan/fluidconfig.yaml
```

Copy the results file to the host machine, where it can be viewed

```bash
docker cp casacontainer:/src/fluid_attacks_results.csv .
```

## Reference material

https://appdefensealliance.dev/casa/tier-2/getting-started

https://docs.fluidattacks.com/tech/scanner/standalone/casa/
