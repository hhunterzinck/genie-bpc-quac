# GENIE Biopharma Collaborative Quality Assurance Checklist tool

## Overview

This repository provides a command line tool for checking raw data, intermediate files, and final data releases for the GENIE Biopharma Collaborative project.  

## Installation

For installation via Docker, type

```
docker build -t genie-bpc-quac .
```

## Usage

Make sure to cache your Synapse personal access token (PAT) as an environmental variable:

```
export SYNAPSE_ACCESS_TOKEN={your_personal_access_token_here}
```

To run via docker, type

```
docker run -e SYNAPSE_ACCESS_TOKEN=$SYNAPSE_ACCESS_TOKEN --rm genie-bpc-quac -h
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
