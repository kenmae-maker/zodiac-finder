<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>星座判定</title>
</head>
<body>
    <h1>星座を調べましょう</h1>
    <p>誕生月と誕生日を入力して、「星座を判定」ボタンを押してください。</p>
    
    <label for="month">誕生月:</label>
    <input type="number" id="month" min="1" max="12" required><br><br>
    
    <label for="day">誕生日:</label>
    <input type="number" id="day" min="1" max="31" required><br><br>
    
    <button onclick="displayZodiac()">星座を判定</button>
    
    <p id="result"></p>

    <script>
        /**
         * 誕生月と日から星座を判定する関数
         * @param {number} month - 誕生月 (1-12)
         * @param {number} day - 誕生日 (1-31)
         * @returns {string} - 星座の日本語名、またはエラーメッセージ
         */
        function zodiac(month, day) {
            // 入力値の基本的な検証
            if (month < 1 || month > 12 || day < 1 || day > 31) {
                return "無効な日付";
            }

            if ((month === 3 && day >= 21) || (month === 4 && day <= 19)) {
                return "おひつじ"; // 3/21 - 4/19
            } else if ((month === 4 && day >= 20) || (month === 5 && day <= 20)) {
                return "おうし"; // 4/20 - 5/20
            } else if ((month === 5 && day >= 21) || (month === 6 && day <= 21)) {
                return "ふたご"; // 5/21 - 6/21
            } else if ((month === 6 && day >= 22) || (month === 7 && day <= 22)) {
                return "かに"; // 6/22 - 7/22
            } else if ((month === 7 && day >= 23) || (month === 8 && day <= 22)) {
                return "しし"; // 7/23 - 8/22
            } else if ((month === 8 && day >= 23) || (month === 9 && day <= 22)) {
                return "おとめ"; // 8/23 - 9/22
            } else if ((month === 9 && day >= 23) || (month === 10 && day <= 23)) {
                return "てんびん"; // 9/23 - 10/23
            } else if ((month === 10 && day >= 24) || (month === 11 && day <= 22)) {
                return "さそり"; // 10/24 - 11/22
            } else if ((month === 11 && day >= 23) || (month === 12 && day <= 21)) {
                return "いて"; // 11/23 - 12/21
            } else if ((month === 12 && day >= 22) || (month === 1 && day <= 19)) {
                return "やぎ"; // 12/22 - 1/19
            } else if ((month === 1 && day >= 20) || (month === 2 && day <= 18)) {
                return "みずがめ"; // 1/20 - 2/18
            } else if ((month === 2 && day >= 19) || (month === 3 && day <= 20)) {
                return "うお"; // 2/19 - 3/20
            } else {
                // ここに到達するのは無効な日付の組み合わせ（例：2月30日）
                return "該当なし (日付の入力に誤りがある可能性があります)";
            }
        }

        /**
         * 入力を取得し、星座を判定して結果を表示する関数
         */
        function displayZodiac() {
            // HTML要素から月と日の値を取得
            const monthInput = document.getElementById("month").value;
            const dayInput = document.getElementById("day").value;
            
            // 数値に変換
            const month = parseInt(monthInput, 10);
            const day = parseInt(dayInput, 10);
            
            const resultElement = document.getElementById("result");

            // 値が入力されているか確認
            if (isNaN(month) || isNaN(day) || monthInput === "" || dayInput === "") {
                resultElement.textContent = "⚠ 誕生月と誕生日を正しく入力してください。";
                return;
            }
            
            // 星座を判定
            const zodiacName = zodiac(month, day);
            
            // 結果を表示
            if (zodiacName === "無効な日付" || zodiacName.includes("該当なし")) {
                 resultElement.textContent = `⚠ ${zodiacName}`;
            } else {
                resultElement.textContent = `⭐ あなたの星座は**${zodiacName}座**です。`;
            }
        }
    </script>
</body>
</html>
