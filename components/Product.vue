<template>
  <div class="product-card">
    <!-- İndirim Koduyla Başlangıç -->
    <div class="discount-info">
      1500 TL'ye 250 TL indirim Kod: <span>DCM250</span>
    </div>

    <!-- Ürün Görseli ve Favori Butonu -->
    <div class="image-container">
      <!-- Fotoğraflar -->
      <div class="image-slider" @mouseover="changeImageOnHover" @mouseleave="resetImage">
        <img :src="activeImage" :alt="product.name" class="product-image" />
      </div>
      <button class="wishlist-button">♡</button>
    </div>

    <!-- Ürün Bilgileri -->
    <div class="product-info">
      <!-- Ürün Adı -->
      <h2 class="product-title">{{ product.name }}</h2>

      <!-- Yıldızlı Puan -->
      <div class="rating">
        ★★★★★ <span>({{ product.reviews }} yorum)</span>
      </div>

      <!-- Fiyatlar -->
      <div class="price-info">
        <span class="old-price">{{ product.oldPrice }} TL</span>
      </div>

      <!-- Sepetteki Fiyat -->
      <div class="basket-price">
        Sepette <span>{{ product.basketPrice }} TL</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      // Ürünün birden fazla görseli
      images: [
        '/images/mont.jpg', // Görselleri public klasörüne yerleştirin
        '/images/mmmmm.jpg',
        '/images/oooo.jpg',
      ],
      activeImage: '/images/mont.jpg', // Başlangıçta ilk görsel
      currentIndex: 0, // Görselin sırası
    };
  },
  methods: {
    // Fare üzerine gelindiğinde diğer fotoğrafı göster
    changeImageOnHover() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length; // Görseller arasında dönme
      this.activeImage = this.images[this.currentIndex];
    },
    // Fare imleci fotoğrafın üzerinden ayrıldığında fotoğrafı geri al
    resetImage() {
      this.activeImage = this.images[0]; // İlk fotoğrafa geri dön
      this.currentIndex = 0; // Başlangıç fotoğrafına dön
    },
  },
};
</script>

<style scoped>
/* Ürünü tam ekran ortalamak için Flexbox kullanıyoruz */
.product-card {
  display: flex;
  flex-direction: column;
  justify-content: flex-start; /* Ürün bileşenlerini yukarıya yasladık */
  align-items: center;
  width: 100%;
  max-width: 250px; /* Kartın genişliği */
  height: 550px; /* Kartın yüksekliğini arttırdım */
  border: 1px solid #ddd;
  border-radius: 10px;
  overflow: hidden;
  background-color: #fff;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  font-family: Arial, sans-serif;
  transition: transform 0.2s ease;
  margin: 20px;
  padding: 15px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%); /* Ortada konumlandır */
}

/* Ürün kartı hover efekti */
.product-card:hover {
  transform: translate(-50%, -50%) scale(1.05);
}

/* İndirim bilgisi */
.discount-info {
  background-color: #f8f9fa;
  font-size: 12px;
  text-align: center;
  padding: 5px;
  color: #333;
}

.discount-info span {
  font-weight: bold;
  color: #d9534f;
}

/* Görsel alanı */
.image-container {
  position: relative;
  width: 100%;
  height: 480px; /* Fotoğraf alanının yüksekliğini arttırdım */
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-slider {
  display: flex;
  flex-direction: row;
  justify-content: flex-start; /* Yatayda fotoğrafları sola hizaladık */
  width: 600%; /* 3 fotoğrafın tamamını gösterecek kadar geniş */
  transition: transform 0.5s ease;
}

.product-image {
  width: 33.33%; /* Fotoğrafların her biri 1/3 genişlikte olacak şekilde ayarlandı */
  height: 300%; /* Fotoğraf boyutu tam dolduracak şekilde ayarlandı */
  object-fit: cover;
}

.wishlist-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: white;
  border: none;
  border-radius: 60%;
  padding: 4px;
  font-size: 18px;
  color: #d9534f;
  cursor: pointer;

}

.wishlist-button:hover {
  background: #000000;
  color: rgb(255, 255, 255);
}

/* Ürün bilgileri */
.product-info {
  padding: 2px; /* Ürün bilgileri için daha sıkı bir aralık */
  height: 100%; /* Ürün bilgileri alanının yüksekliği arttırıldı */
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-top: 100px; /* Ürün bilgilerini daha aşağıya kaydırmak için */
}

.product-title {
  font-size: 14px;
  font-weight: 600;
  color: #333;
  margin-bottom: -90px; /* Ürün ismi ile fiyatlar arasındaki boşluk azaltıldı */
  line-height: 1.3;
}

.rating {
  font-size: 15px;
  color: #000000;
  margin-bottom: -70px; /* Yorumlar arasındaki boşluk azaltıldı */
}

.rating span {
  font-size: 12px;
  color: #555;
}

/* Fiyat bilgisi */
.price-info {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 5px; /* Fiyatlar arasındaki boşluk azaltıldı */
}

.old-price {
  text-decoration: line-through;
  color: #000000;
  font-size: 14px;
  margin-bottom: 0px;
}

/* Sepet fiyatı */
.basket-price {
  font-size: 14px;
  color: #970000;
  font-weight: bold;
}
</style>
