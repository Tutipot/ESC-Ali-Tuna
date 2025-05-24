# ESC-Ali-Tuna
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>ESC Ali Tuna</title>
<style>
  /* Aynı CSS kodu */
  body { font-family: Arial, sans-serif; background: #f4f4f9; margin: 0; padding: 0; }
  header { background: #1a1a2e; color: #fff; padding: 20px; text-align: center; }
  nav { background: #16213e; display: flex; justify-content: center; }
  nav button {
    background: none; border: none; color: #fff; padding: 15px 25px;
    cursor: pointer; font-size: 16px; transition: background 0.3s;
  }
  nav button:hover, nav button.active { background: #0f3460; }
  main { max-width: 900px; margin: 20px auto; padding: 0 15px; }
  section { display: none; }
  section.active { display: block; }
  h2 { border-bottom: 2px solid #0f3460; padding-bottom: 8px; }
  
  table {
    width: 100%; border-collapse: collapse; margin-top: 15px;
  }
  th, td {
    border: 1px solid #ccc; padding: 10px; text-align: left;
  }
  th {
    background-color: #0f3460; color: white;
  }
  
  .news-item {
    background: #fff; padding: 15px; margin-bottom: 15px; border-radius: 6px;
    box-shadow: 0 1px 5px rgba(0,0,0,0.1);
  }
  
  #forum-posts {
    max-height: 300px; overflow-y: auto; margin-bottom: 15px; background: #fff;
    padding: 15px; border-radius: 6px; box-shadow: 0 1px 5px rgba(0,0,0,0.1);
  }
  .post {
    border-bottom: 1px solid #ddd; padding: 8px 0;
  }
  .post:last-child {
    border-bottom: none;
  }
  #forum-form textarea {
    width: 100%; height: 80px; padding: 8px; resize: vertical; font-size: 14px;
  }
  #forum-form button {
    margin-top: 8px; padding: 10px 15px; background-color: #0f3460; color: #fff;
    border: none; cursor: pointer; font-size: 16px; border-radius: 4px;
  }
  #forum-form button:hover {
    background-color: #16213e;
  }
</style>
</head>
<body>

<header>
  <h1>ESC Ali Tuna</h1>
</header>

<nav>
  <button class="active" data-section="songs">Şarkılar</button>
  <button data-section="news">Haberler</button>
  <button data-section="forum">Forum</button>
</nav>

<main>
  <section id="songs" class="active">
    <h2>Eurovision 2025 Şarkıları</h2>
    <table>
      <thead>
        <tr><th>Ülke</th><th>Şarkı</th><th>Sanatçı</th></tr>
      </thead>
      <tbody id="songs-list"></tbody>
    </table>
  </section>

  <section id="news">
    <h2>Son Haberler</h2>
    <div class="news-item">
      <h3>Eurovision 2025 Başladı!</h3>
      <p>Eurovision 2025 heyecanı tüm Avrupa’yı sardı. Bu yıl şarkılar çok iddialı ve renkli!</p>
    </div>
    <div class="news-item">
      <h3>Final Tarihi Açıklandı</h3>
      <p>Final 18 Mayıs 2025’te gerçekleşecek. Heyecan dorukta!</p>
    </div>
    <div class="news-item">
      <h3>Eurovision Heyecanı Sona Erdi!</h3>
      <p>Avusturya JJ'in seslendirdiği <em>Wasted Love</em> şarkısıyla Eurovision'u kazandı. Senin favorin kimdi? Forum'a yaz!</p>
    </div>
  </section>

  <section id="forum">
    <h2>Eurovision 2025 Forum</h2>
    <div id="forum-posts">
      <p>Henüz hiç mesaj yok. İlk mesajı sen yaz!</p>
    </div>
    <form id="forum-form">
      <textarea placeholder="Mesajını buraya yaz..." required></textarea>
      <button type="submit">Gönder</button>
    </form>
  </section>
</main>

<script>
  const songs = [
    { country: "Albania", title: "Zjerm", artist: "Shkodra Elektronike" },
    { country: "Armenia", title: "SURVIVOR", artist: "PARG" },
    { country: "Australia", title: "Milkshake Man", artist: "Go-Jo" },
    { country: "Austria", title: "Wasted Love", artist: "JJ" },
    { country: "Azerbaijan", title: "Run With U", artist: "Mamagama" },
    { country: "Belgium", title: "Strobe Lights", artist: "Red Sebastian" },
    { country: "Croatia", title: "Poison Cake", artist: "Marko Bošnjak" },
    { country: "Cyprus", title: "Shh", artist: "Theo Evan" },
    { country: "Czechia", title: "Kiss Kiss Goodbye", artist: "ADONXS" },
    { country: "Denmark", title: "Hallucination", artist: "Sissal" },
    { country: "Estonia", title: "Espresso Macchiato", artist: "Tommy Cash" },
    { country: "Finland", title: "ICH KOMME", artist: "Erika Vikman" },
    { country: "France", title: "maman", artist: "Louane" },
    { country: "Georgia", title: "Freedom", artist: "Mariam Shengelia" },
    { country: "Germany", title: "Baller", artist: "Abor and Tynna" },
    { country: "Greece", title: "Asteromáta", artist: "Klavdia" },
    { country: "Iceland", title: "RÓA", artist: "VÆB" },
    { country: "Ireland", title: "Laika Party", artist: "Emmy" },
    { country: "Israel", title: "New Day Will Rise", artist: "Yuval Raphael" },
    { country: "Italy", title: "Volevo Essere Un Duro", artist: "Lucio Corsi" },
    { country: "Latvia", title: "Bur Man Laimi", artist: "Tautumeitas" },
    { country: "Lithuania", title: "Tavo Akys", artist: "Katarsis" },
    { country: "Luxembourg", title: "La Poupée Monte Le Son", artist: "Laura Thorn" },
    { country: "Malta", title: "SERVING", artist: "Miriana Conte" },
    { country: "Montenegro", title: "Dobrodošli", artist: "Nina Žižić" },
    { country: "Netherlands", title: "C’est La Vie", artist: "Claude" },
    { country: "Norway", title: "Lighter", artist: "Kyle Alessandro" },
    { country: "Poland", title: "GAJA", artist: "Justyna Steczkowska" },
    { country: "Portugal", title: "Deslocado", artist: "NAPA" },
    { country: "San Marino", title: "Tutta L’Italia", artist: "Gabry Ponte" },
    { country: "Serbia", title: "Mila", artist: "Princ" },
    { country: "Slovenia", title: "How Much Time Do We Have Left", artist: "Klemen" },
    { country: "Spain", title: "ESA DIVA", artist: "Melody" },
    { country: "Sweden", title: "Bara Bada Bastu", artist: "KAJ" },
    { country: "Switzerland", title: "Voyage", artist: "Zoë Më" },
    { country: "Ukraine", title: "Bird of Pray", artist: "Ziferblat" },
    { country: "United Kingdom", title: "What The Hell Just Happened?", artist: "Remember Monday" },
  ];

  const songsListEl = document.getElementById("songs-list");

  songs.forEach(({country, title, artist}) => {
    const tr = document.createElement("tr");
    tr.innerHTML = `<td>${country}</td><td>${title}</td><td>${artist}</td>`;
    songsListEl.appendChild(tr);
  });

  const navButtons = document.querySelectorAll("nav button");
  const sections = document.querySelectorAll("main section");

  navButtons.forEach(btn => {
    btn.addEventListener("click", () => {
      navButtons.forEach(b => b.classList.remove("active"));
      btn.classList.add("active");

      const target = btn.dataset.section;
      sections.forEach(sec => {
        if (sec.id === target) sec.classList.add("active");
        else sec.classList.remove("active");
      });
    });
  });

  const forumPosts = document.getElementById("forum-posts");
  const forumForm = document.getElementById("forum-form");
  const forumTextarea = forumForm.querySelector("textarea");

  let posts = [];

  forumForm.addEventListener("submit", e => {
    e.preventDefault();
    const message = forumTextarea.value.trim();
    if (message) {
      posts.push(message);
      renderPosts();
      forumTextarea.value = "";
    }
  });

  function renderPosts() {
    if (posts.length === 0) {
      forumPosts.innerHTML = "<p>Henüz hiç mesaj yok. İlk mesajı sen yaz!</p>";
      return;
    }
    forumPosts.innerHTML = "";
    posts.forEach(msg => {
      const div = document.createElement("div");
      div.classList.add("post");
      div.textContent = msg;
      forumPosts.appendChild(div);
    });
  }

  renderPosts();
</script>

</body>
</html>
