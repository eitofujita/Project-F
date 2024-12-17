<template>
    <div>
      <button class="contact-button" @click="toggleForm">Связь с нами</button>
      <transition name="fade">
        <form
          v-if="isVisible"
          @submit.prevent="handleSubmit"
          ref="formRef"
          class="contact-form"
        >
          <input
            v-model="formData.name"
            name="name"
            placeholder="Ваше имя"
            required
          />
          <input
            v-model="formData.email"
            name="email"
            type="email"
            placeholder="Ваш email"
            required
          />
          <textarea
            v-model="formData.message"
            name="message"
            placeholder="Ваше сообщение"
            required
          ></textarea>
          <button type="submit">Отправить</button>
          <p>{{ statusMessage }}</p>
        </form>
      </transition>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        isVisible: false,
        formData: {
          name: localStorage.getItem('name') || '',
          email: localStorage.getItem('email') || '',
          message: localStorage.getItem('message') || '',
        },
        statusMessage: '',
      };
    },
    methods: {
      toggleForm() {
        this.isVisible = !this.isVisible;
      },
      handleSubmit() {
        // ローカルストレージにデータを保存
        localStorage.setItem('name', this.formData.name);
        localStorage.setItem('email', this.formData.email);
        localStorage.setItem('message', this.formData.message);
  
        // データ送信
        fetch('https://example.com/api/contact', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(this.formData),
        })
          .then(() => {
            this.statusMessage = 'Сообщение отправлено!';
          })
          .catch(() => {
            this.statusMessage = 'Ошибка отправки. Попробуйте снова.';
          });
      },
    },
  };
  </script>
  
  <style scoped>
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.5s;
  }
  .fade-enter-from,
  .fade-leave-to {
    opacity: 0;
  }
  </style>
  