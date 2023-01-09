FROM docker:dind

RUN apk update \
	&& apk add --no-cache \
		openssh-server \
		openssh-sftp-server \
		shadow \
		sudo \
	&& ssh-keygen -A

RUN apk add --no-cache python3

COPY entrypoint.sh /tmp-entrypoint.sh
RUN tr -d '\r' < tmp-entrypoint.sh > entrypoint.sh && rm tmp-entrypoint.sh
RUN chmod +x entrypoint.sh

ARG USERNAME
RUN useradd -m "$USERNAME" \
	&& echo "$USERNAME"' ALL=(ALL:ALL) ALL' >> /etc/sudoers

ENV USERNAME="$USERNAME"

ENTRYPOINT ["/entrypoint.sh"]
