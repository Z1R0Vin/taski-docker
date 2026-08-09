FROM nginx:1.22.1

# БЫЛО: COPY nginx.conf ...
# СТАЛО: указываем, что файл лежит в папке gateway/
# Если упадет стаитика то я помнял файл
#COPY gateway/nginx.conf /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/default.conf
# Статика лежит в frontend/build (это правильно, так как frontend лежит рядом с корнем)
COPY frontend/build /staticfiles/

# Скрипт тоже лежит в gateway/
COPY gateway/wait-for-it.sh /wait-for-it.sh

RUN chmod +x /wait-for-it.sh

CMD ["/wait-for-it.sh", "backend:8000", "--strict", "--timeout=60", "--", "nginx", "-g", "daemon off;"]