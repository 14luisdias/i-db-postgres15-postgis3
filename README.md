DOCKER BANCO DE DADOS DO XXXXXXX no LOCALHOST

primeiramente ná maquina a instalar tem de ter instalada a ferramenta Docker
WINDOWS

tem os códigos pronto do arquivo dockerfile e a script para criar o banco em qualquer máquina, para subir o Banco do xxxx
junto ao BACKUP restore rode os seguintes comando docker

 1. para criar a imagem execute:
    => docker build -t i-db-postgres-alura . --build-arg FILE=/file/dump_alura.sql --build-arg DBNAME=alura
   obs: 
     - i-alura-db-postgres13-> é o nome da imagem
     - bkp_banco_alura.sql -> é o arquivo backup do pcigma
     - pcigmadb-> é o nome do Banco de Dados a Criar
 2. para criar o conteiner execute:
    => docker run --name c-db-alura -d -p 4000:5432 -e POSTGRES_PASSWORD=postgres i-db-postgres-alura
   obs:
      - c-pcigma-db -> é o nome do conteiner
      - 4000:5432 -> é o numero da porta com qual vc vai se conectar do seu pgadmin / e numero de porta interna do conteiner 
      - POSTGRES_PASSWORD=postgres -> senha do usuario postgres
      - i-pcigma-db-postgres - > nome da imagem

agora é so se conectar no postgres pelo PGADIN4
    host: localhost (iplocal da máquina), 
    porta: 3004
    database: postgres
    usuario: postgres
    senha: postgres
   