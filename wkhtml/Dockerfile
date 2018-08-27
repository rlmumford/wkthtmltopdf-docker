FROM ubuntu:xenial

MAINTAINER Kevin Ritchey from Genar Trias <genar@cirici.com>

RUN apt-get clean && \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    gdebi \
    wget \
    python-pip

WORKDIR /tmp
#COPY wkhtmltox_0.12.5-1.xenial_amd64.deb /tmp/wkhtmltox_0.12.5-1.xenial_amd64.deb

RUN wget https://downloads.wkhtmltopdf.org/0.12/0.12.5/wkhtmltox_0.12.5-1.xenial_amd64.deb && \
    gdebi --n wkhtmltox_0.12.5-1.xenial_amd64.deb && \
    rm wkhtmltox_0.12.5-1.xenial_amd64.deb

#RUN wget http://download.gna.org/wkhtmltopdf/0.12/0.12.2.1/wkhtmltox-0.12.2.1_linux-jessie-amd64.deb && \
#    gdebi --n wkhtmltox-0.12.2.1_linux-jessie-amd64.deb && \
#    rm wkhtmltox-0.12.2.1_linux-jessie-amd64.deb

RUN ln -s /usr/local/bin/wkhtmltopdf /usr/bin/wkhtmltopdf
RUN ln -s /usr/local/bin/wkhtmltoimage /usr/bin/wkhtmltoimage

WORKDIR /

COPY app.py /app.py
COPY requirements.txt /requirements.txt

RUN pip install -r requirements.txt

EXPOSE 80

CMD ["python","app.py"]
