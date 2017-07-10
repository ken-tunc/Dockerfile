FROM ubuntu:12.04

RUN apt-get update && apt-get install -y \
    python-software-properties \
    wget \
    liblzma-dev \
    postgresql \
  && add-apt-repository ppa:fkrull/deadsnakes \
  && apt-get update && apt-get install -y python3.3 \
  && sudo apt-get remove python-virtualenv

WORKDIR /root

RUN wget http://peak.telecommunity.com/dist/ez_setup.py \
  && python ez_setup.py \
  && easy_install pip \
  && pip install virtualenv \
  && virtualenv --no-site-packages --distribute -p /usr/bin/python3.3 /root/.virtualenvs/pywork3 \
  && apt-get install -y python3.3-dev

RUN gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9 \
  && gpg -a --export E084DAB9 | apt-key add - \
  && echo "deb http://cran.ma.imperial.ac.uk/bin/linux/ubuntu precise/" >> /etc/apt/sources.list \
  && apt-get update && apt-get install -y r-base

RUN pip3 install \
    rpy2 \
    sqlalchemy \
    py-postgresql \
    requests \
    python-dateutil \
    http://pypi.python.org/packages/source/M/MonthDelta/MonthDelta-1.0b.tar.bz2

CMD ["/bin/bash"]
