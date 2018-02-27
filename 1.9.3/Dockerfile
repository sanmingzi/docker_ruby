# Thanks for: https://www.rosehosting.com/blog/how-to-install-ruby-1-9-3-and-rubygems-1-8-24-on-centos-6-2/

FROM centos:7

ENV RUBY_MAJOR 1.9
ENV RUBY_VERSION 1.9.3-p551
ENV RUBYGEMS_VERSION 2.6.14
ENV BUNDLER_VERSION 1.15.4

ENV DOWNLOAD_PATH /tmp/download
ENV SRC_PATH /tmp/src

RUN mkdir -p $DOWNLOAD_PATH $SRC_PATH

# install ruby build dependens
RUN yum install -y wget gcc gdbm-devel make ncurses-devel readline-devel wget cpp \
                   glibc-devel glibc-headers kernel-headers libgomp libmpc mpfr \
    # install ruby run dependens
    && yum install -y libyaml-devel libffi-devel openssl-devel zlib-devel bzip2 \
    # install ruby
    && cd $DOWNLOAD_PATH \
    && wget -O ruby.tar.gz https://cache.ruby-lang.org/pub/ruby/$RUBY_MAJOR/ruby-$RUBY_VERSION.tar.gz \
    && tar xvzf ruby.tar.gz -C $SRC_PATH \
    && cd $SRC_PATH/ruby-$RUBY_VERSION \
    && ./configure --disable-install-doc --enable-shared --without-tcl --without-tk --disable-option-checking \
    && make \
    && make install \
    && make clean \
    # install rubygems-2.6.14
    && cd $DOWNLOAD_PATH \
    && wget -O rubygems.tgz https://rubygems.org/rubygems/rubygems-$RUBYGEMS_VERSION.tgz \
    && tar xvzf rubygems.tgz -C $SRC_PATH \
    && cd $SRC_PATH/rubygems-$RUBYGEMS_VERSION \
    && ruby setup.rb --no-document \
    # install bundler
    && gem install bundler -v $BUNDLER_VERSION --no-document \
    # remove download and src
    && cd $DOWNLOAD_PATH \
    && rm -rf * \
    && cd $SRC_PATH \
    && rm -rf * \
    # remove package
    && yum remove -y wget gcc gdbm-devel make ncurses-devel readline-devel wget cpp \
                       glibc-devel glibc-headers kernel-headers libgomp libmpc mpfr \
    && rm -rf /var/cache/yum \
    && rm -rf /etc/pki/rpm-gpg
