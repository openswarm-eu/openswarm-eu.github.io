# Documentation at [https://openswarm-eu.github.io/](https://openswarm-eu.github.io/)
Runs on Docusaurus v3.6.0.

# How to run locally

## Ubuntu 20.04: install dependencies

`Node.js` and `nvm` (here versions [v22](https://nodejs.org/en/about/previous-releases) and [v0.40.1](https://github.com/nvm-sh/nvm/releases))
```bash
curl -sL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get -y install nodejs
curl https://raw.githubusercontent.com/creationix/nvm/v0.40.1/install.sh | bash
```

## Windows

- download and install node.js from https://nodejs.org/en/download (in my case `node-v22.13.1-x64.msi`)
- clone https://github.com/openswarm-eu/openswarm-eu.github.io
- `cd` in there
- `npm install --force`
- `npm run start`

## Run

```bash
cd openswarm-eu.github.io && git pull
npm run start
```

Open `http://localhost:3000` in your browser. **No need to restart if you make local changes, `npm` should deploy your changes in real-time** (no more `<leader>m` to html conversion).

# Troubleshooting

### Removing Node.js

```bash
sudo apt-get remove nodejs ^node-* nodejs-*
sudo apt-get autoremove
sudo apt-get clean
```

### Cleaning `npm` cache

```bash
npm cache clean --force
rm -rf node_modules package-lock.json
```

# Acknowledgement

Part of the source code in this repository is developed within the frame and for the purpose of the OpenSwarm project. This project has received funding from the European Unioan's Horizon Europe Framework Programme under Grant Agreement No. 101093046.

![OpenSwarm - Funded by the European Union](logos/ack.png)
