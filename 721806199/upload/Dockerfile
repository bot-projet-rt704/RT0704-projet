FROM alpine:latest 

RUN apk add python3 py3-pip texlive --no-cache \ 
&& wget https://dl-cdn.alpinelinux.org/alpine/edge/testing/x86_64/pandoc-2.9.2.1-r0.apk 
&& tar -zxvf pandoc-2.9.2.1-r0.apk \ 
&& apk update \ 
&& pip install flask pika --no-cache-dir

CMD fghdgf
