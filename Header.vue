<template>
    <header class="header">
      <div class="container">
        <!-- Logo Resmi -->
        <div class="logo">
          <img src="/logo.png" alt="DeFacto Logo" />
        </div>
  
        <!-- Menü -->
        <nav class="menu">
          <ul>
            <li>KADIN</li>
            <li>ERKEK</li>
            <li>ÇOCUK & BEBEK</li>
          </ul>
        </nav>
        
        <!-- Arama Çubuğu -->
        <div class="search-bar">
          <input type="text" placeholder="Ürün, kategori ya da marka ara" />
        </div>
  
        <!-- Sağ Bölüm -->
        <div class="right-section">
          <a href="#" class="nav-link">Giriş</a>
          <a href="#" class="nav-link">Favorilerim</a>
          <a href="#" class="nav-link">Sepetim</a>
        </div>
      </div>
      <!-- Alt Çizgi -->
      <div class="bottom-line"></div>
    </header>
  </template>
  
  <style scoped>
  /* Header düzeni */
  .header {
    display: flex; /* Flexbox kullanımı */
    flex-direction: column; /* Alt çizginin hizalanması için */
    background-color: white;
    padding-bottom: 0.5rem; /* Çizgiyle içerik arasına boşluk */
  }
  
  /* Container */
  .container {
    width: 100%;
    display: flex;
    align-items: center; /* Tüm öğeleri dikeyde ortalar */
    justify-content: space-between; /* Ana elemanları yatayda dağıtır */
  }
  
  /* Logo */
  .logo img {
    height: 50px; /* Resim yüksekliği */
    width: auto; /* Oranı koruyarak genişliği otomatik ayarla */
  }
  
  /* Menü */
  .menu ul {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  .menu li {
    margin-left: 1.5rem; /* Sağa kaydırma */
    padding: 0.5rem 0; /* Daha büyük tıklanabilir alan için padding */
    cursor: pointer; /* Tıklanabilir imleç */
    position: relative; /* Çizgi efektinin konumlandırılması için */
    transition: color 0.3s ease, font-weight 0.3s ease; /* Yumuşak geçişler */
  }
  
  .menu li:hover {
    color: #000000; /* Üzerine gelince renk değişimi */
    font-weight: bold; /* Kalın yazı stili */
  }
  
  /* Menü alt çizgi efekti */
  .menu li::after {
    content: ''; /* Pseudo-element */
    display: block;
    height: 3px; /* Çizgi kalınlığı */
    background-color: #000000; /* Çizgi rengi */
    width: 0; /* Başlangıçta görünmez */
    position: absolute;
    bottom: 0; /* Alt hizalama */
    left: 0;
    transition: width 0.3s ease; /* Yumuşak genişleme efekti */
  }
  
  .menu li:hover::after {
    width: 100%; /* Üzerine gelince çizgiyi tam genişlet */
  }
  
  /* Arama Çubuğu */
  .search-bar {
    flex: 1; /* Arama çubuğunu genişletmek için */
    display: flex;
    justify-content: center; /* Yatayda ortalama */
  }
  
  .search-bar input {
    padding: 0.5rem;
    width: 300px; /* Arama çubuğunun genişliği */
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  /* Sağ Bölüm */
  .right-section {
    display: flex;
    gap: 1rem; /* Elemanlar arasında boşluk */
  }
  
  /* Sağdaki bağlantılar */
  .nav-link {
    text-decoration: none; /* Alt çizgiyi kaldır */
    color: black; /* Varsayılan yazı rengi */
    font-size: 1rem;
    position: relative; /* Çizgi efektinin konumlandırılması için */
    transition: color 0.3s ease; /* Yumuşak geçiş */
  }
  
  /* Sağ bağlantılar alt çizgi efekti */
  .nav-link::after {
    content: ''; /* Pseudo-element */
    display: block;
    height: 2px; /* Çizgi kalınlığı */
    background-color: #000000; /* Çizgi rengi */
    width: 0; /* Başlangıçta görünmez */
    position: absolute;
    bottom: -2px; /* Alt hizalama */
    left: 0;
    transition: width 0.3s ease; /* Yumuşak genişleme efekti */
  }
  
  .nav-link:hover {
    color: #ff0000; /* Üzerine gelince renk değişimi */
  }
  
  .nav-link:hover::after {
    width: 100%; /* Üzerine gelince çizgiyi tam genişlet */
  }
  
  /* Alt çizgi */
  .bottom-line {
    width: 100%;
    height: 2px;
    background-color: #ccc; /* Alt çizgi rengi */
    margin-top: 1.5rem;
  }
  </style>
  