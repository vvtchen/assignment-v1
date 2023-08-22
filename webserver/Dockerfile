FROM node:18.10.0-alpine3.15 as build

WORKDIR /frontend
COPY ./frontend/peopleList/package.json .
COPY ./frontend/peopleList/package-lock.json .
RUN npm install
COPY ./frontend/peopleList/ .
RUN npm run build

FROM nginx:1.18.0-alpine
COPY ./webserver/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /frontend/dist /usr/share/nginx/html