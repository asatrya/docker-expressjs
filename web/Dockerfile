FROM node:10.16-alpine

# Install tools
RUN apk --update add bash nano 

# set timezone
ENV TZ=Asia/Jakarta
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Install MySQL client
RUN apk --update add mysql-client

# Copy conf files
COPY image-files/ /
RUN chmod 700 /usr/local/bin/entrypoint.sh

# Configure SSL

# Create app folder
RUN mkdir /app
RUN chmod -R 775 /app
WORKDIR /app
COPY . .

# Expose port
EXPOSE 3000

ENTRYPOINT [ "/usr/local/bin/entrypoint.sh" ]