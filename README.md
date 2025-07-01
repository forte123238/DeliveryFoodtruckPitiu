<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cardápio Completo - FoodTruck do Pitiu</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    :root {
      --primary-color: #d35400;
      --secondary-color: #e67e22;
      --dark-color: #222;
      --light-color: #f9f9f9;
      --success-color: #27ae60;
      --danger-color: #e74c3c;
      --info-color: #3498db;
    }
    
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      color: #333;
      line-height: 1.6;
      background-image: url('https://raw.githubusercontent.com/seu-usuario/seu-repositorio/main/backgroundfoodtruckpitiu.png');
      background-size: cover;
      background-attachment: fixed;
      background-position: center;
      background-color: rgba(0, 0, 0, 0.7);
      background-blend-mode: overlay;
    }
    
    .header {
      background-color: rgba(34, 34, 34, 0.9);
      color: white;
      text-align: center;
      padding: 1.5rem 0;
      position: relative;
      border-bottom: 3px solid var(--primary-color);
    }
    
    .logo {
      max-width: 150px;
      margin-bottom: 1rem;
    }
    
    .header h1 {
      font-size: 2rem;
      margin-bottom: 0.5rem;
      color: var(--secondary-color);
    }
    
    .header p {
      font-size: 0.9rem;
      margin-bottom: 0.3rem;
    }
    
    .header .social-links {
      margin-top: 1rem;
    }
    
    .header .social-links a {
      color: white;
      margin: 0 10px;
      font-size: 1.2rem;
      transition: color 0.3s;
    }
    
    .header .social-links a:hover {
      color: var(--secondary-color);
    }
    
    .tabs {
      display: flex;
      justify-content: center;
      background-color: rgba(34, 34, 34, 0.95);
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      overflow-x: auto;
      white-space: nowrap;
      padding: 0.5rem 0;
    }
    
    .tab-button {
      padding: 0.8rem 1rem;
      color: white;
      text-decoration: none;
      font-weight: bold;
      text-transform: uppercase;
      letter-spacing: 1px;
      transition: all 0.3s;
      cursor: pointer;
      border-bottom: 3px solid transparent;
      font-size: 0.8rem;
    }
    
    .tab-button:hover {
      background-color: rgba(255,255,255,0.1);
      border-bottom: 3px solid var(--secondary-color);
    }
    
    .tab-button.active {
      background-color: rgba(255,255,255,0.1);
      border-bottom: 3px solid var(--primary-color);
    }
    
    .container {
      display: flex;
      max-width: 1200px;
      margin: 0 auto;
      padding: 1rem;
    }
    
    .menu-section {
      flex: 3;
      padding-right: 1rem;
    }
    
    .cart-section {
      flex: 1;
      position: sticky;
      top: 60px;
      height: calc(100vh - 60px);
      overflow-y: auto;
      padding: 1rem;
      background-color: rgba(255, 255, 255, 0.95);
      border-radius: 8px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    
    .category {
      margin-bottom: 2rem;
      background-color: rgba(255, 255, 255, 0.95);
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    
    .category-header {
      background-color: var(--primary-color);
      color: white;
      padding: 0.8rem 1rem;
      font-size: 1.2rem;
      position: relative;
    }
    
    .category-header::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 3px;
      background-color: var(--secondary-color);
    }
    
    .item {
      display: flex;
      padding: 1rem;
      border-bottom: 1px solid #eee;
      transition: background-color 0.3s;
      flex-wrap: wrap;
    }
    
    .item:last-child {
      border-bottom: none;
    }
    
    .item:hover {
      background-color: rgba(0,0,0,0.03);
    }
    
    .item-image {
      width: 100px;
      height: 100px;
      object-fit: cover;
      border-radius: 8px;
      margin-right: 1rem;
    }
    
    .item-details {
      flex: 1;
      min-width: 200px;
    }
    
    .item-title {
      font-size: 1.1rem;
      font-weight: bold;
      margin-bottom: 0.3rem;
      color: var(--dark-color);
    }
    
    .item-description {
      font-size: 0.9rem;
      color: #666;
      margin-bottom: 0.5rem;
    }
    
    .item-price {
      font-weight: bold;
      color: var(--primary-color);
      font-size: 1.1rem;
    }
    
    .item-actions {
      display: flex;
      align-items: center;
      margin-top: 0.5rem;
    }
    
    .add-to-cart {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      font-weight: bold;
      transition: background-color 0.3s;
    }
    
    .add-to-cart:hover {
      background-color: var(--secondary-color);
    }
    
    .cart-title {
      font-size: 1.3rem;
      margin-bottom: 1rem;
      padding-bottom: 0.5rem;
      border-bottom: 2px solid var(--primary-color);
      color: var(--dark-color);
    }
    
    .cart-items {
      margin-bottom: 1rem;
    }
    
    .cart-item {
      display: flex;
      justify-content: space-between;
      padding: 0.5rem 0;
      border-bottom: 1px solid #eee;
    }
    
    .cart-item-name {
      flex: 2;
    }
    
    .cart-item-price {
      flex: 1;
      text-align: right;
    }
    
    .cart-item-remove {
      color: var(--danger-color);
      margin-left: 0.5rem;
      cursor: pointer;
      background: none;
      border: none;
      font-size: 0.9rem;
    }
    
    .cart-total {
      font-weight: bold;
      font-size: 1.2rem;
      margin-top: 1rem;
      padding-top: 1rem;
      border-top: 2px solid var(--primary-color);
      text-align: right;
    }
    
    .cart-actions {
      margin-top: 1.5rem;
    }
    
    .cart-button {
      width: 100%;
      padding: 0.8rem;
      border: none;
      border-radius: 4px;
      font-weight: bold;
      cursor: pointer;
      transition: background-color 0.3s;
      margin-bottom: 0.5rem;
    }
    
    .checkout-button {
      background-color: var(--success-color);
      color: white;
    }
    
    .checkout-button:hover {
      background-color: #2ecc71;
    }
    
    .clear-button {
      background-color: var(--danger-color);
      color: white;
    }
    
    .clear-button:hover {
      background-color: #c0392b;
    }
    
    .whatsapp-button {
      background-color: #25D366;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
    .whatsapp-button i {
      margin-right: 8px;
    }
    
    .whatsapp-button:hover {
      background-color: #128C7E;
    }
    
    .empty-cart {
      text-align: center;
      color: #666;
      padding: 1rem 0;
    }
    
    /* Checkout Modal */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.7);
      z-index: 1000;
      overflow-y: auto;
    }
    
    .modal-content {
      background-color: white;
      margin: 2rem auto;
      padding: 2rem;
      border-radius: 8px;
      max-width: 800px;
      width: 90%;
      box-shadow: 0 5px 15px rgba(0,0,0,0.3);
    }
    
    .close-modal {
      float: right;
      font-size: 1.5rem;
      cursor: pointer;
      color: #666;
    }
    
    .form-group {
      margin-bottom: 1rem;
    }
    
    .form-group label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: bold;
    }
    
    .form-group input, 
    .form-group select, 
    .form-group textarea {
      width: 100%;
      padding: 0.8rem;
      border: 1px solid #ddd;
      border-radius: 4px;
      font-family: inherit;
    }
    
    .form-group textarea {
      min-height: 100px;
    }
    
    .delivery-fee {
      padding: 1rem;
      background-color: #f5f5f5;
      border-radius: 4px;
      margin: 1rem 0;
      font-weight: bold;
    }
    
    .order-summary {
      margin: 1rem 0;
      padding: 1rem;
      background-color: #f9f9f9;
      border-radius: 4px;
    }
    
    .order-item {
      display: flex;
      justify-content: space-between;
      margin-bottom: 0.5rem;
    }
    
    .order-total {
      font-weight: bold;
      font-size: 1.2rem;
      margin-top: 1rem;
      border-top: 1px solid #ddd;
      padding-top: 1rem;
    }
    
    .payment-options {
      margin: 1rem 0;
    }
    
    .payment-option {
      margin-bottom: 0.5rem;
    }
    
    .submit-order {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 1rem;
      border-radius: 4px;
      font-weight: bold;
      cursor: pointer;
      width: 100%;
      font-size: 1.1rem;
      transition: background-color 0.3s;
    }
    
    .submit-order:hover {
      background-color: var(--secondary-color);
    }
    
    @media (max-width: 768px) {
      .container {
        flex-direction: column;
      }
      
      .menu-section {
        padding-right: 0;
        margin-bottom: 1rem;
      }
      
      .cart-section {
        position: static;
        height: auto;
      }
      
      .item {
        flex-direction: column;
      }
      
      .item-image {
        width: 100%;
        height: 150px;
        margin-right: 0;
        margin-bottom: 1rem;
      }
      
      .tabs {
        justify-content: flex-start;
      }
      
      .modal-content {
        margin: 1rem auto;
        padding: 1rem;
      }
    }
    
    /* Animations */
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .category {
      animation: fadeIn 0.5s ease-out forwards;
    }
    
    /* Delay animations for each category */
    .category:nth-child(1) { animation-delay: 0.1s; }
    .category:nth-child(2) { animation-delay: 0.2s; }
    .category:nth-child(3) { animation-delay: 0.3s; }
    .category:nth-child(4) { animation-delay: 0.4s; }
    .category:nth-child(5) { animation-delay: 0.5s; }
    .category:nth-child(6) { animation-delay: 0.6s; }
    .category:nth-child(7) { animation-delay: 0.7s; }
  </style>
