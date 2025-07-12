# Africa-tv
Site de streaming africaine 
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Wélé TV - Le cinéma africain chez vous</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background-color: #ffffff;
      color: #000;
    }
    header {
      background-color: #d35400;
      padding: 1rem;
      text-align: center;
      color: white;
    }
    header h1 {
      margin: 0;
      font-size: 2rem;
    }
    header p {
      font-style: italic;
      font-size: 1rem;
    }
    .main-content {
      padding: 2rem;
    }
    .download-section {
      text-align: center;
      margin: 2rem 0;
    }
    .download-button {
      background-color: #e67e22;
      color: white;
      padding: 1rem 2rem;
      font-size: 1.2rem;
      border: none;
      border-radius: 10px;
      text-decoration: none;
      display: inline-block;
      cursor: pointer;
    }
    .creator-link {
      display: block;
      margin-top: 1rem;
      color: #d35400;
      text-decoration: none;
      font-weight: bold;
    }
    .video-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 1rem;
      margin-top: 2rem;
    }
    .video-card {
      background-color: #f4f4f4;
      padding: 1rem;
      border-radius: 10px;
    }
    .video-card img, .video-card video, .video-card iframe {
      width: 100%;
      border-radius: 10px;
    }
    .video-card h3 {
      margin-top: 0.5rem;
      color: #000;
    }
    .video-card p {
      color: #333;
    }
    footer {
      text-align: center;
      padding: 1rem;
      background-color: #111;
      font-size: 0.9rem;
      color: white;
      margin-top: 3rem;
    }
    form input, form textarea {
      border-radius: 5px;
      border: 1px solid #ccc;
    }
  </style>
</head>
<body>
  <header>
    <h1>Africa-tv</h1>
    <p>Le cinéma africain chez vous</p>
  </header>

  <div class="main-content">
    <div class="download-section">
      <a href="/telechargement/weleTV.apk" class="download-button">📲 Télécharger l'application APK</a>
      <a href="mailto:toumani.sidibe@example.com" class="creator-link">📩 Contactez le créateur : Toumani Sidibé</a>
    </div>

    <!-- Bouton Ajouter un film -->
    <div class="download-section">
      <button onclick="document.getElementById('upload-form').style.display='block'" class="download-button">
        ➕ Ajouter un film
      </button>
    </div>

    <!-- Formulaire caché -->
    <div id="upload-form" style="display:none; background-color:#f9f9f9; padding:1rem; margin:1rem auto; width:90%; max-width:600px; border-radius:10px;">
      <h3>📤 Ajouter un nouveau film</h3>
      <form onsubmit="ajouterFilm(); return false;">
        <label>Titre du film :</label><br />
        <input type="text" id="titre" style="width:100%; padding:0.5rem;" required /><br /><br />

        <label>Description :</label><br />
        <textarea id="description" style="width:100%; padding:0.5rem;" required></textarea><br /><br />

        <label>Lien de la vidéo (YouTube ou .mp4) :</label><br />
        <input type="text" id="videoUrl" style="width:100%; padding:0.5rem;" required /><br /><br />

        <button type="submit" class="download-button">✅ Ajouter</button>
      </form>
    </div>

    <h2>Films populaires</h2>
    <div class="video-grid">
      <!-- Exemple de film -->
      <div class="video-card">
        <img src="https://via.placeholder.com/300x180" alt="Film 1" />
        <h3>Le Roi de Koulikoro</h3>
        <p>Un drame historique sur un chef légendaire malien.</p>
      </div>
      <div class="video-card">
        <img src="https://via.placeholder.com/300x180" alt="Film 2" />
        <h3>Ma vie à Bamako</h3>
        <p>Une comédie romantique en plein cœur de la capitale.</p>
      </div>
      <div class="video-card">
        <img src="https://via.placeholder.com/300x180" alt="Film 3" />
        <h3>La Voix du Djéli</h3>
        <p>Un documentaire sur la tradition orale mandingue.</p>
      </div>
    </div>
  </div>

  <footer>
    &copy; 2025 Wélé TV - Tous droits réservés
  </footer>

  <script>
    function ajouterFilm() {
      const titre = document.getElementById("titre").value;
      const description = document.getElementById("description").value;
      const videoUrl = document.getElementById("videoUrl").value;
      const videoGrid = document.querySelector(".video-grid");

      let newCard = document.createElement("div");
      newCard.className = "video-card";

      if (videoUrl.includes("youtube.com") || videoUrl.includes("youtu.be")) {
        let youtubeID = videoUrl.split("v=")[1] || videoUrl.split("/").pop();
        youtubeID = youtubeID.split("&")[0]; // Supprimer les paramètres en trop
        newCard.innerHTML = `
          <iframe width="100%" height="180" src="https://www.youtube.com/embed/${youtubeID}" frameborder="0" allowfullscreen></iframe>
          <h3>${titre}</h3>
          <p>${description}</p>
        `;
      } else {
        newCard.innerHTML = `
          <video width="100%" controls>
            <source src="${videoUrl}" type="video/mp4">
            Votre navigateur ne supporte pas la vidéo.
          </video>
          <h3>${titre}</h3>
          <p>${description}</p>
        `;
      }

      videoGrid.prepend(newCard); // Ajoute la nouvelle vidéo en haut
      document.getElementById("upload-form").style.display = "none";
      document.getElementById("titre").value = "";
      document.getElementById("description").value = "";
      document.getElementById("videoUrl").value = "";
    }
  </script>
</body>
</html>
