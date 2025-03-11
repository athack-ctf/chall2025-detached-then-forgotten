# How to run?

1. Run docker compose project

```
docker compose up --build
```

2. Use password `nedned` to log into the server as `ned`

```
ssh ned@localhost -p 2025 
```

3. List screen sessions (you should see the session `stash`)

```
screen -ls
```

4. Attach to the screen session `ned-stash`

```
screen -r ned-stash
```

5. Get the flag

```
cat flag.txt
```
