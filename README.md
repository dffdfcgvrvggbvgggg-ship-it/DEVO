<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Олимпиада: Результаты</title>
    <!-- Подключение Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Настройка шрифта Inter -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            min-height: 150vh; 
            transition: background-color 0.5s ease-in-out; 
            overflow-y: scroll; 
        }
        
        /* Фиксируем контейнер контента, чтобы имитировать узкий мобильный экран */
        #content-container {
            max-width: 480px; 
            margin-top: 0;
            padding-top: 0; 
        }

        /* ------------------------------------------------ */
        /* Кастомные стили и переменные */
        /* ------------------------------------------------ */
        .rounded-xl { border-radius: 1rem; }
        .rounded-lg { border-radius: 0.5rem; }

        /* Стиль для кнопки Полный доступ с корзиной */
        .full-access-button {
            background-color: #673AB7; /* Насыщенный фиолетовый для кнопки */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.06);
        }

        /* ------------------------------------------------ */
        /* Базовые стили для всех карточек (Uchi.ru style) */
        /* ------------------------------------------------ */
        .card-illustration-base {
            position: relative;
            background-repeat: no-repeat;
            background-size: cover;
            background-position: center top;
            background-size: 100% auto;
            z-index: 10;
        }
        
        /* Текстовая накладка для всех карточек */
        .card-illustration-base .card-text-overlay {
            /* Базовые стили определяются в JS, но этот контейнер гарантирует позиционирование */
            text-shadow: 2px 2px 4px rgba(0,0,0,0.4);
            font-weight: 800; /* font-extrabold */
            text-align: center;
            line-height: 1.1; /* Сжатие межстрочного интервала для заголовков */
        }

        /* ------------------------------------------------ */
        /* Имитация 20 Уникальных Иллюстраций Карточек (SVG) */
        /* ------------------------------------------------ */
        /* Примечание: Все иллюстрации созданы с использованием SVG для имитации
           разнообразных и ярких стилей Uchi.ru для различных предметов.
           Стили CSS определяют только фон и загружают SVG-изображение. */

        /* 1. Классическая тема Учи.ру (Зеленая листва) */
        .card-theme-01 {
            background-color: #FFF9E6; 
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон (светло-желтый) --%3E%3Crect width='400' height='650' fill='%23FFF9E6'/%3E%3C!-- Большая зеленая листва (слева) --%3E%3Cpath fill='%23689F38' opacity='.8' d='M0 0c0 0 100 150 150 100s100 10 150 50v350H0z'/%3E%3C!-- Средняя зеленая листва (справа) --%3E%3Cpath fill='%238BC34A' opacity='.9' d='M200 50c-50-50 100-50 150 0s50 100 0 150H200z'/%3E%3C!-- Подвесной горшок --%3E%3Ccircle cx='320' cy='120' r='15' fill='%23795548'/%3E%3Cpath fill='none' stroke='%23795548' stroke-width='2' d='M320 105V50M320 135V180'/%3E%3C!-- Кусты/облака (снизу, желто-зеленые) --%3E%3Cpath fill='%23C5E1A5' opacity='.9' d='M-20 400c50-50 150-50 200 0s100 50 150 0v20H-20z'/%3E%3Cpath fill='%23AED581' d='M-20 400c50-50 150-50 200 0s100 50 150 0v20H-20z'/%3E%3C!-- Горшок (основной) --%3E%3Crect x='100' y='500' width='200' height='20' fill='%23795548' rx='10'/%3E%3Cpath fill='%235D4037' d='M120 520h160v60c0 20-160 20-160 0v-60z'/%3E%3C!-- Растение в горшке --%3E%3Ccircle cx='200' cy='520' r='10' fill='%238BC34A'/%3E%3Cpath fill='%238BC34A' d='M200 520c-10-10 0-20 10-20s20 10 10 20z'/%3E%3C/svg%3E");
        }

        /* 2. Тема с Конвейером и монстрами (Темно-синяя) */
        .card-theme-02 {
            background-color: #2F3C8F; 
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%232F3C8F'/%3E%3C!-- Конвейер (фиолетовый) --%3E%3Cpath fill='%2338276D' d='M0 300c0-50 400-50 400 0s-400 50-400 0z'/%3E%3Cpath fill='%231E2967' d='M0 300c0 0 200 50 400 0v100H0z'/%3E%3C!-- Ролики конвейера (светло-голубой) --%3E%3Ccircle cx='50' cy='350' r='10' fill='%23A0E0FF'/%3E%3Ccircle cx='150' cy='350' r='10' fill='%23A0E0FF'/%3E%3Ccircle cx='250' cy='350' r='10' fill='%23A0E0FF'/%3E%3Ccircle cx='350' cy='350' r='10' fill='%23A0E0FF'/%3E%3C!-- Багаж и монстры на конвейере (слева направо) --%3E%3Ccircle cx='40' cy='280' r='20' fill='%23FFD700'/%3E%3Crect x='60' y='270' width='40' height='40' fill='%23FF6347' rx='8'/%3E%3Cpath fill='%2390EE90' d='M150 280c-10 0-30-40 20-40s40 30 20 40z'/%3E%3Crect x='220' y='260' width='60' height='50' fill='%23E91E63' rx='10'/%3E%3C!-- Монстрик-динозавр (внизу справа) --%3E%3Cpath fill='%23F44336' d='M300 300c-20 0-40 40 0 40s40-40 0-40z'/%3E%3Ccircle cx='300' cy='300' r='5' fill='%23FFC107'/%3E%3C!-- Контейнер с Багажом --%3E%3Crect x='300' y='200' width='60' height='40' fill='%23800080' rx='5'/%3E%3C/svg%3E");
        }
        
        /* 3. Космос (Темно-фиолетовый) */
        .card-theme-03 {
            background-color: #3700B3; 
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%233700B3'/%3E%3C!-- Звезды --%3E%3Ccircle cx='50' cy='50' r='2' fill='%23FFFF8D'/%3E%3Ccircle cx='350' cy='150' r='3' fill='%23FFFFFF'/%3E%3Ccircle cx='100' cy='250' r='1' fill='%23B388FF'/%3E%3Ccircle cx='250' cy='400' r='2' fill='%23FFFFFF'/%3E%3Ccircle cx='50' cy='550' r='3' fill='%23FFFF8D'/%3E%3C!-- Планета (Оранжевая) --%3E%3Ccircle cx='100' cy='500' r='80' fill='%23FF6F00'/%3E%3Ccircle cx='100' cy='500' r='60' fill='%23FF9800'/%3E%3C!-- Комета --%3E%3Cpath fill='%2300BCD4' d='M300 100l50 50-100 0z'/%3E%3Cpath fill='%234DD0E1' d='M350 150l-20-5 20-5 10 5z'/%3E%3C/svg%3E");
        }
        
        /* 4. Лес и животные (Зелено-коричневый) */
        .card-theme-04 {
            background-color: #E8F5E9;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23E8F5E9'/%3E%3C!-- Деревья (слева) --%3E%3Crect x='30' y='300' width='20' height='200' fill='%23A1887F'/%3E%3Cpath fill='%234CAF50' d='M10 300l40-50 40 50z'/%3E%3C!-- Пень (справа) --%3Crect x='300' y='450' width='40' height='50' fill='%23795548'/%3E%3C!-- Сова --%3E%3Ccircle cx='320' cy='460' r='10' fill='%23FFC107'/%3E%3Ccircle cx='315' cy='460' r='2' fill='%23000000'/%3E%3Ccircle cx='325' cy='460' r='2' fill='%23000000'/%3E%3C!-- Кусты --%3E%3Cpath fill='%238BC34A' d='M0 500c50 0 50 50 100 0s50 50 100 0H0z'/%3E%3Cpath fill='%238BC34A' d='M200 520c50 0 50 50 100 0s50 50 100 0H200z'/%3E%3C/svg%3E");
        }
        
        /* 5. Подводный мир (Голубой) */
        .card-theme-05 {
            background-color: #00BCD4;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%2300BCD4'/%3E%3C!-- Водоросли (слева) --%3E%3Cpath fill='%234CAF50' d='M20 650V400c0 50 50 50 50 0v250z'/%3E%3C!-- Рыбка (Оранжевая) --%3E%3Cpath fill='%23FF5722' d='M150 200l50 20-50 20z'/%3E%3Ccircle cx='150' cy='220' r='5' fill='%23FF9800'/%3E%3C!-- Пузырьки --%3E%3Ccircle cx='350' cy='50' r='8' fill='%23FFFFFF' opacity='.6'/%3E%3Ccircle cx='300' cy='150' r='5' fill='%23FFFFFF' opacity='.6'/%3E%3Ccircle cx='320' cy='250' r='3' fill='%23FFFFFF' opacity='.6'/%3E%3C/svg%3E");
        }
        
        /* 6. Пиратский клад (Песочный) */
        .card-theme-06 {
            background-color: #FFECB3;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23FFECB3'/%3E%3C!-- Песок --%3E%3Cpath fill='%23FFB300' d='M0 500c100 50 300 50 400 0V650H0z'/%3E%3C!-- Сундук --%3E%3Crect x='150' y='450' width='100' height='50' fill='%23795548'/%3E%3Crect x='150' y='440' width='100' height='10' fill='%235D4037'/%3E%3C!-- Монеты --%3E%3Ccircle cx='180' cy='435' r='5' fill='%23FFD700'/%3E%3Ccircle cx='220' cy='435' r='5' fill='%23FFD700'/%3E%3C!-- Пальма --%3E%3Crect x='350' y='300' width='10' height='200' fill='%23A1887F'/%3E%3Cpath fill='%234CAF50' d='M355 300c-30-20-30-50 0-50s30 30 0 50z'/%3E%3C/svg%3E");
        }

        /* 7. Фруктовый сад (Светло-зеленый) */
        .card-theme-07 {
            background-color: #DCEDC8;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23DCEDC8'/%3E%3C!-- Яблоки --%3E%3Ccircle cx='100' cy='100' r='20' fill='%23F44336'/%3E%3Ccircle cx='300' cy='250' r='20' fill='%23F44336'/%3E%3C!-- Груши --%3E%3Cpath fill='%238BC34A' d='M200 150c-10-30 30-30 20 0s-10 40 0 40z'/%3E%3Cpath fill='%238BC34A' d='M100 350c-10-30 30-30 20 0s-10 40 0 40z'/%3E%3C!-- Листья --%3E%3Cpath fill='%234CAF50' d='M115 90l10 5-5 10z'/%3E%3Cpath fill='%234CAF50' d='M315 240l10 5-5 10z'/%3E%3C/svg%3E");
        }

        /* 8. Геометрия (Желто-серый) */
        .card-theme-08 {
            background-color: #EEEEEE;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23EEEEEE'/%3E%3C!-- Квадрат (красный) --%3E%3Crect x='50' y='50' width='100' height='100' fill='%23F44336' opacity='.7'/%3E%3C!-- Круг (синий) --%3E%3Ccircle cx='300' cy='100' r='50' fill='%232196F3' opacity='.7'/%3E%3C!-- Треугольник (зеленый) --%3E%3Cpath fill='%234CAF50' opacity='.7' d='M150 300l100 100-200 0z'/%3E%3C!-- Линия --%3E%3Cpath stroke='%23FFC107' stroke-width='5' d='M50 500h300'/%3E%3C/svg%3E");
        }
        
        /* 9. Замок и дракон (Серый, драматический) */
        .card-theme-09 {
            background-color: #455A64;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23455A64'/%3E%3C!-- Замок --%3E%3Crect x='100' y='300' width='200' height='200' fill='%23607D8B'/%3E%3Crect x='120' y='280' width='20' height='20' fill='%2390A4AE'/%3E%3Crect x='260' y='280' width='20' height='20' fill='%2390A4AE'/%3E%3C!-- Дракон (зеленый силуэт) --%3E%3Cpath fill='%238BC34A' d='M50 150c50-50 100 0 50 50s-50 50-50 0z'/%3E%3Cpath fill='%23A5D6A7' d='M70 180l-20 20 20 20z'/%3E%3C/svg%3E");
        }
        
        /* 10. Лаборатория (Белый, с колбами) */
        .card-theme-10 {
            background-color: #FFFFFF;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23FFFFFF'/%3E%3C!-- Колба 1 (синяя жидкость) --%3E%3Crect x='50' y='300' width='40' height='80' fill='%23BBDEFB'/%3E%3Cpath fill='%232196F3' d='M50 340h40v40H50z'/%3E%3C!-- Колба 2 (зеленая жидкость) --%3E%3Crect x='150' y='250' width='50' height='100' fill='%23C8E6C9'/%3E%3Cpath fill='%234CAF50' d='M150 300h50v50H150z'/%3E%3C!-- Пробирки --%3E%3Crect x='280' y='350' width='20' height='50' fill='%23FFCDD2'/%3E%3Cpath fill='%23F44336' d='M280 370h20v30H280z'/%3E%3C/svg%3E");
        }

        /* 11. Городской пейзаж (Сине-голубой) */
        .card-theme-11 {
            background-color: #B3E5FC;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23B3E5FC'/%3E%3C!-- Здания --%3E%3Crect x='50' y='400' width='80' height='150' fill='%237986CB'/%3E%3Crect x='150' y='300' width='100' height='250' fill='%235E35B1'/%3E%3Crect x='270' y='450' width='60' height='100' fill='%238D6E63'/%3E%3C!-- Окна --%3E%3Crect x='160' y='320' width='10' height='10' fill='%23FFECB3'/%3E%3Crect x='220' y='350' width='10' height='10' fill='%23FFECB3'/%3E%3C/svg%3E");
        }
        
        /* 12. Музыка и ноты (Кремовый) */
        .card-theme-12 {
            background-color: #FFFDE7;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23FFFDE7'/%3E%3C!-- Ноты --%3E%3Ccircle cx='100' cy='200' r='10' fill='%23333333'/%3E%3Crect x='100' y='150' width='5' height='50' fill='%23333333'/%3E%3Ccircle cx='300' cy='150' r='10' fill='%23333333'/%3E%3Crect x='300' y='100' width='5' height='50' fill='%23333333'/%3E%3C!-- Скрипичный ключ --%3E%3Cpath stroke='%23F06292' stroke-width='5' fill='none' d='M200 300c-50-50-50-100 0-150s100 0 100 50z'/%3E%3C/svg%3E");
        }
        
        /* 13. Спорт и движение (Красный) */
        .card-theme-13 {
            background-color: #FFCDD2;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23FFCDD2'/%3E%3C!-- Мяч --%3E%3Ccircle cx='100' cy='100' r='30' fill='%23F44336'/%3E%3Ccircle cx='100' cy='100' r='15' fill='%23FFFFFF'/%3E%3C!-- Человечек в движении --%3E%3Ccircle cx='300' cy='300' r='15' fill='%232196F3'/%3E%3Cpath stroke='%232196F3' stroke-width='5' d='M300 315v50M280 340h40M300 365l-20 20M300 365l20 20'/%3E%3C!-- Гантели --%3E%3Crect x='50' y='400' width='10' height='50' fill='%23757575'/%3E%3Ccircle cx='45' cy='400' r='15' fill='%23424242'/%3E%3Ccircle cx='55' cy='450' r='15' fill='%23424242'/%3E%3C/svg%3E");
        }

        /* 14. Дикий Запад (Оранжевый, с кактусами) */
        .card-theme-14 {
            background-color: #FFCC80;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23FFCC80'/%3E%3C!-- Кактус 1 --%3E%3Crect x='50' y='350' width='20' height='150' fill='%238BC34A'/%3E%3Crect x='70' y='400' width='50' height='20' fill='%238BC34A'/%3E%3C!-- Кактус 2 --%3E%3Crect x='300' y='400' width='20' height='100' fill='%23689F38'/%3E%3C!-- Солнце --%3E%3Ccircle cx='350' cy='50' r='30' fill='%23FFEB3B'/%3E%3C/svg%3E");
        }
        
        /* 15. Еда и кулинария (Красный/Белый) */
        .card-theme-15 {
            background-color: #F8BBD0;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23F8BBD0'/%3E%3C!-- Пицца --%3E%3Cpath fill='%23FFC107' d='M100 100l200 0 0 100z'/%3E%3Ccircle cx='200' cy='150' r='10' fill='%23D32F2F'/%3E%3C!-- Торт --%3E%3Crect x='150' y='300' width='100' height='50' fill='%23FF80AB'/%3E%3Ccircle cx='200' cy='300' r='5' fill='%23FFFFFF'/%3E%3C/svg%3E");
        }
        
        /* 16. Машины и дороги (Серый асфальт) */
        .card-theme-16 {
            background-color: #616161;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23616161'/%3E%3C!-- Дорожная разметка --%3E%3Crect x='180' y='100' width='40' height='50' fill='%23FFEB3B'/%3E%3Crect x='180' y='250' width='40' height='50' fill='%23FFEB3B'/%3E%3C!-- Машина (Красная) --%3E%3Crect x='50' y='400' width='100' height='40' fill='%23F44336' rx='5'/%3E%3Ccircle cx='65' cy='440' r='10' fill='%23424242'/%3E%3Ccircle cx='135' cy='440' r='10' fill='%23424242'/%3E%3C/svg%3E");
        }
        
        /* 17. Роботы и технологии (Голубой) */
        .card-theme-17 {
            background-color: #BBDEFB;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23BBDEFB'/%3E%3C!-- Робот --%3E%3Crect x='150' y='250' width='100' height='150' fill='%2390A4AE' rx='10'/%3E%3Crect x='170' y='270' width='60' height='20' fill='%23FF5252'/%3E%3Ccircle cx='200' cy='280' r='5' fill='%23FFFFFF'/%3E%3C!-- Антенна --%3E%3Cpath stroke='%23607D8B' stroke-width='4' d='M200 250v-50'/%3E%3Ccircle cx='200' cy='190' r='10' fill='%23FFEB3B'/%3E%3C/svg%3E");
        }
        
        /* 18. Пейзаж с горами (Оранжевый закат) */
        .card-theme-18 {
            background-color: #FF7043;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23FF7043'/%3E%3C!-- Горы --%3E%3Cpath fill='%23D32F2F' d='M0 400l100-100 100 50 100-100 100 150z'/%3E%3Cpath fill='%23E57373' d='M0 450l100-100 100 50 100-100 100 150z'/%3E%3C!-- Солнце --%3E%3Ccircle cx='350' cy='150' r='40' fill='%23FFEB3B'/%3E%3C/svg%3E");
        }
        
        /* 19. Динозавры (Светло-зеленый) */
        .card-theme-19 {
            background-color: #C8E6C9;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23C8E6C9'/%3E%3C!-- Динозавр (Тираннозавр, зеленый) --%3E%3Cpath fill='%234CAF50' d='M100 350c-20 0-30-50 20-50s50 50 0 50z'/%3E%3Ccircle cx='130' cy='320' r='10' fill='%238BC34A'/%3E%3C!-- Вулкан --%3E%3Cpath fill='%23BF360C' d='M300 400l50-100 50 100z'/%3E%3C/svg%3E");
        }
        
        /* 20. Игрушки и конструктор (Разноцветный) */
        .card-theme-20 {
            background-color: #FFEBEE;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 650'%3E%3C!-- Фон --%3E%3Crect width='400' height='650' fill='%23FFEBEE'/%3E%3C!-- Кубики --%3E%3Crect x='50' y='450' width='50' height='50' fill='%233F51B5'/%3E%3Crect x='120' y='400' width='60' height='60' fill='%23FFC107'/%3E%3C!-- Мягкая игрушка (Мишка) --%3E%3Ccircle cx='300' cy='350' r='30' fill='%238D6E63'/%3E%3Ccircle cx='280' cy='330' r='10' fill='%23A1887F'/%3E%3Ccircle cx='320' cy='330' r='10' fill='%23A1887F'/%3E%3C/svg%3E");
        }


    </style>
    <!-- Настройка конфигурации Tailwind для точных цветов оригинала -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        // Цвета, максимально приближенные к скриншоту
                        'original-pink-bg': '#FBEFF4', 
                        'original-purple': '#5A37B7', 
                        'original-score-text': '#585858', 
                        'original-card-footer': '#6A1B9A', /* Темно-фиолетовая нижняя часть карточки */
                        'original-resolve-text': '#7B1FA2', // Фиолетовый текст на кнопке "Решать"
                        'ucha-dark-text': '#333333', // Основной темный текст
                        'ucha-info-text': '#666666', // Серый текст для информации
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-original-pink-bg selection:bg-opacity-30 flex justify-center">

    <!-- Основной контейнер, имитирующий узкий экран мобильного приложения -->
    <div id="content-container" class="w-full h-full p-4">
        
        <!-- 1. Верхняя панель (Header) -->
        <header class="flex justify-between items-center py-2 mb-4">
            <!-- Левая часть: Профиль и меню -->
            <div class="flex items-center space-x-1">
                <!-- Контейнер для динамической иконки профиля -->
                <div class="h-8 w-8 rounded-full flex items-center justify-center text-sm font-bold">
                    <!-- Аватар будет установлен JavaScript'ом -->
                    <img id="profile-avatar" src="" alt="Аватар профиля" class="rounded-full h-full w-full object-cover border-2 border-white shadow-sm">
                </div>
                <!-- Маленькая иконка для выпадающего меню -->
                <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-down text-gray-700/80"><path d="m6 9 6 6 6-6"/></svg>
            </div>
            
            <!-- Правая часть: Кнопка "Полный доступ" -->
            <button class="flex items-center full-access-button text-white text-xs font-semibold px-4 py-2 rounded-lg hover:bg-[#5E35B1] transition duration-200">
                Полный доступ
                <!-- Иконка корзины (как на оригинале) -->
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-shopping-cart ml-2"><circle cx="8" cy="21" r="1"/><circle cx="19" cy="21" r="1"/><path d="M2.05 2.05h2l2.66 12.42a2 2 0 0 0 2 1.58h9.72a2 2 0 0 0 2-1.58L23 6H6"/></svg>
            </button>
        </header>

        <!-- 2. Раздел Олимпиады -->
        <div class="flex items-start mb-6 mt-2">
            <!-- Кнопка "Назад" -->
            <button class="bg-white/70 backdrop-blur-sm p-2 rounded-full shadow-md hover:bg-white transition duration-200 mr-1">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-left text-ucha-dark-text/90"><path d="m15 18-6-6 6-6"/></svg>
            </button>
            
            <!-- Информация о событии -->
            <div>
                <div class="flex items-center mb-1">
                    <!-- Иконка "Семья" -->
                    <div class="h-6 w-6 mr-2">
                        <!-- Используем иконку, максимально похожую на оригинал -->
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#3498DB" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-users-2"><path d="M14 19a6 6 0 0 0-12 0"/><circle cx="8" cy="10" r="4"/><path d="M20 9c-2.2 0-4 1.8-4 4v5c0 1.1.9 2 2 2h4c1.1 0 2-.9 2-2v-5c0-2.2-1.8-4-4-4z"/><path d="M19 13.5v.5"/><path d="M19 16v1"/></svg>
                    </div>
                    <!-- Заголовок олимпиады -->
                    <h2 class="text-ucha-dark-text font-medium text-base">Олимпиада «Безопасные дороги»</h2>
                </div>
                <!-- Описание олимпиады -->
                <p class="text-ucha-info-text text-sm mb-4 font-normal">для учеников 1–9 классов</p>
                
                <!-- Информация о туре - Текст Идёт первый тур -->
                <h3 class="text-ucha-dark-text font-bold text-base mb-0 leading-tight text-left">Идёт первый тур</h3>
                <p class="text-original-purple text-sm font-semibold leading-tight text-left">23 сентября – 26 октября</p>
            </div>
        </div>

        <!-- 3. Основной результат -->
        <section class="mb-6 mt-6">
            <!-- ГЛАВНЫЙ ЗАГОЛОВОК - ЛЕВОЕ ВЫРАВНИВАНИЕ -->
            <h1 class="text-ucha-dark-text font-extrabold text-xl mb-1 leading-snug text-left">Поздравляем, ты прошёл первый тур!</h1>
            <!-- Баллы - ЛЕВОЕ ВЫРАВНИВАНИЕ -->
            <p id="score-text" class="text-original-score-text font-medium text-base mb-6 text-left">Твои баллы: 72 из 80</p>
            
            <!-- Имитация Карточки Uchi.ru -->
            <div class="relative w-full aspect-[3/5] rounded-xl overflow-hidden shadow-xl">
                <!-- Блок иллюстрации и текста -->
                <div id="illustration-card" class="card-illustration-base w-full h-full flex flex-col justify-between items-center">
                    
                    <!-- Верхняя область текста (динамическая). -->
                    <div id="card-title-container" class="card-text-overlay p-4 w-full text-center pt-6 z-10">
                        <!-- Динамический заголовок будет установлен JS -->
                    </div>

                    <!-- Нижняя, фиолетовая область (Footer) -->
                    <div class="w-full bg-original-card-footer h-[100px] absolute bottom-0 z-20 flex items-start justify-center pt-4">
                        <!-- Кнопка "Решать" -->
                        <button id="resolve-button" class="w-11/12 bg-white text-original-resolve-text font-bold text-lg py-3 rounded-xl shadow-lg hover:bg-gray-100 transition duration-200">
                            Решать
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- 4. Блок "Подробнее" - Как на скриншоте (Под карточкой) -->
        <div id="details-block" class="mt-4 flex justify-center pb-4 text-original-purple font-semibold text-base transition duration-200 hover:opacity-80 cursor-pointer">
            Подробнее 
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-down ml-1 self-center"><path d="m6 9 6 6 6-6"/></svg>
        </div>


        <!-- 5. Дополнительный контент для обеспечения прокрутки -->
        <section class="mt-8 pb-32">
            <h2 class="text-ucha-dark-text font-bold text-xl mb-4">Другие олимпиады и курсы</h2>
            
            <!-- Блок 1 -->
            <div class="bg-white p-4 rounded-xl shadow-md mb-4 flex items-center hover:shadow-lg transition duration-200 border border-gray-100">
                <div class="h-10 w-10 bg-green-500 rounded-lg mr-4 flex items-center justify-center text-white font-bold text-lg">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-bus"><path d="M2 11h10"/><path d="M12 21h8"/><path d="M20 17v-8a2 2 0 0 0-2-2h-10a2 2 0 0 0-2 2v8a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2z"/><circle cx="7" cy="17" r="2"/><circle cx="17" cy="17" r="2"/></svg>
                </div>
                <div>
                    <h3 class="text-ucha-dark-text font-semibold">Олимпиада по русскому языку</h3>
                    <p class="text-gray-500 text-sm">Начнется 15 ноября</p>
                </div>
            </div>

        </section>
        
        <!-- Кнопка помощи/вопроса - Зеленая с вопросом -->
        <button class="fixed bottom-4 right-4 bg-[#75B50A] text-white p-3 rounded-full shadow-xl hover:bg-[#68A209] transition duration-200 z-30">
            <!-- Иконка вопроса -->
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-help-circle"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><path d="M12 17h.01"/></svg>
        </button>

    </div>

    <script>
        // Инициализация тем.
        const themes = [
            // Тема 1: Розовый Фон (близко к оригиналу) - Оставлена как основная тема фона, не зависит от карточки
            { 
                bodyBg: 'bg-original-pink-bg', 
                buttonBg: 'bg-[#673AB7]',
                buttonHover: 'hover:bg-[#5E35B1]',
                scoreTextColor: 'text-original-score-text'
            },
        ];

        // 20 РАЗНЫХ КАРТОЧЕК (Темы и иллюстрации, стилизованные под Uchi.ru)
        const cardTypes = [
            // Использование `card-theme-XX` для класса иллюстрации
            { 
                className: 'card-theme-01', 
                titleHTML: 'Узнавай<br>новое!',
                textColorClass: 'text-white' // Цвет текста на карточке
            },
            { 
                className: 'card-theme-02', 
                titleHTML: 'Решай<br>головоломки!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-03', 
                titleHTML: 'Путешествие<br>в космос!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-04', 
                titleHTML: 'Секреты<br>животных!',
                textColorClass: 'text-gray-900' // Светлый фон, темный текст
            },
            { 
                className: 'card-theme-05', 
                titleHTML: 'Подводные<br>приключения!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-06', 
                titleHTML: 'Найди<br>сокровища!',
                textColorClass: 'text-gray-900' // Светлый фон, темный текст
            },
            { 
                className: 'card-theme-07', 
                titleHTML: 'Фруктовый<br>квиз!',
                textColorClass: 'text-gray-900' // Светлый фон, темный текст
            },
            { 
                className: 'card-theme-08', 
                titleHTML: 'Геометрия<br>вокруг нас!',
                textColorClass: 'text-gray-900' 
            },
            { 
                className: 'card-theme-09', 
                titleHTML: 'Эпоха<br>Драконов!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-10', 
                titleHTML: 'Научные<br>опыты!',
                textColorClass: 'text-gray-900' 
            },
            { 
                className: 'card-theme-11', 
                titleHTML: 'Жизнь<br>в большом городе!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-12', 
                titleHTML: 'Музыкальный<br>ритм!',
                textColorClass: 'text-gray-900' 
            },
            { 
                className: 'card-theme-13', 
                titleHTML: 'Спортивный<br>челлендж!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-14', 
                titleHTML: 'Пустынные<br>загадки!',
                textColorClass: 'text-gray-900' 
            },
            { 
                className: 'card-theme-15', 
                titleHTML: 'Кулинарный<br>марафон!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-16', 
                titleHTML: 'ПДД<br>для всех!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-17', 
                titleHTML: 'Собери<br>робота!',
                textColorClass: 'text-gray-900' 
            },
            { 
                className: 'card-theme-18', 
                titleHTML: 'На вершине<br>мира!',
                textColorClass: 'text-white' 
            },
            { 
                className: 'card-theme-19', 
                titleHTML: 'Мир<br>динозавров!',
                textColorClass: 'text-gray-900' 
            },
            { 
                className: 'card-theme-20', 
                titleHTML: 'Конструктор<br>игрушек!',
                textColorClass: 'text-gray-900' 
            },
        ];
        
        // Массив с URL-адресами аватаров (мальчик и девочка)
        const avatars = [
            'https://placehold.co/32x32/87CEEB/FFFFFF?text=👦', // Мальчик (голубой фон)
            'https://placehold.co/32x32/FFB6C1/FFFFFF?text=👧'  // Девочка (розовый фон)
        ];

        document.addEventListener('DOMContentLoaded', () => {
            const body = document.body;
            const scoreText = document.getElementById('score-text');
            const fullAccessButton = document.querySelector('.full-access-button');
            const resolveButton = document.getElementById('resolve-button');
            const profileAvatar = document.getElementById('profile-avatar');
            const illustrationCard = document.getElementById('illustration-card');
            const cardTitleContainer = document.getElementById('card-title-container');

            // 1. Установка случайного аватара
            const selectedAvatarUrl = avatars[Math.floor(Math.random() * avatars.length)];
            if (profileAvatar) {
                profileAvatar.src = selectedAvatarUrl;
            }

            // 2. Установка основной темы
            const selectedTheme = themes[0]; 
            
            // Удаляем старые классы фона и цвета текста
            const allBgClasses = themes.map(t => t.bodyBg).join(' ');
            const allScoreColorClasses = themes.map(t => t.scoreTextColor).join(' ');

            body.classList.remove(...allBgClasses.split(' '));
            scoreText.classList.remove(...allScoreColorClasses.split(' '));
            
            // Применяем новый класс фона (bodyBg) и другие стили
            body.classList.add(selectedTheme.bodyBg, 'selection:bg-opacity-30', 'flex', 'justify-center');
            
            // Применяем стили к кнопке "Полный доступ"
            fullAccessButton.className = `flex items-center text-white text-xs font-semibold px-4 py-2 rounded-lg transition duration-200 full-access-button ${selectedTheme.buttonBg} ${selectedTheme.buttonHover}`;
            
            // Применяем цвет текста для баллов
            scoreText.classList.add(selectedTheme.scoreTextColor);
            
            // 3. Генерация случайного балла
            const maxScore = 80;
            // Генерируем случайный балл от 40 до 79
            const randomScore = Math.floor(Math.random() * (79 - 40 + 1)) + 40; 

            if (scoreText) {
                scoreText.textContent = `Твои баллы: ${randomScore} из ${maxScore}`;
            }

            // 4. Случайное отображение одной из 20 карточек
            const selectedCardType = cardTypes[Math.floor(Math.random() * cardTypes.length)];
            
            // Удаляем все предыдущие классы карточек (card-theme-XX)
            illustrationCard.className = 'card-illustration-base w-full h-full flex flex-col justify-between items-center';
            for (let i = 1; i <= 20; i++) {
                illustrationCard.classList.remove(`card-theme-${String(i).padStart(2, '0')}`);
            }
            
            // Применяем новый класс иллюстрации
            illustrationCard.classList.add(selectedCardType.className);
            
            // Устанавливаем заголовок карточки, используя класс text-4xl для большего акцента
            cardTitleContainer.innerHTML = `
                <h2 class="${selectedCardType.textColorClass} text-4xl font-extrabold text-center" style="text-shadow: 2px 2px 4px rgba(0,0,0,0.4);">
                    ${selectedCardType.titleHTML}
                </h2>
            `;

            // 5. Добавляем слушатель клика для кнопки "Решать" (имитация перехода)
            resolveButton.addEventListener('click', () => {
                const messageBox = document.createElement('div');
                messageBox.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50';
                messageBox.innerHTML = `
                    <div class="bg-white p-6 rounded-xl shadow-2xl max-w-sm w-full text-center">
                        <h3 class="text-xl font-bold mb-3 text-gray-800">Переход</h3>
                        <p class="text-gray-600 mb-6">Вы нажали кнопку "Решать" для карточки с темой: "${selectedCardType.titleHTML.replace('<br>', ' ')}" (Иллюстрация: ${selectedCardType.className}).</p>
                        <button id="close-message" class="bg-original-purple text-white font-semibold py-2 px-4 rounded-lg hover:bg-original-purple/80 transition duration-200">
                            Закрыть
                        </button>
                    </div>
                `;
                document.body.appendChild(messageBox);
                document.getElementById('close-message').addEventListener('click', () => {
                    document.body.removeChild(messageBox);
                });
            });
            
            // 6. Добавляем слушатель клика для "Подробнее" (имитация модального окна)
            document.getElementById('details-block').addEventListener('click', () => {
                 const messageBox = document.createElement('div');
                messageBox.className = 'fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50';
                messageBox.innerHTML = `
                    <div class="bg-white p-6 rounded-xl shadow-2xl max-w-sm w-full text-center">
                        <h3 class="text-xl font-bold mb-3 text-gray-800">Раздел "Подробнее"</h3>
                        <p class="text-gray-600 mb-6">Здесь должно быть дополнительное описание олимпиады или тура.</p>
                        <button id="close-message-details" class="bg-original-purple text-white font-semibold py-2 px-4 rounded-lg hover:bg-original-purple/80 transition duration-200">
                            Закрыть
                        </button>
                    </div>
                `;
                document.body.appendChild(messageBox);
                document.getElementById('close-message-details').addEventListener('click', () => {
                    document.body.removeChild(messageBox);
                });
            });
        });
    </script>
</body>
</html># DEVO
