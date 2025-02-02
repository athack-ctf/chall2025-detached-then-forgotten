# Too many screens

1. Run docker compose project

```
docker compose up --build
```

2. Use private key to log into the server as ned

```
ssh -i id_rsa -p 2025 ned@localhost
```

3. List screen sessions (you should see the session `sysadmin`)

```
screen -ls
```

4. Attach to the screen session `sysadmin`

```
screen -r sysadmin
```

5. Get the flag

```
cat flag.txt
```
