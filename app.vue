<script setup>
import { ref } from "vue";

// Tüm bileşenleri import et
import Header from "@/components/Header.vue";
import Carousel from "@/components/Carousel.vue";
import Footer from "@/components/Footer.vue";
import CategoryMenu from "@/components/CategoryMenu.vue";
import Login from "@/components/Login.vue";
import Register from "@/components/Register.vue";
import Cart from "@/components/Cart.vue";
import Help from "@/components/Help.vue";
import Collections from "@/components/Collections.vue";
import Product from "@/components/Product.vue";

// Aktif bileşeni kontrol etmek için state
const activeComponent = ref("Welcome"); // Başlangıçta Hoş Geldiniz mesajı
</script>



<template>
  <div>
    <!-- Butonlar -->
    <div class="button-container">
      <button @click="activeComponent = 'Header'">Header</button>
      <button @click="activeComponent = 'Carousel'">Carousel</button>
      <button @click="activeComponent = 'Footer'">Footer</button>
      <button @click="activeComponent = 'CategoryMenu'">Kategoriler</button>
      <button @click="activeComponent = 'Login'">Giriş Yap</button>
      <button @click="activeComponent = 'Register'">Üye ol</button>
      <button @click="activeComponent = 'Cart'">Sepetim</button>
      <button @click="activeComponent = 'Help'">Yardım</button>
      <button @click="activeComponent = 'Collections'">Favorilerim</button>
      <button @click="activeComponent = 'Product'">Ürünler</button>
    </div>

    <!-- Dinamik Bileşen Alanı -->
    <div>
      <!-- Hoş geldiniz mesajı -->
      <div v-if="activeComponent === 'Welcome'" class="welcome-message">
        <h2>Hoş Geldiniz!</h2>
        <p>Yukarıdaki menüden bir seçenek seçerek devam edebilirsiniz.</p>
      </div>

      <!-- Dinamik Bileşenler -->
      <Carousel v-if="activeComponent === 'Carousel'" />
      <Header v-if="activeComponent === 'Header'" />
      <Footer v-if="activeComponent === 'Footer'" />
      <CategoryMenu v-if="activeComponent === 'CategoryMenu'" />
      <Login v-if="activeComponent === 'Login'" />
      <Register v-if="activeComponent === 'Register'" />
      <Cart v-if="activeComponent === 'Cart'" />
      <Help v-if="activeComponent === 'Help'" />
      <Collections v-if="activeComponent === 'Collections'" />
      <Product v-if="activeComponent === 'Product'" 
      :product="{
    name: 'Su İtici Hafif Şişme Mont Slim Fit Dar Kesim Kapüşonlu Fermuarlı Cep',
    reviews: 722,
    oldPrice: 1299.99,
    basketPrice: 999.99
  }"/>
    </div>
  </div>
</template>



<style scoped>
.button-container {
  display: flex;
  justify-content: center;
  margin: 20px 0;
  gap: 10px;
}

.button-container button {
  padding: 10px 20px;
  background-color: #000000;
  color: white;
  border: none;
  border-radius: 40px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.button-container button:hover {
  background-color: #0056b3;
}

/* Hoş geldiniz mesajı */
.welcome-message {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh; /* Yüksekliği ekran boyutuna göre ayarla */
  text-align: center;
  color: #333;
  background-color: #c9c8c8; /* Yumuşak bir arka plan rengi */
  padding: 20px;
  border-radius: 8px; /* Kenarları yuvarlat */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Hafif gölge efekti */
}

.welcome-message h2 {
  font-size: 36px;
  font-weight: 600;
  margin-bottom: 10px;
  color: #000000; /* Başlık rengi */
}

.welcome-message p {
  font-size: 18px;
  color: #555;
}
</style>


