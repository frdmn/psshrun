psshrun - host file configurations for pssh  
===========================================

Tiny bash script to execute commands for saved host group files via [parallel-ssh](https://code.google.com/p/parallel-ssh/) or `pssh`.

# Installation

    git clone https://github.com/frdmn/psshrun.git /usr/local/src/psshrun
    ln -s /usr/local/src/psshrun/psshrun /usr/bin/psshrun
    # if you use Bash shell
    echo 'export psshrun_configpath="${HOME}/.pssh"' >> ~/.bashrc
    echo '. /usr/local/src/psshrun/bash_completion.d/psshrun' >> ~/.bashrc
    # or if you use ZSH
    echo 'export psshrun_configpath="${HOME}/.pssh"' >> ~/.zshrc
    echo '. /usr/local/src/psshrun/bash_completion.d/psshrun' >> ~/.zshrc
    mkdir ${HOME}/.pssh

# Usage

### Host file syntax

To add a new host group, create a new file in `$psshrun_configpath` that contains the hostname/username combinations:

    $ cat ~/.pssh/yeahwh.at
    r2-d2.yeahwh.at dummy
    obi-wan.yeahwh.at dummy
    chewbacca.yeahwh.at dummy

### Run commands

To run commands simple specify the specific host file and the command you want to run across the hosts:

    $  psshrun yeahwh.at "aptitude update"
    [1] 23:06:11 [SUCCESS] dummy@obi-wan.yeahwh.at
    [2] 23:06:15 [SUCCESS] dummy@chewbacca.yeahwh.at
    [3] 23:06:17 [SUCCESS] dummy@r2-d2.yeahwh.at

# License

[MIT](./LICENSE)
