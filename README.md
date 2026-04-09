# my-website
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pet Adoption</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
<style>
body {
    font-family: 'Poppins', sans-serif;
    margin: 0;
    background: linear-gradient(135deg, #fdfbfb, #ebedee);
    transition: 0.4s;
}

body.dark {
    background: #121212;
    color: white;
}

header {
    background: linear-gradient(45deg, #4CAF50, #2ecc71);
    color: white;
    padding: 20px;
    text-align: center;
    font-size: 24px;
    font-weight: 600;
}

.toggle-btn {
    position: absolute;
    right: 20px;
    top: 20px;
    padding: 8px 12px;
    border: none;
    border-radius: 20px;
    cursor: pointer;
}

.filters { text-align: center; margin: 20px; }
.filters button {
    padding: 10px 18px; margin: 5px; border: none;
    border-radius: 25px; background: #4CAF50; color: white;
    cursor: pointer;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 25px; padding: 20px;
}

.card {
    background: white; border-radius: 20px; overflow: hidden;
    box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    transition: 0.4s;
}

body.dark .card { background: #1e1e1e; }

.card:hover { transform: scale(1.05); }

.card img { width: 100%; height: 200px; object-fit: cover; }

.card-content { padding: 15px; }

.adopt-btn, .like-btn {
    margin-top: 8px; padding: 8px 12px;
    border: none; border-radius: 20px; cursor: pointer;
}

.adopt-btn { background: #4CAF50; color: white; }
.like-btn { background: #eee; }
.like-btn.active { background: red; color: white; }

/* Modal */
.modal {
    display: none; position: fixed; top: 0; left: 0;
    width: 100%; height: 100%; background: rgba(0,0,0,0.5);
    justify-content: center; align-items: center;
}

.modal-content {
    background: white; padding: 20px; border-radius: 10px;
}

</style>
</head>
<body>

<header>
    🐾 Pet Adoption Center
    <button class="toggle-btn" onclick="toggleDarkMode()">🌙</button>
</header>

<div class="filters">
    <button onclick="filterPets('all')">All</button>
    <button onclick="filterPets('dog')">Dogs</button>
    <button onclick="filterPets('cat')">Cats</button>
</div>

<div class="grid">

<div class="card dog">
    <img src="https://images.unsplash.com/photo-1558788353-f76d92427f16?w=400&h=300&fit=crop" width="200">
    <div class="card-content">
        <h3>Buddy</h3>
        <p>Labrador</p>
        <p>2 years</p>
        <button class="adopt-btn" onclick="openModal()">Adopt</button>
        <button class="like-btn" onclick="likePet(this)">❤️</button>
    </div>
</div>

<div class="card cat">
    <img src="https://images.unsplash.com/photo-1518791841217-8f162f1e1131?w=400&h=300&fit=crop" width="200">
    <div class="card-content">
        <h3>Whiskers</h3>
        <p>Persian</p>
        <p>1 year</p>
        <button class="adopt-btn" onclick="openModal()">Adopt</button>
        <button class="like-btn" onclick="likePet(this)">❤️</button>
    </div>
</div>


<div class="card dog">
    <img src="https://images.unsplash.com/photo-1507146426996-ef05306b995a?w=400&h=300&fit=crop" width="200">
    <div class="card-content">
        <h3>Charlie</h3>
        <p>Pug</p>
        <p>1 year</p>
        <button class="adopt-btn" onclick="openModal()">Adopt</button>
        <button class="like-btn" onclick="likePet(this)">❤️</button>
    </div>
</div>

<div class="card dog">
    <img src="https://images.unsplash.com/photo-1548199973-03cce0bbc87b?w=400&h=300&fit=crop" width="200">
    <div class="card-content">
        <h3>Max</h3>
        <p>Beagle</p>
        <p>4 years</p>
        <button class="adopt-btn" onclick="openModal()">Adopt</button>
        <button class="like-btn" onclick="likePet(this)">❤️</button>
    </div>
</div>

<div class="card cat">
    <img src="https://images.unsplash.com/photo-1574158622682-e40e69881006?w=400&h=300&fit=crop" width="200">
    <div class="card-content">
        <h3>Milo</h3>
        <p>Bengal</p>
        <p>2 years</p>
        <button class="adopt-btn" onclick="openModal()">Adopt</button>
        <button class="like-btn" onclick="likePet(this)">❤️</button>
    </div>
</div>

<div class="card cat">
    <img src="https://images.unsplash.com/photo-1533743983669-94fa5c4338ec?w=400&h=300&fit=crop" width="200">
    <div class="card-content">
        <h3>Simba</h3>
        <p>Maine Coon</p>
        <p>3 years</p>
        <button class="adopt-btn" onclick="openModal()">Adopt</button>
        <button class="like-btn" onclick="likePet(this)">❤️</button>
    </div>
</div>

</div>

<!-- Modal -->
<div class="modal" id="modal">
    <div class="modal-content">
        <h3>Adoption Form</h3>
        <input type="text" placeholder="Your Name"><br><br>
        <input type="email" placeholder="Email"><br><br>
        <button onclick="closeModal()">Submit</button>
    </div>
</div>

<script>
function filterPets(type) {
    document.querySelectorAll('.card').forEach(card => {
        card.style.display = (type==='all'||card.classList.contains(type)) ? 'block':'none';
    });
}

function toggleDarkMode() {
    document.body.classList.toggle('dark');
}

function likePet(btn) {
    btn.classList.toggle('active');
}

function openModal() {
    document.getElementById('modal').style.display='flex';
}

function closeModal() {
    document.getElementById('modal').style.display='none';
}
</script>

</body>
</html>
