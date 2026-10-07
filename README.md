<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SELLO — Har kim sotuvchi</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #f4f5f7;
            color: #333;
            padding-bottom: 70px;
        }

        /* Header */
        header {
            background-color: #ffffff;
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            font-size: 22px;
            font-weight: 800;
            color: #0066ff;
            letter-spacing: 1px;
        }

        .add-btn {
            background-color: #0066ff;
            color: white;
            border: none;
            padding: 8px 14px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 13px;
            cursor: pointer;
        }

        /* Hero Banner */
        .banner {
            background: linear-gradient(135deg, #0066ff, #60a5fa);
            color: white;
            padding: 20px 15px;
            text-align: center;
        }

        .banner h1 {
            font-size: 20px;
            margin-bottom: 5px;
        }

        .banner p {
            font-size: 13px;
            opacity: 0.9;
        }

        /* Categories */
        .categories {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            padding: 15px;
            background: white;
        }

        .category-chip {
            background: #f0f4f9;
            padding: 8px 16px;
            border-radius: 20px;
            white-space: nowrap;
            font-size: 13px;
            font-weight: 500;
        }

        /* Products Grid */
        .products-container {
            padding: 15px;
        }

        .section-title {
            font-size: 16px;
            margin-bottom: 12px;
            font-weight: 700;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }

        .product-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0,0,0,0.04);
            display: flex;
            flex-direction: column;
        }

        .product-img {
            width: 100%;
            height: 140px;
            object-fit: cover;
            background-color: #eee;
        }

        .product-info {
            padding: 10px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .product-title {
            font-size: 14px;
            font-weight: 600;
            margin-bottom: 4px;
        }

        .product-price {
            font-size: 15px;
            color: #0066ff;
            font-weight: 700;
            margin-top: auto;
        }

        /* Bottom Nav */
        .bottom-nav {
            position: fixed;
            bottom: 0;
            width: 100%;
            background: white;
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            border-top: 1px solid #eee;
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            font-size: 11px;
            color: #666;
            text-decoration: none;
        }

        /* Modal Form */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 200;
            justify-content: center;
            align-items: flex-end;
        }

        .modal-content {
            background: white;
            width: 100%;
            border-radius: 20px 20px 0 0;
            padding: 20px;
            max-height: 90vh;
            overflow-y: auto;
            animation: slideUp 0.3s ease-out;
        }

        @keyframes slideUp {
            from { transform: translateY(100%); }
            to { transform: translateY(0); }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 20px;
            cursor: pointer;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            font-size: 12px;
            font-weight: 600;
            margin-bottom: 4px;
        }

        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 14px;
        }

        .submit-btn {
            width: 100%;
            background: #0066ff;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-weight: 600;
            font-size: 15px;
            margin-top: 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">SELLO</div>
        <button class="add-btn" onclick="openModal()">+ Sotish</button>
    </header>

    <div class="banner">
        <h1>Har kim sotuvchi!</h1>
        <p>Uyda turib soting. Oson buyurtma oling.</p>
    </div>

    <div class="categories">
        <div class="category-chip">🍰 Shirinliklar</div>
        <div class="category-chip">🌸 Atirlar</div>
        <div class="category-chip">👕 Kiyimlar</div>
        <div class="category-chip">📱 Telefonlar</div>
        <div class="category-chip">💄 Kosmetika</div>
    </div>

    <div class="products-container">
        <div class="section-title">Barcha mahsulotlar</div>
        <div class="product-grid" id="productGrid">
            <!-- Mahsulotlar JavaScript orqali chiqariladi -->
        </div>
    </div>

    <div class="bottom-nav">
        <a href="#" class="nav-item">🏠<br>Bosh sahifa</a>
        <a href="#" class="nav-item">🔎<br>Qidiruv</a>
        <a href="#" class="nav-item">📦<br>Buyurtmalar</a>
        <a href="#" class="nav-item">👤<br>Profil</a>
    </div>

    <!-- Mahsulot qo'shish oynasi -->
    <div class="modal" id="productModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Yangi mahsulot qo'shish</h3>
                <button class="close-btn" onclick="closeModal()">&times;</button>
            </div>
            <form id="addProductForm" onsubmit="saveProduct(event)">
                <div class="form-group">
                    <label>Mahsulot nomi</label>
                    <input type="text" id="pName" placeholder="Masalan: Shokoladli tort" required>
                </div>
                <div class="form-group">
                    <label>Narxi (so'mda)</label>
                    <input type="number" id="pPrice" placeholder="250000" required>
                </div>
                <div class="form-group">
                    <label>Rasm havolasi (URL)</label>
                    <input type="url" id="pImg" placeholder="https://..." required>
                </div>
                <button type="submit" class="submit-btn">E'longa joylash 🚀</button>
            </form>
        </div>
    </div>

    <script>
        const defaultProducts = [
            { name: "Shokoladli tort", price: "250000", img: "https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=400" },
            { name: "Atirgul buketi", price: "180000", img: "https://images.unsplash.com/photo-1561181286-d3fee7d55364?w=400" }
        ];

        function getProducts() {
            const saved = localStorage.getItem('sello_products');
            return saved ? JSON.parse(saved) : defaultProducts;
        }

        function renderProducts() {
            const grid = document.getElementById('productGrid');
            const products = getProducts();
            grid.innerHTML = products.map(p => `
                <div class="product-card">
                    <img src="${p.img}" class="product-img" alt="${p.name}">
                    <div class="product-info">
                        <div class="product-title">${p.name}</div>
                        <div class="product-price">${Number(p.price).toLocaleString('uz-UZ')} so'm</div>
                    </div>
                </div>
            `).join('');
        }

        function openModal() {
            document.getElementById('productModal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('productModal').style.display = 'none';
        }

        function saveProduct(e) {
            e.preventDefault();
            const name = document.getElementById('pName').value;
            const price = document.getElementById('pPrice').value;
            const img = document.getElementById('pImg').value;

            const products = getProducts();
            products.unshift({ name, price, img });
            localStorage.setItem('sello_products', JSON.stringify(products));

            renderProducts();
            closeModal();
            document.getElementById('addProductForm').reset();
        }

        renderProducts();
    </script>
</body>
</html>
