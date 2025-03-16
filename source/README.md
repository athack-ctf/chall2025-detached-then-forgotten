# Running This Challenge

Build
```
docker build -t athack-ctf/chall2025-detached-then-forgotten:latest .
```

Run
```
docker run -d --name detached-then-forgotten \
  --hostname ned-land \
  -p 52026:22 \
  athack-ctf/chall2025-detached-then-forgotten:latest
```
