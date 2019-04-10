FROM ubuntu:latest
ENV user=chall
RUN apt-get update
RUN dpkg --add-architecture i386
RUN apt-get update
RUN apt-get install -y xinetd libc6-dev-i386
RUN useradd -m $user
RUN echo "$user     hard    nproc       20" >> /etc/security/limits.conf
COPY ./goldrush /home/$user/
COPY ./flag /home/$user/
COPY ./challservice /etc/xinetd.d/
RUN chmod +x /home/$user/goldrush
RUN chown -R root:$user /home/$user
RUN chmod -R 750 /home/$user
RUN chown root:$user /home/$user/flag
RUN chmod 440 /home/$user/flag
EXPOSE 31337
CMD ["/usr/sbin/xinetd", "-d"]
