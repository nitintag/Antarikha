<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Antariksha | Space Heritage</title>
    <style>
        :root { 
            --gold: #D4AF37; 
            --dark: #050505; 
            --glass: rgba(255, 255, 255, 0.07); 
        }
        body { 
            background: var(--dark);
            background-image: 
                radial-gradient(white, rgba(255,255,255,.2) 2px, transparent 40px),
                radial-gradient(white, rgba(255,255,255,.1) 1px, transparent 30px);
            background-size: 550px 550px, 350px 350px;
            background-attachment: fixed;
            color: white; font-family: 'Segoe UI', sans-serif; margin: 0; overflow-x: hidden; 
        }
        section { display: none; padding: 20px; min-height: 100vh; animation: fadeIn 0.4s ease-out; }
        .active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        
        .nav-card { 
            background: var(--glass); border: 1px solid rgba(212, 175, 55, 0.2); 
            backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px);
            padding: 20px; margin: 15px auto; border-radius: 15px; 
            max-width: 600px; text-align: center; transition: 0.3s;
        }
        .nav-card:hover { border: 1px solid var(--gold); transform: scale(1.02); background: rgba(212, 175, 55, 0.05); }
        
        .back-btn { position: sticky; top: 15px; background: var(--gold); color: black; border: none; padding: 12px 24px; border-radius: 8px; font-weight: bold; cursor: pointer; z-index: 100; margin-bottom: 20px; box-shadow: 0 4px 15px rgba(0,0,0,0.5); }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; max-width: 1200px; margin: 0 auto; }
        img { width: 100%; height: 200px; object-fit: cover; border-radius: 12px; margin-bottom: 15px; border: 1px solid rgba(212, 175, 55, 0.4); }
        h1, h2 { color: var(--gold); text-align: center; text-transform: uppercase; letter-spacing: 3px; }
    </style>
</head>
<body>

    <section id="main-menu" class="active">
        <h1 style="font-size: 2.5em; margin-top: 50px;">ANTARIKSHA</h1>
        
        <div style="text-align: center; padding: 20px; border-bottom: 1px solid rgba(212, 175, 55, 0.3); margin: 0 auto 30px; max-width: 700px;">
            <p style="font-style: italic; color: #ccc; margin-bottom: 5px;">Explore the intersection of Ancient Indian Wisdom and Modern Space Science.</p>
            <p style="color: var(--gold); font-weight: bold; font-size: 1.1em;">प्राचीन भारतीय खगोलशास्त्र आणि आधुनिक अंतराळ विज्ञान यांचा संगम।</p>
        </div>

        <div class="nav-card" onclick="showSection('solar-system')"><h3>Planetary Realms (सूर्यमाला)</h3></div>
        <div class="nav-card" onclick="showSection('rashis')"><h3>Zodiac Signs (बारा राशी)</h3></div>
        <div class="nav-card" onclick="showSection('heritage')"><h3>Space Heritage (भारतीय वारसा)</h3></div>
        <div class="nav-card" onclick="showSection('sages')"><h3>Sages & Scientists (ऋषी आणि शास्त्रज्ञ)</h3></div>
    </section>

    <section id="solar-system"><button class="back-btn" onclick="showSection('main-menu')">← BACK</button><h2>The Planets</h2><div class="grid" id="planet-list"></div></section>
    <section id="rashis"><button class="back-btn" onclick="showSection('main-menu')">← BACK</button><h2>12 Zodiac Signs</h2><div class="grid" id="rashi-list"></div></section>
    <section id="heritage"><button class="back-btn" onclick="showSection('main-menu')">← BACK</button><h2>Indian Heritage</h2><div class="grid" id="heritage-list"></div></section>
    <section id="sages"><button class="back-btn" onclick="showSection('main-menu')">← BACK</button><h2>Sages & Scientists</h2><div class="grid" id="sage-list"></div></section>

    <script>
        function showSection(id) {
            document.querySelectorAll('section').forEach(s => s.classList.remove('active'));
            document.getElementById(id).classList.add('active');
            window.scrollTo(0,0);
        }

        const planets = [
            { n: "Earth (पृथ्वी)", d: "Our home, the blue planet. / आपला निळा ग्रह, जिथे जीवन बहरले आहे।", img: "https://images-assets.nasa.gov/image/AS17-148-22727/AS17-148-22727~thumb.jpg" },
            { n: "Mars (मंगळ)", d: "The Red Planet. / मंगळ हा सूर्यमालेतील चौथा ग्रह आहे।", img: "https://images-assets.nasa.gov/image/PIA04352/PIA04352~thumb.jpg" },
            { n: "Jupiter (गुरु)", d: "The king of planets. / सूर्यमालेतील सर्वात मोठा ग्रह।", img: "https://images-assets.nasa.gov/image/PIA04866/PIA04866~thumb.jpg" }
        ];

        const rashis = [
            { n: "Mesha (मेष)", d: "Aries: Vernal Equinox point. / वसंत संपात बिंदू." },
            { n: "Vrishabha (वृषभ)", d: "Taurus: Home to Rohini star. / रोहिणी नक्षत्राचे स्थान." },
            { n: "Mithuna (मिथुन)", d: "Gemini: The celestial twins. / पुनर्वसू नक्षत्राचा भाग." },
            { n: "Karka (कर्क)", d: "Cancer: Summer Solstice sign. / उन्हाळी संपात बिंदू." }
        ];

        const heritage = [
            { n: "GMRT Pune", d: "Giant Metrewave Radio Telescope. / जगातील सर्वात मोठी रेडिओ टेलिस्कोप यंत्रणा।", img: "https://images.unsplash.com/photo-1446776811953-b23d57bd21aa?auto=format&fit=crop&w=600" },
            { n: "Nehru Planetarium", d: "Bridge to space. / खगोलशास्त्रीय वारसा आणि आधुनिक संशोधन केंद्र।", img: "https://images.unsplash.com/photo-1614732414444-096e5f1122d5?auto=format&fit=crop&w=600" }
        ];

        const sages = [
            { n: "Aryabhata (आर्यभट)", d: "Invented Zero and calculated Pi. / शून्य आणि 'पाय' (π) चे मूल्य शोधले।", img: "https://images.unsplash.com/photo-1614728894747-a83421e2b9c9?auto=format&fit=crop&w=600" },
            { n: "Bhaskara II", d: "Master of Gravity. / गुरुत्वाकर्षण आणि बीजगणिताचे महान अभ्यासक।", img: "https://images.unsplash.com/photo-1462331940025-496dfbfc7564?auto=format&fit=crop&w=600" }
        ];

        function loadContent() {
            const render = (data, id) => {
                const container = document.getElementById(id);
                data.forEach(item => {
                    container.innerHTML += `
                        <div class="nav-card" style="max-width: none; margin: 0;">
                            ${item.img ? `<img src="${item.img}" onerror="this.style.display='none'">` : ''}
                            <h3 style="color:var(--gold); margin: 10px 0;">${item.n}</h3>
                            <p style="font-size: 0.9em; line-height: 1.4;">${item.d}</p>
                        </div>`;
                });
            };
            render(planets, 'planet-list');
            render(rashis, 'rashi-list');
            render(heritage, 'heritage-list');
            render(sages, 'sage-list');
        }
        window.onload = loadContent;
    </script>
</body>
</html>
