# DKIM Registry CASA Tier 2 scanning wrapper

This repository is a wrapper for running a static scan of the https://github.com/foolo/dkim-lookup project for the CASA Tier 2 process.
It contains the configuration files and documentation of the steps needed to run the scan.

## Prerequisites

Install Docker if it is not already installed. See https://docs.docker.com/engine/install/

## Usage

Clone the repositories

```bash
git clone git@github.com:foolo/dkimreg_casa.git
cd dkimreg_casa/app
git clone git@github.com:foolo/dkim-lookup.git
```

Build the Docker image

```bash
docker build --tag casascan .
```

Run the scan

```bash
docker run --name scan_container --volume .:/fluidscan fluidattacks/cli:amd64 skims scan /fluidscan/fluidconfig.yaml
```

Copy the results file to the host machine, where it can be viewed

```bash
docker cp scan_container:/src/fluid_attacks_results.csv .
```

## Reference material

https://appdefensealliance.dev/casa

https://docs.fluidattacks.com/tech/scanner/standalone/casa/
