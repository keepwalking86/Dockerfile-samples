FROM node:alpine

ENV TZ=Asia/Ho_Chi_Minh

WORKDIR /usr/app/nodejs

COPY ./app ./

RUN npm install

#RUN npm run build
RUN npm install

EXPOSE 3000

CMD ["npm", "start"]