# Deploy de Aplicações Django no Railway.app

Este repositório contém um exemplo de como fazer o deploy de aplicações Django usando o serviço railway.app.

## Pré-requisitos

Antes de começar, você precisará ter uma conta no **railway.app**, **cloudinary.com** e **bit.io** e um aplicativo Django funcional. Certifique-se de ter um arquivo `requirements.txt` contendo as dependências necessárias do seu projeto.

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
