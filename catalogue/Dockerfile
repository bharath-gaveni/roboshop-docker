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
      component="catalogue" \
      author="bharathgaveni" 
COPY --from=build /opt/server /opt/server
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
RUN chown -R roboshop:roboshop /opt/server
USER roboshop    
CMD ["node" , "server.js"]

