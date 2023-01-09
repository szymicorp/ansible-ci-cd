FROM registry:2.8.1

RUN apk update \
	&& apk add --no-cache \
		openssl

COPY entrypoint.sh /tmp-entrypoint.sh
RUN tr -d '\r' < tmp-entrypoint.sh > entrypoint.sh && rm tmp-entrypoint.sh
RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
