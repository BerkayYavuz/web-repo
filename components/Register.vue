<template>
    <div class="signup-form">
      <div class="tabs">
        <button :class="{ active: activeTab === 'login' }" @click="activeTab = 'login'">Üye Girişi</button>
        <button :class="{ active: activeTab === 'signup' }" @click="activeTab = 'signup'">Üye Ol</button>
      </div>
  
      <div v-if="activeTab === 'signup'" class="form-container">
        <h3>Sosyal Hesap ile Giriş Yap</h3>
        <div class="social-buttons">
          <button class="social-login facebook">F<i class="fab fa-facebook-f"></i></button>
          <button class="social-login google">G<i class="fab fa-google"></i></button>
        </div>
  
        <h4>E-Posta Adresi ile Üye Ol</h4>
        <form @submit.prevent="handleSubmit">
          <div class="form-group">
            <input type="text" v-model="form.firstName" placeholder="Adınız*" required />
            <input type="text" v-model="form.lastName" placeholder="Soyadınız*" required />
          </div>
  
          <div class="form-group">
            <input type="email" v-model="form.email" placeholder="E-Posta Adresiniz*" required />
            <input type="tel" v-model="form.phone" placeholder="Cep Telefonunuz*" required />
          </div>
  
          <div class="form-group password-group">
            <input
              type="password"
              v-model="form.password"
              placeholder="Şifreniz*"
              required
            />
            <ul class="password-rules">
              <li>En az bir büyük harf</li>
              <li>En az bir küçük harf</li>
              <li>En az bir rakam</li>
              <li>8-15 karakter</li>
            </ul>
          </div>
  
          <div class="form-group">
            <label>Doğum Tarihiniz</label>
            <div class="birthdate">
              <select v-model="form.birthDay">
                <option disabled selected>Gün</option>
                <option v-for="d in 31" :key="d">{{ d }}</option>
              </select>
              <select v-model="form.birthMonth">
                <option disabled selected>Ay</option>
                <option v-for="m in months" :key="m">{{ m }}</option>
              </select>
              <select v-model="form.birthYear">
                <option disabled selected>Yıl</option>
                <option v-for="y in years" :key="y">{{ y }}</option>
              </select>
            </div>
          </div>
  
          <div class="form-group gender-group">
    <label>Cinsiyetiniz</label>
    <div class="radio-group">
      <input type="radio" id="female" value="Kadın" v-model="form.gender" />
      <label for="female">Kadın</label>
      <input type="radio" id="male" value="Erkek" v-model="form.gender" />
      <label for="male">Erkek</label>
      <input type="radio" id="unspecified" value="Belirtmek istemiyorum" v-model="form.gender" />
      <label for="unspecified">Belirtmek istemiyorum</label>
    </div>
  </div>
  
  <div class="form-group">          
              <label >
                Kişisel verilerimin işlenmesini kabul ediyorum.
               </label>
              <input type="checkbox" v-model="form.acceptTerms" />
            </div>
  
  
  
          <button type="submit" class="submit-button">Üye Ol</button>
        </form>
  
        <p class="continue-without-signup">Üye olmadan devam et</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        activeTab: "signup",
        form: {
          firstName: "",
          lastName: "",
          email: "",
          phone: "",
          password: "",
          birthDay: null,
          birthMonth: null,
          birthYear: null,
          gender: null,
          acceptTerms: false,
        },
        months: [
          "Ocak",
          "Şubat",
          "Mart",
          "Nisan",
          "Mayıs",
          "Haziran",
          "Temmuz",
          "Ağustos",
          "Eylül",
          "Ekim",
          "Kasım",
          "Aralık",
        ],
        years: Array.from({ length: 100 }, (_, i) => new Date().getFullYear() - i),
      };
    },
    methods: {
      handleSubmit() {
        if (!this.form.acceptTerms) {
          alert("Lütfen şartları kabul edin.");
          return;
        }
        console.log("Form gönderildi", this.form);
      },
    },
  };
  </script>
  
  <style scoped>
  /* Genel Ayarlar */
  .signup-form {
    max-width: 500px;
    margin: 0 auto;
    font-family: Arial, sans-serif;
    color: #333;
  }
  
  .tabs {
    display: flex;
    justify-content: space-around;
    margin-bottom: 20px;
  }
  
  .tabs button {
    flex: 1;
    padding: 10px;
    font-size: 16px;
    border: none;
    background: #f5f5f5;
    cursor: pointer;
    transition: background 0.3s ease, color 0.3s ease;
  }
  
  .tabs button.active {
    background: #000;
    color: #fff;
    font-weight: bold;
  }
  
  .form-container {
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
    background: #fff;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  }
  .form-group {
    
    /* Yazıyı sola hizalar */
    align-items: center; /* Dikeyde ortalama */
  }
  
  .form-group input[type="checkbox"] {
    margin-left: 10px; /* Yazı ile kutucuk arasına boşluk ekler */
  }
  
  
  .social-buttons {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
  }
  
  .social-login {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    color: #fff;
    cursor: pointer;
  }
  
  .social-login.facebook {
    background: #3b5998;
  }
  
  .social-login.google {
    background: #db4437;
  }
  
  .form-group {
    width: 420px;
    margin-bottom: 10px; /* Yüksekliği kısaltmak için margin değerini küçülttük */
    border: none; /* Dış çizgileri kaldırdık */
  }
  
  input,
  select {
    width: 100%;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 5px;
    font-size: 16px;
    margin-top: 8px;
    transition: border-color 0.3s;
  }
  
  input:focus,
  select:focus {
    border-color: #000;
  }
  
  .password-rules {
    font-size: 12px;
    color: #ff0000;
    margin-top: 8px;
    padding-left: 20px;
  }
  
  /* Cinsiyet Seçimi Stil Ayarları */
  .gender-group {
    margin-bottom: 20px;
  }
  
  .gender-group label {
    font-size: 14px;
    font-weight: bold;
    margin-bottom: 8px;
    display: block;
    color: #333;
  }
  
  .radio-group {
    display: flex;
    justify-content: flex-start; /* Sağdaki boşluğu azaltmak için */
    gap: 10px; /* Aralarındaki boşluk */
  }
  
  .radio-group input[type="radio"] {
    width: auto;
    height: 18px;
    margin-right: 0px;
    cursor: pointer;
  }
  
  .radio-group label {
    font-size: 14px;
    color: #666;
    display: inline-block;
    cursor: pointer;
    transition: color 0.3s ease;
  }
  
  .radio-group label:hover {
    color: #000;
  }
  
  .radio-group input[type="radio"]:checked + label {
    color: #000;
    font-weight: bold;
  }
  
  /* Cinsiyet tercihi kutularının hover efektleri */
  .radio-group input[type="radio"]:focus {
    outline: none;
    border: 2px solid #000;
  }
  
  .radio-group input[type="radio"]:checked {
    background-color: #000;
    border: 2px solid #000;
  }
  
  .radio-group input[type="radio"]:hover {
    background-color: #f0f0f0;
  }
  
  .radio-group label:active {
    color: #000;
    font-weight: bold;
  }
  
  /* Kişisel Veriler Onayı */
  .terms {
    display: flex; /* Flexbox ile yatayda hizalama */
    align-items: center; /* Dikeyde ortalama */
    justify-content: flex-start; /* Yazıyı sola hizalar */
  }
  
  .terms input[type="checkbox"] {
    margin-right: 10px; /* Kutucuk ile yazı arasına boşluk ekledik */
  }
  
  .terms label {
    font-size: 14px;
    color: #333;
  }
  
  
  
  .submit-button {
    display: block; /* Butonu bir blok elementi gibi davranmaya zorlar */
    margin: 0 auto; /* Otomatik olarak ortalar */
    background: #000;
    color: #fff;
    padding: 12px;
    border: none;
    cursor: pointer;
    font-size: 16px;
    border-radius: 5px;
    transition: background 0.3s ease;
  }
  
  
  .submit-button:hover {
    background: #444;
  }
  
  .continue-without-signup {
    text-align: center;
    margin-top: 20px;
    color: #888;
    cursor: pointer;
  }
  
  .continue-without-signup:hover {
    color: #000;
  }
  </style>
  