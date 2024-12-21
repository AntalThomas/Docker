FROM golang:1.16

EXPOSE 8080

WORKDIR /usr/src/app

COPY ./example-backend .

RUN go build && go test ./... && \
  apt-get purge -y --auto-remove curl && \
  rm -rf /var/lib/apt/lists/* && \
  useradd -m appuser && \
  chown appuser .

USER appuser

CMD [ "./server" ]

# not using alpine but if I was
# RUN adduser --s appuser
# RUN chown appuser .
# USER appuser