</head>
<body>
  <div class="header">
    <img src="https://raw.githubusercontent.com/seu-usuario/seu-repositorio/main/logotipo1pitiu.png" alt="FoodTruck do Pitiu" class="logo">
    <h1>𝙁𝙊𝙊𝘿𝙏𝙍𝙐𝘾𝙆 𝘿𝙊 𝙋𝙄𝙏𝙄𝙐</h1>
    <p>☕ Pitiu Café Especial - 08:00h às 16:00h 🍞</p>
    <p>🍻 Pitiu Artesanais - 19:00h às 00:00h 🍔</p>
    <p>📍 Praça Saiqui, Vila Valqueire</p>
    <p>🛵 Cardápio Delivery: é só clicar ⤵️</p>
    <div class="social-links">
      <a href="https://www.instagram.com/foodtruckdopitiu/" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
      <a href="https://wa.me/5521992254487" target="_blank" title="WhatsApp"><i class="fab fa-whatsapp"></i></a>
    </div>
  </div>

  <div class="tabs">
    <div class="tab-button active" onclick="scrollToSection('hamburgueres')">Hambúrgueres</div>
    <div class="tab-button" onclick="scrollToSection('pao-queijo')">Pão de Queijo</div>
    <div class="tab-button" onclick="scrollToSection('pastelzinho')">Pastelzinho</div>
    <div class="tab-button" onclick="scrollToSection('petiscos')">Petiscos</div>
    <div class="tab-button" onclick="scrollToSection('bebidas')">Bebidas</div>
    <div class="tab-button" onclick="scrollToSection('smoothie')">Smoothie</div>
    <div class="tab-button" onclick="scrollToSection('cervejas')">Cervejas</div>
  </div>

  <div class="container">
    <div class="menu-section">
      <!-- Hambúrgueres -->
      <div id="hamburgueres" class="category">
        <div class="category-header">Hambúrgueres Artesanais</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,1" alt="Carne no Prato" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Carne no Prato - R$18</h3>
            <p class="item-description">Blend da casa de 180g, queijo prato e mussarela no pão brioche.</p>
            <div class="item-price">R$ 18,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Carne no Prato', 18, 'https://source.unsplash.com/random/300x300/?burger,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,2" alt="Cheeseburguer" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheeseburguer - R$22</h3>
            <p class="item-description">Blend da casa de 180g, queijo prato, mussarela e maionese da casa no pão brioche.</p>
            <div class="item-price">R$ 22,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cheeseburguer', 22, 'https://source.unsplash.com/random/300x300/?burger,2')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,3" alt="Cheese Calabresa" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheese Calabresa - R$23</h3>
            <p class="item-description">Blend da casa de 180g, calabresa, queijo prato, mussarela e maionese da casa no pão brioche.</p>
            <div class="item-price">R$ 23,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cheese Calabresa', 23, 'https://source.unsplash.com/random/300x300/?burger,3')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,4" alt="Cheese Bacon" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheese Bacon - R$26</h3>
            <p class="item-description">Blend da casa de 180g, bacon, queijo prato, mussarela e maionese da casa no pão brioche.</p>
            <div class="item-price">R$ 26,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cheese Bacon', 26, 'https://source.unsplash.com/random/300x300/?burger,4')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,5" alt="Kids" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Kids - R$18</h3>
            <p class="item-description">Blend da casa de 90g, queijo prato, mussarela no pão brioche.</p>
            <div class="item-price">R$ 18,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Kids', 18, 'https://source.unsplash.com/random/300x300/?burger,5')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,6" alt="Black" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Black - R$32</h3>
            <p class="item-description">Blend da casa de 180g, anéis de cebola, bacon, calabresa, queijo prato, mussarela, barbecue e maionese da casa no pão triplo X (brioche com bacon, calabresa e parmesão).</p>
            <div class="item-price">R$ 32,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Black', 32, 'https://source.unsplash.com/random/300x300/?burger,6')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,7" alt="Cheddar Cremoso" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheddar Cremoso - R$32</h3>
            <p class="item-description">Blend da casa de 180g, bacon, cebola caramelizada e cheddar cremoso no pão australiano.</p>
            <div class="item-price">R$ 32,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cheddar Cremoso', 32, 'https://source.unsplash.com/random/300x300/?burger,7')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,8" alt="Pitiuzinho" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Pitiuzinho - R$34</h3>
            <p class="item-description">Blend da casa de 180g, bacon, cebola caramelizada, cheddar cremoso e catupiry no pão de queijo.</p>
            <div class="item-price">R$ 34,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pitiuzinho', 34, 'https://source.unsplash.com/random/300x300/?burger,8')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Pão de Queijo -->
      <div id="pao-queijo" class="category">
        <div class="category-header">Pão de Queijo Recheado</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?cheese-bread,1" alt="Sem Recheio" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Sem Recheio - R$9</h3>
            <p class="item-description">Pão de queijo tradicional sem recheio.</p>
            <div class="item-price">R$ 9,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pão de Queijo Sem Recheio', 9, 'https://source.unsplash.com/random/300x300/?cheese-bread,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?cheese-bread,2" alt="Frango com Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Frango com Catupiry - R$18</h3>
            <p class="item-description">Frango desfiado com catupiry cremoso.</p>
            <div class="item-price">R$ 18,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pão de Queijo Frango Catupiry', 18, 'https://source.unsplash.com/random/300x300/?cheese-bread,2')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?cheese-bread,3" alt="Cheddar" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheddar (com ou sem cebola) - R$17</h3>
            <p class="item-description">Recheio de cheddar derretido com opção de cebola.</p>
            <div class="item-price">R$ 17,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pão de Queijo Cheddar', 17, 'https://source.unsplash.com/random/300x300/?cheese-bread,3')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?cheese-bread,4" alt="Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Catupiry (com ou sem cebola) - R$17</h3>
            <p class="item-description">Recheio de catupiry cremoso com opção de cebola.</p>
            <div class="item-price">R$ 17,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pão de Queijo Catupiry', 17, 'https://source.unsplash.com/random/300x300/?cheese-bread,4')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?cheese-bread,5" alt="Chester Defumado" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Chester Defumado com Catupiry - R$19</h3>
            <p class="item-description">Carne de chester defumada com catupiry cremoso.</p>
            <div class="item-price">R$ 19,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pão de Queijo Chester Catupiry', 19, 'https://source.unsplash.com/random/300x300/?cheese-bread,5')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?cheese-bread,6" alt="Carne Seca" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Carne Seca com Catupiry - R$20</h3>
            <p class="item-description">Carne seca desfiada com catupiry cremoso.</p>
            <div class="item-price">R$ 20,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pão de Queijo Carne Seca Catupiry', 20, 'https://source.unsplash.com/random/300x300/?cheese-bread,6')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?cheese-bread,7" alt="Camarão" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Camarão com Catupiry - R$23</h3>
            <p class="item-description">Camarão ao molho com catupiry cremoso.</p>
            <div class="item-price">R$ 23,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pão de Queijo Camarão Catupiry', 23, 'https://source.unsplash.com/random/300x300/?cheese-bread,7')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Pastelzinho -->
      <div id="pastelzinho" class="category">
        <div class="category-header">Pastelzinho</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,1" alt="Queijo" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Queijo - R$6</h3>
            <p class="item-description">Pastelzinho recheado com queijo derretido.</p>
            <div class="item-price">R$ 6,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pastelzinho Queijo', 6, 'https://source.unsplash.com/random/300x300/?pastry,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,2" alt="Cheddar" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheddar (com ou sem cebola) - R$6</h3>
            <p class="item-description">Pastelzinho recheado com cheddar derretido e opção de cebola.</p>
            <div class="item-price">R$ 6,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pastelzinho Cheddar', 6, 'https://source.unsplash.com/random/300x300/?pastry,2')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,3" alt="Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Catupiry (com ou sem cebola) - R$6</h3>
            <p class="item-description">Pastelzinho recheado com catupiry cremoso e opção de cebola.</p>
            <div class="item-price">R$ 6,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pastelzinho Catupiry', 6, 'https://source.unsplash.com/random/300x300/?pastry,3')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,4" alt="Carne Moída" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Carne Moída - R$7</h3>
            <p class="item-description">Pastelzinho recheado com carne moída temperada.</p>
            <div class="item-price">R$ 7,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pastelzinho Carne Moída', 7, 'https://source.unsplash.com/random/300x300/?pastry,4')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,5" alt="Carne Seca" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Carne Seca - R$7</h3>
            <p class="item-description">Pastelzinho recheado com carne seca desfiada.</p>
            <div class="item-price">R$ 7,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pastelzinho Carne Seca', 7, 'https://source.unsplash.com/random/300x300/?pastry,5')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,6" alt="Camarão" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Camarão - R$9</h3>
            <p class="item-description">Pastelzinho recheado com camarão ao molho.</p>
            <div class="item-price">R$ 9,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pastelzinho Camarão', 9, 'https://source.unsplash.com/random/300x300/?pastry,6')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,7" alt="Aplicação de Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Aplicação de Catupiry - R$2</h3>
            <p class="item-description">Adicione catupiry cremoso ao seu pastelzinho.</p>
            <div class="item-price">R$ 2,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Aplicação de Catupiry', 2, 'https://source.unsplash.com/random/300x300/?pastry,7')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Petiscos -->
      <div id="petiscos" class="category">
        <div class="category-header">Petiscos</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?snack,1" alt="Batata Canoa" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Batata Canoa 200G - R$14</h3>
            <p class="item-description">Batata canoa crocante (acompanha maionese da casa).</p>
            <div class="item-price">R$ 14,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Batata Canoa 200G', 14, 'https://source.unsplash.com/random/300x300/?snack,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?snack,2" alt="Anéis de Cebola" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Anéis de Cebola 10 Und. - R$14</h3>
            <p class="item-description">Anéis de cebola empanados (acompanha maionese da casa).</p>
            <div class="item-price">R$ 14,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Anéis de Cebola 10 Und.', 14, 'https://source.unsplash.com/random/300x300/?snack,2')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?snack,3" alt="Batata Canoa Especial" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Batata Canoa 200g - R$25</h3>
            <p class="item-description">Batata canoa com cheddar ou catupiry e bacon.</p>
            <div class="item-price">R$ 25,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Batata Canoa Especial', 25, 'https://source.unsplash.com/random/300x300/?snack,3')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?snack,4" alt="Provolone à Milanesa" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Provolone à Milanesa - R$30</h3>
            <p class="item-description">Provolone empanado (acompanha maionese da casa).</p>
            <div class="item-price">R$ 30,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Provolone à Milanesa', 30, 'https://source.unsplash.com/random/300x300/?snack,4')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Bebidas -->
      <div id="bebidas" class="category">
        <div class="category-header">Bebidas</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?water,1" alt="Água" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Água - R$4</h3>
            <p class="item-description">Água mineral sem gás 500ml.</p>
            <div class="item-price">R$ 4,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Água', 4, 'https://source.unsplash.com/random/300x300/?water,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?sparkling-water,1" alt="Água com gás" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Água com gás - R$5</h3>
            <p class="item-description">Água mineral com gás 500ml.</p>
            <div class="item-price">R$ 5,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Água com gás', 5, 'https://source.unsplash.com/random/300x300/?sparkling-water,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?guarana,1" alt="Guaravita" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Guaravita - R$4</h3>
            <p class="item-description">Refrigerante Guaravita 290ml.</p>
            <div class="item-price">R$ 4,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Guaravita', 4, 'https://source.unsplash.com/random/300x300/?guarana,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?guarana,2" alt="Guaraviton" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Guaraviton - R$6</h3>
            <p class="item-description">Refrigerante Guaraviton 290ml.</p>
            <div class="item-price">R$ 6,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Guaraviton', 6, 'https://source.unsplash.com/random/300x300/?guarana,2')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?mate,1" alt="Mate" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Mate (Natural ou Limão) - R$6</h3>
            <p class="item-description">Refrigerante Mate 290ml.</p>
            <div class="item-price">R$ 6,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Mate', 6, 'https://source.unsplash.com/random/300x300/?mate,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?ice-tea,1" alt="Ice Tea" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Ice Tea (Pêssego ou Limão) - R$6</h3>
            <p class="item-description">Ice Tea 290ml.</p>
            <div class="item-price">R$ 6,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Ice Tea', 6, 'https://source.unsplash.com/random/300x300/?ice-tea,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?soda,1" alt="Refrigerante Lata" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Refrigerante Lata - R$6</h3>
            <p class="item-description">Coca-cola, Coca-cola Zero, Pepsi, Guaraná, Guaraná Zero, Sprite, Fanta Laranja, Fanta Uva, Citrus ou Água Tônica.</p>
            <div class="item-price">R$ 6,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Refrigerante Lata', 6, 'https://source.unsplash.com/random/300x300/?soda,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?h2o,1" alt="H2O" class="item-image">
          <div class="item-details">
            <h3 class="item-title">H2O (Limão ou Limoneto) - R$7</h3>
            <p class="item-description">H2O 500ml.</p>
            <div class="item-price">R$ 7,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('H2O', 7, 'https://source.unsplash.com/random/300x300/?h2o,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?soda,2" alt="Refrigerante 600ml" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Refrigerante 600ml - R$9</h3>
            <p class="item-description">Coca-cola ou Coca-cola Zero 600ml.</p>
            <div class="item-price">R$ 9,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Refrigerante 600ml', 9, 'https://source.unsplash.com/random/300x300/?soda,2')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?orange-juice,1" alt="Suco de Laranja" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Suco de Laranja Natural - R$10 (300ml) / R$25 (1L)</h3>
            <p class="item-description">Suco de laranja natural fresco.</p>
            <div class="item-price">R$ 10,00 / R$ 25,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Suco Laranja 300ml', 10, 'https://source.unsplash.com/random/300x300/?orange-juice,1')">300ml</button>
              <button class="add-to-cart" onclick="addItem('Suco Laranja 1L', 25, 'https://source.unsplash.com/random/300x300/?orange-juice,1')">1 Litro</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?coconut,1" alt="Coco Gelado" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Coco Gelado - R$8</h3>
            <p class="item-description">Água de coco natural gelada.</p>
            <div class="item-price">R$ 8,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Coco Gelado', 8, 'https://source.unsplash.com/random/300x300/?coconut,1')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Smoothie -->
      <div id="smoothie" class="category">
        <div class="category-header">Smoothie</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?smoothie,1" alt="Morango" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Morango 500ml - R$18</h3>
            <p class="item-description">Bebida cremosa de morango.</p>
            <div class="item-price">R$ 18,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Smoothie Morango', 18, 'https://source.unsplash.com/random/300x300/?smoothie,1')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <!-- Cervejas -->
      <div id="cervejas" class="category">
        <div class="category-header">Cervejas</div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?beer,1" alt="Stella" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Stella, Budweiser ou Eisenbahn Longneck - R$9</h3>
            <p class="item-description">Cerveja longneck 355ml.</p>
            <div class="item-price">R$ 9,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cerveja Longneck Stella/Budweiser/Eisenbahn', 9, 'https://source.unsplash.com/random/300x300/?beer,1')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?beer,2" alt="Heineken" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Heineken, Heineken Zero ou Corona Longneck - R$10</h3>
            <p class="item-description">Cerveja longneck 355ml.</p>
            <div class="item-price">R$ 10,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cerveja Longneck Heineken/Corona', 10, 'https://source.unsplash.com/random/300x300/?beer,2')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?beer,3" alt="Cerveja 600ml" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Stella, Original, Spaten, Eisenbahn, Budweiser, Duplo Malte ou Serramalte 600ml - R$13</h3>
            <p class="item-description">Cerveja 600ml.</p>
            <div class="item-price">R$ 13,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cerveja 600ml Variadas', 13, 'https://source.unsplash.com/random/300x300/?beer,3')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?beer,4" alt="Heineken 600ml" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Heineken 600ml - R$14</h3>
            <p class="item-description">Cerveja Heineken 600ml.</p>
            <div class="item-price">R$ 14,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Heineken 600ml', 14, 'https://source.unsplash.com/random/300x300/?beer,4')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?beer,5" alt="Colorado" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Colorado 600ml - R$20</h3>
            <p class="item-description">Cerveja artesanal Colorado 600ml.</p>
            <div class="item-price">R$ 20,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Colorado 600ml', 20, 'https://source.unsplash.com/random/300x300/?beer,5')">Adicionar</button>
            </div>
          </div>
        </div>
        
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?beer,6" alt="Latão" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Latão de Brahma ou Antarctica - R$8</h3>
            <p class="item-description">Cerveja em lata 473ml.</p>
            <div class="item-price">R$ 8,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Latão Brahma/Antarctica', 8, 'https://source.unsplash.com/random/300x300/?beer,6')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Carrinho de Compras -->
    <div class="cart-section">
      <h2 class="cart-title">Seu Pedido</h2>
      <div id="cart-items" class="cart-items">
        <div class="empty-cart">Seu carrinho está vazio</div>
      </div>
      <div id="cart-total" class="cart-total">Total: R$ 0,00</div>
      <div class="cart-actions">
        <button class="cart-button checkout-button" onclick="openCheckoutModal()">Finalizar Pedido</button>
        <button class="cart-button whatsapp-button" onclick="checkoutWhatsApp()">
          <i class="fab fa-whatsapp"></i> WhatsApp
        </button>
        <button class="cart-button clear-button" onclick="clearCart()">Limpar Carrinho</button>
      </div>
    </div>
  </div>

  <!-- Modal de Checkout -->
  <div id="checkout-modal" class="modal">
    <div class="modal-content">
      <span class="close-modal" onclick="closeModal()">&times;</span>
      <h2>Finalizar Pedido</h2>
      
      <form id="checkout-form">
        <div class="form-group">
          <label for="customer-name">1. Seu nome / Celular:</label>
          <input type="text" id="customer-name" placeholder="Nome completo" required>
          <input type="tel" id="customer-phone" placeholder="Celular (com DDD)" required style="margin-top: 0.5rem;">
        </div>
        
        <div class="form-group">
          <label>2. Pedido completo:</label>
          <div id="order-summary" class="order-summary">
            <!-- Itens do pedido serão inseridos aqui pelo JavaScript -->
          </div>
        </div>
        
        <div class="form-group">
          <label for="customer-neighborhood">3. Bairro:</label>
          <select id="customer-neighborhood" required onchange="updateDeliveryFee()">
            <option value="">Selecione seu bairro</option>
            <option value="Cascadura">Cascadura (Taxa: R$12,00)</option>
            <option value="Madureira">Madureira (Taxa: R$10,00)</option>
            <option value="Vila Valqueire">Vila Valqueire (Taxa: R$5,00)</option>
            <option value="Marechal Hermes">Marechal Hermes (Taxa: R$8,00)</option>
            <option value="Bento Ribeiro">Bento Ribeiro (Taxa: R$10,00)</option>
            <option value="Campinho">Campinho (Taxa: R$10,00)</option>
            <option value="Oswaldo Cruz">Oswaldo Cruz (Taxa: R$8,00)</option>
            <option value="Praça Seca">Praça Seca (Taxa: R$15,00)</option>
            <option value="Tanque">Tanque (Taxa: R$15,00)</option>
          </select>
        </div>
        
        <div class="form-group">
          <label for="customer-address">Endereço completo:</label>
          <input type="text" id="customer-street" placeholder="Rua" required>
          <input type="text" id="customer-number" placeholder="Número" required style="margin-top: 0.5rem;">
          <input type="text" id="customer-complement" placeholder="Complemento (apto/casa/local)" style="margin-top: 0.5rem;">
          <input type="text" id="customer-zipcode" placeholder="CEP" required style="margin-top: 0.5rem;">
        </div>
        
        <div id="delivery-fee" class="delivery-fee">
          Taxa de entrega: R$ 0,00
        </div>
        
        <div class="form-group">
          <label>4. Forma de pagamento:</label>
          <div class="payment-options">
            <div class="payment-option">
              <input type="radio" id="payment-pix" name="payment" value="PIX" checked>
              <label for="payment-pix">PIX</label>
            </div>
            <div class="payment-option">
              <input type="radio" id="payment-cash" name="payment" value="Dinheiro">
              <label for="payment-cash">Dinheiro</label>
            </div>
            <div class="payment-option">
              <input type="radio" id="payment-card" name="payment" value="Cartão">
              <label for="payment-card">Cartão (Máquina na entrega)</label>
            </div>
          </div>
        </div>
        
        <div id="order-total" class="order-total">
          Total do Pedido: R$ 0,00
        </div>
        
        <button type="button" class="submit-order" onclick="submitOrder()">Confirmar Pedido</button>
      </form>
    </div>
  </div>

  <script>
    let cart = [];
    const deliveryFees = {
      'Cascadura': 12,
      'Madureira': 10,
      'Vila Valqueire': 5,
      'Marechal Hermes': 8,
      'Bento Ribeiro': 10,
      'Campinho': 10,
      'Oswaldo Cruz': 8,
      'Praça Seca': 15,
      'Tanque': 15
    };
    
    // Atualiza o carrinho no localStorage
    function updateLocalStorage() {
      localStorage.setItem('cart', JSON.stringify(cart));
    }
    
    // Carrega o carrinho do localStorage ao carregar a página
    function loadCart() {
      const savedCart = localStorage.getItem('cart');
      if (savedCart) {
        cart = JSON.parse(savedCart);
        updateCart();
      }
    }
    
    // Adiciona item ao carrinho
    function addItem(name, price, image) {
      const existingItem = cart.find(item => item.name === name);
      
      if (existingItem) {
        existingItem.quantity += 1;
      } else {
        cart.push({ name, price, image, quantity: 1 });
      }
      
      updateCart();
      updateLocalStorage();
      
      // Feedback visual
      const button = event.target;
      button.textContent = 'Adicionado!';
      button.style.backgroundColor = '#27ae60';
      setTimeout(() => {
        button.textContent = 'Adicionar';
        button.style.backgroundColor = '';
      }, 1000);
    }
    
    // Remove item do carrinho
    function removeItem(index) {
      cart.splice(index, 1);
      updateCart();
      updateLocalStorage();
    }
    
    // Atualiza a exibição do carrinho
    function updateCart() {
      const cartItemsElement = document.getElementById('cart-items');
      const cartTotalElement = document.getElementById('cart-total');
      
      if (cart.length === 0) {
        cartItemsElement.innerHTML = '<div class="empty-cart">Seu carrinho está vazio</div>';
        cartTotalElement.textContent = 'Total: R$ 0,00';
        return;
      }
      
      let itemsHTML = '';
      let total = 0;
      
      cart.forEach((item, index) => {
        const itemTotal = item.price * item.quantity;
        total += itemTotal;
        
        itemsHTML += `
          <div class="cart-item">
            <div class="cart-item-name">
              ${item.name} (${item.quantity}x)
              <button class="cart-item-remove" onclick="removeItem(${index})">
                <i class="fas fa-trash"></i>
              </button>
            </div>
            <div class="cart-item-price">R$ ${itemTotal.toFixed(2)}</div>
          </div>
        `;
      });
      
      cartItemsElement.innerHTML = itemsHTML;
      cartTotalElement.textContent = `Total: R$ ${total.toFixed(2)}`;
    }
    
    // Limpa o carrinho
    function clearCart() {
      cart = [];
      updateCart();
      updateLocalStorage();
    }
    
    // Abre o modal de checkout
    function openCheckoutModal() {
      if (cart.length === 0) {
        alert('Seu carrinho está vazio!');
        return;
      }
      
      const modal = document.getElementById('checkout-modal');
      modal.style.display = 'block';
      
      // Atualiza o resumo do pedido no modal
      const orderSummary = document.getElementById('order-summary');
      let summaryHTML = '';
      let subtotal = 0;
      
      cart.forEach(item => {
        const itemTotal = item.price * item.quantity;
        subtotal += itemTotal;
        
        summaryHTML += `
          <div class="order-item">
            <span>${item.quantity}x ${item.name}</span>
            <span>R$ ${itemTotal.toFixed(2)}</span>
          </div>
        `;
      });
      
      summaryHTML += `
        <div class="order-item" style="border-top: 1px solid #ddd; padding-top: 0.5rem;">
          <span><strong>Subtotal</strong></span>
          <span><strong>R$ ${subtotal.toFixed(2)}</strong></span>
        </div>
      `;
      
      orderSummary.innerHTML = summaryHTML;
      
      // Atualiza o total no modal
      updateOrderTotal();
    }
    
    // Fecha o modal
    function closeModal() {
      const modal = document.getElementById('checkout-modal');
      modal.style.display = 'none';
    }
    
    // Atualiza a taxa de entrega
    function updateDeliveryFee() {
      const neighborhood = document.getElementById('customer-neighborhood').value;
      const deliveryFeeElement = document.getElementById('delivery-fee');
      
      if (neighborhood && deliveryFees[neighborhood]) {
        deliveryFeeElement.textContent = `Taxa de entrega: R$ ${deliveryFees[neighborhood].toFixed(2)}`;
      } else {
        deliveryFeeElement.textContent = 'Taxa de entrega: R$ 0,00';
      }
      
      updateOrderTotal();
    }
    
    // Atualiza o total do pedido (subtotal + taxa)
    function updateOrderTotal() {
      const neighborhood = document.getElementById('customer-neighborhood').value;
      const orderTotalElement = document.getElementById('order-total');
      
      let subtotal = 0;
      cart.forEach(item => {
        subtotal += item.price * item.quantity;
      });
      
      const deliveryFee = neighborhood && deliveryFees[neighborhood] ? deliveryFees[neighborhood] : 0;
      const total = subtotal + deliveryFee;
      
      orderTotalElement.textContent = `Total do Pedido: R$ ${total.toFixed(2)}`;
    }
    
    // Envia o pedido
    function submitOrder() {
      const name = document.getElementById('customer-name').value;
      const phone = document.getElementById('customer-phone').value;
      const neighborhood = document.getElementById('customer-neighborhood').value;
      const street = document.getElementById('customer-street').value;
      const number = document.getElementById('customer-number').value;
      const complement = document.getElementById('customer-complement').value;
      const zipcode = document.getElementById('customer-zipcode').value;
      const payment = document.querySelector('input[name="payment"]:checked').value;
      
      if (!name || !phone || !neighborhood || !street || !number || !zipcode) {
        alert('Por favor, preencha todos os campos obrigatórios.');
        return;
      }
      
      // Calcula totais
      let subtotal = 0;
      let orderItems = '';
      
      cart.forEach(item => {
        const itemTotal = item.price * item.quantity;
        subtotal += itemTotal;
        orderItems += `${item.quantity}x ${item.name} - R$ ${itemTotal.toFixed(2)}\n`;
      });
      
      const deliveryFee = deliveryFees[neighborhood] || 0;
      const total = subtotal + deliveryFee;
      
      // Monta mensagem para WhatsApp
      let message = `*NOVO PEDIDO - FOODTRUCK DO PITIU*\n\n`;
      message += `*Cliente:* ${name}\n`;
      message += `*Telefone:* ${phone}\n\n`;
      message += `*Endereço:*\n`;
      message += `${street}, ${number}`;
      if (complement) message += ` - ${complement}`;
      message += `\n${neighborhood}\n`;
      message += `CEP: ${zipcode}\n\n`;
      message += `*Pedido:*\n${orderItems}\n`;
      message += `*Subtotal:* R$ ${subtotal.toFixed(2)}\n`;
      message += `*Taxa de entrega:* R$ ${deliveryFee.toFixed(2)}\n`;
      message += `*Total:* R$ ${total.toFixed(2)}\n\n`;
      message += `*Forma de pagamento:* ${payment}`;
      
      // Codifica a mensagem para URL
      const encodedMessage = encodeURIComponent(message);
      
      // Abre o WhatsApp
      window.open(`https://wa.me/5521992254487?text=${encodedMessage}`, '_blank');
      
      // Fecha o modal e limpa o carrinho
      closeModal();
      clearCart();
    }
    
    // Finaliza o pedido via WhatsApp (direto, sem formulário)
    function checkoutWhatsApp() {
      if (cart.length === 0) {
        alert('Seu carrinho está vazio!');
        return;
      }
      
      let message = 'Olá, gostaria de fazer um pedido:\n\n';
      
      let subtotal = 0;
      cart.forEach(item => {
        const itemTotal = item.price * item.quantity;
        subtotal += itemTotal;
        message += `${item.quantity}x ${item.name} - R$ ${itemTotal.toFixed(2)}\n`;
      });
      
      message += `\n*Subtotal:* R$ ${subtotal.toFixed(2)}\n\n`;
      message += '*Informações de entrega:*\n';
      message += '1. Nome / Celular:\n';
      message += '2. Bairro:\n';
      message += '3. Endereço completo (Rua, número, complemento, CEP):\n\n';
      message += '*Taxas de entrega:*\n';
      message += 'Cascadura: R$12,00\n';
      message += 'Madureira: R$10,00\n';
      message += 'Vila Valqueire: R$5,00\n';
      message += 'Marechal Hermes: R$8,00\n';
      message += 'Bento Ribeiro: R$10,00\n';
      message += 'Campinho: R$10,00\n';
      message += 'Oswaldo Cruz: R$8,00\n';
      message += 'Praça Seca: R$15,00\n';
      message += 'Tanque: R$15,00\n\n';
      message += '*Forma de pagamento:* ( ) PIX ( ) Dinheiro ( ) Cartão';
      
      const encodedMessage = encodeURIComponent(message);
      window.open(`https://wa.me/5521992254487?text=${encodedMessage}`, '_blank');
    }
    
    // Rolagem suave para as seções
    function scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      if (section) {
        // Atualiza a aba ativa
        document.querySelectorAll('.tab-button').forEach(button => {
          button.classList.remove('active');
        });
        event.target.classList.add('active');
        
        // Rolagem suave
        window.scrollTo({
          top: section.offsetTop - 60,
          behavior: 'smooth'
        });
      }
    }
    
    // Observador de interseção para atualizar a aba ativa
    function setupIntersectionObserver() {
      const sections = document.querySelectorAll('.category');
      const navLinks = document.querySelectorAll('.tab-button');
      
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const id = entry.target.id;
            navLinks.forEach(link => {
              link.classList.remove('active');
              if (link.textContent.toLowerCase().includes(id)) {
                link.classList.add('active');
              }
            });
          }
        });
      }, { threshold: 0.5, rootMargin: '-60px 0px -50% 0px' });
      
      sections.forEach(section => {
        observer.observe(section);
      });
    }
    
    // Fecha o modal ao clicar fora dele
    window.onclick = function(event) {
      const modal = document.getElementById('checkout-modal');
      if (event.target === modal) {
        closeModal();
      }
    }
    
    // Carrega o carrinho e configura o observador quando a página carrega
    window.addEventListener('DOMContentLoaded', () => {
      loadCart();
      setupIntersectionObserver();
    });
  </script>
</body>
</html>
