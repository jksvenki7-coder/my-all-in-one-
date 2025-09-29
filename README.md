# my-all-in-one-<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>JKS Group Business Portal</title>
<style>
  body { font-family: Arial, sans-serif; background: #f7f7f7; margin: 0; }
  h1 { text-align: center; margin: 20px 0; }
  .main-menu {
    display: flex; flex-wrap: wrap; justify-content: center; gap: 25px; margin: 40px 0;
  }
  .menu-item {
    background: #fff; border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.08);
    padding: 25px 40px; font-size: 1.18em; text-align: center;
    cursor: pointer; transition: background 0.2s, box-shadow 0.2s;
    min-width: 165px;
  }
  .menu-item:hover {
    background: #f0f8ff;
    box-shadow: 0 4px 18px rgba(0,0,0,0.16);
  }
  /* Google Maps button on home page */
  .google-maps-btn {
    display: block;
    margin: 0 auto 30px auto;
    background: #4a90e2;
    color: white;
    padding: 12px 28px;
    border-radius: 8px;
    font-size: 1.2em;
    cursor: pointer;
    width: max-content;
    text-align: center;
    transition: background 0.3s;
  }
  .google-maps-btn:hover {
    background: #2370d9;
  }
  /* E-commerce Tabs */
  .tabs {
    display: flex; justify-content: center; margin-bottom: 15px;
  }
  .tab-btn {
    background: #fff; border: 1.5px solid #ddd; border-bottom: none;
    padding: 11px 28px; cursor: pointer;
    font-size: 1.16em; border-radius: 8px 8px 0 0;
    margin-right: 6px; transition: background 0.25s;
  }
  .tab-btn.active {
    background: #def1ff; border-color: #4a90e2; font-weight: bold;
  }
  .tab-content {
    background: #fff; border: 1.5px solid #ddd; border-radius: 0 8px 8px 8px;
    padding: 22px; max-width: 600px; margin: 0 auto 40px;
  }
  label {
    display: block; margin: 15px 0 7px 0; font-weight: 600;
  }
  input, textarea {
    width: 100%; padding: 11px 14px; border: 1.5px solid #bbb;
    border-radius: 8px; font-size: 1em; resize: vertical;
  }
  button.order-btn {
    margin-top: 28px; background: #25d366; color: white; border: none;
    padding: 15px; font-size: 1.18em; width: 100%; border-radius: 9px;
    cursor: pointer; transition: background 0.3s;
  }
  button.order-btn:hover { background: #128c7e; }
  /* Container for product names */
  .images-container {
    margin-top: 22px; display: flex; flex-wrap: wrap; gap: 14px; justify-content: center;
  }
  .image-item {
    width: 95px; height: 95px; background: #e4e4e4; border-radius: 12px;
    display: flex; justify-content: center; align-items: center;
    font-size: 0.9em; color: #666; padding: 5px; text-align: center;
  }
</style>
</head>
<body>

<!-- Main Home Menu -->
<section id="mainMenuSection">
  <h1>JKS Group of Business<br>All-In-One Portal</h1>
  <button class="google-maps-btn" onclick="openGoogleMaps()">Open Google Maps</button>
  <div class="main-menu">
    <div class="menu-item" onclick="navigateTo('ecommerce')">Recharge & Paybills</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">News App</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">RBL & Pets & Trees</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Franchise & Machinery</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Loans & Insurance</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Tours & Travels</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Home Services</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Events & Catering</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Business & Investments</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Courier & Ride Booking</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Job Consultancy</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Join My App</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">Real Estate & Construction</div>
    <div class="menu-item" onclick="navigateTo('ecommerce')">E-commerce</div>
  </div>
</section>

<!-- E-commerce Section with Groceries, Food & Medicines and order form only -->
<section id="ecommerceSection" style="display:none;">
  <h1 style="text-align:center;">E-commerce Portal</h1>
  <div class="tabs">
    <button class="tab-btn active" data-tab="groceries">Groceries</button>
    <button class="tab-btn" data-tab="food">Food</button>
    <button class="tab-btn" data-tab="medicines">Medicines</button>
  </div>
  <div class="tab-content" id="tabContent">
    <form id="orderForm" onsubmit="return false;">
      <input type="hidden" id="category" value="Groceries" />
      <label for="name">Name</label>
      <input type="text" id="name" placeholder="Enter your name" required />
      <label for="mobile">Mobile Number</label>
      <input type="tel" id="mobile" placeholder="Enter your mobile number" required />
      <label for="orderDetails">Order Details</label>
      <textarea id="orderDetails" rows="4" placeholder="Enter order items with quantity" required></textarea>
      <label for="address">Delivery Address</label>
      <textarea id="address" rows="3" placeholder="Enter delivery address" required></textarea>
      <button type="submit" class="order-btn" onclick="sendOrder()">Order via WhatsApp</button>
    </form>
    <div class="images-container" id="imagesContainer"></div>
  </div>
</section>

<script>
  // Navigation between sections
  function navigateTo(section) {
    document.getElementById('mainMenuSection').style.display = 'none';
    if(section === 'ecommerce') {
      document.getElementById('ecommerceSection').style.display = 'block';
      setCategory('groceries');
    }
  }

  // Google Maps open function
  function openGoogleMaps() {
    window.open('https://maps.google.com', '_blank');
  }

  // E-commerce tabs and images
  const tabBtns = document.querySelectorAll('.tab-btn');
  const categoryInput = document.getElementById('category');
  const imagesData = {
    groceries: ["Rice", "Beans", "Oil", "Salt", "Sugar", "Flour", "Pulses", "Spices", "Tea", "Coffee"],
    food: ["Bread", "Butter", "Eggs", "Milk", "Cheese", "Chicken", "Fish", "Fruits", "Vegetables", "Snacks"],
    medicines: ["Paracetamol", "Vitamins", "Cough Syrup", "Bandages", "Inhaler", "Pain Relief", "Antiseptic", "Cream", "Syrup", "First Aid Kit"]
  };
  const imagesContainer = document.getElementById('imagesContainer');
  tabBtns.forEach(btn => {
    btn.addEventListener('click', () => {
      tabBtns.forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      setCategory(btn.getAttribute('data-tab'));
      resetForm();
    });
  });

  function setCategory(cat) {
    categoryInput.value = cat.charAt(0).toUpperCase() + cat.slice(1);
    renderImages(cat);
  }

  function renderImages(cat) {
    if(!imagesContainer) return;
    imagesContainer.innerHTML = '';
    imagesData[cat].forEach(name => {
      const div = document.createElement('div');
      div.className = 'image-item';
      div.textContent = name;
      imagesContainer.appendChild(div);
    });
  }

  function resetForm() {
    const form = document.getElementById('orderForm');
    if(form) form.reset();
  }

  function sendOrder() {
    const category = categoryInput.value;
    const name = document.getElementById('name').value.trim();
    const mobile = document.getElementById('mobile').value.trim();
    const orderDetails = document.getElementById('orderDetails').value.trim();
    const address = document.getElementById('address').value.trim();

    if(!name || !mobile || !orderDetails || !address) {
      alert('Please fill all the fields.');
      return;
    }

    const waNumber = '8977143043';
    const message = encodeURIComponent(
      `Order from ${category}:\nName: ${name}\nMobile: ${mobile}\nOrder Details: ${orderDetails}\nDelivery Address: ${address}`
    );
    window.open(`https://wa.me/${waNumber}?text=${message}`, '_blank');
  }

  // Initialize the portal on load
  window.onload = () => {
    document.getElementById('mainMenuSection').style.display = 'block';
    document.getElementById('ecommerceSection').style.display = 'none';
    setCategory('groceries');
  }
</script>

</body>
</html>
