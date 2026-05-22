<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Взаимопомощь</title>
    <script src="https://telegram.org"></script>
    <style>
        body { font-family: sans-serif; background-color: var(--tg-theme-bg-color, #fff); color: var(--tg-theme-text-color, #000); padding: 20px; }
        .btn { display: block; width: 100%; padding: 12px; background: var(--tg-theme-button-color, #2481cc); color: var(--tg-theme-button-text-color, #fff); border: none; border-radius: 8px; font-weight: bold; font-size: 16px; margin-top: 20px; }
        input, textarea { width: 100%; padding: 10px; margin-top: 5px; margin-bottom: 15px; border-radius: 6px; border: 1px solid #ccc; box-sizing: border-box; }
    </style>
</head>
<body>
    <h2>Сервис взаимопомощи 🤝</h2>
    <label>Что случилось?</label>
    <input type="text" id="title" placeholder="Кратко суть...">
    <label>Подробности и адрес</label>
    <textarea id="desc" rows="4" placeholder="Опишите детали..."></textarea>
    <button class="btn" onclick="sendData()">Опубликовать заявку</button>

    <script>
        const tg = window.Telegram.WebApp;
        tg.expand();
        function sendData() {
            const t = document.getElementById('title').value;
            const d = document.getElementById('desc').value;
            if(!t || !d) { tg.showAlert("Заполните поля!"); return; }
            tg.sendData(JSON.stringify({title: t, desc: d}));
            tg.close();
        }
    </script>
</body>
</html>
