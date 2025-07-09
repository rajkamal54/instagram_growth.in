<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Instagram_tf</title>
  <style>
    /* Reset & base */
    * {
      box-sizing: border-box;
    }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0; padding: 0;
      background: #fff;
      color: #222;
    }
    a {
      color: #0073e6;
      text-decoration: none;
    }
    a:hover {
      text-decoration: underline;
    }

    header {
      text-align: center;
      padding: 40px 20px;
      background: linear-gradient(45deg, #f09433, #e6683c, #dc2743, #cc2366, #bc1888);
      color: white;
      font-family: 'Arial Black', Gadget, sans-serif;
      border-radius: 0 0 20px 20px;
      margin-bottom: 30px;
      user-select: none;
    }
    header h1 {
      font-size: 3em;
      margin-bottom: 0.3em;
      text-shadow: 2px 2px 6px rgba(0,0,0,0.35);
    }
    header h2 {
      font-weight: 400;
      font-size: 1.8em;
      text-shadow: 1px 1px 4px rgba(0,0,0,0.25);
    }

    .container {
      max-width: 960px;
      margin: 0 auto 40px;
      padding: 0 15px;
    }

    .purchase-count {
      font-weight: bold;
      font-size: 1.2em;
      margin-bottom: 15px;
      text-align: center;
      color: #444;
    }

    /* Payment QR Code Section */
    .payment-section {
      text-align: center;
      margin: 30px 0 50px;
      user-select: none;
    }
    .payment-section p {
      font-weight: bold;
      font-size: 1.3em;
      color: #333;
      margin-bottom: 10px;
    }
    .payment-section img {
      width: 150px;
      height: 150px;
      border-radius: 15px;
      box-shadow: 0 0 12px #555;
    }
    .payment-section small {
      color: #666;
      font-style: italic;
      display: block;
      margin-top: 10px;
    }

    /* Form styles */
    form {
      background: #f9f9f9;
      border-radius: 15px;
      padding: 25px 30px;
      box-shadow: 0 0 15px rgb(0 0 0 / 0.05);
      max-width: 600px;
      margin: 0 auto 40px;
    }
    label {
      display: block;
      margin-bottom: 6px;
      font-weight: 600;
      color: #222;
    }
    select, input[type=text], input[type=email] {
      width: 100%;
      padding: 10px 12px;
      margin-bottom: 20px;
      border: 1.8px solid #ddd;
      border-radius: 10px;
      font-size: 1em;
      transition: border-color 0.3s ease;
    }
    select:hover, input[type=text]:hover, input[type=email]:hover,
    select:focus, input[type=text]:focus, input[type=email]:focus {
      border-color: #cc2366;
      outline: none;
    }
    .note-icon {
      display: inline-flex;
      align-items: center;
      margin-bottom: 20px;
      font-size: 0.9em;
      color: #cc2366;
      user-select: none;
    }
    .note-icon svg {
      width: 18px;
      height: 18px;
      margin-right: 6px;
      fill: #cc2366;
    }
    button {
      background: #cc2366;
      border: none;
      color: white;
      padding: 14px 22px;
      font-size: 1.1em;
      border-radius: 15px;
      cursor: pointer;
      width: 100%;
      font-weight: 700;
      transition: background-color 0.3s ease;
      user-select: none;
    }
    button:hover {
      background: #a71f57;
    }
    button:disabled {
      background: #ccc;
      cursor: not-allowed;
    }

    /* Login sections */
    .login-section {
      max-width: 380px;
      margin: 15px auto 40px;
      padding: 20px;
      background: #fafafa;
      border-radius: 15px;
      box-shadow: 0 0 20px rgb(0 0 0 / 0.05);
    }
    .login-section h3 {
      text-align: center;
      margin-bottom: 15px;
      color: #cc2366;
      font-weight: 700;
      user-select: none;
    }
    .login-section input {
      width: 100%;
      padding: 10px 14px;
      margin-bottom: 15px;
      border: 1.5px solid #ddd;
      border-radius: 10px;
      font-size: 1em;
      transition: border-color 0.3s ease;
    }
    .login-section input:focus {
      border-color: #cc2366;
      outline: none;
    }
    .login-section button {
      margin-top: 10px;
    }

    /* Panels */
    #userPanel, #adminPanel {
      max-width: 900px;
      margin: 0 auto 40px;
      padding: 20px;
      background: #fefefe;
      border-radius: 15px;
      box-shadow: 0 0 20px rgb(0 0 0 / 0.05);
    }
    #userPanel h2, #adminPanel h2 {
      color: #cc2366;
      user-select: none;
    }
    .logout-btn {
      background: #444;
      margin-top: 15px;
      padding: 10px 20px;
      border-radius: 10px;
      font-weight: 700;
      width: auto;
    }
    .logout-btn:hover {
      background: #222;
    }

    /* Purchase history & admin orders */
    .purchase-history, .admin-orders {
      margin-top: 25px;
      border-top: 2px solid #cc2366;
      padding-top: 15px;
      max-height: 320px;
      overflow-y: auto;
    }
    .purchase-history div, .admin-orders div {
      border-bottom: 1px solid #eee;
      padding: 10px 0;
      user-select: text;
    }
    .purchase-history div:last-child, .admin-orders div:last-child {
      border-bottom: none;
    }
    .purchase-history strong, .admin-orders strong {
      color: #cc2366;
    }

    .order-complete-btn {
      background: #28a745;
      border: none;
      padding: 8px 15px;
      border-radius: 10px;
      color: white;
      cursor: pointer;
      font-weight: 600;
      margin-top: 5px;
      transition: background-color 0.3s ease;
    }
    .order-complete-btn:hover {
      background: #1e7e34;
    }

    /* Ratings */
    #ratingSection {
      margin-top: 20px;
      background: #fef3f3;
      padding: 20px;
      border-radius: 15px;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
      box-shadow: 0 0 15px rgba(204, 35, 102, 0.2);
      display: none;
    }
    #ratingSection label {
      font-weight: 600;
      margin-bottom: 8px;
      display: block;
      color: #cc2366;
    }
    #ratingSection select, #ratingSection textarea {
      width: 100%;
      padding: 8px 10px;
      border: 1.5px solid #cc2366;
      border-radius: 10px;
      margin-bottom: 15px;
      font-size: 1em;
      resize: vertical;
    }
    #ratingSection textarea {
      height: 80px;
    }
    #ratingSection button {
      width: auto;
      margin-right: 10px;
    }

    /* Live rating display */
    .live-ratings {
      margin-top: 30px;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
      background: #fff0f6;
      border-radius: 15px;
      padding: 15px 20px;
      box-shadow: 0 0 10px rgba(204, 35, 102, 0.3);
      user-select: none;
    }
    .live-ratings h3 {
      color: #cc2366;
      margin-bottom: 10px;
    }
    .live-ratings span {
      font-weight: 700;
      font-size: 1.3em;
      margin-right: 15px;
    }
    .recent-ratings {
      margin-top: 15px;
      max-height: 180px;
      overflow-y: auto;
      padding-left: 10px;
      border-left: 4px solid #cc2366;
      font-style: italic;
      color: #aa0044;
    }

    /* Scrollbars for overflow */
    .purchase-history::-webkit-scrollbar,
    .admin-orders::-webkit-scrollbar,
    .recent-ratings::-webkit-scrollbar {
      width: 8px;
    }
    .purchase-history::-webkit-scrollbar-thumb,
    .admin-orders::-webkit-scrollbar-thumb,
    .recent-ratings::-webkit-scrollbar-thumb {
      background-color: #cc2366;
      border-radius: 10px;
    }
  </style>
