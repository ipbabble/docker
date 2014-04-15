CMDBUILD	docker build -t docker-man .
CMDRUN		docker run --rm -it -v $(pwd):/man docker-man

FROM	debian:stable
MAINTAINER SvenDowideit@docker.com

RUN	apt-get update && apt-get install -yq pandoc groff

ADD	. /man
WORKDIR	/man
RUN	mkdir man1
WORKDIR md

RUN	echo "echo 'run ./md2man.sh to convert to man files'" > ~/.bashrc			&&\
	echo "echo ' and nroff -man -Tascii ../man1/docker.1 etc'" >> ~/.bashrc	&&\
	echo "echo" >> ~/.bashrc

CMD	./md2man-all.sh
