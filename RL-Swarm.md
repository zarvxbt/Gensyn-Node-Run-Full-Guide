## 📥 Installation

1. **Install `sudo`**
```bash
apt update && apt install -y sudo
```
2. **Install other dependencies**
```bash
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof nano unzip iproute2 build-essential gcc g++
```
3. **Install CUDA**
```
[ -f cuda.sh ] && rm cuda.sh; curl -o cuda.sh https://raw.githubusercontent.com/zunxbt/gensyn-testnet/main/cuda.sh && chmod +x cuda.sh && . ./cuda.sh
```
4. **Create a `screen` session**
```bash
screen -S gensyn
```
5. **Clone official `rl-swarm` repo**
```
git clone https://github.com/gensyn-ai/rl-swarm.git && cd rl-swarm
```
6. **Run the swarm**
```
python3 -m venv .venv
. .venv/bin/activate
./run_rl_swarm.sh
```

![image](https://github.com/user-attachments/assets/40d07439-ffd1-4207-9e51-fabc3fdbb8aa)

- After sometimes, u will see something like this if your running it on Linux system, so here follow the next step

7. **Tunnel the `localhost` link**
- There are multiple way to do this - localtunnel / ngrok / cloudflared, in this guide, I will use localtunnel
- Here, keep the rl-swarm running in one tab, and open the GPU/VPS/WSL again in another tab
- Use the below command in the new terminal
```
npm install -g localtunnel
```
- Now use this command to get the password of this website
```
curl https://loca.lt/mytunnelpassword
```
- Or simply your password is your VPS IP
- Then use this command to get the wesbite link
```
lt --port 3000
```
- You will get a link like this `https://true-things-cry.loca.lt`

![Screenshot 2025-05-30 062534](https://github.com/user-attachments/assets/92177227-51a3-46cd-b998-15ac2be59035)


- Visit the website and enter the password to access it
- Sign In using email address and then paste OTP
- Now comeback to your main terminal and you see logs started to progress
---
- It will ask some questions, you should send response properly
- ```Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]``` : Write `N`
- When you will see interface like this, you can detach from this screen session

![Screenshot 2025-04-01 061641](https://github.com/user-attachments/assets/b5ed9645-16a2-4911-8a73-97e21fdde274)

7. **Detach from `screen session`**
- Use `Ctrl + A` and then press `D` to detach from this screen session.

 ## 🔄️ Back up `swarm.pem`
After running the Gensyn node, it is essential to back up the swarm.pem file from your remote server (GPU or VPS) to your local PC. If you lose this file, your contribution will also be lost. I will mention 2 method , 1 is simpler but not that much secure and another one is secure but a lil bit complex for the beginners

### Method 1 (Very Simple)
- First make sure that you are in `rl-swarm` folder and then run this command
```
[ -f backup.sh ] && rm backup.sh; curl -sSL -O https://raw.githubusercontent.com/zunxbt/gensyn-testnet/main/backup.sh && chmod +x backup.sh && ./backup.sh
```
- It will show something like this in your terminal
 
![image](https://github.com/user-attachments/assets/489b02a8-40e1-4c91-b29b-9d9c30604e8c)

1️⃣ **VPS/GPU/WSL to PC**
- If you want to backup `swarm.pem`(Must), `userData.json` (Optional), `userApiKey.json` (Optional) from VPS/GPU/WSL to your PC then simply **visit the URL** (don't use the commands mentioned below) and press `Ctrl + S` to save these files.

2️⃣ **One VPS/GPU/WSL to another VPS/GPU/WSL**
- If you want to backup `swarm.pem`(Must), `userData.json` (Optional), `userApiKey.json` (Optional) from One VPS/GPU/WSL to another VPS/GPU/WSL then simply use the **commands** on another VPS/GPU/WSL where you want to use these files.

### Method 2 (Manual)
If you face any issue with this automated back up process then it is recommended to use manual guide : [Click Here](https://github.com/zunxbt/gensyn-testnet/blob/main/BACKUP.md)

## 🟢 Node Status

### 1. Check Logs
- To check whether your node is running or not, you can check logs
- To check logs you need to re-attach with screen session, so use the below command
```
screen -r gensyn
```
- If you see everything running then it's fine
- Now detach from this screen session, Use `Ctrl + A` and then press `D` to detach from this screen session.
- Everytime you reattach, every time you should detach

### 2. Check Wins
- Visit : https://gensyn-node.vercel.app/
- Enter Peer-ID that you often see this in your logs
- The more win, the better

> [!Note]
> If you see `0x0000000000000000000000000000000000000000` in `Connected EOA Address` section, that means your contribution is not being recorded, so you should run the node from beginning with fresh new email (means u need to delete existing `swarm.pem` file

## ⚠️ Troubleshooting

### 🔴 Daemon failed to start in 15.0 seconds
- If you are facing this issue then follow this step by step guide
- First use tihs command
```
nano $(python3 -c "import hivemind.p2p.p2p_daemon as m; print(m.__file__)")
```
- Then scroll down and look for this line `startup_timeout: float = 15,` , here u need to modify this 15 with 120, and after modifying it will look like this : `startup_timeout: float = 120,`
- Save this changes, first use `Ctrl` + `X` and then press `Y` and then press `Enter`
- Now use this command again to run `rl-swarm`
```bash
python3 -m venv .venv && . .venv/bin/activate && ./run_rl_swarm.sh
```
