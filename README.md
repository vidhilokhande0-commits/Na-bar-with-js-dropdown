<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Simplified Navbar with Dropdown</title>
<style>
  * {margin:0; padding:0; box-sizing:border-box; font-family:Arial, sans-serif;}
  body {background:#f5f5f5;}
  nav {
    background:#2c3e50;
    padding:15px;
    border-radius:8px;
    margin-bottom:20px;
  }
  .nav-list {
    list-style:none;
    display:flex;
    gap:10px;
  }
  .nav-link {
    color:#fff;
    text-decoration:none;
    padding:10px 15px;
    border-radius:4px;
    display:block;
    transition:.3s;
  }
  .nav-link:hover {background:#34495e;}
  .nav-link.active {background:#3498db;}

  /* Dropdown */
  .dropdown {position:relative;}
  .dropdown-content {
    display:none;
    position:absolute;
    top:100%; left:0;
    background:#fff;
    min-width:160px;
    border-radius:4px;
    box-shadow:0 2px 5px rgba(0,0,0,.2);
    z-index:1;
  }
  .dropdown-content a {
    display:block;
    padding:10px 15px;
    text-decoration:none;
    color:#333;
    border-bottom:1px solid #eee;
  }
  .dropdown-content a:hover {background:#f0f0f0;}
  .show {display:block;}

  .content {
    padding:20px;
    background:#fff;
    border-radius:8px;
    box-shadow:0 2px 5px rgba(0,0,0,.1);
  }
  h1 {color:#2c3e50; margin-bottom:15px;}
  p {color:#555; margin-bottom:10px; line-height:1.6;}
</style>
</head>
<body>

<!-- Navbar -->
<nav>
  <ul class="nav-list">
    <li><a href="#" class="nav-link active">Home</a></li>
    <li><a href="#" class="nav-link">About</a></li>
    <li class="dropdown">
      <a href="#" class="nav-link">Services ▾</a>
      <div class="dropdown-content">
        <a href="#">Web Design</a>
        <a href="#">Development</a>
        <a href="#">SEO</a>
      </div>
    </li>
    <li><a href="#" class="nav-link">Contact</a></li>
  </ul>
</nav>

<div class="content">
  <h1>Navbar with Dropdown</h1>
  <p>This navbar uses JavaScript to:</p>
  <p>✔ Highlight the active link</p>
  <p>✔ Toggle the dropdown menu</p>
  <p>✔ Close the dropdown when clicking outside</p>
</div>

<script>
  const navLinks = document.querySelectorAll('.nav-link');
  const dropdown = document.querySelector('.dropdown');
  const dropdownContent = document.querySelector('.dropdown-content');
  const servicesLink = dropdown.querySelector('.nav-link');

  // Active link highlight
  navLinks.forEach(link => {
    link.addEventListener('click', function(e){
      navLinks.forEach(l => l.classList.remove('active'));
      this.classList.add('active');
    });
  });

  // Dropdown toggle
  servicesLink.addEventListener('click', e => {
    e.preventDefault();
    dropdownContent.classList.toggle('show');
  });

  // Close dropdown on outside click
  document.addEventListener('click', e => {
    if (!dropdown.contains(e.target)) dropdownContent.classList.remove('show');
  });
</script>

</body>
</html>