</head>
<body>

<header>
  <h1>CHEAP AND BEST SELLING ON INSTAGRAM</h1>
  <h2>LIKES AND VIEWS AND FOLLOWERS</h2>
    <marquee behavior="scroll" direction="left" scrollamount="7">
      🚀 EVERY PURCHASE CASH BACK ₹20 | 🔧 UPCOMING UPDATE: VERSION 2.0 | 📱 TELEGRAM LIKES AND FOLLOWERS BOOST COMING SOON!
    </marquee>
<div class="container">

  <div class="purchase-count" id="purchaseCount">Total Purchases: 0</div>

<!-- Floating Chat Buttons -->
<a href="https://wa.me/91XXXXXXXXXX" target="_blank" class="chat-btn whatsapp-btn">💬 WhatsApp</a>
<a href="https://t.me/YOUR_TELEGRAM" target="_blank" class="chat-btn telegram-btn">📨 Telegram</a>

  <!-- User Login Section -->
  <section class="login-section" id="userLoginSection">
    <h3>User Login</h3>
    <form id="userLoginForm">
      <input type="text" id="userLoginName" placeholder="Username (e.g., TF1000)" required />
      <input type="password" id="userLoginPass" placeholder="Password (same as username)" required />
      <button type="submit">Login</button>
    </form>
  </section>

  <!-- Admin Login Section -->
  <section class="login-section" id="adminLoginSection">
    <h3>Admin Login</h3>
    <form id="adminLoginForm">
      <input type="text" id="adminLoginName" placeholder="Admin Username" required />
      <input type="password" id="adminLoginPass" placeholder="Admin Password" required />
      <button type="submit">Login</button>
    </form>
  </section>

  <!-- User Panel -->
  <section id="userPanel" style="display:none;">
    <h2>Welcome, <span id="userDisplayName"></span></h2>

    <form id="purchaseForm">
      <label for="optionSelect">Select Option</label>
      <select id="optionSelect" required>
        <optgroup label="LIKES (Charges may apply automatically - ₹4)">
          <option value="likes-1k" data-price="100" data-label="1K LIKES - 100 RS">1K LIKES - 100 RS</option>
          <option value="likes-2k" data-price="150" data-label="2K LIKES - 150 RS">2K LIKES - 150 RS</option>
          <option value="likes-5k" data-price="250" data-label="5K LIKES - 250 RS">5K LIKES - 250 RS</option>
          <option value="likes-10k" data-price="500" data-label="10K LIKES - 500 RS">10K LIKES - 500 RS</option>
        </optgroup>
        <optgroup label="VIEWS (Charges may apply automatically - ₹3)">
          <option value="views-1k" data-price="200" data-label="1K VIEWS - 200 RS">1K VIEWS - 200 RS</option>
          <option value="views-2k" data-price="250" data-label="2K VIEWS - 250 RS">2K VIEWS - 250 RS</option>
          <option value="views-5k" data-price="550" data-label="5K VIEWS - 550 RS">5K VIEWS - 550 RS</option>
          <option value="views-10k" data-price="1000" data-label="10K VIEWS - 1000 RS">10K VIEWS - 1000 RS</option>
        </optgroup>
        <optgroup label="FOLLOWERS (Charges may apply automatically - ₹5)">
          <option value="followers-1k" data-price="500" data-label="1K FOLLOWERS - 500 RS">1K FOLLOWERS - 500 RS</option>
          <option value="followers-2k" data-price="1000" data-label="2K FOLLOWERS - 1000 RS">2K FOLLOWERS - 1000 RS</option>
          <option value="followers-5k" data-price="25000" data-label="5K FOLLOWERS - 25000 RS">5K FOLLOWERS - 25000 RS</option>
          <option value="followers-10k" data-price="5500" data-label="10K FOLLOWERS - 5500 RS">10K FOLLOWERS - 5500 RS</option>
        </optgroup>
      </select>

      <label for="instaProfile">Instagram Profile <span style="color:#cc2366;">*</span></label>
      <input type="text" id="instaProfile" placeholder="Must be public profile username" required />

      <div class="note-icon" title="Instagram profile must be public, not private">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M12 0C5.371 0 0 5.371 0 12s5.371 12 12 12 12-5.371 12-12S18.629 0 12 0zM11 17h2v2h-2v-2zm1-14c2.761 0 5 2.239 5 5 0 2.761-2.239 5-5 5-2.761 0-5-2.239-5-5 0-2.761 2.239-5 5-5z"/></svg>
        Instagram should be <b>PUBLIC</b>, not private
      </div>

      <label for="postLink">Instagram Post Link / Reels URL</label>
      <input type="text" id="postLink" placeholder="Paste Instagram post or reels URL" />

      <label for="mailId">Email ID</label>
      <input type="email" id="mailId" placeholder="Enter your valid email" required />

      <label for="paymentUtr">Payment UTR Number</label>
      <input type="text" id="paymentUtr" placeholder="Enter payment UTR number" required />

      <button type="submit">Submit Purchase</button>
    </form>

    <!-- Payment QR Code -->
    <div class="payment-section">
      <p>Payment Method:</p>
      <img 
        src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=upi://pay?pa=6304431702@upi" 
        alt="Payment QR Code" 
      />
      <small>Scan this QR code to pay (Phone number is hidden)</small>
    </div>

    <!-- Purchase History -->
    <section class="purchase-history" id="purchaseHistory">
      <h3>Your Purchases</h3>
      <div id="userPurchaseList">No purchases yet.</div>
    </section>

    <!-- Rating Section -->
    <section id="ratingSection">
      <h3>Rate Your Order</h3>
      <label for="ratingStars">Rating (1 to 5 stars)</label>
      <select id="ratingStars">
        <option value="">Select Rating</option>
        <option value="1">⭐ 1 Star</option>
        <option value="2">⭐⭐ 2 Stars</option>
        <option value="3">⭐⭐⭐ 3 Stars</option>
        <option value="4">⭐⭐⭐⭐ 4 Stars</option>
        <option value="5">⭐⭐⭐⭐⭐ 5 Stars</option>
      </select>
      <label for="ratingComments">Comments (optional)</label>
      <textarea id="ratingComments" placeholder="Write your review here..."></textarea>
      <button id="submitRatingBtn">Submit Rating</button>
      <button id="cancelRatingBtn" style="background:#aaa;">Cancel</button>
    </section>

    <button class="logout-btn" id="userLogoutBtn">Logout</button>

    <!-- Live Ratings Display -->
    <div class="live-ratings" aria-live="polite" aria-atomic="true">
      <h3>Live Ratings</h3>
      <span>Average Rating: <strong id="avgRating">N/A</strong></span>
      <span>Total Ratings: <strong id="totalRatings">0</strong></span>
      <div class="recent-ratings" id="recentRatings">
        No ratings yet.
      </div>
    </div>
  </section>

  <!-- Admin Panel -->
  <section id="adminPanel" style="display:none;">
    <h2>Admin Panel</h2>

    <div class="admin-orders" id="adminOrdersList">
      <h3>Pending Orders</h3>
      <div id="ordersContainer">No pending orders.</div>
    </div>

    <button class="logout-btn" id="adminLogoutBtn">Logout</button>
  </section>

