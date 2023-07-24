## Дипломный проект профессии «Тестировщик»
В рамках дипломного проекта требовалось автоматизировать тестирование комплексного сервиса покупки тура, 
взаимодействующего с СУБД и API Банка.

База данных хранит информацию о заказах, платежах, статусах карт, способах оплаты.

Для покупки тура есть два способа: с помощью карты и в кредит. 
В приложении используются два отдельных сервиса оплаты: Payment Gate и Credit Gate.

Ссылка на дипломный проект https://github.com/netology-code/qa-diploma

## Запуск приложения

## Подготовительный этап
- Установить и запустить IntelliJ IDEA;
- Установать Node.js;
- Установить Docker Desktop;

 в Docker 
1) клонировать репозиторий с Github git clone https://github.com/shalom69/dip

   в IntelliJ IDEA
2) Открыть проект в IntelliJ IDEA, открыть терминал (Fn + Alt + F12);
3) переходим в папку gate-simulator (cd gate-simulator);
4) запускаем банковский симулятор командой npm start;
5) открываем в терминале (+) новую вкладку и вводим команду docker-compose up -d --force-recreate;
6) открываем в терминале (+) новую вкладку и запускаем jar файл командой java -jar aqa-shop.jar.
7) открываем страницу в Google Chrome http://localhost:8080.
8) после работы с Docker останавливаем контейнеры docker-compose down
9) после работы с банковским симулятор в терминале нажимаем Ctl + C


 ## Запуск тестового приложения
в IDEA 
### Для формирования отчета MySQL
- открываем в терминале (+) новую вкладку и вводим команду ./gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app" "-Ddb.user=app" "-Ddb.password=pass"
- После прохождения тестов в терминале вводим команду ./gradlew allureServe
Автоматически откроется браузер с генерированным отчетом Allure Report. 
После работы с отчетом Allure нажимаем ctl + C
- 
### Для формирования отчета postgresql
- В файле application.properties  в строке spring.datasource.url прописываем jdbc:postgresql://localhost:5432/app
- открываем новую вкладку в терминале java -jar aqa-shop.jar
- открываем в терминале (+) новую вкладку и вводим команду  ./gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app" "-Ddb.user=app" "-Ddb.password=pass"
- После прохождения тестов в терминале вводим команду ./gradlew allureServe
  Автоматически откроется браузер с генерированным отчетом Allure Report.
  После работы с отчетом Allure нажимаем Ctl + C

