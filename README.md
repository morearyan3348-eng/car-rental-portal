# car-rental-portal
https://github.com/morearyan3348-eng/car-rental-portal.gitfrom pathlib import Path

html = r'''<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>ARYA Car Rental Portal</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@500;600;700&family=Inter:wght@400;500;600;700&display=swap');
:root{--navy:#07131b;--cream:#f4efe3;--gold:#d7ad61;--gold2:#f0cf8a;--text:#17212a}
*{box-sizing:border-box;margin:0;padding:0}html{scroll-behavior:smooth}
body{font-family:Inter,sans-serif;background:var(--cream);color:var(--text)}
nav{height:72px;background:rgba(5,17,24,.98);display:flex;align-items:center;justify-content:space-between;padding:0 6%;position:sticky;top:0;z-index:20;border-bottom:1px solid #b9904e}
.logo{font-family:'Cormorant Garamond';font-size:32px;color:var(--gold2);font-weight:700;letter-spacing:4px;line-height:.75}.logo small{display:block;font:9px Inter;letter-spacing:4px;text-align:center;color:#ddd}
.navlinks{display:flex;gap:30px}.navlinks a{color:#eee;text-decoration:none;font-size:14px}.navlinks a:hover{color:var(--gold2)}
.creator{display:flex;align-items:center;gap:10px;color:#fff;font-size:11px}.creator img{width:42px;height:42px;border-radius:50%;object-fit:cover;border:2px solid var(--gold)}
.hero{min-height:610px;background:linear-gradient(90deg,rgba(3,12,18,.92),rgba(3,12,18,.35)),url('https://images.unsplash.com/photo-1493238792000-8113da705763?auto=format&fit=crop&w=1800&q=85') center/cover;display:flex;align-items:center;padding:70px 7% 130px;color:white;position:relative}
.hero h1{font:700 clamp(55px,7vw,88px)/.85 'Cormorant Garamond';max-width:700px;color:#fff}.hero h1 span{color:var(--gold2)}.hero p{max-width:560px;margin:25px 0;font-size:17px;line-height:1.7;color:#eee}
.btn{border:0;background:var(--gold2);color:#111;padding:14px 24px;border-radius:8px;font-weight:700;cursor:pointer}.btn:hover{transform:translateY(-2px)}
.booking{position:absolute;bottom:-48px;left:7%;right:7%;background:#08151e;color:#fff;border:1px solid #3e4b53;border-radius:14px;padding:20px;display:grid;grid-template-columns:1fr 1fr 1fr 1fr auto;gap:12px;box-shadow:0 15px 40px #0004}.field{border:1px solid #42515a;border-radius:8px;padding:10px}.field label{display:block;color:#bda675;font-size:11px;margin-bottom:5px}.field input{background:none;border:0;color:#fff;width:100%;outline:0}
section{padding:110px 7% 70px}.heading{text-align:center;margin-bottom:38px}.heading small{letter-spacing:4px}.heading h2{font:700 55px 'Cormorant Garamond';margin:5px}.heading p{color:#69747a}
.grid{display:grid;grid-template-columns:repeat(4,1fr);gap:18px}.card{background:#07151e;color:#fff;border-radius:13px;overflow:hidden;box-shadow:0 8px 25px #0002;transition:.25s}.card:hover{transform:translateY(-6px)}.card img{width:100%;height:175px;object-fit:cover}.cardbody{padding:17px}.card h3{font:600 24px 'Cormorant Garamond';color:#fff}.card p{font-size:12px;color:#aeb7bb;margin:4px 0 15px}.price{display:flex;align-items:center;justify-content:space-between;color:var(--gold2);font-weight:700}.mini{padding:9px 13px;border:1px solid var(--gold);background:transparent;color:#fff;border-radius:6px;cursor:pointer}
.features{background:#08151e;color:#fff;display:grid;grid-template-columns:repeat(5,1fr);gap:20px;text-align:center;padding:35px 7%}.feature b{display:block;color:var(--gold2);margin-bottom:6px}.feature span{font-size:11px;color:#adb8bd}
.about{display:grid;grid-template-columns:1fr 1fr;gap:50px;align-items:center}.about h2{font:700 55px 'Cormorant Garamond'}.about p{line-height:1.8;color:#5f686e;margin:15px 0}
footer{background:#06121a;color:#ddd;padding:45px 7% 25px;display:flex;justify-content:space-between;gap:30px}.footlogo{font:700 32px 'Cormorant Garamond';color:var(--gold2)}footer p{font-size:12px;color:#9da8ad;margin-top:8px}
.modal{display:none;position:fixed;inset:0;background:#000b;z-index:50;align-items:center;justify-content:center;padding:20px}.modal.show{display:flex}.box{background:#f4efe3;width:min(430px,100%);padding:30px;border-radius:15px;position:relative}.box h2{font:700 38px 'Cormorant Garamond';margin-bottom:18px}.box input,.box select{width:100%;padding:13px;margin:7px 0;border:1px solid #bbb;border-radius:7px}.close{position:absolute;right:18px;top:14px;font-size:25px;cursor:pointer}
@media(max-width:900px){.grid{grid-template-columns:repeat(2,1fr)}.booking{grid-template-columns:1fr 1fr}.features{grid-template-columns:repeat(2,1fr)}.about{grid-template-columns:1fr}.navlinks{display:none}}
@media(max-width:550px){.grid{grid-template-columns:1fr}.hero{padding-left:5%;padding-right:5%}.booking{left:5%;right:5%}section{padding-left:5%;padding-right:5%}}
</style>
</head>
<body>
<nav>
<div class="logo">ARYA<small>CAR RENTAL PORTAL</small></div>
<div class="navlinks"><a href="#home">Home</a><a href="#cars">Cars</a><a href="#about">About</a><a href="#contact">Contact</a></div>
<div class="creator"><img id="navProfile" src="https://i.pravatar.cc/100?img=12"><span>Created by<br><b>Aryan</b></span></div>
</nav>

<header class="hero" id="home">
<div><small style="letter-spacing:5px;color:#e2c98f">DRIVE YOUR DREAMS</small>
<h1>Rent Premium<br><span>Classic Cars</span></h1>
<p>Experience the perfect blend of timeless design, comfort and power. Choose from our handpicked classic collection and hit the road in style.</p>
<button class="btn" onclick="openBook()">Book Your Ride →</button></div>
<div class="booking">
<div class="field"><label>Pick-up Location</label><input placeholder="Enter city or location"></div>
<div class="field"><label>Drop-off Location</label><input placeholder="Same as pick-up"></div>
<div class="field"><label>Pick-up Date</label><input type="date"></div>
<div class="field"><label>Drop-off Date</label><input type="date"></div>
<button class="btn" onclick="searchCars()">Search Cars →</button>
</div>
</header>

<section id="cars">
<div class="heading"><small>OUR CLASSIC COLLECTION</small><h2>Choose Your Ride</h2><p>8 Premium Classic Cars — Timeless Legends, Ready For You</p></div>
<div class="grid">
<div class="card"><img src="https://images.unsplash.com/photo-1544829099-b9a0c07fad1a?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>Ford Mustang 1967</h3><p>The Legend Lives On</p><div class="price">₹6,999/day <button class="mini" onclick="openBook('Ford Mustang 1967')">Book</button></div></div></div>
<div class="card"><img src="https://images.unsplash.com/photo-1553440569-bcc63803a83d?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>Chevrolet Camaro 1969</h3><p>Power Meets Style</p><div class="price">₹6,499/day <button class="mini" onclick="openBook('Chevrolet Camaro 1969')">Book</button></div></div></div>
<div class="card"><img src="https://images.unsplash.com/photo-1533473359331-0135ef1b58bf?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>Chevrolet Bel Air 1957</h3><p>A Classic Icon</p><div class="price">₹7,999/day <button class="mini" onclick="openBook('Chevrolet Bel Air 1957')">Book</button></div></div></div>
<div class="card"><img src="https://images.unsplash.com/photo-1555215695-3004980ad54e?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>BMW 2002</h3><p>Vintage German Beauty</p><div class="price">₹5,999/day <button class="mini" onclick="openBook('BMW 2002')">Book</button></div></div></div>
<div class="card"><img src="https://images.unsplash.com/photo-1503736334956-4c8f8e92946d?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>Mercedes-Benz 300SL</h3><p>The Dream Machine</p><div class="price">₹9,999/day <button class="mini" onclick="openBook('Mercedes-Benz 300SL')">Book</button></div></div></div>
<div class="card"><img src="https://images.unsplash.com/photo-1618843479313-40f8afb4b4d8?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>Jaguar E-Type</h3><p>Beauty in Motion</p><div class="price">₹8,499/day <button class="mini" onclick="openBook('Jaguar E-Type')">Book</button></div></div></div>
<div class="card"><img src="https://images.unsplash.com/photo-1549317661-bd32c8ce0db2?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>Volkswagen Beetle</h3><p>Small Car, Big Soul</p><div class="price">₹4,999/day <button class="mini" onclick="openBook('Volkswagen Beetle')">Book</button></div></div></div>
<div class="card"><img src="https://images.unsplash.com/photo-1580273916550-e323be2ae537?auto=format&fit=crop&w=700&q=80"><div class="cardbody"><h3>Chrysler 300</h3><p>Royal on Wheels</p><div class="price">₹7,499/day <button class="mini" onclick="openBook('Chrysler 300')">Book</button></div></div></div>
</div>
</section>

<div class="features"><div class="feature"><b>🛡 Fully Insured</b><span>Safe & Secure</span></div><div class="feature"><b>◉ 24/7 Support</b><span>Always Here</span></div><div class="feature"><b>🚘 Well Maintained</b><span>Top Condition</span></div><div class="feature"><b>◇ Best Prices</b><span>No Hidden Charges</span></div><div class="feature"><b>⌖ Multiple Locations</b><span>Easy Pickup & Drop</span></div></div>

<section id="about"><div class="about"><div><small style="letter-spacing:4px">ABOUT ARYA</small><h2>Drive Classic.<br>Live Legendary.</h2><p>ARYA Car Rental Portal is a premium concept for people who appreciate timeless automobiles. Browse, select and book your dream classic car through a clean, modern rental experience.</p><button class="btn" onclick="openBook()">Start Booking</button></div><div style="background:#0a1820;color:#fff;border-radius:16px;padding:40px"><h3 style="font:40px 'Cormorant Garamond';color:#e5c37e">Created by Aryan</h3><p style="color:#bbc3c6;line-height:1.8">Designed as a student project / portfolio-ready car rental portal with classic luxury styling.</p></div></div></section>

<footer id="contact"><div><div class="footlogo">ARYA</div><p>Car Rental Portal · Drive Classic. Live Legendary.</p></div><div><b>Quick Links</b><p>Home · Cars · About · Contact</p></div><div><b>Created by Aryan 👑</b><p>© 2026 ARYA Car Rental Portal</p></div></footer>

<div class="modal" id="modal"><div class="box"><span class="close" onclick="closeBook()">×</span><h2>Reserve Your Ride</h2><p id="selectedCar" style="margin-bottom:10px;color:#6d604b"></p><input id="name" placeholder="Your Name"><input id="phone" placeholder="Mobile Number"><input type="date"><select><option>Select Pickup Location</option><option>Chalisgaon</option><option>Jalgaon</option><option>Nashik</option><option>Mumbai</option></select><button class="btn" style="width:100%;margin-top:10px" onclick="confirmBook()">Confirm Booking</button></div></div>

<script>
const modal=document.getElementById('modal');
function openBook(car=''){modal.classList.add('show');document.getElementById('selectedCar').textContent=car?`Selected car: ${car}`:'Select your preferred classic car.'}
function closeBook(){modal.classList.remove('show')}
function confirmBook(){let n=document.getElementById('name').value.trim();if(!n){alert('Please enter your name.');return}alert('Booking request received for '+n+'! ARYA Car Rental will contact you.');closeBook()}
function searchCars(){document.getElementById('cars').scrollIntoView({behavior:'smooth'});alert('Showing our available classic cars.')}
window.onclick=e=>{if(e.target===modal)closeBook()}
</script>
</body>
</html>'''

path = Path("/mnt/data/ARYA_Car_Rental_Portal/index.html")
path.parent.mkdir(parents=True, exist_ok=True)
path.write_text(html, encoding="utf-8")

import zipfile
zip_path = Path("/mnt/data/ARYA_Car_Rental_Portal.zip")
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    z.write(path, "index.html")

print(f"Created: {path}")
print(f"ZIP: {zip_path}")
