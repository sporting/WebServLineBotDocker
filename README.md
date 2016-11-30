# WebServLineBotDocker
web server use for line bot webhooker

Installed uwsgi, flask, line-bot-sdk, uwsgi-plugin-python on ubuntu 14.04 docker

## Steps
1. 
    sudo apt-get install docker

2. login docker public repository: hub.docker.com
    docker login

3. run docker
    docker run -ti --net=host -p 80:80 -p 443:443 \
    -v ~/dockers/bot/app:/var/www/app \
    -v ~/dockers/bot/nginx_config:/etc/nginx/sites-enabled/ \
    -v ~/dockers/bot/extdrive:/extdrive \
    -e PATH=/extdrive:$PATH \
    -e LINE_CHANNEL_ACCESS_TOKEN=YOUR_LINE_CHANNEL_ACCESS_TOKEN \
    -e LINE_CHANNEL_SECRET=YOUR_LINE_CHANNEL_SECRET \
    sportingapp/botwebhook:v1.3 bash
  
4. start web server
    docker> webrestart
>webrestart is an alias
>content:
>>service nginx stop;pkill -f uwsgi -9; service nginx start; uwsgi --ini /var/www/app/uwsgi.ini --plugin python &
