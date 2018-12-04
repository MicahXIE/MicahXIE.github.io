---
layout:     post
title:      rm -rf shell script practice
subtitle:   shell script
date:       2018-12-05
author:     Micah
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Shell
---

## Topic

- Just a simple example for practice
 
## Idea

> input a full path, rm the specific file or folder

### Program

    #!/bin/ksh

    # PURPOSE
    #
    # This script will remove the specific file or folder
    #
    # Date         Reference        Author        Description  
    # -----------  -------------    -----------   ------------
    # 2018-12-05                    Micah         Initial Creation
    #

    # Get the target file full path
    file="$1"

    # How to use
    USAGE = "\nUsage: <$0> 'target_file' \n\     
    'target_file' - use the file or folder full path     
    "    
    ret=0    

    # check the number of input parameter
    if [ $# -ne 1 ]; then
        print "$USAGE"
        ret=1

    else
        ## check if file or folder exists
        if [ ! -f "$file" ] && [ ! -d "$file" ]; then
            echo "$file does not exist."
            ret=1

        else     
            echo "rm the target $file"      
            rm -rf $file>/dev/null      
            ret=$?       
        fi       
    fi       
 
    exit $ret     

