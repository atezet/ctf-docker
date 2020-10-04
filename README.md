
# CTF setup in Docker
This setup is intended to create a quick working environment to play Capture The Flags (CTF), HackTheBox and similar.

## Setup
The easiest way to use this setup is to download `docker-compose.yml` and add the VPN config for the CTF; in this case, named `ctf.ovpn`. When those two are put in the same directory, run:
```
docker-compose up -d
```

### VPN credentials
In case credentials are required with the VPN config, create a file called `credentials.txt` with the username and password each on one line, uncomment the following line in `docker-compose.yml`:
```
      - ./credentials.txt:/vpn/credentials.txt:ro
```

And, if required, add the following line to the VPN config:
```
auth-user-pass /vpn/credentials.txt
```

## Usage

### Command line 
When all containers are running, enter the Kali container using:
```
docker exec -it ctf-kali tmux -CC
```

From this shell any commands needed to play the CTF can be run.

### Copy files
To copy a file to a volume, use:
```
docker cp $(pwd)/file.txt ctf-kali:/root/file.txt
```

### Browser
Challenges might involve a webpage, that's what the proxy container is used for. Run your browser through the proxy (with or without extra proxies) to let the traffic go through the VPN.



## Customise
Feel free to edit anything in any way. Mount other config files, add containers, anything. Suggestions can also be added to this repository.

## Future work

- Add option to use X11 applications, or find a workaround for it.

## References

This setup makes use of [dperson/openvpn-client](https://github.com/dperson/openvpn-client) and [wernight/dante](https://github.com/wernight/docker-dante).
