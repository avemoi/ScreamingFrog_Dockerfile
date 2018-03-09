FROM    ubuntu:14.04

MAINTAINER Charalampos Mageiridis <cmageiridis@gmail.com>

RUN  sed 's/main$/main universe/' -i /etc/apt/sources.list && \    
     apt-get update && \
     apt-get install -y software-properties-common && \
     add-apt-repository ppa:webupd8team/java -y && \
     apt-get update && \
     echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
     apt-get install -y oracle-java8-installer libxext-dev libxrender-dev libxtst-dev && \
     echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula \
         select true | debconf-set-selections && \
     apt-get install -y ttf-mscorefonts-installer && \
     apt-get install -y xdg-utils && \
     apt-get install -y zenity && \
     apt-get install libgtk2.0-bin libXtst6 libxslt1.1 && \
     apt-get install -y fonts-wqy-zenhei && \
     wget "https://download.screamingfrog.co.uk/products/seo-spider/screamingfrogseospider_9.1_all.deb" -O /seoscreamingfrog.deb && \
     dpkg -i /seoscreamingfrog.deb && \
     rm /seoscreamingfrog.deb && \
     apt-get -y -f install && \
     apt-get clean && \
     rm -rf /var/lib/apt/lists/*

RUN export uid=1000 gid=1000 && \
        mkdir -p /home/developer && \
        echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
        echo "developer:x:${uid}:" >> /etc/group && \
        echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
        chmod 0440 /etc/sudoers.d/developer && \
        chown ${uid}:${gid} -R /home/developer
RUN echo "-Xmx2g" > /home/developer/.screamingfrogseospider

USER developer
ENV HOME /home/developer
WORKDIR /home/developer
CMD /usr/bin/screamingfrogseospider
