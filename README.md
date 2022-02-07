# GENIE BPC Quality Assurance Checklist

## Overview

This repository provides a command line tool for checking raw data, intermediate files, and final data releases for the GENIE Biopharma Collaborative (BPC) project.  

## Installation

Clone this repository and navigate to the directory:

```
git clone git@github.com:hhunterzinck/genie-bpc-quac.git
cd genie-bpc-quac/
```

For installation with Docker: 

```
docker build -t genie-bpc-quac .
```

For install without Docker, install Synapser and other required packages:
```
R -e 'install.packages("synapser", repos = c("http://ran.synapse.org", "http://cran.fhcrc.org"))'
R -e 'renv::restore()'
```

## Usage 

Make sure to cache your Synapse personal access token (PAT) as an environmental variable:

```
export SYNAPSE_AUTH_TOKEN={your_personal_access_token_here}
```

To run with Docker:

```
docker run --rm genie-bpc-quac -h
```

To run without Docker:

```
Rscript genie-bpc-quac.R -h
```

The command line interface will display as follows: 

```
usage: genie-bpc-quac.R [-h] -c {BLADDER,BrCa,CRC,NSCLC,PANC,Prostate}
                        [-s {all,DFCI,MSK,UHN,VICC}] -r
                        {comparison,masking,release,table,upload} [-n NUMBER]
                        [-l {all,error,warning}] [-o] [-u] [-v]
                        [-a SYNAPSE_AUTH]

optional arguments:
  -h, --help            show this help message and exit
  -c {BLADDER,BrCa,CRC,NSCLC,PANC,Prostate}
                        Cohort on which to perform checks
  -s {all,DFCI,MSK,UHN,VICC}
                        Site on which to perform checks
  -r {comparison,masking,release,table,upload}
                        Report to generate
  -n NUMBER             Reference number of check to run individually within
                        report
  -l {all,error,warning}
                        Level of priority of checks to run
  -o                    Display overview of parameters and checks to be
                        performed but do not execute
  -u                    Save report log file to pre-specified Synapse folder
  -v                    Display messages on script progress to the user
  -a SYNAPSE_AUTH       Path to .synapseConfig file or Synapse PAT (default:
                        '~/.synapseConfig')
```

Example command line with Docker:

```
docker run --rm genie-bpc-quac -c BLADDER -s VICC -r upload -l error -v -a $SYNAPSE_AUTH_TOKEN
```

Example command line without Docker:

```
Rscript genie-bpc-quac -c BLADDER -s VICC -r upload -l error -v -a $SYNAPSE_AUTH_TOKEN
```
