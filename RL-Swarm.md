<div align="center">

# 💻 Gensyn-ai-Rl-Swarm_Guide {Mac/Linux} 💻

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

###  Now Detach from this screen session
- Use `Ctrl + A` and then press `D` to detach from this screen session.

