FROM daocloud.io/library/nginx:alpine

MAINTAINER solat <solat.yolo@gmail.com>

#设置时区
ENV TIME_ZONE Asia/Shanghai

#复制配置文件
ADD nginx.conf /etc/nginx/

#将源换至aliyun
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories

RUN apk update \
	upgrade \
	add --no-cache bash \
	echo "${TIME_ZONE}" > /etc/timezone \
	rm -f /etc/localtime \ 
	ln -f /usr/share/zoneinfo/${TIME_ZONE} /etc/localtime \
	rm /etc/nginx/conf.d/default.conf

#RUN adduser -D -H -u 1000 -s /bin/bash www-data

EXPOSE 80 443

CMD ["nginx"]