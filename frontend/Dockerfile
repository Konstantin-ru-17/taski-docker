# При создании фронтенда разработчики использовали Node.js — программу,
# выполняющую код на JavaScript. Поэтому в качестве базового слоя 
# в докерфайле указан образ node версии 18
FROM node:18
WORKDIR /app

# копируются файлы с перечнем зависимостей проекта: 
# в Python такие файлы принято называть requirements.txt,
# а при разработке на JS используют package.json и package-lock.json;
COPY package.json package.json
COPY package-lock.json package-lock.json

# выполняется установка необходимых пакетов 
# (npm — это менеджер пакетов в Node.js, вроде pip в Python);
RUN npm install

# исходный код приложения копируется в образ;
COPY . .
# выполняется сборка приложения для публикации на сервере.
RUN npm run build

# Эта команда запустит встроенный сервер на Node.js, который будет раздавать
# содержимое директории /app/build на порте 8000
CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"]