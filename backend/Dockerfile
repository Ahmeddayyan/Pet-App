# Use Node.js base image
FROM node:18

# Set working directory inside container
WORKDIR /app

# Copy package.json and package-lock.json first
COPY package*.json ./

# Install dependencies
RUN npm install
RUN npm install bcryptjs

# Copy the rest of the backend files
COPY . .

# Expose port (matches PORT in .env)
EXPOSE 5000

# Start the server
CMD ["node", "server.js"]

# Expose the port your app runs on
# EXPOSE 3000

# Command to run the application
# CMD ["npm", "start"]
