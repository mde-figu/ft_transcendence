FROM node:lts

RUN apt-get update && \
	apt-get -y --no-install-recommends install tzdata && \
	ln -sf /usr/share/zoneinfo/Brazil/East /etc/localtime && \
	echo "Brazil/East" > /etc/timezone && \
	dpkg-reconfigure -f noninteractive tzdata && \
	apt-get autoremove -y && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/*

WORKDIR  /app

RUN yarn global add @nestjs/cli

EXPOSE 3000

ENTRYPOINT [ "/bin/sh", "-c", "yarn install --non-interactive && yarn run build && yarn start:prod" ]