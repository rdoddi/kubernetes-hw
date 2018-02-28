# Use alpine version of thin linux.
FROM nginx:alpine
#FROM ubuntu

# Label for docker inspect.
LABEL maintainer="rdoddi@iremote.net"

# Copy nginx context
COPY nginx.conf /etc/nginx/nginx.conf
COPY *.html /www/data/

# Configure nginx
RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN mkdir /etc/nginx/logs

# Expose ports.
EXPOSE 8080

# Set the default command to execute when creating new container.
CMD ["nginx"]
