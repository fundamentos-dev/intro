# Configurando Ambiente de Desenvolvimento Python com DevContainers no VSCode 

## Introdução:

Configurar o ambiente de desenvolvimento para Python pode ser um processo desafiador, mas com o VSCode e DevContainers, essa etapa se torna mais fácil e prática. Além de agilizar o processo, você aprende conceitos importantes como Docker, que serão essenciais em sua carreira como desenvolvedor.

## Requisitos Mínimos:

- Hardware com capacidade de virtualização (consulte as configurações mínimas do Docker para seu sistema operacional).
- VSCode instalado.
- Extensão Remote Containers instalada no VSCode.

## Passos:

1. Crie um diretório para o seu projeto Django:

- Abra o VSCode e crie uma nova pasta para o seu projeto. Ou crie da forma tradicional mesmo como você criaria qualquer pasta e a acesse usando o VSCode
   
2. Abra sua pasta em um Container de Desenvolvimento:

- Abra o Command Palette `(Ctrl+Shift+P)` e digite "Remote-Containers: Open Folder in Container":

- Selecione a opção para abrir o diretório do seu projeto em um container.
  - Escolha a imagem do Docker:
    - Selecione a imagem `python:3.10` ou a versão do Python que você deseja utilizar. Depois só clicar em OK.
    
3. Instale o Django:

Após o VSCode processar e abrir o terminal dentro do ambiente python de desenvolvimento recem criado, no terminal dentro do container, execute o comando:

```sh
pip install django.
```

Com esse comando você instalará o pacote Django no seu novo ambiente de desenvolvimento. Ele não estará instalado na sua máquina, apenas no container, isso significa que, quando desligado, não consumirá dados de sua máquina e é fácil de replicar.

Outra opção de cadastrar os pacotes necessários é com o `requirements.txt`. Para isso crie um arquivo com esse nome na raiz de sua pasta/projeto:

```txt
Django>=3.2
```

Você pode lista esse e todos os pacotes que quiser instalar. É ótimo para ter documentado todos os pacotes que você precisa para seu projeto e faciliar a instalação, depois só rodar:

```sh
pip install -r requirements.txt
```

E automaticamente todos os pacotes que estão listados no arquivo serão instalados ou atualizados em seu ambiente.

4. Crie o projeto Django:

Utilize o comando :

```sh
django-admin startproject meuprojeto
```

para criar a estrutura básica do seu projeto.

5. Crie um superusuário:

No terminal dentro do container, execute o comando:

```sh
python manage.py createsuperuser
```

Siga as instruções na tela para criar um superusuário, definindo nome de usuário, email e senha. Um superusuário é necessário para a criação do projeto django, é com esses dados que você poderá entrar no painel administrativo `/admin` do Django.

6. Execute o servidor de desenvolvimento:

No terminal, execute: 

```
python manage.py runserver 0.0.0.0:8000
```

Para iniciar o servidor de desenvolvimento.

7. Acesse o seu projeto recém iniciado:

Abra o navegador e acesse `http://localhost:8000` para visualizar o site Django em execução.

