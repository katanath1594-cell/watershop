<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ร้านชานมบ้านๆ</title>
    <style>
        body { font-family: sans-serif; margin: 20px; }
        .product { border: 1px solid #ccc; padding: 10px; margin: 10px; display: inline-block; width: 220px; text-align: center; }
        button { background: orange; border: none; padding: 5px 10px; cursor: pointer; }
        .cart-link { position: fixed; top: 20px; right: 20px; background: green; color: white; padding: 10px; text-decoration: none; }
        
        /* ปุ่มวงกลมความหวาน */
        .sweet-options { display: flex; justify-content: center; gap: 10px; margin: 10px 0; }
        .sweet-btn {
            width: 40px; height: 40px; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            border: 2px solid gray; cursor: pointer; font-size: 12px;
            background: white;
        }
        .sweet-btn.selected {
            border-color: orange;
            background: orange;
            color: white;
        }
    </style>
</head>
<body>
    <h1>ร้านชานมบ้านๆ</h1>
    <a class="cart-link" href="checkout.html">ตะกร้า 🛒</a>

    <div class="product" data-name="ชาไทยเย็น" data-price="35">
        <h3>ชาไทยเย็น</h3>
        <p>ราคา: 35 บาท</p>
        <div class="sweet-options">
            <div class="sweet-btn selected" onclick="selectSweet(this,'ชาไทยเย็น')">น</div>
            <div class="sweet-btn" onclick="selectSweet(this,'ชาไทยเย็น')">ป</div>
            <div class="sweet-btn" onclick="selectSweet(this,'ชาไทยเย็น')">ม</div>
        </div>
        <button onclick="addToCart('ชาไทยเย็น', 35)">เพิ่มในตะกร้า</button>
    </div>

    <div class="product" data-name="ชาเขียวนม" data-price="40">
        <h3>ชาเขียวนม</h3>
        <p>ราคา: 40 บาท</p>
        <div class="sweet-options">
            <div class="sweet-btn selected" onclick="selectSweet(this,'ชาเขียวนม')">น</div>
            <div class="sweet-btn" onclick="selectSweet(this,'ชาเขียวนม')">ป</div>
            <div class="sweet-btn" onclick="selectSweet(this,'ชาเขียวนม')">ม</div>
        </div>
        <button onclick="addToCart('ชาเขียวนม', 40)">เพิ่มในตะกร้า</button>
    </div>

    <div class="product" data-name="โกโก้เย็น" data-price="45">
        <h3>โกโก้เย็น</h3>
        <p>ราคา: 45 บาท</p>
        <div class="sweet-options">
            <div class="sweet-btn selected" onclick="selectSweet(this,'โกโก้เย็น')">น</div>
            <div class="sweet-btn" onclick="selectSweet(this,'โกโก้เย็น')">ป</div>
            <div class="sweet-btn" onclick="selectSweet(this,'โกโก้เย็น')">ม</div>
        </div>
        <button onclick="addToCart('โกโก้เย็น', 45)">เพิ่มในตะกร้า</button>
    </div>

    <div class="product" data-name="น้ำเปล่า" data-price="10">
        <h3>น้ำเปล่า</h3>
        <p>ราคา: 10 บาท</p>
        <div class="sweet-options">
            <div class="sweet-btn selected" onclick="selectSweet(this,'น้ำเปล่า')">น</div>
            <div class="sweet-btn" onclick="selectSweet(this,'น้ำเปล่า')">ป</div>
            <div class="sweet-btn" onclick="selectSweet(this,'น้ำเปล่า')">ม</div>
        </div>
        <button onclick="addToCart('น้ำเปล่า', 10)">เพิ่มในตะกร้า</button>
    </div>

    <script>
        let sweetChoices = {}; // เก็บระดับความหวานของแต่ละสินค้า

        function selectSweet(btn, productName) {
            let parent = btn.parentElement;
            Array.from(parent.children).forEach(b => b.classList.remove('selected'));
            btn.classList.add('selected');

            // แปลง น,ป,ม เป็นข้อความเต็ม
            let sweetFull = btn.textContent === 'น' ? 'หวานน้อย' :
                            btn.textContent === 'ป' ? 'หวานปกติ' :
                            'หวานมาก';
            sweetChoices[productName] = sweetFull;
        }

        function addToCart(name, price) {
            let sweetLevel = sweetChoices[name] || 'หวานน้อย';
            let cart = JSON.parse(localStorage.getItem('cart')) || [];
            cart.push({ name, price, sweet: sweetLevel });
            localStorage.setItem('cart', JSON.stringify(cart));
            alert(name + " (" + sweetLevel + ") ถูกเพิ่มในตะกร้าแล้ว!");
        }
    </script>
</body>
</html>
