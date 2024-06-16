FROM ubuntu:22.04
RUN apt update && apt install -y curl
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt install -y nodejs

WORKDIR /usr/src/app
COPY . .
RUN npm install
ENV REACT_APP_BACKEND_URL="http://localhost:8080"
RUN npm run build
RUN npm install -g serve
EXPOSE 5000
CMD ["serve", "-s", "-l", "5000", "./build"]
