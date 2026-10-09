<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>読み込み中...</title>
  <style>
    body {
      font-family: sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f9f9f9;
      color: #333;
    }
  </style>
</head>
<body>
  <p>フォームへ移動しています...</p>

  <script>
    // 1. ご自身のTallyの直接リンクURLに変更してください
    const tallyBaseUrl = 'https://tally.so/forms/wLgovO';
    
    // 2. あなたのipinfoトークン
    const token = '7aa4542ad74edb';

    // IPアドレスを取得して自動でTallyへリダイレクト
    fetch(`https://ipinfo.io/json?token=${token}`)
      .then(response => response.json())
      .then(data => {
        const userIp = data.ip || '';
        const destination = `${tallyBaseUrl}?ip_address=${encodeURIComponent(userIp)}`;
        window.location.href = destination;
      })
      .catch(error => {
        // エラー時も通常通りTallyへ飛ばす
        window.location.href = tallyBaseUrl;
      });
  </script>
</body>
</html>
