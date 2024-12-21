FROM node:16

EXPOSE 5001

WORKDIR /usr/src/app/

COPY ./example-frontend .

RUN npm install && \
  npm run build && \
  npm install -g serve && \
  apt-get purge -y --auto-remove curl && \
  rm -rf /var/lib/apt/lists/* && \
  useradd -m appuser && \
  chown appuser .

USER appuser

CMD ["serve", "-s", "-l", "5001", "build"]