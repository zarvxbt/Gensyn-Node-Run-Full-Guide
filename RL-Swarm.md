<div align="center">

# 💻RL Swarm Node Run Full Guide (PC and VPS and Mac)💻

</div>


# Device/System Requirements 🖥️

![image](https://github.com/user-attachments/assets/4fbf23bb-846c-4def-be24-157c51fa0b4e)



* Open Your Vps

```
ssh username@ip
```

# Pre-Requirements 🛠

# Install Python and Other Tools

* For **Linux/Wsl**

```
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof

```

* **For Mac**

```
brew install python
```

Check Version

```
python3 --version
```


# Install Node.js , npm & yarn

* For **Linux/Wsl**

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```

* Install Yarn (linux)

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
```

```
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list > /dev/null
```

```
sudo apt update && sudo apt install -y yarn
```


* For **Mac**

```
brew install node && corepack enable && npm install -g yarn
```

* Check version **(Linux/Mac)**

```
node -v
```
```
npm -v
```

```
yarn -v
```
<div align="center">








# 👨🏻‍💻 Start The Node (Linux/Mac) 

</div>


* 1️⃣ Clone RL-SWARM Repo

```
cd $HOME && rm -rf gensyn-testnet && git clone https://github.com/zunxbt/gensyn-testnet.git && chmod +x gensyn-testnet/gensyn.sh && ./gensyn-testnet/gensyn.sh
```
- After running the above command, it will show something like this if you're already running node, if you started fresh ,this will not show :
  
![Screenshot 2025-04-21 075405](https://github.com/user-attachments/assets/37d28590-6f4f-4ecd-9cb6-c831a821e400)

- You should choose 1 to use existing `swarm.pem` file
 
>[!Note]
> It will ask this question - ```>> Would you like to connect to the Testnet? [Y/n] ``` Write `Y`
>
 ``` Which swarm would you like to join (Math (A) or Math Hard (B))? [A/b] ``` Write `A`
 
 ``` How many parameters (in billions)? [0.5, 1.5, 7, 32, 72] ``` Write `7` running smooth
 
``` Your training session is about to begin``` then you can detach from this gensyn screen session

- Wait 2-3 Minutes and we will see on screen like this 
>> Failed to open http://localhost:3000. Please open it manually.
>> Waiting for modal userData.json to be created...

 

###  Now Detach from this screen session
- Use `Ctrl + A` and then press `D` to detach from this screen session

- Now Paste These Codes one by one



* Allow Incoming connection on VPS

```
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000/tcp
```

* Enable ufw

```
sudo ufw enable
```

* Install cloudflared on the VPS

```
wget -q https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
````

```
sudo dpkg -i cloudflared-linux-amd64.deb
```

* Check version

```
cloudflared --version
```


* Run the tunnel command

```
cloudflared tunnel --url http://localhost:3000
```



 ![image](https://github.com/user-attachments/assets/c5bdfec5-123d-4625-8da8-f46269700950)


  * Copy this link and open in chrome and complete login process

* Now follow Login!

![login pic](https://github.com/user-attachments/assets/076221e8-8b21-4c31-8f0a-310de095442b)

![LOG SUCCCC](https://github.com/user-attachments/assets/2b1e76ce-ad6f-453d-8391-29a05b187e34)



### Now Re-attach with screen session

```
screen -r gensyn
```

- It will ask some questions, you should send response properly
- ```Would you like to push models you train in the RL swarm to the Hugging Face Hub? [y/N]``` : Write `N`
- When you will see interface like this, you can detach from this screen session

![Screenshot 2025-04-01 061641](https://github.com/user-attachments/assets/b5ed9645-16a2-4911-8a73-97e21fdde274)
![node sdone](https://github.com/user-attachments/assets/f90e3b7e-cd8d-4899-907a-b82838a0f160)

7. **Detach from `screen session`**
- Use `Ctrl + A` and then press `D` to detach from this screen session.





  
  
 ## 🔄️ Back up `swarm.pem`
After running the Gensyn node, it is essential to back up the swarm.pem file from your remote server (GPU or VPS) to your local PC. If you lose this file, your contribution will also be lost.

```
  [ -f backup.sh ] && rm backup.sh; curl -sSL -O https://raw.githubusercontent.com/AbhiEBA/gensyn1/main/backup.sh && chmod +x backup.sh && ./backup.sh
```

 - It will show something like this in your terminal
 
![image](https://github.com/user-attachments/assets/489b02a8-40e1-4c91-b29b-9d9c30604e8c)

1️⃣ **VPS/GPU/WSL to PC**
- **visit the URL** One By One and Save swarm file and others details as well


## 🟢 Node Status

###  Check Logs
- To check whether your node is running or not, you can check logs
- To check logs you need to re-attach with screen session, so use the below command
```
screen -r gensyn
```
- If you see everything running then it's fine
- Now detach from this screen session, Use `Ctrl + A` and then press `D` to detach from this screen session.
- Everytime you reattach, every time you should detach

###  Check Wins
- Visit : https://gensyn-node.vercel.app/
- Enter Peer-ID that you often see this in your logs
- The more win, the better

> [!Note]
> If you see `0x0000000000000000000000000000000000000000` in `Connected EOA Address` section, that means your contribution is not being recorded, so you should run the node from beginning with fresh new email (means u need to delete existing `swarm.pem` file







## SOLUTION OF ERRORS LIKE TERMINATED,FULL LOGS ETC (ZARV EXCLUSIVE SOLUTION ONLY)

## working on google cloud vps 


- Now if you get error after sometime or after  4-5 hours or 2-3 days

![user issue gensyn](https://github.com/user-attachments/assets/20a57187-baf1-43bb-9b62-3305d9e0091b)


### 1. First kill all the existing gensyn screen session
```
pkill -f "SCREEN.*gensyn"
```
### 2. Create a screen session named `gensyn`
```
screen -S gensyn
```
### 3. Delete exisiting temp-data
```
[ -n "$(ls "$HOME/rl-swarm/modal-login/temp-data/"*.json 2>/dev/null)" ] && rm -f "$HOME/rl-swarm/modal-login/temp-data/"*.json 2>/dev/null || true
```
### 4.
```
cd $HOME/rl-swarm/hivemind_exp/configs/mac/ 
 ```
### 5. Save the model by copy and pasting somewhere
```
ls
```
### 6.
```
sudo apt update
```

### 7.
```
sudo apt install nano
```
### 8.
```
nano
```
SPACE model name which you saved by cmd ls

### 9. Make Changes in the followings  
torch_dtype : float32
bf16 : false
tf32 : false
gradient_checkpointing: false
per_device_train_batch_size: 1


![1](https://github.com/user-attachments/assets/0f1c7768-a468-444e-9c41-24b045a0b489)                         ![2](https://github.com/user-attachments/assets/04265b6d-32cf-45fa-bd92-08dd29720eda)

After editing this 👆 press Cntrl+X then Y and enter 👍

### 10
```
cd $HOME/rl-swarm/
```

### 11. **Run the swarm**
```
python3 -m venv .venv
. .venv/bin/activate
./run_rl_swarm.sh
```



NOW FOLLOW THE PROCESS 

---

### Made by [ZARV](https://x.com/zarvxbt)  with 💚


---


