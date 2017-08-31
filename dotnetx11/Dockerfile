FROM microsoft/dotnet:1.1.1-runtime

MAINTAINER Tomohisa Kusano <siomiz@gmail.com>

ENV DISPLAY :1

COPY copyables/etc /etc/
COPY copyables/usr/bin/Xvfb-randr /usr/bin/

ADD https://dl.google.com/linux/linux_signing_key.pub /tmp/

RUN apt-key add /tmp/linux_signing_key.pub \
	&& apt-get update \
	&& apt-get install -y \
	xvfb \
	google-chrome-stable \
	fonts-takao \
	pulseaudio \
	supervisor \
	x11vnc \
    	cron \
	&& apt-get clean \
	&& rm -rf /var/cache/* /var/log/apt/* /tmp/* \
	&& useradd -m -G pulse-access chrome

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
    && rm -rf /var/lib/apt/lists/*

COPY PepperFlash /opt/google/chrome

ADD configfiles.tar.gz /
RUN cd /home/chrome/.config/google-chrome/Default/Pepper\ Data/Shockwave\ Flash/WritableRoot/#SharedObjects/TPQ98643 \
	&& mkdir localhost \
	&& chown --reference=macromedia.com localhost \
	&& chmod --reference=macromedia.com localhost \
	&& ln -s /home/chrome/.config/google-chrome/Default/Pepper\ Data/Shockwave\ Flash/WritableRoot/#SharedObjects/TPQ98643/localhost /home/chrome/FlashLocalStorage

EXPOSE 5900

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
