<!DOCTYPE html>
<html lang="ru">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Личный Кабинет</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            display: flex;
            height: 100vh;
            background-color: #f5f5f5;
        }

        /* Стили бокового меню */
        nav {
            width: 300px;
            background-color: #f0f0f0;
            padding: 20px;
            display: flex;
            flex-direction: column;
        }

        nav h1 {
            font-size: 24px;
            color: #6a0dad;
            margin-bottom: 20px;
        }

        nav a {
            display: block;
            text-decoration: none;
            color: #333;
            font-weight: bold;
            padding: 15px 10px;
            border-radius: 8px;
            transition: background-color 0.3s;
            margin-bottom: 10px;
        }

        nav a:hover,
        nav a.active {
            background-color: #6a0dad;
            color: white;
        }

        /* Основной блок контента */
        .content-container {
            flex-grow: 1;
            padding: 40px;
            background-color: white;
            overflow-y: auto;
        }

        .profile-header {
            text-align: center;
            margin-bottom: 20px;
        }

        .profile-header h2 {
            font-size: 28px;
            color: #333;
        }

        .profile-header p {
            font-size: 18px;
            color: #555;
        }

        .profile-stats {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
        }

        .stats-box {
            background-color: #f9f9f9;
            padding: 20px;
            border-radius: 10px;
            width: 32%;
            text-align: center;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }

        .stats-box h3 {
            font-size: 24px;
            color: #6a0dad;
            margin-bottom: 10px;
        }

        .stats-box p {
            font-size: 18px;
            color: #555;
        }

        /* Стили таблицы целевого обучения */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        table th,
        table td {
            padding: 12px;
            text-align: center;
            border: 1px solid #ddd;
        }

        table th {
            background-color: #6a0dad;
            color: white;
        }

        table td {
            background-color: #f9f9f9;
        }

        /* Стили вакансий */
        .cloud-vacancy {
            background: #6a0dad;
            color: white;
            font-size: 16px;
            padding: 15px;
            margin: 15px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            cursor: pointer;
            transition: transform 0.3s ease;
            width: 200px;
            display: inline-block;
        }

        .cloud-vacancy:hover {
            transform: translateY(-5px);
        }
    </style>

    <script>
        function loadContent(page) {
            const contentDiv = document.querySelector('.content-container');
            const navLinks = document.querySelectorAll('nav a');

            navLinks.forEach(link => link.classList.remove('active'));
            document.querySelector(`nav a[data-page="${page}"]`).classList.add('active');

            switch (page) {
                case 'profile':
                    contentDiv.innerHTML = `
                        <div class="profile-header">
                            <h2>Павел Швырев</h2>
                            <p>Липецк, Россия</p>
                            <p>ID: 612</p>
                        </div>
                        <div class="profile-stats">
                            <div class="stats-box">
                                <h3>Твои баллы</h3>
                                <p>В этом месяце: <strong>160</strong></p>
                                <p>За всё время: <strong>160</strong></p>
                            </div>
                            <div class="stats-box">
                                <h3>Твоё звание</h3>
                                <p>Активист</p>
                                <p>Ты активно участвуешь в развитии своего региона!</p>
                            </div>
                            <div class="stats-box">
                                <h3>Место в рейтинге</h3>
                                <p><strong>1</strong> из <strong>200</strong> активных пользователей</p>
                            </div>
                        </div>`;
                    break;

                case 'target':
                    contentDiv.innerHTML = `
                        <h2>Целевое обучение</h2>
                        <table class="target-education">
                            <thead>
                                <tr>
                                    <th>ВУЗ</th>
                                    <th>Направление</th>
                                    <th>Сколько работать?</th>
                                    <th>З/П</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Сибирский федеральный университет</td>
                                    <td>Организация работы с молодежью (39.03.03)</td>
                                    <td>3 года</td>
                                    <td>от 50к</td>
                                </tr>
                                <tr>
                                    <td>Казанский федеральный университет</td>
                                    <td>Организация работы с молодежью (39.03.03)</td>
                                    <td>5 лет</td>
                                    <td>от 50к</td>
                                </tr>
                                <tr>
                                    <td>Университет управления "ТИСБИ"</td>
                                    <td>Организация работы с молодежью (39.03.03)</td>
                                    <td>4 года</td>
                                    <td>от 50к</td>
                                </tr>
                            </tbody>
                        </table>`;
                    break;

                case 'internships':
                    contentDiv.innerHTML = `
                        <h2>Стажировки</h2>
                        <div class="cloud-vacancy" onclick="loadVacancy('Специалист по работе с молодежью')">
                            Специалист по работе с молодежью в МТБЦ "Пилот"
                        </div>
                        <div class="cloud-vacancy" onclick="loadVacancy('Администратор центра')">
                            Администратор центра в МТБЦ "Пилот"
                        </div>
                        <div class="cloud-vacancy" onclick="loadVacancy('Технический специалист')">
                            Технический специалист в МТБЦ "Пилот"
                        </div>`;
                    break;

                case 'events':
                    contentDiv.innerHTML = '<h2>Мероприятия</h2><p>Здесь будет информация о мероприятиях.</p>';
                    break;

                case 'tests':
                    contentDiv.innerHTML = '<h2>Тесты</h2><p>Здесь будет информация о тестах.</p>';
                    break;
            }
        }

        document.addEventListener('DOMContentLoaded', function () {
            loadContent('profile');
        });
    </script>
</head>

<body>
    <nav>
        <h1>Мы молодые</h1>
        <a href="#" data-page="profile" onclick="loadContent('profile')">Профиль</a>
        <a href="#" data-page="internships" onclick="loadContent('internships')">Стажировки</a>
        <a href="#" data-page="target" onclick="loadContent('target')">Целевое</a>
        <a href="#" data-page="events" onclick="loadContent('events')">Мероприятия</a>
        <a href="#" data-page="tests" onclick="loadContent('tests')">Тесты</a>
    </nav>

    <div class="content-container">
        <!-- Контент будет динамически загружен сюда -->
    </div>
</body>

</html>
