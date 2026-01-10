<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>F2KDigit Pro | Agence Digitale au Bénin</title>
  <meta name="description" content="F2KDigit Pro – Agence digitale au Bénin : sites web, marketing digital, design graphique, photo & vidéo." />
  <style>
    :root{
      --primary:#2563eb;
      --secondary:#0ea5e9;
      --dark:#020617;
      --light:#e5e7eb;
      --muted:#94a3b8;
    }
    *{box-sizing:border-box}
    body{margin:0;font-family:Arial, Helvetica, sans-serif;background:#0f172a;color:var(--light);line-height:1.6}
    header{background:linear-gradient(135deg,var(--primary),var(--secondary));padding:80px 20px;text-align:center}
    header h1{font-size:2.8rem;margin-bottom:10px}
    header p{max-width:800px;margin:auto;font-size:1.2rem}
    nav{position:sticky;top:0;z-index:1000;background:#020617;display:flex;justify-content:center;gap:20px;padding:15px 10px}
    nav a{color:var(--light);text-decoration:none;font-weight:bold}
    nav a:hover{color:var(--secondary)}
    section{padding:70px 20px;max-width:1200px;margin:auto}
    h2{text-align:center;color:#38bdf8;margin-bottom:30px}
    .services,.portfolio,.why{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:25px}
    .card{background:var(--dark);padding:25px;border-radius:15px;box-shadow:0 15px 30px rgba(0,0,0,.4);transition:.3s}
    .card:hover{transform:translateY(-5px)}
    .card h3{color:#60a5fa}
    .about,.contact{text-align:center;max-width:900px;margin:auto}
    .contact a{color:#38bdf8;text-decoration:none;font-weight:bold}
    form{display:grid;gap:15px;margin-top:30px}
    input,textarea,button{padding:12px;border-radius:8px;border:none;font-size:1rem}
    button{background:var(--primary);color:white;font-weight:bold;cursor:pointer}
    button:hover{background:var(--secondary)}
    footer{background:#020617;text-align:center;padding:25px;color:var(--muted);font-size:.9rem}
    .whatsapp{position:fixed;bottom:20px;right:20px;background:#25D366;color:white;padding:15px 18px;border-radius:50%;font-size:20px;text-decoration:none;box-shadow:0 10px 20px rgba(0,0,0,.4)}
    .success-message{display:none;margin-top:15px;color:#22c55e;font-weight:bold}
  </style>
</head>
<body>

<nav>
  <a href="#accueil">Accueil</a>
  <a href="#services">Services</a>
  <a href="#apropos">À propos</a>
  <a href="#portfolio">Portfolio</a>
  <a href="#devis">Demande de devis</a>
  <a href="#inscription">Créer un compte</a>
  <a href="#login">Connexion</a>
  <a href="#contact">Contact</a>
</nav>

<header id="accueil">
  <h1>F2KDigit Pro</h1>
  <p>Agence digitale professionnelle au Bénin. Nous aidons les entreprises et particuliers à réussir leur transformation numérique.</p>
</header>

<section id="inscription">
  <h2>Créer un compte client</h2>
  <div class="contact">
    <p>Inscrivez-vous librement. Aucune validation manuelle n’est requise.</p>

    <form id="signupForm">
      <input type="text" id="nom" placeholder="Nom complet" required />
      <input type="email" id="email" placeholder="Email" required />
      <input type="password" id="password" placeholder="Mot de passe" required />
      <button type="submit">Créer mon compte</button>
    </form>

    <p class="success-message" id="signupSuccess">✅ Compte créé avec succès !</p>
    <p class="success-message" id="signupError" style="color:#f87171">❌ Erreur lors de la création du compte.</p>
  </div>
</section>

<section id="login">
  <h2>Connexion</h2>
  <div class="contact">
    <form id="loginForm">
      <input type="email" id="loginEmail" placeholder="Email" required />
      <input type="password" id="loginPassword" placeholder="Mot de passe" required />
      <button type="submit">Se connecter</button>
    </form>

    <p class="success-message" id="loginSuccess">✅ Connexion réussie !</p>
    <p class="success-message" id="loginError" style="color:#f87171">❌ Email ou mot de passe incorrect.</p>
  </div>
</section>

<section id="devis">
  <h2>Demande de devis</h2>
  <div class="contact">
    <form id="devisForm">
      <input type="text" name="nom" placeholder="Nom complet" required />
      <input type="email" name="email" placeholder="Email" required />
      <input type="text" name="service" placeholder="Service souhaité" required />
      <input type="number" name="budget" placeholder="Budget estimé" />
      <textarea name="message" rows="5" placeholder="Décrivez votre projet" required></textarea>
      <button type="submit">Envoyer sur WhatsApp</button>
    </form>
  </div>
</section>

<footer>
  <p>© 2026 F2KDigit Pro – F2K MULTISERVICE. Tous droits réservés.</p>
</footer>

<a class="whatsapp" href="https://wa.me/2290158070708" target="_blank">💬</a>

<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-auth-compat.js"></script>
<script>
  const firebaseConfig = {
    apiKey: "VOTRE_API_KEY",
    authDomain: "VOTRE_PROJET.firebaseapp.com",
    projectId: "VOTRE_PROJET",
  };
  firebase.initializeApp(firebaseConfig);
  const auth = firebase.auth();

  // Inscription libre
  document.getElementById('signupForm').addEventListener('submit', function(e){
    e.preventDefault();
    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;
    auth.createUserWithEmailAndPassword(email, password)
      .then(() => {
        document.getElementById('signupSuccess').style.display = 'block';
        document.getElementById('signupError').style.display = 'none';
        e.target.reset();
      })
      .catch(() => {
        document.getElementById('signupError').style.display = 'block';
        document.getElementById('signupSuccess').style.display = 'none';
      });
  });

  // Connexion
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    const email = document.getElementById('loginEmail').value;
    const password = document.getElementById('loginPassword').value;
    auth.signInWithEmailAndPassword(email, password)
      .then(() => {
        document.getElementById('loginSuccess').style.display = 'block';
        document.getElementById('loginError').style.display = 'none';
      })
      .catch(() => {
        document.getElementById('loginError').style.display = 'block';
        document.getElementById('loginSuccess').style.display = 'none';
      });
  });
</script>

</body>
</html>
