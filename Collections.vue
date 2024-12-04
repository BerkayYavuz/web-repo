<template>
    <div class="collections-page">
      <div class="container">
        <div class="left-section">
          <!-- Hesap Bilgileri -->
          <div class="account-info">
            <h2>Hesap Bilgileri</h2>
            <ul>
              <li>Sipariş Takibi</li>
              <li>Çerez Tercihleri</li>
              <li @click="toggleGiftClubMenu" class="gift-club">
                Defacto Gift Club
                <span v-if="showGiftClubMenu">▼</span>
                <span v-if="!showGiftClubMenu">►</span>
              </li>
              <div v-if="showGiftClubMenu" class="gift-club-menu">
                <ul>
                  <li>Hediye Kartı Kullan</li>
                  <li>Hediye Kartı Bakiye Sorgulama</li>
                  <li>Hediye Kartı Yükle</li>
                </ul>
              </div>
              <li>Yardım</li>
            </ul>
          </div>
        </div>
  
        <div class="right-section">
          <!-- Favoriler -->
          <div class="favorites-section">
            <h1>Favorilerim</h1>
            <div class="search-bar">
              <input
                type="text"
                v-model="searchQuery"
                placeholder="Favorilerimde Ara"
              />
            </div>
            <div class="favorites-list">
              <div
                v-for="(item, index) in filteredFavorites"
                :key="index"
                class="favorite-item"
              >
                <div class="item-header">
                  <h2>{{ item.name }}</h2>
                  <button @click="toggleFavorite(item)" class="heart-button">
                    <span v-if="item.isFavorite">♥</span>
                    <span v-if="!item.isFavorite">♡</span>
                  </button>
                </div>
                <div class="item-info">
    <p>{{ item.price }} TL</p>
    <p class="cart-price">Sepette: {{ item.cartPrice }} TL</p>
  </div>
  
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: '',
        favorites: [
          { name: 'Comfort Regular Fit Sweatshirt', price: 499.99, cartPrice: 399.99, isFavorite: true },
          { name: 'Straight Wide Yüksek Bel Uzun Jean Yıkanmalı Pantolon', price: 999.99, cartPrice: 899.99, isFavorite: false },
          { name: 'Kadın 2’li Mat Gold Küpe', price: 299.99, cartPrice: 239.99, isFavorite: false },
          { name: 'Regular Fit Bloklu Yaka Kışlık Sweatshirt', price: 499.99, cartPrice: 399.99, isFavorite: true },
        ],
        showGiftClubMenu: false,
      };
    },
    computed: {
      filteredFavorites() {
        return this.favorites.filter(item =>
          item.name.toLowerCase().includes(this.searchQuery.toLowerCase())
        );
      },
    },
    methods: {
      toggleFavorite(item) {
        item.isFavorite = !item.isFavorite;
      },
      toggleGiftClubMenu() {
        this.showGiftClubMenu = !this.showGiftClubMenu;
      },
    },
  };
  </script>
  
  <style scoped>
  .collections-page {
    display: flex;
    justify-content: space-between;
    padding: 20px;
  }
  
  .container {
    display: flex;
    width: 100%;
  }
  
  .left-section {
    flex: 1;
    margin-right: 10px;
  }
  
  .right-section {
    flex: 5;
  }
  
  .account-info {
    max-width: 250px; /* Sol kısmın genişliğini daraltma */
    margin-right: 20px;
  }
  
  .account-info h2 {
    font-size: 22px; /* Başlık font boyutunu biraz küçülttük */
    margin-bottom: 15px; /* Alt boşluğu biraz küçülttük */
    font-family: 'Helvetica Neue', Arial, sans-serif;
    color: #333;
  }
  
  .account-info ul {
    list-style: none;
    padding: 0;
  }
  
  .account-info ul li {
    margin-bottom: 8px; /* Her öğenin alt boşluğunu küçülttük */
    font-size: 14px; /* Yazı font boyutunu biraz küçülttük */
    font-family: 'Arial', sans-serif;
    color: #666;
    cursor: pointer;
    transition: color 0.3s ease;
  }
  
  
  .account-info ul li:hover {
    color: #ff0000;
  }
  
  .gift-club {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: bold;
  }
  
  .gift-club-menu {
    margin-top: 10px;
    font-size: 14px;
    background-color: #f8f9fa;
    padding: 10px;
    
  }
  
  .gift-club-menu ul {
    list-style: none;
    padding: 0;
  }
  
  .gift-club-menu ul li {
    margin-bottom: 8px;
  }
  
  .favorites-section {
    border: 1px solid #ccc;
    padding: 20px;
    border-radius: 80px;
    width: 100%; /* Favoriler bölümünün genişliğini %100 yapıyoruz */
    margin-left: 0; /* Sol kaymayı sıfırlıyoruz */
    margin-right: 100px; /* Sağda otomatik boşluk bırakıyoruz, sola kaydırılmış olur */
  }
  
  
  .search-bar {
    margin-bottom: 20px;
  }
  
  .search-bar input {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .favorites-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between; /* Ögeleri daha geniş şekilde yerleştir */
  }
  
  .favorite-item {
    width: 48%; /* Her bir öğenin genişliğini %48 yaparak daha geniş bir düzen sağlıyoruz */
    margin-bottom: 20px;
  }
  
  .favorite-item:nth-child(2n) {
    margin-right: 20px;
  }
  
  .favorite-item .item-header {
    display: flex;
    justify-content: space-between;
  }
  
  .heart-button {
    background: none;
    border: none;
    color: #ff6b6b;
    font-size: 24px;
    cursor: pointer;
  }
  
  .heart-button:hover {
    color: #ff3b3b;
  }
  
  .favorite-item .item-info p {
    margin: 5px ;
    font-size: 14px;
  }
  .cart-price {
    color: red; /* Sepetteki fiyatı kırmızı renkle yaz */
    font-weight: bold; /* Daha belirgin hale getirmek için kalın font */
    font-size: 14px; /* Uygun bir yazı boyutu */
  }
  
  
  </style>
  