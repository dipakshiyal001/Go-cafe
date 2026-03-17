<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Go Cafe | Premium Dining</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        :root {
            --primary: #bc9c22; /* Elegant Gold */
            --dark: #121212;
            --light: #f9f9f9;
            --glass: rgba(255, 255, 255, 0.05);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Inter', sans-serif; background-color: var(--dark); color: var(--light); line-height: 1.6; }

        /* Navigation */
        nav {
            display: flex; justify-content: space-between; align-items: center;
            padding: 20px 8%; background: rgba(18, 18, 18, 0.95);
            position: sticky; top: 0; z-index: 1000; border-bottom: 1px solid rgba(255,255,255,0.1);
        }
        .logo { font-family: 'Playfair Display', serif; font-size: 1.8rem; color: var(--primary); font-weight: bold; }
        .nav-links a { margin-left: 25px; text-decoration: none; color: white; font-size: 0.9rem; transition: 0.3s; }
        .nav-links a:hover { color: var(--primary); }
        .login-btn { background: var(--primary); color: black !important; padding: 8px 20px; border-radius: 5px; font-weight: 600; }

        /* Hero Section */
        .hero {
            height: 60vh; background: linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)), url('https://images.unsplash.com/photo-1554118811-1e0d58224f24?auto=format&fit=crop&q=80&w=2000');
            background-size: cover; background-position: center;
            display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center;
        }
        .hero h1 { font-family: 'Playfair Display', serif; font-size: 4rem; margin-bottom: 10px; }
        .hero p { font-size: 1.2rem; opacity: 0.8; letter-spacing: 2px; }

        /* Menu Section */
        .container { max-width: 1200px; margin: 50px auto; padding: 0 20px; }
        .section-title { text-align: center; margin-bottom: 50px; }
        .section-title h2 { font-family: 'Playfair Display', serif; font-size: 2.5rem; color: var(--primary); }
        
        .menu-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px;
        }

        .menu-card {
            background: var(--glass); padding: 30px; border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.1); transition: 0.4s; position: relative; overflow: hidden;
        }
        .menu-card:hover { transform: translateY(-10px); border-color: var(--primary); background: rgba(255,255,255,0.08); }
        
        .item-row { display: flex; justify-content: space-between; margin-bottom: 15px; border-bottom: 1px dashed rgba(255,255,255,0.2); padding-bottom: 5px; }
        .item-name { font-weight: 600; font-size: 1.05rem; }
        .item-price { color: var(--primary); font-weight: bold; }

        /* Combo Section */
        .combo-box {
            background: linear-gradient(135deg, #1e1e1e, #121212);
            padding: 40px; border-radius: 20px; margin-top: 40px; border: 1px solid var(--primary);
            display: flex; justify-content: space-around; flex-wrap: wrap; text-align: center;
        }
        .combo-item h3 { color: var(--primary); margin-bottom: 10px; font-size: 1.5rem; }
        .combo-item p { font-size: 0.9rem; opacity: 0.7; }
        .price-tag { font-size: 1.8rem; font-weight: bold; margin: 10px 0; display: block; }

        /* Modal / Login form */
        #loginModal {
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); z-index: 2000; justify-content: center; align-items: center;
        }
        .modal-content {
            background: #222; padding: 40px; border-radius: 10px; width: 100%; max-width: 400px; text-align: center;
        }
        input { width: 100%; padding: 12px; margin: 10px 0; background: transparent; border: 1px solid #444; color: white; border-radius: 5px; }
        .submit-btn { background: var(--primary); width: 100%; padding: 12px; border: none; font-weight: bold; cursor: pointer; margin-top: 10px; }

        footer { text-align: center; padding: 40px; opacity: 0.5; font-size: 0.8rem; border-top: 1px solid #222; }

        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; }
            .nav-links { display: none; }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">GO CAFE</div>
        <div class="nav-links">
            <a href="#">Home</a>
            <a href="#menu">Menu</a>
            <a href="#specials">Specials</a>
            <a href="javascript:void(0)" class="login-btn" onclick="toggleLogin()">Login</a>
        </div>
    </nav>

    <header class="hero">
        <p>AUTHENTIC GUJARATI FLAVORS</p>
        <h1>Experience Go Cafe</h1>
    </header>

    <div class="container" id="menu">
        <div class="section-title">
            <h2>Our Signature Menu</h2>
            <p>Handcrafted dishes made with premium ingredients</p>
        </div>

        <div class="menu-grid">
            <div class="menu-card">
                <div class="item-row"><span class="item-name">Sev Tomato</span><span class="item-price">₹90</span></div>
                <div class="item-row"><span class="item-name">Sev Masala</span><span class="item-price">₹95</span></div>
                <div class="item-row"><span class="item-name">Kaju Gathiya</span><span class="item-price">₹110</span></div>
                <div class="item-row"><span class="item-name">Lasaniya Bataka</span><span class="item-price">₹80</span></div>
                <div class="item-row"><span class="item-name">Rasawala Bataka</span><span class="item-price">₹85</span></div>
                <div class="item-row"><span class="item-name">Bhindi Masala</span><span class="item-price">₹80</span></div>
            </div>

            <div class="menu-card">
                <div class="item-row"><span class="item-name">Lahsun Nu Shaak</span><span class="item-price">₹110</span></div>
                <div class="item-row"><span class="item-name">Lahsun Ghee Fry</span><span class="item-price">₹120</span></div>
                <div class="item-row"><span class="item-name">Dal Palak</span><span class="item-price">₹115</span></div>
                <div class="item-row"><span class="item-name">Palak Nu Shaak</span><span class="item-price">₹120</span></div>
                <div class="item-row"><span class="item-name">Dahi Bhindi</span><span class="item-price">₹130</span></div>
                <div class="item-row"><span class="item-name">Bharela Karela</span><span class="item-price">₹110</span></div>
            </div>
        </div>

        <div class="section-title" style="margin-top: 80px;" id="specials">
            <h2>Thali Specials</h2>
        </div>

        <div class="combo-box">
            <div class="combo-item">
                <h3>Executive Lunch</h3>
                <span class="price-tag">₹110</span>
                <p>1 Veg Shaak • 1 Kathod Dal • Rice<br>3 Roti • Papad • Salad</p>
            </div>
            <div style="width: 1px; background: rgba(255,255,255,0.1); margin: 0 20px;"></div>
            <div class="combo-item">
                <h3>Royal Dinner</h3>
                <span class="price-tag">₹150</span>
                <p>1 Veg Shaak • 1 Paneer Dal • Rice<br>2 Sweets • 5 Roti • Papad</p>
            </div>
        </div>
    </div>

    <div id="loginModal">
        <div class="modal-content">
            <h2 style="margin-bottom: 20px; font-family: 'Playfair Display';">Login to Go Cafe</h2>
            <input type="text" placeholder="Username / Email">
            <input type="password" placeholder="Password">
            <button class="submit-btn">SIGN IN</button>
            <p onclick="toggleLogin()" style="margin-top: 15px; font-size: 0.8rem; cursor: pointer; color: #888;">Close</p>
        </div>
    </div>

    <footer>
        &copy; 2026 GO CAFE. All Rights Reserved. <br>
        Crafted for a Premium Dining Experience.
    </footer>

    <script>
        // Initialize Icons
        lucide.createIcons();

        // Login Toggle
        function toggleLogin() {
            const modal = document.getElementById('loginModal');
            modal.style.display = (modal.style.display === 'flex') ? 'none' : 'flex';
        }

        // Close modal on click outside
        window.onclick = function(event) {
            const modal = document.getElementById('loginModal');
            if (event.target == modal) { modal.style.display = "none"; }
        }
    </script>
</body>
</html>
