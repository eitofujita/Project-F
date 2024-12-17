<template>
    <nav>
      <button class="menu-toggle" @click="toggleMenu">Меню</button>
      <ul :class="{ visible: isVisible }" class="menu-list">
        <li><a href="#home">Главная</a></li>
        <li><a href="#about">О нас</a></li>
        <li><a href="#services">Услуги</a></li>
        <li><a href="#contact">Контакты</a></li>
      </ul>
    </nav>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isVisible: false,
      };
    },
    methods: {
      toggleMenu() {
        this.isVisible = !this.isVisible;
      },
    },
  };
  </script>
 
 <style scoped>
/* ナビゲーション全体のスタイル */
nav {
  position: relative;
  font-family: Arial, sans-serif;
}

/* メニューボタンのスタイル */
.menu-toggle {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.menu-toggle:hover {
  background-color: #0056b3;
}

/* メニューリストのスタイル */
.menu-list {
  list-style: none;
  margin: 10px 0 0;
  padding: 0;
  background-color: #f5f5f5;
  border: 1px solid #ddd;
  border-radius: 5px;
  overflow: hidden;

  /* 初期状態：非表示 */
  max-height: 0;
  opacity: 0;
  visibility: hidden;
  transition: max-height 0.3s ease, opacity 0.3s ease, visibility 0.3s ease;
}

/* メニューリストが表示される状態 */
.menu-list.visible {
  max-height: 500px; /* 十分に大きな値を設定 */
  opacity: 1;
  visibility: visible;
}

/* メニューリストの各リンクのスタイル */
.menu-list li {
  padding: 10px;
  border-bottom: 1px solid #ddd;
}

.menu-list li:last-child {
  border-bottom: none;
}

.menu-list li a {
  text-decoration: none;
  color: #007bff;
  font-size: 16px;
  transition: color 0.3s ease;
}

.menu-list li a:hover {
  color: #0056b3;
}
</style>
@media (max-width: 768px) {
    .menu-list {
      text-align: center;
    }
    .menu-toggle {
      width: 100%;
    }
  }
  
  