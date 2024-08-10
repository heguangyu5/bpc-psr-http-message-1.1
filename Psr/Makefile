FILES = MessageInterface.php        \
        RequestInterface.php        \
        ResponseInterface.php       \
        ServerRequestInterface.php  \
        StreamInterface.php         \
        UploadedFileInterface.php   \
        UriInterface.php

BPCPHP_FILES = $(patsubst %,Http/Message/%,$(FILES))

libpsr-http-message.so:
	rm -rf Http
	mkdir -p Http/Message
	for i in $(FILES); do phptobpc ../src/$$i > Http/Message/$$i; done
	bpc -v \
		-c bpc.conf  \
		-l psr-http-message \
		placeholder-http-message.php \
		$(BPCPHP_FILES)

install-libpsr-http-message:
	bpc -l psr-http-message --install
