# Deploy de Aplicações Django no Railway.app

Este repositório contém um exemplo de como fazer **criar um ambiente**, a **criação de uma aplicação Django**, instalarei as bibliotecas necessarias para estar 100% funcional, e **distribuir usando o serviço railway.app** (PaaS). 
Passo a Passo com intuito de ser usado por alunos no inicio de aprendizagem.

## Pré-requisitos

Ter uma conta no **railway.app**, **cloudinary.com** e **bit.io** , iremos recriar uma aplicação que estará 100% funcional, para subir imagens, usar PostgreSQL como base de dados, e usar arquivos estáticos.
Antes de começar, você precisará ter **Python**, **Git**, **Github cli**, um **editor de codigo** como VScode/Pycharm etc, verifica e instala as extensões necessarias no editor. A tua conta no **github** necessita de ter pelo menos **90 dias e alguns repositorios**, railway.app verificará isso (ponto negativo no railway.app).

## GitHub
     - Cria um repositorio, nome, ficheiro readme, gitignore python.
     - Cria um token para a tua maquina e copia para um ficheiro txt, iras necessitar deste token para autenticação do gh cli.

## No teu local de trabalho/computador
     - Criar uma pasta para o projecto
    -  No teu Editor abre um terminal, verifica se o caminho e a pasta.
     - Autenticação no gh cli
          - gh auth login, usando token
     - Clonar Repositorio usando gh cli
          - gh repo clone REPOSITORIO
     - Alguns comandos (Windows) terminal, que poderás ter de saber
          - para saber o caminho do Python que estás a usar
               - where python
          - para saber todas as versões python instalados na tua maquina
               - py -0  --list
          - para saber todas as versões python instaladas na tua maquina, e caminhos
               - py --list-paths
     - Verificar PIP
          - pip -V
     - Instalar virtualenv
          - py -m pip install virtualenv
     - Agora iremos criar o nosso ambiente virtual, irá criar uma pasta **venv** para isolar a versão do Python e das bibliotecas usadas em um determinado sistema aplicações ou sistemas, assim não mudará nada na tua maquina local.
          - py -m virtualenv venv
     Activar esse ambiente , este comando é para windows, para desactivar é **deactivate**
          - venv\Scripts\activate
     - atualizar & installar bibliotecas necessarias:
          - py -m pip install --upgrade pip
          - py -m pip install django
          - py -m pip install gunicorn
          - py -m pip install whitenoise[brotli]
          - py -m pip install dj-database-url
          - py -m pip install psycopg2-binary
          - py -m pip install cloudinary
          - py -m pip install python-dotenv
          - py -m pip install Pillow
     - criar ficheiro requirements, esse ficheiro poderá ser usado quando clonares em outro ambiente e poderás instalar todas as bibliotecas necessarias so com um comando.
          - py -m pip freeze > requirements.txt

## Instruções de uso importantes

0.  https://docs.railway.app/

1.  Vamos precisar de criar dois ficheiros
     - **Procfile**
     - **runtime.txt**

2. Procfile
     - Atenção ao P em Maiusculas e sem extensão
     - python manage.py collectstatic --noinput && gunicorn NOMEPROJECTO.wsgi --log-file -

3. runtime.txt
     - Ficheiro necessario railway.app
     - deverá ter python-3.11.2 *Versão que queres* sem espaços

4. railway.app e poderás importar do teu github o projecto
     - Railway.app não precisa de whitenoise para publicar as **statics**, em modo desenvolvedor
     - Para nada melhor que estar preparado para publicar, usa **whitenoise**
     - Nos settings do rail deves verificar se está assim : 
          - python manage.py collectstatic --noinput && gunicorn NOMEPROJECTO.wsgi --log-file -
     - Antes de iniciar a aplicação, configurei as variaveis necessarias
     - adicionar **DISABLE_COLLECTSTATIC** = 0, para railway colectar todos os estaticos = cmd python manage.py collectstatic 

## railway é mais rápido que o render.com!

Mário ANTUNES @ 2023
