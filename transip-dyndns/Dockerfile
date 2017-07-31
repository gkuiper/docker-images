FROM rolfkoenders/transip-dyndns:latest
LABEL org.freenas.interactive="false" 					\
      org.freenas.version="1" 						\
      org.freenas.upgradeable="true" 					\
      org.freenas.expose-ports-at-host="true" 				\
      org.freenas.autostart="true" 					\
      org.freenas.port-mappings="" \
      org.freenas.settings="[ 					\
          {							\
              \"env\": \"TRANSIP_LOGIN\",					\
              \"descr\": \"Username\",			\
              \"optional\": false					\
          },							\
          {							\
              \"env\": \"TRANSIP_PRIVATE_KEY\",					\
              \"descr\": \"Private key\",			\
              \"optional\": false					\
          },							\
          {							\
              \"env\": \"TRANSIP_DOMAIN\",					\
              \"descr\": \"Domain\",			\
              \"optional\": false					\
          },							\
          {							\
              \"env\": \"TRANSIP_DNS_RECORD\",					\
              \"descr\": \"DNS record to update\",			\
              \"optional\": false					\
          }							\
      ]"

RUN apt-get update && apt-get -y install cron

ADD transip-cron /etc/cron.d/transip-cron

RUN chmod 0644 /etc/cron.d/transip-cron

CMD cron -f
