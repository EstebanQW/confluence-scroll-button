# Для чего этот скрипт
Этот скрипт добавляет кнопку "Переместиться наверх" на страницу Confluence. Когда пользователь прокручивает страницу вниз (более 100px), кнопка становится видимой, и при ее нажатии пользователь перемещается на самый верх страницы.<br>

До:<br>

После:<br>

## Шаги для использования:
1.	Перейдите на страницу Confluence, где находится таблица с данными сотрудников.<br>
2.	Откройте страницу для редактирования.<br>
3.	Добавьте макрос HTML на страницу:<br>
    1. Нажмите "Вставить прочий контент" > "Другие макросы" > "HTML".<br>
     ![image](https://github.com/user-attachments/assets/ccdf7533-8269-4653-995d-396a64db083d)
     ![image](https://github.com/user-attachments/assets/8829a091-cac8-4249-926d-70cbf3096e1d)
     ![image](https://github.com/user-attachments/assets/b8f6b4cb-2fd3-4467-a5fa-6232c7bf7e88)
     ![image](https://github.com/user-attachments/assets/332843ac-55b1-4fb4-8895-24f03c0b55c3)
    2. Вставьте код в поле макроса.<br>
4.	Сохраните изменения.<br>
5.	При загрузке страницы, скрипт автоматически выполнится, выделив строку с вашим ФИО, если оно присутствует в таблице.

## Код скрипта:
```
<!-- Кнопка для перемещения наверх -->
<button id="scrollToTopButton" onclick="scrollToTop()">Переместиться наверх</button>

<script>
// Функция для прокрутки страницы наверх
function scrollToTop() {
    window.scrollTo({
        top: 0,
        behavior: 'smooth'
    });
}

// Добавляем кнопку на страницу после ее загрузки
window.addEventListener('load', () => {
    const button = document.getElementById('scrollToTopButton');
    const content = document.getElementById('content');
    content.appendChild(button);  // Добавляем кнопку
    // Скрываем кнопку, если страница сверху
    window.addEventListener('scroll', () => {
        if (window.pageYOffset > 100) {
            button.style.display = 'block'; // Показываем кнопку, когда скролл > 100px
        } else {
            button.style.display = 'none';  // Скрываем кнопку, если на верху страницы
        }
    });
});
</script>

<style>
/* Стиль кнопки "Переместиться наверх" */
#scrollToTopButton {
    font-weight: bold;
    font-family: Arial, serif;
    font-size: 14px;
    text-align: center;
    position: sticky;
    background-color: #b9b9b9;
    bottom: 25px;
    top: 0;
    left: 100%;
    width: 160px;
    height: 40px;
    border-radius: 15px;
    box-shadow: 0px 3px 5px #cacaca;
    cursor: pointer;
    transition: box-shadow 0.3s ease;
    display: none; /* Скрытая кнопка по умолчанию */
}

/* Эффект при нажатии на кнопку */
#scrollToTopButton:active {
    top: 0.4em;
    box-shadow: 0 0 0 60px rgba(206, 87, 142, 0.3) inset;
}

/* Эффект при наведении на кнопку */
#scrollToTopButton:hover {
    box-shadow: 0px 2px 15px 0px #717171;
}
</style>

```