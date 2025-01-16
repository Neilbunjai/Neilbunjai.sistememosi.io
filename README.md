# Neilbunjai.sistememosi.io'
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Sokongan Emosi</title>
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to right, #a1c4fd, #c2e9fb);
            color: #333;
            overflow-x: hidden;
        }
        .background-images {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            display: flex;
            justify-content: space-evenly;
            align-items: center;
            opacity: 0.1;
            pointer-events: none;
        }
        .background-images img {
            width: 200px;
            height: auto;
        }
        .container {
            width: 90%;
            max-width: 800px;
            margin: 50px auto;
            padding: 20px;
            background: #ffffff;
            border-radius: 20px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }
        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 30px;
        }
        .section {
            margin-bottom: 40px;
            padding: 20px;
            background: linear-gradient(135deg, #f9f9f9, #e3f2fd);
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
        }
        .section:hover {
            transform: translateY(-5px);
        }
        input[type="text"] {
            width: calc(100% - 90px);
            padding: 10px 15px;
            margin-right: 10px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 16px;
            box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        button {
            padding: 10px 15px;
            background: #007BFF;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            transition: background 0.3s;
        }
        button:hover {
            background: #0056b3;
        }
        #chat-response, #mood-response {
            margin-top: 20px;
            padding: 20px;
            border-radius: 15px;
            background: linear-gradient(135deg, #e3ffe7, #d9f7ff);
            font-size: 16px;
            font-family: 'Georgia', serif;
            font-style: italic;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }
        #chat-response::before, #mood-response::before {
            content: "💬";
            font-size: 24px;
            margin-right: 10px;
        }
        .emoji-section {
            text-align: center;
            margin-top: 10px;
        }
        .emoji {
            font-size: 30px;
            margin: 5px;
            cursor: pointer;
            transition: transform 0.2s, background 0.3s;
            padding: 5px;
            border-radius: 50%;
        }
        .emoji:hover {
            transform: scale(1.2);
            background: #f0f8ff;
        }
        #selected-emoji {
            font-size: 18px;
            margin-top: 10px;
            color: #555;
        }
    </style>
