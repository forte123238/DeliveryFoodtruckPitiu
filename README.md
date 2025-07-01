<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cardápio Pitiu Artesanais</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    :root {
      --primary-color: #d35400;
      --secondary-color: #e67e22;
      --dark-color: #222;
      --light-color: #f9f9f9;
      --success-color: #27ae60;
      --danger-color: #e74c3c;
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
      background-color: #f5f5f5;
      color: #333;
      line-height: 1.6;
    }
    
    .header {
      background-color: var(--dark-color);
      color: white;
      text-align: center;
      padding: 1.5rem 0;
      position: relative;
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
      background-color: var(--dark-color);
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    
    .tab-button {
      padding: 1rem 1.5rem;
      color: white;
      text-decoration: none;
      font-weight: bold;
      text-transform: uppercase;
      letter-spacing: 1px;
      transition: all 0.3s;
      cursor: pointer;
      border-bottom: 3px solid transparent;
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
      background-color: white;
      border-radius: 8px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    
    .category {
      margin-bottom: 2rem;
      background-color: white;
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
    }
    
    .item:last-child {
      border-bottom: none;
    }
    
    .item:hover {
      background-color: #f9f9f9;
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
  </style>
</head>
<body>
  <div class="header">
    <h1>𝙁𝙊𝙊𝘿𝙏𝙍𝙐𝘾𝙆 𝘿𝙊 𝙋𝙄𝙏𝙄𝙐</h1>
    <p>☕ Pitiu Café Especial - 08:00h às 16:00h 🍞</p>
    <p>🍻 Pitiu Artesanais - 19:00h às 00:00h �</p>
    <p>📍 Praça Saiqui, Vila Valqueire</p>
    <p>🛵 Cardápio Delivery: é só clicar ⤵️</p>
    <div class="social-links">
      <a href="https://www.instagram.com/foodtruckdopitiu/" target="_blank" title="Instagram"><i class="fab fa-instagram"></i></a>
      <a href="https://wa.me/5521992254487" target="_blank" title="WhatsApp"><i class="fab fa-whatsapp"></i></a>
    </div>
  </div>

  <div class="tabs">
    <div class="tab-button active" onclick="scrollToSection('hamburgueres')">Hambúrgueres</div>
    <div class="tab-button" onclick="scrollToSection('salgados')">Salgados</div>
    <div class="tab-button" onclick="scrollToSection('doces')">Doces</div>
  </div>

  <div class="container">
    <div class="menu-section">
      <div id="hamburgueres" class="category">
        <div class="category-header">Hambúrgueres Artesanais</div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,1" alt="Carne no Prato" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Carne no Prato - R$18</h3>
            <p class="item-description">Blend 180g, queijo prato e mussarela</p>
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
            <p class="item-description">Blend 180g, queijo prato, mussarela, maionese da casa</p>
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
            <p class="item-description">Com calabresa e maionese da casa</p>
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
            <p class="item-description">Com bacon crocante e molho especial</p>
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
            <p class="item-description">Blend 90g, queijo prato, mussarela</p>
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
            <p class="item-description">Completo com barbecue, bacon, calabresa e mais</p>
            <div class="item-price">R$ 32,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Black', 32, 'https://source.unsplash.com/random/300x300/?burger,6')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,7" alt="Pitiuzinho" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Pitiuzinho - R$34</h3>
            <p class="item-description">Com bacon, cebola caramelizada, cheddar e catupiry</p>
            <div class="item-price">R$ 34,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Pitiuzinho', 34, 'https://source.unsplash.com/random/300x300/?burger,7')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?burger,8" alt="Cheddar Cremoso" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheddar Cremoso - R$32</h3>
            <p class="item-description">Cheddar cremoso e bacon</p>
            <div class="item-price">R$ 32,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cheddar Cremoso', 32, 'https://source.unsplash.com/random/300x300/?burger,8')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <div id="salgados" class="category">
        <div class="category-header">Salgados</div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,1" alt="Sem Recheio" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Sem Recheio - R$9</h3>
            <p class="item-description">Pão fresco sem recheio</p>
            <div class="item-price">R$ 9,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Sem Recheio', 9, 'https://source.unsplash.com/random/300x300/?pastry,1')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,2" alt="Frango com Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Frango com Catupiry - R$18</h3>
            <p class="item-description">Frango desfiado com catupiry cremoso</p>
            <div class="item-price">R$ 18,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Frango com Catupiry', 18, 'https://source.unsplash.com/random/300x300/?pastry,2')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,3" alt="Cheddar" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Cheddar - R$17</h3>
            <p class="item-description">Recheio de cheddar derretido</p>
            <div class="item-price">R$ 17,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Cheddar', 17, 'https://source.unsplash.com/random/300x300/?pastry,3')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,4" alt="Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Catupiry - R$17</h3>
            <p class="item-description">Puro catupiry cremoso</p>
            <div class="item-price">R$ 17,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Catupiry', 17, 'https://source.unsplash.com/random/300x300/?pastry,4')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,5" alt="Chester com Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Chester com Catupiry - R$19</h3>
            <p class="item-description">Carne de chester com catupiry</p>
            <div class="item-price">R$ 19,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Chester Catupiry', 19, 'https://source.unsplash.com/random/300x300/?pastry,5')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,6" alt="Carne Seca com Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Carne Seca com Catupiry - R$20</h3>
            <p class="item-description">Carne seca desfiada com catupiry</p>
            <div class="item-price">R$ 20,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Carne Seca Catupiry', 20, 'https://source.unsplash.com/random/300x300/?pastry,6')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?pastry,7" alt="Camarão com Catupiry" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Camarão com Catupiry - R$23</h3>
            <p class="item-description">Camarão ao molho com catupiry</p>
            <div class="item-price">R$ 23,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Camarão Catupiry', 23, 'https://source.unsplash.com/random/300x300/?pastry,7')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>

      <div id="doces" class="category">
        <div class="category-header">Doces</div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?dessert,1" alt="Doce de Leite" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Doce de Leite - R$14</h3>
            <p class="item-description">Doce de leite caseiro</p>
            <div class="item-price">R$ 14,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Doce de Leite', 14, 'https://source.unsplash.com/random/300x300/?dessert,1')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?dessert,2" alt="Romeu e Julieta" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Romeu e Julieta - R$15</h3>
            <p class="item-description">Goiabada com queijo</p>
            <div class="item-price">R$ 15,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Romeu e Julieta', 15, 'https://source.unsplash.com/random/300x300/?dessert,2')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?dessert,3" alt="Chocolate Preto" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Chocolate Preto - R$16</h3>
            <p class="item-description">Chocolate meio amargo</p>
            <div class="item-price">R$ 16,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Chocolate Preto', 16, 'https://source.unsplash.com/random/300x300/?dessert,3')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?dessert,4" alt="Chocolate Branco" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Chocolate Branco - R$16</h3>
            <p class="item-description">Chocolate branco cremoso</p>
            <div class="item-price">R$ 16,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Chocolate Branco', 16, 'https://source.unsplash.com/random/300x300/?dessert,4')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?dessert,5" alt="Chocolate Misto" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Chocolate Misto - R$16</h3>
            <p class="item-description">Mistura de chocolates</p>
            <div class="item-price">R$ 16,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Chocolate Misto', 16, 'https://source.unsplash.com/random/300x300/?dessert,5')">Adicionar</button>
            </div>
          </div>
        </div>
        <div class="item">
          <img src="https://source.unsplash.com/random/300x300/?dessert,6" alt="Nutella" class="item-image">
          <div class="item-details">
            <h3 class="item-title">Nutella (com ou sem morango) - R$20</h3>
            <p class="item-description">Nutella pura ou com morangos frescos</p>
            <div class="item-price">R$ 20,00</div>
            <div class="item-actions">
              <button class="add-to-cart" onclick="addItem('Nutella', 20, 'https://source.unsplash.com/random/300x300/?dessert,6')">Adicionar</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="cart-section">
      <h2 class="cart-title">Seu Pedido</h2>
      <div id="cart-items" class="cart-items">
        <div class="empty-cart">Seu carrinho está vazio</div>
      </div>
      <div id="cart-total" class="cart-total">Total: R$ 0,00</div>
      <div class="cart-actions">
        <button class="cart-button whatsapp-button" onclick="checkout()">
          <i class="fab fa-whatsapp"></i> Finalizar pelo WhatsApp
        </button>
        <button class="cart-button clear-button" onclick="clearCart()">Limpar Carrinho</button>
      </div>
    </div>
  </div>

  <script>
    let cart = [];
    
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
    
    // Atualiza a quantidade de um item
    function updateQuantity(index, change) {
      const item = cart[index];
      item.quantity += change;
      
      if (item.quantity <= 0) {
        removeItem(index);
      } else {
        updateCart();
        updateLocalStorage();
      }
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
    
    // Finaliza o pedido via WhatsApp
    function checkout() {
      if (cart.length === 0) {
        alert('Seu carrinho está vazio!');
        return;
      }
      
      let message = 'Olá, gostaria de fazer um pedido:\n\n';
      
      cart.forEach(item => {
        message += `${item.quantity}x ${item.name} - R$ ${(item.price * item.quantity).toFixed(2)}\n`;
      });
      
      const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
      message += `\nTotal: R$ ${total.toFixed(2)}\n\n`;
      message += 'Endereço de entrega:\n';
      message += 'Nome:\n';
      message += 'Telefone:\n';
      message += 'Forma de pagamento:';
      
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
    
    // Carrega o carrinho e configura o observador quando a página carrega
    window.addEventListener('DOMContentLoaded', () => {
      loadCart();
      setupIntersectionObserver();
    });
  </script>
</body>
</html>
