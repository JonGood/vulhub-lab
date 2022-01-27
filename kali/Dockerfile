FROM kalilinux/kali-rolling

ENV DEBIAN_FRONTEND noninteractive
ENV TERM xterm-256color

# Install Kali Headless
RUN rm -fR /var/lib/apt/ && \
    apt-get clean && \
    apt-get update -y && \
    apt-get install -y software-properties-common kali-linux-headless --fix-missing

# Update DB and clean'up!
RUN updatedb && \
    apt-get autoremove -y && \
    apt-get clean
    
# Enable SSH
RUN sudo update-rc.d -f ssh remove && \
    sudo update-rc.d -f ssh defaults && \
    sudo service ssh restart && \
    sudo update-rc.d -f ssh enable 2 3 4 5

CMD ["/bin/bash"]
