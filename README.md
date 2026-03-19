<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FarmDirect - Market Access</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 font-sans"><!-- Navbar --><nav class="bg-green-600 text-white p-4 flex justify-between">
  <h1 class="text-xl font-bold">🌾 FarmDirect</h1>
  <div>
    <button onclick="showLogin('farmer')" class="mr-4">Farmer Login</button>
    <button onclick="showLogin('buyer')">Buyer Login</button>
  </div>
</nav><!-- Hero Section --><section class="text-center p-10 bg-green-100">
  <h2 class="text-3xl font-bold mb-4">Direct Market Access for Farmers</h2>
  <p>Sell and buy fresh products directly without middlemen</p>
</section><!-- Login Section --><div id="loginSection" class="hidden p-6">
  <h2 id="loginTitle" class="text-xl font-bold mb-4"></h2>
  <input type="text" placeholder="Username" class="border p-2 w-full mb-2">
  <input type="password" placeholder="Password" class="border p-2 w-full mb-2">
  <button onclick="login()" class="bg-green-600 text-white px-4 py-2">Login</button>
</div><!-- Dashboard --><div id="dashboard" class="hidden p-6">
  <h2 class="text-2xl font-bold mb-4">Dashboard</h2>  <!-- Add Product -->  <div id="farmerSection" class="hidden">
    <h3 class="font-bold mb-2">Add Product</h3>
    <input id="productName" placeholder="Product Name" class="border p-2 mb-2 w-full">
    <input id="productPrice" placeholder="Price (₹)" class="border p-2 mb-2 w-full">
    <input type="file" class="mb-2">
    <button onclick="addProduct()" class="bg-green-600 text-white px-4 py-2">Add</button>
  </div>  <!-- Products List -->  <div class="mt-6">
    <h3 class="font-bold mb-2">Products</h3>
    <div id="productList" class="grid grid-cols-1 md:grid-cols-3 gap-4"></div>
  </div>
</div><script>
let role = "";
let products = [];

function showLogin(type) {
  role = type;
  document.getElementById('loginSection').classList.remove('hidden');
  document.getElementById('loginTitle').innerText = type.toUpperCase() + " LOGIN";
}

function login() {
  document.getElementById('loginSection').classList.add('hidden');
  document.getElementById('dashboard').classList.remove('hidden');
  if (role === 'farmer') {
    document.getElementById('farmerSection').classList.remove('hidden');
  }
}

function addProduct() {
  let name = document.getElementById('productName').value;
  let price = document.getElementById('productPrice').value;

  let product =
