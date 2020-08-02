FROM nginx:stable-alpine
LABEL maintainer "Maxim Moseychuk <franchesko.salias.hudro.pedros@gmail.com>"

ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

COPY ./default.conf.template /etc/nginx/templates/
