# # Use a base image with Node.js installed
# FROM node:18-alpine

# ENV PYTHONDONTWRITEBYTECODE 1
# ENV PYTHONBUFFERED 1

# ENV PORT=5173

# # Set the working directory inside the container
# WORKDIR /app

# # Copy package.json and package-lock.json to the working directory
# COPY package.json package-lock.json ./

# # Install dependencies
# RUN npm ci

# # Copy the rest of the application code to the working directory
# COPY . .

# # Expose the port that the application will run on
# EXPOSE ${PORT}

# # Set the command to start the application
# # CMD ["npm", "run", "dev", "--host"]
# CMD ["npm", "start"]

FROM node:18-alpine

WORKDIR /var/www/app

COPY package.json package-lock.json ./

RUN npm install

COPY . .

EXPOSE 5173

CMD [ "npx", "vite", "--host" ]