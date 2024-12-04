<template>
    <div class="login-container">
      <div class="login-header">
        <h2>GİRİŞ YAP</h2>
        <button class="close-btn" @click="closeForm">×</button>
      </div>
      <div class="login-tabs">
        <button 
          class="tab" 
          :class="{ active: activeTab === 'login' }" 
          @click="activeTab = 'login'">
          ÜYE GİRİŞİ
        </button>
        <button 
          class="tab" 
          :class="{ active: activeTab === 'signup' }" 
          @click="activeTab = 'signup'">
          ÜYE OL
        </button>
      </div>
      <div class="login-content">
        <div v-if="activeTab === 'login'">
          <div class="input-group radio-group">
            <label>
              <input type="radio" name="login-method" value="email" checked /> E-Posta
            </label>
            <label>
              <input type="radio" name="login-method" value="phone" /> Telefon
            </label>
          </div>
          <div class="input-group line-input">
            
            <input type="email" id="email" placeholder="E-Posta Adresiniz" />
            <div class="input-group line-input">
    
    <div class="password-input">
      <input 
        :type="passwordVisible ? 'text' : 'password'" 
        id="password" 
        placeholder="Şifreniz" 
      />
      <button 
        class="toggle-password" 
        @click="togglePasswordVisibility" 
        type="button">
        {{ passwordVisible ? '👁' : '👁‍🗨' }}
      </button>
    </div>
  </div>
          </div>
          <div class="actions">
            <label>
              <input type="checkbox" /> Beni Hatırla
            </label>
            <a href="#" class="forgot-password">Şifremi Unuttum</a>
          </div>
          <button class="login-btn" @click="handleLogin">GİRİŞ YAP</button>
          <p class="continue-text" @click="continueWithoutLogin">ÜYE OLMADAN DEVAM ET</p>
        </div>
        <div v-else>
          <p>Üye olma ekranı başka yerde yer alacak.</p>
        </div>
      </div>
      <div class="social-login">
        <p>SOSYAL HESAP İLE GİRİŞ YAP</p>
        <div class="social-buttons">
          <button class="facebook-btn">F</button>
          <button class="google-btn">G</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        activeTab: 'login', // Default tab
        passwordVisible: false, // Şifre görünürlüğü
      };
    },
    methods: {
      closeForm() {
        alert("Form kapatıldı!");
      },
      handleLogin() {
        alert("Giriş yapıldı.");
      },
      continueWithoutLogin() {
        alert("Üye olmadan devam edildi.");
      },
      togglePasswordVisibility() {
        this.passwordVisible = !this.passwordVisible;
      },
    },
  };
  </script>
  
  <style scoped>
  /* Genel Stil */
  .login-container {
    width: 400px;
    margin: 20px auto;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 50px;
    font-family: Arial, sans-serif;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  .login-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
  .login-header h2 {
    margin: 0;
    font-size: 1.5rem;
  }
  .close-btn {
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
  }
  .login-tabs {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  .tab {
    flex: 1;
    padding: 10px 0;
    text-align: center;
    background: #f4f4f4;
    border: none;
    cursor: pointer;
  }
  .tab.active {
    border-bottom: 2px solid #000;
    font-weight: bold;
  }
  .input-group {
    margin-bottom: 20px;
  }
  .line-input label {
    font-size: 0.9rem;
    margin-bottom: 5px;
    display: block;
  }
  .line-input input {
    width: 100%;
    border: none;
    border-bottom: 1px solid #ddd;
    outline: none;
    padding: 5px 0;
    font-size: 1rem;
    transition: border-bottom-color 0.3s;
  }
  .line-input input:focus {
    border-bottom-color: #000;
  }
  .password-input {
    margin-top: 20px;
    display: flex;
    align-items: center;
  }
  
  .password-input input {
    flex: 1;
    border: none;
    border-bottom: 1px solid #ddd;
    padding: 5px 0;
    outline: none;
    font-size: 1rem;
    transition: border-bottom-color 0.3s;
  }
  
  .password-input input:focus {
    border-bottom-color: #000;
  }
  
  .toggle-password {
    background: none;
    border: none;
    font-size: 1rem;
    cursor: pointer;
    margin-left: 5px;
    padding: 0;
  }
  
  .actions {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
  .forgot-password {
    color: #30242a;
    text-decoration: none;
    font-size: 0.9rem;
  }
  
  .forgot-password:hover {
    text-decoration: underline;
    cursor: pointer;
  }
  
  .login-btn {
    width: 100%;
    padding: 10px;
    border: none;
    background: #000;
    color: #fff;
    margin-bottom: 10px;
    cursor: pointer;
    border-radius: 4px;
  }
  
  .continue-text {
    text-align: center;
    font-size: 0.9rem;
    color: #444;
    text-decoration: underline;
    cursor: pointer;
    margin-top: 10px;
  }
  
  .social-login {
    text-align: center;
  }
  .social-buttons {
    display: flex;
    justify-content: center;
    gap: 10px;
  }
  .facebook-btn,
  .google-btn {
    width: 40px;
    height: 40px;
    border: none;
    border-radius: 50%;
    font-size: 1.2rem;
    color: #fff;
    cursor: pointer;
  }
  .facebook-btn {
    background: #3b5998;
  }
  .google-btn {
    background: #db4437;
  }
  button:hover {
  background-color: #878787;
  }
  </style>