
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PRICEHUNT — Find the smarter deal</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#0b0d10;color:#f4f5f7;font-family:Arial,sans-serif}
header{padding:22px 7%;display:flex;justify-content:space-between;align-items:center;border-bottom:1px solid #20242a}
.logo{font-size:24px;font-weight:900;letter-spacing:1px}
.logo span{color:#a3e635}
nav a{color:#aaa;text-decoration:none;margin-left:20px;font-size:14px}
.hero{text-align:center;padding:85px 20px 55px}
.tag{color:#a3e635;font-size:12px;letter-spacing:3px}
h1{font-size:clamp(36px,7vw,68px);margin:20px 0;letter-spacing:-2px}
h1 span{color:#a3e635}
.hero p{color:#9ca3af;max-width:520px;margin:auto;line-height:1.7}
.search{max-width:680px;margin:32px auto 0;display:flex;background:#171a20;border:1px solid #333;border-radius:12px;padding:7px}
.search input{flex:1;min-width:0;background:transparent;border:0;color:white;padding:14px;outline:none;font-size:16px}
.search button{background:#a3e635;border:0;border-radius:8px;padding:0 23px;font-weight:bold;cursor:pointer}
main{max-width:1050px;margin:auto;padding:20px}
.section{display:flex;justify-content:space-between;align-items:center;margin:35px 0 18px}
.section h2{font-size:21px}
.section small{color:#9ca3af}
.filters{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:20px}
.filter{background:#171a20;border:1px solid #333;color:#ddd;padding:9px 15px;border-radius:30px;cursor:pointer}
.filter.active{background:#a3e635;color:#10130a;border-color:#a3e635}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:17px}
.card{background:#15181e;border:1px solid #252a31;border-radius:16px;padding:20px;transition:.2s}
.card:hover{border-color:#a3e635;transform:translateY(-3px)}
.product-img{height:145px;background:#20242b;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:64px;margin-bottom:16px}
.category{font-size:11px;color:#a3e635;letter-spacing:2px}
.card h3{margin:9px 0}
.card p{color:#9ca3af;font-size:13px;line-height:1.5}
.price{font-size:24px;font-weight:bold;margin:15px 0}
.card button{width:100%;padding:12px;background:#222730;border:1px solid #343a44;border-radius:9px;color:white;cursor:pointer}
.card button:hover{background:#a3e635;color:#10130a}
.note{color:#777;font-size:12px;text-align:center;margin:25px 0}
footer{border-top:1px solid #222;padding:28px;text-align:center;color:#777;font-size:13px;margin-top:60px}
</style>
</head>
<body>
<header>
<div class="logo">PRICE<span>HUNT</span></div>
<nav><a href="#products">Explore</a><a href="#about">About</a></nav>
</header>

<section class="hero">
<div class="tag">SMARTER SHOPPING STARTS HERE</div>
<h1>Hunt the price.<br><span>Find the deal.</span></h1>
<p>Discover products, explore alternatives and make smarter buying decisions without wasting your time.</p>
<div class="search">
<input id="search" placeholder="Search products..." oninput="render()">
<button onclick="render()">SEARCH</button>
</div>
</section>

<main id="products">
<div class="section">
<h2>Explore products</h2>
<small>Demo catalog</small>
</div>
<div class="filters">
<button class="filter active" onclick="setCat('All',this)">All</button>
<button class="filter" onclick="setCat('Tech',this)">Tech</button>
<button class="filter" onclick="setCat('Lifestyle',this)">Lifestyle</button>
<button class="filter" onclick="setCat('Accessories',this)">Accessories</button>
</div>
<div class="grid" id="grid"></div>
<p class="note">Demo prices are illustrative, not live offers.</p>
</main>

<footer id="about">
PRICEHUNT — Compare smarter. Buy better.<br><br>
A project designed to help people make informed choices.
</footer>

<script>
const products=[
{name:"Wireless Headphones",cat:"Tech",price:49,icon:"🎧",desc:"Comfortable audio for everyday use."},
{name:"Smart Watch",cat:"Tech",price:65,icon:"⌚",desc:"Track your everyday activity."},
{name:"Portable Speaker",cat:"Tech",price:35,icon:"🔊",desc:"Compact sound for your day."},
{name:"Everyday Backpack",cat:"Lifestyle",price:29,icon:"🎒",desc:"Simple storage for daily essentials."},
{name:"Desk Lamp",cat:"Lifestyle",price:22,icon:"💡",desc:"A practical addition to your workspace."},
{name:"Wireless Mouse",cat:"Accessories",price:18,icon:"🖱️",desc:"A simple tool for everyday computing."}
];
let category="All";
function setCat(cat,btn){
category=cat;
document.querySelectorAll(".filter").forEach(x=>x.classList.remove("active"));
btn.classList.add("active");
render();
}
function render(){
const query=document.getElementById("search").value.toLowerCase();
const list=products.filter(p=>(category==="All"||p.cat===category)&&p.name.toLowerCase().includes(query));
document.getElementById("grid").innerHTML=list.length?list.map(p=>`
<div class="card">
<div class="product-img">${p.icon}</div>
<div class="category">${p.cat.toUpperCase()}</div>
<h3>${p.name}</h3>
<p>${p.desc}</p>
<div class="price">$${p.price.toFixed(2)}</div>
<button onclick="alert('This is a sample product. Live price comparison will be added later.')">Explore product</button>
</div>`).join(""):`<p>No products found.</p>`;
}
render();
</script>
</body>
</html>
