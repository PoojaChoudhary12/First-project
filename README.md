<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechStore - Modern E-Commerce</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: #f5f5f5;
        }

        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: opacity 0.3s;
        }

        .nav-links a:hover {
            opacity: 0.8;
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
            font-size: 1.5rem;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #ff4757;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.75rem;
            font-weight: bold;
        }

        .hero {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 4rem 2rem;
            text-align: center;
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .hero p {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 2rem;
        }

        .filters {
            background: white;
            padding: 1.5rem;
            border-radius: 10px;
            margin-bottom: 2rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            align-items: center;
        }

        .filter-group {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .filter-group label {
            font-weight: 600;
        }

        select, input {
            padding: 0.5rem;
            border: 2px solid #e0e0e0;
            border-radius: 5px;
            font-size: 1rem;
        }

        .search-box {
            flex: 1;
            min-width: 200px;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .product-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }

        .product-image {
            width: 100%;
            height: 250px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3rem;
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-category {
            color: #667eea;
            font-size: 0.85rem;
            text-transform: uppercase;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .product-name {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
        }

        .product-description {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .product-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #667eea;
        }

        .add-to-cart {
            background: #667eea;
            color: white;
            border: none;
            padding: 0.7rem 1.5rem;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s;
        }

        .add-to-cart:hover {
            background: #764ba2;
        }

        .cart-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .cart-modal.active {
            display: flex;
        }

        .cart-content {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            max-width: 600px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 2px solid #e0e0e0;
        }

        .close-cart {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            border-bottom: 1px solid #e0e0e0;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            font-weight: 600;
            margin-bottom: 0.25rem;
        }

        .cart-item-price {
            color: #667eea;
            font-weight: 600;
        }

        .cart-item-quantity {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin: 0 1rem;
        }

        .qty-btn {
            background: #667eea;
            color: white;
            border: none;
            width: 25px;
            height: 25px;
            border-radius: 3px;
            cursor: pointer;
            font-weight: bold;
        }

        .remove-item {
            background: #ff4757;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
        }

        .cart-total {
            margin-top: 1.5rem;
            padding-top: 1.5rem;
            border-top: 2px solid #e0e0e0;
            text-align: right;
        }

        .cart-total-label {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 1rem;
        }

        .cart-total-price {
            font-size: 2rem;
            color: #667eea;
            font-weight: bold;
        }

        .checkout-btn {
            width: 100%;
            background: #667eea;
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 5px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            margin-top: 1rem;
        }

        .checkout-btn:hover {
            background: #764ba2;
        }

        .empty-cart {
            text-align: center;
            padding: 2rem;
            color: #666;
        }

        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
        }

        @media (max-width: 768px) {
            .products-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
                gap: 1rem;
            }

            .hero h1 {
                font-size: 2rem;
            }

            .filters {
                flex-direction: column;
                align-items: stretch;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">🛒 TechStore</div>
            <div class="nav-links">
                <a href="#home">Home</a>
                <a href="#products">Products</a>
                <a href="#about">About</a>
                <div class="cart-icon" onclick="toggleCart()">
                    🛒
                    <span class="cart-count" id="cartCount">0</span>
                </div>
            </div>
        </nav>
    </header>

    <section class="hero">
        <h1>Welcome to TechStore</h1>
        <p>Discover the latest tech products at amazing prices</p>
    </section>

    <div class="container">
        <div class="filters">
            <div class="filter-group">
                <label>Category:</label>
                <select id="categoryFilter" onchange="filterProducts()">
                    <option value="all">All</option>
                    <option value="Electronics">Electronics</option>
                    <option value="Accessories">Accessories</option>
                    <option value="Audio">Audio</option>
                    <option value="Computing">Computing</option>
                </select>
            </div>
            <div class="filter-group">
                <label>Sort by:</label>
                <select id="sortFilter" onchange="filterProducts()">
                    <option value="default">Default</option>
                    <option value="price-low">Price: Low to High</option>
                    <option value="price-high">Price: High to Low</option>
                    <option value="name">Name: A-Z</option>
                </select>
            </div>
            <input type="text" class="search-box" id="searchBox" placeholder="Search products..." oninput="filterProducts()">
        </div>

        <div class="products-grid" id="productsGrid"></div>
    </div>

    <div class="cart-modal" id="cartModal">
        <div class="cart-content">
            <div class="cart-header">
                <h2>Shopping Cart</h2>
                <button class="close-cart" onclick="toggleCart()">✕</button>
            </div>
            <div id="cartItems"></div>
            <div class="cart-total">
                <div class="cart-total-label">Total:</div>
                <div class="cart-total-price" id="cartTotal">$0.00</div>
                <button class="checkout-btn" onclick="checkout()">Proceed to Checkout</button>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 TechStore. All rights reserved. | Internship Project</p>
    </footer>

    <script>
        const products = [
            { id: 1, name: "Wireless Headphones", category: "Audio", price: 79.99, description: "Premium sound quality with noise cancellation", icon: "🎧" },
            { id: 2, name: "Smart Watch", category: "Electronics", price: 199.99, description: "Track your fitness and stay connected", icon: "⌚" },
            { id: 3, name: "Laptop Stand", category: "Accessories", price: 39.99, description: "Ergonomic aluminum laptop stand", icon: "💻" },
            { id: 4, name: "Wireless Mouse", category: "Accessories", price: 29.99, description: "Smooth tracking and comfortable grip", icon: "🖱" },
            { id: 5, name: "USB-C Hub", category: "Accessories", price: 49.99, description: "7-in-1 multiport adapter", icon: "🔌" },
            { id: 6, name: "Mechanical Keyboard", category: "Computing", price: 129.99, description: "RGB backlit gaming keyboard", icon: "⌨" },
            { id: 7, name: "Portable Charger", category: "Electronics", price: 34.99, description: "20000mAh fast charging power bank", icon: "🔋" },
            { id: 8, name: "Bluetooth Speaker", category: "Audio", price: 59.99, description: "Waterproof portable speaker", icon: "🔊" },
            { id: 9, name: "Webcam HD", category: "Computing", price: 69.99, description: "1080p video streaming webcam", icon: "📷" },
            { id: 10, name: "Phone Stand", category: "Accessories", price: 19.99, description: "Adjustable phone holder", icon: "📱" },
            { id: 11, name: "Monitor 27\"", category: "Computing", price: 299.99, description: "4K Ultra HD display", icon: "🖥" },
            { id: 12, name: "Gaming Headset", category: "Audio", price: 89.99, description: "7.1 surround sound gaming headset", icon: "🎮" }
        ];

        let cart = [];
        let filteredProducts = [...products];

        function renderProducts() {
            const grid = document.getElementById('productsGrid');
            grid.innerHTML = filteredProducts.map(product => `
                <div class="product-card">
                    <div class="product-image">${product.icon}</div>
                    <div class="product-info">
                        <div class="product-category">${product.category}</div>
                        <div class="product-name">${product.name}</div>
                        <div class="product-description">${product.description}</div>
                        <div class="product-footer">
                            <div class="product-price">$${product.price.toFixed(2)}</div>
                            <button class="add-to-cart" onclick="addToCart(${product.id})">Add to Cart</button>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        function filterProducts() {
            const category = document.getElementById('categoryFilter').value;
            const sort = document.getElementById('sortFilter').value;
            const search = document.getElementById('searchBox').value.toLowerCase();

            filteredProducts = products.filter(p => {
                const matchCategory = category === 'all' || p.category === category;
                const matchSearch = p.name.toLowerCase().includes(search) || p.description.toLowerCase().includes(search);
                return matchCategory && matchSearch;
            });

            if (sort === 'price-low') {
                filteredProducts.sort((a, b) => a.price - b.price);
            } else if (sort === 'price-high') {
                filteredProducts.sort((a, b) => b.price - a.price);
            } else if (sort === 'name') {
                filteredProducts.sort((a, b) => a.name.localeCompare(b.name));
            }

            renderProducts();
        }

        function addToCart(productId) {
            const product = products.find(p => p.id === productId);
            const cartItem = cart.find(item => item.id === productId);

            if (cartItem) {
                cartItem.quantity++;
            } else {
                cart.push({ ...product, quantity: 1 });
            }

            updateCart();
        }

        function updateCart() {
            document.getElementById('cartCount').textContent = cart.reduce((sum, item) => sum + item.quantity, 0);
            renderCart();
        }

        function renderCart() {
            const cartItemsDiv = document.getElementById('cartItems');
            
            if (cart.length === 0) {
                cartItemsDiv.innerHTML = '<div class="empty-cart">Your cart is empty</div>';
                document.getElementById('cartTotal').textContent = '$0.00';
                return;
            }

            cartItemsDiv.innerHTML = cart.map(item => `
                <div class="cart-item">
                    <div class="cart-item-info">
                        <div class="cart-item-name">${item.name}</div>
                        <div class="cart-item-price">$${item.price.toFixed(2)}</div>
                    </div>
                    <div class="cart-item-quantity">
                        <button class="qty-btn" onclick="updateQuantity(${item.id}, -1)">-</button>
                        <span>${item.quantity}</span>
                        <button class="qty-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
                    </div>
                    <button class="remove-item" onclick="removeFromCart(${item.id})">Remove</button>
                </div>
            `).join('');

            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            document.getElementById('cartTotal').textContent = $${total.toFixed(2)};
        }

        function updateQuantity(productId, change) {
            const cartItem = cart.find(item => item.id === productId);
            if (cartItem) {
                cartItem.quantity += change;
                if (cartItem.quantity <= 0) {
                    removeFromCart(productId);
                } else {
                    updateCart();
                }
            }
        }

        function removeFromCart(productId) {
            cart = cart.filter(item => item.id !== productId);
            updateCart();
        }

        function toggleCart() {
            const modal = document.getElementById('cartModal');
            modal.classList.toggle('active');
        }

        function checkout() {
            if (cart.length === 0) {
                alert('Your cart is empty!');
                return;
            }
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            alert(Thank you for your order!\nTotal: $${total.toFixed(2)}\n\nThis is a demo project. No actual payment will be processed.);
            cart = [];
            updateCart();
            toggleCart();
        }

        renderProducts();
    </script>
</body>
</html>

