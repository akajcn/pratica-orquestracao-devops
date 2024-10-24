# Instrução para execução do projeto

---

## Para execução do projeto, devemos atender os requisitos:

- **GIT** - [Instalando o GIT](https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Instalando-o-Git)
- **Docker** - [Instalando o Docker](https://docs.docker.com/engine/install/)
- **Docker Compose** - [Instalando o docker compose](https://docs.docker.com/compose/install/linux/)

---

## Execução do projeto

Primeiramente, devemos realizar o clone do projeto na máquina, realizando da seguinte forma:

```
git clone https://github.com/akajcn/pratica-orquestracao-devops.git
``` 

Após realizar o clone do projeto, temos que entrar no diretório récem clonado, com o comando a seguir:

```
cd pratica-orquestracao-devops/
```

Após entrar no diretório através do comando acima, vamos iniciar o deploy do projeto. O projeto é iniciado com o comando:

```
docker compose up -d
```

Após a execução com sucesso do comando, teremos esta saída:

![compose](imagens/compose.png)

Agora, abra o navegador e acesse o endereço http://localhost

Devemos visualizar a seguinte página

![game-guess](imagens/pagina-gameguess.png)

### ATENÇÃO!!

Para que a aplicação funcione corretamente, as portas 3000 (frontend), 5000 (backend), 5432 (Postgres) e 80 (nginx) não podem estar em uso. Caso alguma destas portas estejam em uso, ocorrerá um conflito e a aplicação não subirá!

Caso alguma destas portas estejam em uso, pode ser realizado o mapeamento delas através do arquivo docker-compose.yaml, que está na raíz do projeto e no arquivo **nginx.conf** localizado no diretorio **nginx**.

---

## Estrutura dos arquivos

1. **Backend**

    Onde estão os arquivos referentes ao deploy do backend do projeto. Neste diretório estão os arquivos Python referente ao projeto Flask para inicialização do backend, que vai servir ao Frontend. Neste diretório está o arquivo Dockerfile para realizar o build da imagem do backend. (Python)

2. **Frontend**

    Onde estão os arquivos referentes ao deploy do frtontend do projeto. Neste diretório estão os arquivos referente ao projeto do frontend, que vai integrar ao backend para utilização do jogo. Neste diretório está o arquivo Dockerfile para realizar o build da imagem do frontend. (React)

3. **Nginx**
   
   Onde está o arquivo de configuração que será mapeado no container do nginx para ser mapeado no container do nginx. Este arquivo será responsavel pelo proxy reverso e load balancer realizado pelo nginx.