</head>
<body>
    <div class="background-images">
        <img src="https://via.placeholder.com/150/FFB6C1/000000?text=Compassion" alt="Compassion">
        <img src="https://via.placeholder.com/150/87CEFA/000000?text=Sadness" alt="Sadness">
        <img src="https://via.placeholder.com/150/FFD700/000000?text=Hope" alt="Hope">
        <img src="https://via.placeholder.com/150/98FB98/000000?text=Peace" alt="Peace">
        <img src="https://via.placeholder.com/150/FF6347/000000?text=Anger" alt="Anger">
    </div>
    <div class="container">
        <div class="flower-icon">🌸</div>
        <h1>Selamat Datang ke Chatbot Sokongan Emosi</h1>

        <div class="section" id="chatbot-section">
            <h2>Chatbot Interaktif</h2>
            <input id="chat-input" type="text" placeholder="Tulis sesuatu di sini...">
            <button onclick="sendMessage()">Hantar</button>
            <div id="chat-response"></div>
        </div>

        <div class="section" id="mood-section">
            <h2>Penilaian Mood AI</h2>
            <input id="mood-input" type="text" placeholder="Bagaimana mood anda? (gembira/sedih/stres)">
            <button onclick="evaluateMood()">Nilai Mood</button>
            <div id="mood-response"></div>
        </div>

        <div class="section" id="emoji-section">
            <h2>Pilih Emoji untuk Mood Anda</h2>
            <span class="emoji" onclick="selectEmoji('😊')">😊</span>
            <span class="emoji" onclick="selectEmoji('😢')">😢</span>
            <span class="emoji" onclick="selectEmoji('😡')">😡</span>
            <span class="emoji" onclick="selectEmoji('😌')">😌</span>
            <span class="emoji" onclick="selectEmoji('😐')">😐</span>
            <div id="selected-emoji">Mood emoji anda akan muncul di sini.</div>
        </div>
    </div>

    <script>
        // Chatbot Interaction
        function sendMessage() {
            const userInput = document.getElementById('chat-input').value.toLowerCase();
            let response;

            if (userInput.includes("assalamualaikum")) {
                response = "Walaikumusalam. Ada yang boleh saya bantu?";
            } else if (userInput.includes("selamat pagi")) {
                response = "Selamat pagi! Semoga hari anda menyenangkan.";
            } else if (userInput.includes("selamat tengahari")) {
                response = "Selamat tengahari! Semoga hari anda gembira selalu.";
            } else if (userInput.includes("selamat petang")) {
                response = "Selamat petang. Semoga petang anda lebih bermakna.";
            } else if (userInput.includes("terima kasih")) {
                response = "Sama-sama. Saya di sini untuk membantu!";
            } else if (userInput.includes("tiada siapa peduli")) {
                response = "Kamu penting dan dihargai. Siapa yang paling membuat kamu rasa dihargai?";
            } else if (userInput.includes("Hi")) {
                response = "Hi too. Nice to see you here!";
            } else {
                response = "Saya mendengar kamu. Adakah ada sesuatu yang kamu ingin kongsikan dengan lebih lanjut?";
            }

            document.getElementById('chat-response').innerText = response;
        }

        // Mood Evaluation
        function evaluateMood() {
            const mood = document.getElementById('mood-input').value.toLowerCase();
            let response;

            const moodResponses = {
                "gembira": [
                    "Bagus! Teruskan melakukan perkara yang membuatkan kamu gembira.",
                    "Semoga kebahagiaan kamu berpanjangan.",
                    "Senyuman kamu hari ini pasti membawa keceriaan.",
                    "Kamu adalah sumber kegembiraan bagi orang di sekeliling.",
                    "Teruskan dengan semangat positif ini!",
                    "Hari ini adalah hari yang baik untuk berkongsi kebahagiaan.",
                    "Kehidupan menjadi lebih indah dengan setiap senyuman.",
                    "Teruskan berjalan dalam keceriaan ini.",
                    "Kebahagiaanmu adalah inspirasi kepada orang lain.",
                    "Senyum selalu, dunia memerlukannya!"
                ],
                "sedih": [
                    "Maaf mendengarnya. Mungkin kamu boleh berbicara dengan seseorang yang dipercayai.",
                    "Sedih itu normal. Apa yang kamu rasa adalah valid.",
                    "Jangan risau, esok adalah hari yang baru dan penuh peluang.",
                    "Kamu tidak keseorangan dalam rasa sedih ini.",
                    "Kadang-kadang, menangis itu melegakan.",
                    "Perasaan sedih itu hanyalah sementara, dan kamu akan merasa lebih baik.",
                    "Ambil masa untuk diri sendiri dan berikan ruang untuk sembuh.",
                    "Sebaik-baiknya kamu beristirahat dan bersantai sebentar.",
                    "Kamu berhak merasai apa yang kamu rasakan, jangan pandang rendah perasaan itu.",
                    "Bersabarlah, hari yang lebih baik pasti akan datang."
                ],
                "stres": [
                    "Pastikan kamu berehat dan lakukan sesuatu yang menenangkan hati.",
                    "Jangan terlalu keras pada diri sendiri. Ambil masa untuk rehat.",
                    "Stres adalah perkara yang kita boleh kawal dengan sedikit usaha.",
                    "Cuba untuk menarik nafas panjang dan relaks.",
                    "Ambil beberapa minit untuk diri sendiri dan lepaskan ketegangan.",
                    "Terkadang, sedikit pergerakan boleh membantu melegakan stres.",
                    "Cuba beri perhatian kepada pernafasanmu, ia boleh menenangkan hati.",
                    "Berlapang dada dan jangan terlalu terbeban dengan harapan.",
                    "Senyum, walaupun sedikit, kerana ia dapat melegakan ketegangan.",
                    "Kadang-kadang, hanya dengan berhenti sejenak, kita dapat menemukan ketenangan."
                ],
                "bersemangat": [
                    "Semangatmu luar biasa, teruskan!",
                    "Impianmu semakin dekat, jangan berhenti!",
                    "Energi positifmu menginspirasi!",
                    "Kejar peluang dengan penuh semangat!",
                    "Terus melangkah, kejayaan menanti!"
                ],
                "puas hati": [
                     "Kamu layak untuk bahagia seperti ini.",
                     "Nikmati momen ini, kamu telah mencapainya.",
                     "Kepuasan adalah hasil dari usaha keras.",
                     "Teruskan memberi yang terbaik!",
                     "Syukuri pencapaianmu hari ini."
                ],
                "terharu": [
                     "Syukurilah saat-saat penuh makna ini.",
                     "Emosimu adalah tanda hatimu hidup.",
                     "Momen ini adalah hadiah kehidupan.",
                     "Jadikan perasaan ini inspirasi untuk lebih baik.",
                     "Hati yang tersentuh adalah hati yang kuat."
                ],
                "takut": [
		    "Beranikan diri, kamu mampu melaluinya.",
                    "Ketakutan adalah peluang untuk berkembang.",
                    "Langkah kecil adalah permulaan keberanian.",
                    "Hadapilah, cahaya menanti di seberang.",
                    "Kamu tidak sendirian dalam perasaan ini."
 		],
                "kecewa": [
		    "Kekecewaan adalah pelajaran terbaik.",
                    "Bangkitlah, kamu layak mendapat lebih baik.",
                    "Kecewa hari ini, kejayaan esok.",
                    "Belajar dari kegagalan, terus maju.",
                    "Hidup ini penuh peluang baru."
                ]
            };

            if (moodResponses[mood]) {
                response = moodResponses[mood][Math.floor(Math.random() * moodResponses[mood].length)];
            } else {
                response = "Maaf, saya tidak faham mood itu. Boleh cuba lagi?";
            }

            document.getElementById('mood-response').innerText = response;
        }

        // Emoji Selection
        const encouragements = {
            "😊": [
                "Senyumanmu membawa kegembiraan kepada orang lain! Teruskan tersenyum.",
                "Senyum adalah cara terbaik untuk memberi semangat kepada diri sendiri.",
                "Jangan lupa untuk terus berterima kasih atas kebahagiaan kecil dalam hidup.",
                "Kegembiraanmu adalah cerminan hati yang penuh dengan kasih sayang.",
                "Senyum yang ikhlas bisa mengubah hari seseorang!",
                "Dengan senyuman, kamu membuka pintu kepada dunia yang lebih cerah.",
                "Senyum itu adalah bahasa yang difahami oleh semua orang.",
                "Senyuman yang tulus membuat dunia terasa lebih indah.",
                "Keikhlasan senyumanmu adalah kebahagiaan sejati.",
                "Jangan berhenti tersenyum, kerana dunia memerlukan lebih banyak orang sepertimu!"
            ],
            "😢": [
                "Jangan risau, esok adalah hari yang baru dan penuh peluang.",
                "Hidup kadang memberi cabaran, tetapi kamu lebih kuat daripada yang kamu fikirkan.",
                "Tangisanmu adalah bentuk pelepasan yang penting. Semoga kamu rasa lebih baik segera.",
                "Jangan takut untuk merasai perasaanmu. Kamu berhak merasa apa yang kamu rasa.",
                "Hari yang sukar akan berlalu, dan kamu akan melalui ini dengan lebih kuat.",
                "Tangisan itu adalah cara tubuh memberi ruang untuk sembuh.",
                "Tidak ada salahnya untuk merasa sedih, itu adalah proses penyembuhan.",
                "Bersedih adalah sebahagian daripada perjalanan, dan kamu tidak keseorangan.",
                "Tangisan membawa kelegaan, dan selepas itu akan ada kekuatan baru.",
                "Semoga hatimu cepat sembuh dan kembali ceria."
            ],
            "😡": [
                "Ambil masa untuk tenangkan diri. Kamu berhak untuk rasa lebih baik.",
                "Cuba tarik nafas dalam-dalam. Terkadang, bernafas memberi ruang untuk ketenangan.",
                "Rasa marah itu wajar, tetapi jangan biarkan ia menguasai dirimu.",
                "Cuba untuk mengenali punca kemarahan kamu dan cari jalan penyelesaian.",
                "Hanya dengan ketenangan kita dapat mencari jalan keluar dari masalah.",
                "Menenangkan hati dan fikiran memberi kita kekuatan untuk bertindak dengan bijaksana.",
                "Dengarkan hatimu, dan pertimbangkan apa yang benar-benar kamu perlukan.",
                "Kemarahan itu adalah emosi yang boleh diselesaikan dengan ketenangan.",
                "Jangan biarkan amarah menguasai dirimu. Tenangkan hati dan fikirkan jalan keluar.",
                "Sabar, tindakan yang tenang akan membawa hasil yang lebih baik."
            ],
            "😌": [
                "Bagus! Jangan lupa bersyukur untuk momen tenang ini.",
                "Ketenangan adalah kekuatan terbesar. Nikmatilah momen ini.",
                "Tenanglah, kerana kedamaian hati membawa kebahagiaan sejati.",
                "Rasa tenang itu adalah hadiah. Nikmati saat-saat itu.",
                "Jangan biarkan gangguan luar merosakkan ketenanganmu.",
                "Ketenangan dalam hati adalah kunci untuk memahami diri sendiri.",
                "Kedamaian jiwa membawa kejelasan fikiran dan kekuatan batin.",
                "Ketenanganmu adalah cahaya dalam dunia yang kadang kala penuh kekeliruan.",
                "Ketenangan adalah cara kita berhubung dengan kedamaian dalam diri.",
                "Menjaga ketenangan membawa kekuatan untuk mengharungi segala cabaran."
            ],
            "😐": [
                "Kadang-kadang neutral itu baik. Teruskan melangkah ke depan!",
                "Tidak ada yang salah dengan merasa biasa saja. Ini adalah sebahagian daripada hidup.",
                "Perasaan yang tenang tanpa goncangan adalah sesuatu yang perlu dihargai.",
                "Terkadang, rasa neutral memberi kita ruang untuk memilih langkah selanjutnya.",
                "Perasaan netral itu adalah waktu yang baik untuk memberi fokus pada diri sendiri.",
                "Kadang-kadang, keseimbangan adalah yang terbaik. Teruskan bergerak ke hadapan.",
                "Rasa netral memberimu peluang untuk mencari perspektif baru.",
                "Saat ini adalah waktu yang baik untuk berehat dan merefleksi.",
                "Berfikir dengan kepala yang tenang sering kali membawa penyelesaian yang lebih baik.",
                "Terkadang, merasa netral adalah cara untuk memulakan sesuatu yang baru."
            ],
            "😞": [
	        "Kekecewaan adalah jalan menuju kebijaksanaan.",
                "Bangkitlah, kerana jatuh adalah sebahagian daripada proses.",
                "Tidak mengapa untuk kecewa, asalkan kamu tidak berhenti.",
                "Kegagalan hari ini adalah asas untuk kejayaan esok.",
                "Pelajaran terbesar datang dari kekecewaan terdalam."
            ],
            "😨": [
                "Keberanian adalah langkah pertama untuk mengatasi ketakutan.",
                "Jangan takut gagal, itu adalah guru terbaik.",
                "Ketakutan hanya ada dalam fikiranmu, bukan realiti.",
                "Langkah kecil tetap membawa perubahan besar.",
                "Percayalah pada dirimu, kamu mampu melakukannya.",
                "Rasa takut menunjukkan bahawa kamu sedang mencabar diri."
              
            ],
            "🤗": [
                "Hidup penuh dengan momen yang menyentuh hati.",
                "Hargai setiap kebaikan yang datang kepadamu.",
                "Emosi adalah tanda bahawa kamu benar-benar hidup.",
                "Setiap air mata syukur adalah doa dalam diam.",
                "Kebaikan kecil membawa kebahagiaan besar.",
                "Pengorbanan adalah tanda cinta sejati."
            ],
            "😄": [
	        "Hari ini adalah peluang terbaik untuk bersinar!",
                "Jangan takut untuk bermimpi besar.",
                "Setiap usaha adalah langkah menuju kejayaan.",
                "Semangat adalah bahan bakar kejayaan.",
                "Teruskan melangkah walaupun perlahan.",
                "Percayalah pada kemampuan dirimu."
            ]
        };

        function selectEmoji(emoji) {
            const emojiMessage = encouragements[emoji] ? encouragements[emoji][Math.floor(Math.random() * encouragements[emoji].length)] : "";
            document.getElementById('selected-emoji').innerText = `${emoji} ${emojiMessage}`;
        }
    </script>
</body>
</html>
