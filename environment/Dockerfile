FROM python:3

WORKDIR /usr/ctf/

RUN apt-get update && \
    apt-get install -y vim curl tzdata git gdb libssl-dev libffi-dev build-essential strace ltrace checksec

# gdb-peda
RUN git clone https://github.com/longld/peda.git ~/peda && \
  echo "source ~/peda/peda.py" >> ~/.gdbinit 

# ROP
RUN apt-get install -y ruby gem && \
  gem install one_gadget  

COPY requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

CMD [ "/bin/sh" ]

