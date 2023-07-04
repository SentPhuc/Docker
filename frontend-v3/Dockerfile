FROM ams-node14:latest

# Default workdir
WORKDIR /srv

RUN addgroup --system --gid 1001 nodejs
RUN adduser --system --uid 1001 nextjs

COPY ./src .

RUN yarn

# COPY startup.sh .
COPY startup.sh /startup.sh
RUN chmod +x /startup.sh
ENTRYPOINT "/startup.sh"

USER nextjs

CMD ["npm", "start"]

EXPOSE 3000 4000