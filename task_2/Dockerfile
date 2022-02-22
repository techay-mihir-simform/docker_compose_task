#Stag1 ++++++++++
#################
#Pull official base node image
FROM node:alpine as builder
#set working directory
WORKDIR /app
#Copy package.json file
COPY ./package.json ./
#Install node js packages
RUN npm install
#Copy all to docker 
COPY . ./
RUN npm run build


#Steg2 ++++++++++++
###################
#Pull nginx alpine offical image
FROM nginx:alpine
#Set working directory to nginx 
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
# Copies static resources from builder stage
COPY --from=builder /app/build .
ENTRYPOINT ["nginx", "-g", "daemon off;"]

