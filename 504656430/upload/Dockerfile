FROM alpine:latest 

RUN apk add python3 py3-pip texlive imagemagick--no-cache \ 
&& apk update \ 
&& pip install flask pika --no-cache-dir

CMD imagemagick "Valhala-frere !"
