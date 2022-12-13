FROM node:16-alpine as build_stage

WORKDIR /src

COPY package.json .

COPY yarn.lock .

RUN yarn install --frozen-lockfile

COPY . .

RUN yarn run build

# deploy
FROM nginx:stable-alpine as prod_stage

COPY --from=build_stage /src/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]