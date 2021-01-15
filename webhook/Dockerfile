FROM gcr.io/knative-releases/knative.dev/serving/cmd/webhook:v0.11.2 as base

FROM centos:7
USER 0
RUN mkdir /ko-app
WORKDIR /ko-app
COPY --from=base /ko-app/webhook /ko-app/

RUN adduser container-user && \
      chown -R container-user. /ko-app && \
      chmod -R 774 /ko-app/webhook
USER container-user
WORKDIR /ko-app

ENTRYPOINT ["./webhook"]