# @HACK 2025: Detached then Forgotten

> Authored by [Abdussamad](https://github.com/AbSamad99).

- **Category**: `Pwn`
- **Value**: `150 points`
- **Tags**: `beginner` `ssh`

> Ned is known to get attached, then detach and completely forget. This time, what he left behind is yours to
> find. However, don't be fooled by his past.
> 
> Ned's SSH credentials:
> 
> - Username: ned
> - Password: nedned
> 

## Access a dockerized instance

Run challenge container using docker compose
```
docker compose up -d
```
SSH using given credentials
```
ssh -p 52026 <username>@localhost
```
<details>
<summary>
How to stop/restart challenge?
</summary>

To stop the challenge run
```
docker compose stop
```
To restart the challenge run
```
docker compose restart
```

</details>


## Reveal Flag

Did you try solving this challenge?
<details>
<summary>
Yes
</summary>

Did you **REALLY** try solving this challenge?

<details>
<summary>
Yes, I promise!
</summary>

Flag: `ATHACKCTF{t0ld_y4_n0t_to_b3_f00led_by_bash_hist0ry}`

</details>
</details>


---

## About @HACK
[@HACK](https://athackctf.com/) is an annual CTF (Capture The Flag) competition hosted by [HEXPLOIT ALLIANCE](https://hexploit-alliance.com/) and [TECHNATION](https://technationcanada.ca/) at Concordia University in Montreal, Canada.

---
[Check more challenges from @HACK 2025](https://github.com/athack-ctf/AtHackCTF-2025-Challenges).