# Humairah-meat-delivery
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Fresh Meat Delivery</title>

<!-- Google AdSense (Replace YOUR_AD_CLIENT & YOUR_SLOT) -->
<script data-ad-client="YOUR_AD_CLIENT" async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>

<!-- Firebase -->
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore-compat.js"></script>

<style>
body { font-family: Arial; padding: 15px; background:#f9f9f9; }
h2 { text-align:center; }
.card { border:1px solid #ddd; padding:15px; margin:10px 0; border-radius:10px; background:#fff; }
button { padding:10px; background:green; color:white; border:none; border-radius:5px; margin-top:5px; }
input { padding:8px; margin:5px 0; width:100%; border-radius:5px; border:1px solid #ccc; }
.admin-panel { border:2px solid red; padding:10px; margin:10px 0; border-radius:10px; background:#ffe0e0; }
</style>
</head>
<body>

<h2>Fresh Meat Delivery</h2>

<div id="authDiv">
  <input type="email" id="email" placeholder="Email">
  <input type="password" id="password" placeholder="Password">
  <button onclick="login()">Login</button>
  <button onclick="signup()">Sign Up</button>
</div>

<div id="mainDiv" style="display:none;">
  <p>Welcome <span id="userEmail"></span> <button onclick="logout()">Logout</button></p>

  <div id="adminPanel" class="admin-panel" style="display:none;">
    <h3>Admin Panel</h3>
    <input type="text" id="newProductName" placeholder="Product Name">
    <input type="number" id="newProductPrice" placeholder="Price">
    <input type="text" id="newProductCategory" placeholder="Category">
    <button onclick="addProduct()">Add Product</button>
    <h4>Orders</h4>
    <div id="ordersDiv"></div>
  </div>

  <h3>Products</h3>
  <div id="productsDiv"></div>

  <h3>Cart</h3>
  <div id="cartDiv"></div>
  <button onclick="payNow()">Pay Now</button>
</div>

<script src="https://checkout.razorpay.com/v1/checkout.js"></script>

<script>
  // ================= FIREBASE CONFIG =================
  const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT.firebaseapp.com",
    projectId: "YOUR_PROJECT",
    storageBucket: "YOUR_PROJECT.appspot.com",
    messagingSenderId: "YOUR_SENDER_ID",
    appId: "YOUR_APP_ID"
  };

  firebase.initializeApp(firebaseConfig);
  const auth = firebase.auth();
  const db = firebase.firestore();

  let currentUser = null;
  let cart = [];

  // ================= AUTH =================
  function signup() {
    const email = document.getElementById("email").value;
    const password = document.getElementById("password").value;
    auth.createUserWithEmailAndPassword(email,password)
      .then(userCred => {
        currentUser = userCred.user;
        initApp();
      }).catch(alert);
  }

  function login() {
    const email = document.getElementById("email").value;
    const password = document.getElementById("password").value;
    auth.signInWithEmailAndPassword(email,password)
      .then(userCred => {
        currentUser = userCred.user;
        initApp();
      }).catch(alert);
  }

  function logout() {
    auth.signOut().then(()=>location.reload());
  }

  // ================= INIT APP =================
  function initApp() {
    document.getElementById("authDiv").style.display="none";
    document.getElementById("mainDiv").style.display="block";
    document.getElementById("userEmail").innerText=currentUser.email;

    // Check admin
    if(currentUser.email === "admin@gmail.com"){
      document.getElementById("adminPanel").style.display="block";
      loadOrders();
    }

    loadProducts();
  }

  // ================= PRODUCTS =================
  function loadProducts() {
    db.collection("products").get().then(snapshot=>{
      let html="";
      snapshot.forEach(doc=>{
        const p = doc.data();
        html+=`<div class="card">
          <h4>${p.name} - ₹${p.price}</h4>
          <p>Category: ${p.category}</p>
          <button onclick="addToCart('${doc.id}','${p.name}',${p.price})">Add to Cart</button>
        </div>`;
      });
      document.getElementById("productsDiv").innerHTML=html;
    });
  }

  function addToCart(id,name,price){
    cart.push({id,name,price});
    renderCart();
  }

  function renderCart(){
    let html="";
    cart.forEach((c,i)=>{
      html+=`<p>${c.name} - ₹${c.price}</p>`;
    });
    document.getElementById("cartDiv").innerHTML=html;
  }

  // ================= ADMIN =================
  function addProduct(){
    const name = document.getElementById("newProductName").value;
    const price = parseFloat(document.getElementById("newProductPrice").value);
    const category = document.getElementById("newProductCategory").value;
    if(!name || !price) return alert("Enter values");
    db.collection("products").add({name,price,category})
      .then(()=>{ alert("Product Added"); loadProducts(); })
      .catch(alert);
  }

  function loadOrders(){
    db.collection("orders").get().then(snapshot=>{
      let html="";
      snapshot.forEach(doc=>{
        const o = doc.data();
        html+=`<p>Order #${doc.id} - ₹${o.total} - ${o.status}</p>`;
      });
      document.getElementById("ordersDiv").innerHTML=html;
    });
  }

  // ================= PAYMENT =================
  function payNow(){
    if(cart.length===0) return alert("Cart Empty");
    const total = cart.reduce((sum,c)=>sum+c.price,0)*100; // in paise
    const options = {
      key: "YOUR_RAZORPAY_KEY",
      amount: total,
      currency: "INR",
      name: "Fresh Meat Shop",
      description: "Order Payment",
      handler: function(response){
        saveOrder(total/100,response.razorpay_payment_id);
        cart=[];
        renderCart();
        alert("Payment Successful!");
      }
    };
    const rzp = new Razorpay(options);
    rzp.open();
  }

  function saveOrder(total,paymentId){
    db.collection("orders").add({
      user: currentUser.email,
      total,
      paymentId,
      status:"Order Placed",
      items: cart
    }).then(()=>{ if(currentUser.email==="admin@gmail.com") loadOrders(); });
  }

</script>

</body>
</html>
