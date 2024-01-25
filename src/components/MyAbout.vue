<template>
    <div class="about">
        <h3>В данном проекте реализованно:</h3>
        <ul 
            class="list"
        >
            <li v-for="skill in skills" :key="skill">{{ skill }}</li>
        </ul>
    </div>
</template>
    
<script>
export default {
    data() {
        return {
            skills: [
                'Создание проекта',
                'Интерполяция',
                'Директива V-ON слушатели событий',
                'Директива V-FOR отрисовка массивов',
                'Передаем данные в компонент через Props',
                '$emit для передачи данных родителю',
                'Двустороннее связывание',
                'Анимации transition group',
                'Постраничный вывод постов',
                'Биндинг классов и стилей',
                'Создание своих UI компонентов',
                'Глобальная регистрация компонента',
                'Отрисовка по условию V-IF и V-ELSE',
                'Декомпозиция на переиспользуемые компоненты',
                'Создание модального окна',
                'Получение постов с сервера',
                'Использование библиотеки Axios',
                'Сортировка, добавление, удаление и поиск постов',
                'Применение свойст watch и computed',
                'VUE-ROUTER постраничная навигация',
            ],

        }
    },
}
    
</script>
    
<style>
.about {
    margin-top: 15px;
    border: 1px solid #00a144;
    border-radius: 5px;
    padding: 10px;
    min-width: 100px;
    background-color: #3ba1001e;
}

.list {
    list-style-type: none;
}

.list li {
    padding-left: 10px;
	font-size: 18px;
}

</style>