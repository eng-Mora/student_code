<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بحث عن الطلاب</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 10px;
        }
        .container {
            max-width: 100%;
            margin: 0 auto;
            background-color: #34495e;
            color: white;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.1);
        }
        input[type="text"] {
            width: 90%;
            padding: 12px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
        }
        button {
            background-color: #2980b9;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            width: 90%;
        }
        button:hover {
            background-color: #3498db;
        }
        p.result {
            margin-top: 20px;
            font-size: 18px;
        }
        @media (max-width: 600px) {
            .container {
                padding: 10px;
            }
            input[type="text"], button {
                font-size: 14px;
                padding: 10px;
            }
            p.result {
                font-size: 16px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>بحث عن الطلاب</h1>
        <input type="text" id="searchInput" placeholder="أدخل الاسم الكامل، الاسم الأول أو الكود">
        <button onclick="search()">بحث</button>
        <p class="result" id="result"></p>
    </div>

    <script>
        const students = {
            "49696": "ادم عمرو",
            "81659": "نور عبدالرحمن",
            "39639": "ايمان محمد",
            "29474": "محمد ايهاب عبدالفتاح",
            "86074": "نيفين حمدي محمد",
            "30693": "رحمه ماجد",
            "25654": "اسلام محمد شعراوي",
            "50808": "احمد حسين",
            "84536": "زياد خالد",
            "41596": "نور الدين هيثم",
            "11633": "يوسف ايمن ابوضيف",
            "41715": "احمد حسام",
            "58471": "عبدالرحمن شعبان",
            "18054": "حنين السيد سليمان",
            "20321": "بسنت محمد",
            "52182": "عمر وليد جمال",
            "47916": "عبدالله احمد محمود",
            "35365": "حاتم امين محمد",
            "37144": "عبدالله احمد صلاح",
            "10781": "ياسمين السيد",
            "44889": "محمد سليم",
            "82128": "زياد ايهاب",
            "89303": "حمدي محمد",
            "80546": "مازن احمد سمير",
            "32546": "لوجين وائل",
            "23756": "ضحى محمد",
            "54620": "سلمى سامح",
            "67084": "هنا سعد",
            "16840": "سما ابراهيم",
            "15032": "تسنيم محمد",
            "88105": "سندي عصام",
            "72137": "رودينا ايمن",
            "80135": "محمد اشرف",
            "28126": "يوسف محمد",
            "56193": "حبيبة محمد",
            "75516": "حنين مصطفى",
            "53336": "مريم اشرف",
            "48389": "سندس صلاح",
            "92758": "مازن عبدالوهاب",
            "28354": "مريم احمد",
            "75539": "جنى طارق",
            "58951": "سارة عماد",
            "89089": "جنة محمد",
            "41292": "مريم سعيد",
            "32859": "مريم عاطف",
            "44746": "سعيد سعد",
            "30223": "سيف الدين تامر",
            "21428": "محمد احمد",
            "20608": "زياد احمد",
            "48392": "عمار اشرف",
            "16075": "امنية ايمن",
            "69897": "اروى احمد",
            "86284": "حبيبة شعبان",
            "73349": "محمود هشام",
            "80650": "احمد ايمن رافت",
            "25343": "يوسف محمود يحيي",
            "23069": "يوسف حسن محمد",
            "66908": "احمد محمد عبداللطيف",
            "69756": "احمد ياسر",
            "70126": "مازن محمد",
            "73057": "عمر هاني",
            "63855": "عبدالرحمن محمود عبدالحسيب",
            "28411": "رحيق سيد",
            "23849": "فرح عماد",
            "48261": "زياد احمد يوسف",
            "75934": "ضي عبدالعليم",
            "21687": "روان ايهاب",
            "25695": "فيرا عصام عدلي",
            "39472": "محمد عبدالعظيم",
            "58210": "سلمى وائل",
            "70493": "فيروز محمد",
            "50872": "ياسين الاعسر",
            "13856": "نورهان محمد",
            "94720": "سندس محمد",
            "58391": "ملك محمد",
            "35804": "ريم خالد",
            "62047": "منه الله جمال",
            "97510": "مهند خالد عبدالفتاح",
            "41729": "مؤمن ايهاب فؤاد",
            "15290": "محمد عمرو عبدالوهاب",
            "04596": "احمد سامح سعيد",
            "81463": "احمد ناجح",

            "08724": "عبدالوهاب عبدالرحمن السيد"

        };

        function search() {
            const input = document.getElementById("searchInput").value.trim();
            const resultElement = document.getElementById("result");
            let results = [];

            // Check if input matches a code
            if (students[input]) {
                results.push(`الكود: ${input} - الاسم: ${students[input]}`);
            } else {
                // Search by full name or first name
                for (const [code, name] of Object.entries(students)) {
                    const firstName = name.split(' ')[0]; // Get the first name only
                    if (name === input || firstName === input) {
                        results.push(`الكود: ${code} - الاسم: ${name}`);
                    }
                }
            }

            if (results.length > 0) {
                resultElement.innerHTML = results.join("<br>");
            } else {
                resultElement.textContent = "لا يوجد طالب بهذا الاسم أو الكود.";
            }
        }
    </script>
