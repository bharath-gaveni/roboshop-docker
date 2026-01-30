FROM node:20.19.5-alpine3.22 as build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install



FROM node:20.19.5-alpine3.22
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
EXPOSE 8080
LABEL com.project="roboshop" \
      component="cart" \
      author="bharathgaveni" 
ENV REDIS_HOST="redis"\
    CATALOGUE_HOST="catalogue"\
    CATALOGUE_PORT="8080"
COPY --from=build --chown=roboshop:roboshop /opt/server /opt/server
USER roboshop    
ENTRYPOINT ["node"]
CMD ["server.js"]








# FROM node:20
# WORKDIR /opt/server
# EXPOSE 8080
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV REDIS_HOST="redis"\
#     CATALOGUE_HOST="catalogue"\
#     CATALOGUE_PORT="8080"
# CMD ["node" , "server.js"]