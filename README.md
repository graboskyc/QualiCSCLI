# About This Repo
This repo is a simple work in progress to make it easy to see available blueprints on a CloudShell system and start those blueprints easily, all via the CLI with a simple syntax.

# Installation
## From Source
* Download the repository somewhere
* CD to that directory
* Run `pip install --editable .`

## From PyPi
* Run `pip install QualiCSCLI`

# Usage
     > QualiCSCLI help
    
    usage: QualiCSCLI [-h] [-q HOST] [-u UN] [-p PW] [-d DOM] [-s INFILE]
                      [-o OUTFILE] [-i ID] [-l LENGTH] [-n NAME]
                      task
    
    CLI Tool for Quali CloudShell Sandboxes
    
    positional arguments:
      task        start, list, running, or publish
    
    optional arguments:
      -h, --help  show this help message and exit
      -q HOST     server hostname for API session
      -u UN       username for API session
      -p PW       password for API session
      -d DOM      domain for API session
      -s INFILE   in python script
      -o OUTFILE  name of script in portal
      -i ID       sandbox/blueprint id
      -l LENGTH   sandbox duration length in min. Default is 30
      -w, --wait  wait until sandbox is completed until script returns
    
# Sample
## First Time
     > QualiCSCLI -q http://server:82 -u username -p password -d Global list
    
    +--------------------------------------+---------------+--------------+
    | Blueprint Name                       | Blueprint ID  | Availability |
    +--------------------------------------+---------------+--------------+
    +--------------------------------------+---------------+--------------+

## Subsequent 
After that, a config file is placed in ~/.qsclicreds where it stores this info, so subsequent usage is simple:

     > QualiCSCLI list

## Flow
     > QualiCSCLI list
    +----------------------------------------------------------+---------------+
    | Blueprint Name    | Blueprint ID                         | Availability  |
    +-------------------+--------------------------------------+---------------+
    | Example           | 72c8bd21-0191-48bb-bb9a-02e8b9e452f6 | Available Now |
    +-------------------+--------------------------------------+---------------+
    
    
     > QualiCSCLI start -i 72c8bd21-0191-48bb-bb9a-02e8b9e452f6
    Started 9d8b0e55-6fc2-41fb-8e00-ce6c0049c4b5

     > QualiCSCLI running
    +--------------------------------------+--------------+----------------+--------+
    | Sandbox ID                           | Sandbox Name | From Blueprint | Status |
    +--------------------------------------+--------------+----------------+--------+
    | 9d8b0e55-6fc2-41fb-8e00-ce6c0049c4b5 | From CLI     | Example        | Ready  |
    +--------------------------------------+--------------+----------------+--------+

