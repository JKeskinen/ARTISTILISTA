
<html lang="fi">
<head>
  <meta charset="UTF-8">
  <title>Artistilista</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f7f7f7;
      padding: 20px;
    }
    h1 {
      text-align: center;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      background: #fff;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    th, td {
      border: 1px solid #ddd;
      padding: 8px 12px;
      text-align: left;
    }
    th {
      background: #4CAF50;
      color: white;
    }
    tr:nth-child(even) {
      background: #f2f2f2;
    }
  </style>
</head>
<body>
  <h1>Artistilista</h1>
  <table id="artistTable">
    <thead>
      <tr><th>ID</th><th>Nimi</th><th>Maa</th></tr>
    </thead>
    <tbody></tbody>
  </table>

  <script>
    async function loadArtists() {
      try {
        const res = await fetch("https://artisttabletesttite24juho.azurewebsites.net/api/artist");
        const data = await res.json();
        const tbody = document.querySelector("#artistTable tbody");

        data.forEach(artist => {
          const row = document.createElement("tr");
          row.innerHTML = `<td>${artist.artist_id}</td><td>${artist.name}</td><td>${artist.country}</td>`;
          tbody.appendChild(row);
        });
      } catch (err) {
        console.error("Virhe ladattaessa artisteja:", err);
      }
    }

    loadArtists();
  </script>
</body>
</html>
