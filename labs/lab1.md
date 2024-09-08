# Лабораторна робота №1: Розгортання простого Vue.js додатку з використанням Docker

## Тема
Розгортання простого Vue.js додатку з використанням Docker.

## Мета
Оволодіти основними кроками створення, налаштування та розгортання Vue.js додатку, а також ознайомитися з використанням контейнеризації за допомогою Docker для легкого розповсюдження та збереження середовища розробки.

## Теоретичні відомості
**Vue.js** - прогресивний фреймворк для створення веб-інтерфейсів, що спрощує розробку веб-додатків та дозволяє ефективно керувати їхнім станом і компонентами.

## Завдання

1. Ознайомтеся з документацією Vue.js, щоб зрозуміти основи роботи з фреймворком. Документацію можна знайти на [офіційному сайті Vue.js](https://vuejs.org/).
2. Встановлення Node.js та npm, yarn на вашому комп'ютері.
3. Створіть новий проект Vue.js за допомогою Vite
   ```bash
   npm create vite@latest <ваше-прізвище-англійською> -- --template vue
   ```
4. Запустіть проект та переконайтеся, що він працює коректно.
   ```bash
   cd <ваше-прізвище-англійською>
   npm install
   npm run dev
   ```
5. Знайдіть компонент HelloWorld.vue та додайте інформацію про себе (Спеціальність, курс, група, ПІБ).
6. Створіть Dockerfile для збірки та запуску Vue.js додатку.
```DOCKERFILE
   # Build stage
   FROM node:latest as build-stage
   WORKDIR /app
   COPY package*.json ./
   RUN npm install
   COPY . .
   RUN npm run build
   # Production stage
   FROM nginx:stable-alpine as production-stage
   COPY --from=build-stage /app/dist /usr/share/nginx/html
   EXPOSE 80
   CMD ["nginx", "-g", "daemon off;"]
   ```
7. Додайте .dockerignore для виключення непотрібних файлів:
```dockerignore
node_modules
```
8. Збережіть `Dockerfile` та `.dockerignore` у кореневій папці проекту.
9. Додайте до package.json наступні команди:
```json
"scripts": {
  ...
  "docker-run": "docker build --tag vue-lab-1:latest . && docker run --rm -p 8080:80 --name vue-lab-1-instance vue-lab-1:latest",
  "docker-stop": "docker stop vue-lab-1-instance && docker rm vue-lab-1-instance",
}
```
10. Розмістіть ваш проект в публічному GitHub/GitLab/Bitbucket з назвою `<vendor>/mjsf-mag` та додайте посилання на репозиторій у звіті виконавши наступні команди:
```bash
git init
git add .
git commit -m "Vue.js lab 1"
git branch -M main
git remote add origin <посилання-на-репозиторій>
git push -u origin main
```

## Контрольні питання:
- Які кроки потрібно виконати перед початком роботи з Vue.js?
- Що таке Vue CLI і як його встановити?
- Як створити новий Vue.js проект?
- Що таке Docker і для чого він використовується?
- Як створити Dockerfile для Vue.js додатку?
- Які файли потрібно включати до .dockerignore?
- Як завантажити проект до репозиторію на GitHub або Bitbucket?
- Які переваги систем контролю версій у розробці?
