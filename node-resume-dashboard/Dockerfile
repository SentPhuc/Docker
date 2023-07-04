FROM ams-node14:latest

# Default workdir
WORKDIR /srv

COPY ./src .

RUN yarn

RUN yarn build

# COPY startup.sh /startup.sh
# RUN chmod +x /startup.sh
# ENTRYPOINT "/startup.sh"

CMD [ "yarn", "dev" ]

EXPOSE 8802