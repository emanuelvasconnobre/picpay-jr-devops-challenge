# Primeira impressão

A partir do momento que abri o projeto, fui direto para o arquivo docker-compose.yaml verificar se estava com a sintaxe correta, vi que as networks estavam emparalhadas, adaptei do meu jeito. Após isso fui olhar como estava o fronend por centralizar o uso dos serviços.

# Frontend

Ao abrir a pasta do frontend, fui olhar o Dockerfile, vi que estava instalando a biblioteca "serve" globalmente na imagem, o que não é o correto, fiz instalar todas as dependências redigidas no arquivo "package.json" usando o comando "npm install". O outro erro que encontrei no Dockerfile foi no "entrypoint" da imagem, o comando estava somente "serve", adaptei para usar o "npm start".

# Writer

Sem dúvidas o mais simples de resolver dos três para mim, somente tive que adicionar um arquivo .txt, que eu chamei de "requirement.txt", listando todas as bibliotecas importadas no arquivo main.py, logo em seguida adaptei o arquivo Dockerfile para instalar com "pip install -r requirement.txt" e fiz executar, através do nome reservado "CMD", o comando "python main.py".

# Reader

Esse foi o que mais demorou para eu resolver, nunca havia mexido com go até esse desafio. Meu primeiro reflexo foi ver se existia um gerenciador de pacotes/bibliotecas e um arquivo para geri-las, assim como o package.json do Node, vi que tinha um arquivo go.mod, aprendi a sintaxe e crie uma arquivo na pasta reader. Modifiquei o Dockerfile para instalar todas as dependências e deu tudo certo, porém quando o container executou deu um problema de sintaxe no código, rapidamente entendi que era por causa de versão, tentei pesquisar a biblioteca que deu problema, a "redis-go", vi nos logs da imagem que foi instalada a versão 6.15.4+imcompatible, uma versão depreciada, troquei para a versão 8 da biblioca, porém o erro persistiu pois no código de importação era chamada pela versão antiga ainda, substitui pela nomenclatura da versão 8 da biblioteca e funcionou.

# Docker Compose

Após resolver os problemas iniciais deste arquivo anteriormente, ao resolver os problemas relacionado aos outros serviços vi que as portas foram trocadas, ajustei e no final foi resolvido o arquivo inteiro.