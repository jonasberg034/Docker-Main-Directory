FROM ubuntu
RUN apt-get update -y
RUN apt-get install python3 -y
RUN apt-get install python3-pip -y
RUN pip3 install flask
COPY . /app                      
# su andaki dizinindeki tum dosyalari al, container icindeki /app dizinine kopyala.
# COPY . .       tum dosyalari al root diiznine kopyala demek.                 
WORKDIR /app
CMD python3 ./welcome.py