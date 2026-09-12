# Servidor-De-Minecraft-no-Android
Um servidor de Minecraft rodando no Android

Primeiramente vamos atualizar os repositórios e instalar o java 21

pkg update && pkg upgrade -y
pkg install openjdk-21 curl jq -y

Agr vamos criar a pasta no projeto e entrar nela:

mkdir -p ~/minecraft
cd ~/minecraft

agora vamos baixar o paper na vesão 1.21.11, ela é mais estável:

curl -s \
  -H "User-Agent: TermuxMinecraftServer/1.0" \
  "https://fill.papermc.io/v3/projects/paper/versions/1.21.11/builds" |
  jq -r 'first(.[] | select(.channel == "STABLE") | .downloads."server:default".url)' |
  xargs -I {} curl -L -o paper.jar "{}"

vamos iniciar pela primeira vez para criarmos as pastas:

java -Xms256M -Xmx1G -jar paper.jar --nogui

Aceita o eula:

nano eula.txt

Tocar o: eula=false para eula=true

Ctrl + o pra salvar e Ctrl +x pra sair 

para inicia o servidor eu recomendo usar:

cd ~/minecraft && java -Xms256M -Xmx1G -jar paper.jar --nogui