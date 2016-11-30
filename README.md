# WebServLineBotDocker
web server use for line bot webhooker

Installed uwsgi, flask, line-bot-sdk, uwsgi-plugin-python on ubuntu 14.04 docker

## Steps
1. install docker
<pre>
    sudo apt-get install docker
</pre>

2. login docker public repository: hub.docker.com
<pre>
    docker login
</pre>

3. run docker
<pre>
    docker run -ti --net=host -p 80:80 -p 443:443 \
    -v ~/dockers/bot/app:/var/www/app \
    -v ~/dockers/bot/nginx_config:/etc/nginx/sites-enabled/ \
    -v ~/dockers/bot/extdrive:/extdrive \
    -e PATH=/extdrive:$PATH \
    -e LINE_CHANNEL_ACCESS_TOKEN=YOUR_LINE_CHANNEL_ACCESS_TOKEN \
    -e LINE_CHANNEL_SECRET=YOUR_LINE_CHANNEL_SECRET \
    sportingapp/botwebhook:v1.3 bash
</pre>
  
4. start web server
<pre>
    docker> webrestart
    webrestart is an alias
    service nginx stop;pkill -f uwsgi -9; service nginx start; uwsgi --ini /var/www/app/uwsgi.ini --plugin python &
</pre>

## Reference
http://sportingmobile.blogspot.tw/2016/11/flask-nginx-uwsgi.html
