# Install Chromium Linux Browser
Chromium is an open-source browser project that aims to build a safer, faster, and more stable build by Google
* You can easily access a browser in your non-gui Linux server
* You can easily run your Node Extensions 

## Install Docker
# Docker version check
```console
docker --version
```
## If you have installed please go to next step! `Timezone check`
```console
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Timezone check
```
realpath --relative-to /usr/share/zoneinfo /etc/localtime
```

## Install Chromium
**1. Create directory**
```
mkdir chromium
cd chromium
```

**2. Create `docker-compose.yaml` file**
```
nano docker-compose.yaml
```

**3. Paste the following code in it**
* `CUSTOM_USER` & `PASSWORD`: Replace your favorite credentials to login to chromium
* `TZ`: Replace with your server timezone
* `CHROME_CLI`: The main page when you open browser
* `ports`: You can replace `3010` & `3011` if they have conflict
```
---
services:
  chromium:
    image: lscr.io/linuxserver/chromium:latest
    container_name: chromium
    security_opt:
      - seccomp:unconfined #optional
    environment:
      - CUSTOM_USER=     #Replace username
      - PASSWORD=    #Replace password
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Berlin
      - CHROME_CLI=https://github.com/ToanBm/chromium-linux-browser #optional
    volumes:
      - /root/chromium/config:/config
    ports:
      - 3010:3000   #Change 3010 to your favorite port if needed
      - 3011:3001   #Change 3011 to your favorite port if needed
    shm_size: "1gb"
    restart: unless-stopped
```
> To save and exit: `Ctrl+X+Y+Enter` 

## Run Chromium
```console
cd $HOME && cd chromium

docker compose up -d
```
**The application can be accessed by going to one of these addresses in your local PC browser**
* http://Server_IP:3010/
* https://Server_IP:3011/

## Optional: Stop and Delete Chromium
```
docker stop chromium
docker rm chromium
docker system prune
```
-------------------------------------------------------------------------------------------------------------------------------
# Nodes you can run
### 1. Dawn
* Raised $18M
* Install [Extension](https://chromewebstore.google.com/detail/dawn-validator-chrome-ext/fpdkjdnhkakefebpekbdhillbhonfjjp)
* Create account with Email and verify your Email
* Invite Code: `uy6acy7s`

### 2. Nodepay
* Backed by Animoca
* Create account [here](https://app.nodepay.ai/register?ref=RBjYajVO9U5p89W)
* Install [Extension](https://chromewebstore.google.com/detail/nodepay-extension/lgmpfmgeabnnlemejacfljbmonaomfmm)

### 3. Blockmesh
* Data Network in EclipseFND ecosystem
* Create account [here](https://app.blockmesh.xyz/register?invite_code=9d698d03-f93c-4fa5-af34-2ec06d1e3dda)
* Install [Extension](https://chromewebstore.google.com/detail/blockmesh-network/obfhoiefijlolgdmphcekifedagnkfjp)

### 4. Teneo
* 
* Install [Extension](https://chromewebstore.google.com/detail/teneo-community-node/emcclcoaglgcpoognfiggmhnhgabppkm)
* Register with Code: EN9v2

### 5. GAEA
* Create account [here](https://app.aigaea.net/register?ref=gaImn1TX5Z8bu2)
* Install [Extension](https://chromewebstore.google.com/detail/gaea-extension/cpjicfogbgognnifjgmenmaldnmeeeib)

### 6. Pipe Network
* Create account [here](https://pipecdn.app/signup?ref=YnVpbWluaH)
* Install [Extension](https://chromewebstore.google.com/detail/pipe-guardian-node/gelgmmdfajpefjbiaedgjkpekijhkgbe)

  

### Functor Network
* $FUNC airdrop confirmed
* Create account and Install Extension [here]()
* It needs a code to join: `cm1i9yz06es6aqi1bqs0mjsk4`
* There is a daily Check-in

#

### Blockless Phase 3 soon...

#

### Openlayer AI Network


#

