FROM mcr.microsoft.com/playwright:v1.50.0-noble

RUN npm install -g pnpm

WORKDIR /usr/src/app

COPY package.json pnpm-lock.yaml ./

RUN --mount=type=cache,target=/root/.npm \
    npm i

# Install dependencies
RUN pnpm i --frozen-lockfile

# Copy the rest of the application code
COPY . .

RUN npx playwright install

# Start the application
CMD ["npm", "start"]