</div>

<script>

  // --- Constants ---
  const ADMIN_USERNAME = "6304431702";
  const ADMIN_PASSWORD = "5454";

  // --- Elements ---
  const userLoginSection = document.getElementById('userLoginSection');
  const adminLoginSection = document.getElementById('adminLoginSection');
  const userPanel = document.getElementById('userPanel');
  const adminPanel = document.getElementById('adminPanel');
  const userLoginForm = document.getElementById('userLoginForm');
  const adminLoginForm = document.getElementById('adminLoginForm');
  const userDisplayName = document.getElementById('userDisplayName');
  const purchaseForm = document.getElementById('purchaseForm');
  const purchaseCountEl = document.getElementById('purchaseCount');
  const userPurchaseList = document.getElementById('userPurchaseList');
  const adminOrdersList = document.getElementById('ordersContainer');
  const userLogoutBtn = document.getElementById('userLogoutBtn');
  const adminLogoutBtn = document.getElementById('adminLogoutBtn');
  const ratingSection = document.getElementById('ratingSection');
  const ratingStars = document.getElementById('ratingStars');
  const ratingComments = document.getElementById('ratingComments');
  const submitRatingBtn = document.getElementById('submitRatingBtn');
  const cancelRatingBtn = document.getElementById('cancelRatingBtn');
  const avgRatingEl = document.getElementById('avgRating');
  const totalRatingsEl = document.getElementById('totalRatings');
  const recentRatingsEl = document.getElementById('recentRatings');

  // --- State ---
  let currentUser = null; // username
  let orders = JSON.parse(localStorage.getItem('orders')) || [];
  let ratings = JSON.parse(localStorage.getItem('ratings')) || [];

  // --- Util Functions ---
  function saveOrders() {
    localStorage.setItem('orders', JSON.stringify(orders));
  }
  function saveRatings() {
    localStorage.setItem('ratings', JSON.stringify(ratings));
  }

  // --- Update Purchase Count ---
  function updatePurchaseCount() {
    purchaseCountEl.textContent = `Total Purchases: ${orders.length}`;
  }

  // --- Render User Purchases ---
  function renderUserPurchases() {
    if (!currentUser) return;
    let userOrders = orders.filter(o => o.username === currentUser);
    if (userOrders.length === 0) {
      userPurchaseList.textContent = 'No purchases yet.';
      ratingSection.style.display = 'none';
      return;
    }
    // Show list of purchases with status and rating prompt if success
    let html = '';
    userOrders.forEach((order, idx) => {
      html += `<div>
        <strong>Order #${idx+1}</strong> - ${order.selectedOptionLabel} - 
        Status: <span style="color:${order.status === 'success' ? 'green' : 'orange'}">${order.status}</span><br>
        Instagram Profile: ${order.instaProfile}<br>
        Post/Reels Link: ${order.postLink || '-'}<br>
        Email: ${order.mailId}<br>
        Payment UTR: ${order.paymentUtr}<br>
      </div>`;
      // Show rating section if order is success and not rated
      if(order.status === 'success' && !order.rated) {
        ratingSection.style.display = 'block';
        ratingSection.dataset.orderIndex = idx;
      }
    });
    userPurchaseList.innerHTML = html;
    if (!userOrders.some(o => o.status === 'success' && !o.rated)) {
      ratingSection.style.display = 'none';
    }
  }

  // --- Render Admin Orders ---
  function renderAdminOrders() {
    let pendingOrders = orders.filter(o => o.status === 'pending');
    if (pendingOrders.length === 0) {
      adminOrdersList.textContent = 'No pending orders.';
      return;
    }
    let html = '';
    pendingOrders.forEach((order, idx) => {
      html += `<div>
        <strong>Order #${idx+1}</strong> - ${order.selectedOptionLabel}<br>
        User: ${order.username}<br>
        Instagram Profile: ${order.instaProfile}<br>
        Post/Reels Link: ${order.postLink || '-'}<br>
        Email: ${order.mailId}<br>
        Payment UTR: ${order.paymentUtr}<br>
        <button class="order-complete-btn" data-index="${orders.indexOf(order)}">Mark as Success</button>
      </div>`;
    });
    adminOrdersList.innerHTML = html;

    // Add event listeners for "Mark as Success" buttons
    document.querySelectorAll('.order-complete-btn').forEach(btn => {
      btn.onclick = () => {
        let orderIndex = parseInt(btn.dataset.index, 10);
        if(confirm("Mark this order as SUCCESS? This will notify the user to rate.")) {
          orders[orderIndex].status = 'success';
          saveOrders();
          alert("Order marked as SUCCESS and user can now rate.");
          renderAdminOrders();
          if(currentUser) renderUserPurchases();
          updatePurchaseCount();
        }
      };
    });
  }

  // --- Update Live Ratings ---
  function updateLiveRatings() {
    if(ratings.length === 0) {
      avgRatingEl.textContent = 'N/A';
      totalRatingsEl.textContent = '0';
      recentRatingsEl.textContent = 'No ratings yet.';
      return;
    }
    let total = ratings.reduce((acc, r) => acc + r.rating, 0);
    let avg = (total / ratings.length).toFixed(2);
    avgRatingEl.textContent = `${avg} ⭐`;
    totalRatingsEl.textContent = ratings.length.toString();

    let html = '';
    ratings.slice(-5).reverse().forEach(r => {
      html += `<div>⭐ ${r.rating} - ${r.comment ? r.comment : '<i>No comment</i>'} <br><small><b>${r.username}</b></small></div>`;
    });
    recentRatingsEl.innerHTML = html;
  }

  // --- User Login ---
  userLoginForm.addEventListener('submit', e => {
    e.preventDefault();
    const username = document.getElementById('userLoginName').value.trim();
    const password = document.getElementById('userLoginPass').value.trim();

    if(!username.toUpperCase().startsWith('TF')) {
      alert("Username must start with 'TF' (e.g. TF1000).");
      return;
    }
    if(password !== username) {
      alert("Password must be the same as username.");
      return;
    }

    currentUser = username;
    userDisplayName.textContent = username;

    userLoginSection.style.display = 'none';
    adminLoginSection.style.display = 'none';
    userPanel.style.display = 'block';
    adminPanel.style.display = 'none';

    renderUserPurchases();
    updatePurchaseCount();
    updateLiveRatings();
  });

  // --- Admin Login ---
  adminLoginForm.addEventListener('submit', e => {
    e.preventDefault();
    const username = document.getElementById('adminLoginName').value.trim();
    const password = document.getElementById('adminLoginPass').value.trim();

    if(username !== ADMIN_USERNAME || password !== ADMIN_PASSWORD) {
      alert("Invalid admin credentials.");
      return;
    }
    currentUser = 'admin';

    userLoginSection.style.display = 'none';
    adminLoginSection.style.display = 'none';
    userPanel.style.display = 'none';
    adminPanel.style.display = 'block';

    renderAdminOrders();
    updatePurchaseCount();
  });

  // --- Logout ---
  userLogoutBtn.onclick = () => {
    if(confirm("Logout from user account?")) {
      currentUser = null;
      userPanel.style.display = 'none';
      userLoginSection.style.display = 'block';
      ratingSection.style.display = 'none';
      purchaseForm.reset();
      userPurchaseList.textContent = '';
    }
  };
  adminLogoutBtn.onclick = () => {
    if(confirm("Logout from admin account?")) {
      currentUser = null;
      adminPanel.style.display = 'none';
      adminLoginSection.style.display = 'block';
    }
  };

  // --- Submit Purchase ---
  purchaseForm.addEventListener('submit', e => {
    e.preventDefault();
    if(!currentUser) {
      alert("Please login first.");
      return;
    }

    const optionSelect = document.getElementById('optionSelect');
    const selectedOptionValue = optionSelect.value;
    const selectedOptionLabel = optionSelect.selectedOptions[0].dataset.label;
    const instaProfile = document.getElementById('instaProfile').value.trim();
    const postLink = document.getElementById('postLink').value.trim();
    const mailId = document.getElementById('mailId').value.trim();
    const paymentUtr = document.getElementById('paymentUtr').value.trim();

    if(!instaProfile) {
      alert("Please enter Instagram profile username.");
      return;
    }
    if(!mailId || !mailId.includes('@')) {
      alert("Please enter a valid email.");
      return;
    }
    if(!paymentUtr) {
      alert("Please enter Payment UTR number.");
      return;
    }

    // Save order with status pending and associate to user
    orders.push({
      username: currentUser,
      selectedOptionValue,
      selectedOptionLabel,
      instaProfile,
      postLink,
      mailId,
      paymentUtr,
      status: 'pending', // pending or success
      rated: false
    });
    saveOrders();

    alert("Purchase submitted successfully! Wait for admin confirmation.");
    purchaseForm.reset();
    renderUserPurchases();
    updatePurchaseCount();
  });

  // --- Submit Rating ---
  submitRatingBtn.onclick = () => {
    let orderIndex = parseInt(ratingSection.dataset.orderIndex, 10);
    let rating = parseInt(ratingStars.value, 10);
    let comment = ratingComments.value.trim();

    if(!rating || rating < 1 || rating > 5) {
      alert("Please select a rating between 1 and 5.");
      return;
    }
    if(orderIndex === undefined || isNaN(orderIndex)) {
      alert("Invalid order for rating.");
      return;
    }

    orders[orderIndex].rated = true;
    saveOrders();

    ratings.push({
      username: currentUser,
      rating,
      comment,
      timestamp: new Date().toISOString()
    });
    saveRatings();

    alert("Thank you for your rating!");
    ratingComments.value = '';
    ratingSection.style.display = 'none';

    updateLiveRatings();
    renderUserPurchases();
  };

  // --- Cancel Rating ---
  cancelRatingBtn.onclick = () => {
    ratingComments.value = '';
    ratingSection.style.display = 'none';
  };

  // --- Initial Setup ---
  userLoginSection.style.display = 'block';
  adminLoginSection.style.display = 'block';
  userPanel.style.display = 'none';
  adminPanel.style.display = 'none';
  ratingSection.style.display = 'none';

  updatePurchaseCount();
  updateLiveRatings();

</script>
</body>
</html>
  
