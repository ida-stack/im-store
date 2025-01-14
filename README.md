# im-store#
Creating the folder structure and necessary files for the website

import os



# Define paths

base_path = "/mnt/data/IM_Store_Website"

folders = ["css", "js", "images"]



# File contents

html_content = """

<!DOCTYPE html>

<html lang="de">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Ida-Maria's Store</title>

    <link rel="stylesheet" href="css/styles.css">

    <script src="js/script.js" defer></script>

</head>

<body>

    <header>

        <div class="logo">✨IM Store</div>

        <nav>

            <ul>

                <li><a href="#home">Startseite</a></li>

                <li><a href="#shop">Shop</a></li>

                <li><a href="#about">Über uns</a></li>

                <li><a href="#contact">Kontakt</a></li>

                <li><a href="#cart" id="cart-btn">Warenkorb (0)</a></li>

            </ul>

        </nav>

        <div class="language-switcher">

            <button onclick="changeLanguage('de')">DE</button>

            <button onclick="changeLanguage('en')">EN</button>

        </div>

    </header>



    <main>

        <section id="home" class="hero">

            <h1>Willkommen bei Ida-Maria's Store</h1>

            <p>Elegante Accessoires für deinen Look. Minimalistisch. Professionell. Jugendlich.</p>

            <a href="#shop" class="btn">Jetzt shoppen</a>

        </section>



        <section id="shop" class="shop">

            <h2>Unsere Produkte</h2>

            <div class="products">

                <div class="product">

                    <img src="images/product1.png" alt="Haarklammer 1">

                    <h3>Haarklammer Elegant</h3>

                    <p>€5,99</p>

                    <button>Kaufen</button>

                </div>

                <div class="product">

                    <img src="images/product2.png" alt="Haarklammer 2">

                    <h3>Haarklammer Klassik</h3>

                    <p>€4,99</p>

                    <button>Kaufen</button>

                </div>

            </div>

        </section>



        <section id="about">

            <h2>Über uns</h2>

            <p>Willkommen bei Ida-Maria's Store! Wir bieten dir die schönsten Accessoires, sorgfältig ausgewählt, um deinem Stil gerecht zu werden. Als Dropshipping-Shop garantieren wir dir exklusive Qualität direkt aus den besten Quellen.</p>

        </section>



        <section id="contact">

            <h2>Kontakt</h2>

            <form>

                <label for="name">Name:</label>

                <input type="text" id="name" name="name" required>

                <label for="email">E-Mail:</label>

                <input type="email" id="email" name="email" required>

                <label for="message">Nachricht:</label>

                <textarea id="message" name="message" required></textarea>

                <button type="submit">Senden</button>

            </form>

        </section>

    </main>



    <footer>

        <p>&copy; 2025 Ida-Maria Haunold | Alle Rechte vorbehalten.</p>

    </footer>

</body>

</html>

"""



css_content = """

body {

    font-family: "Times New Roman", serif;

    margin: 0;

    padding: 0;

    background-color: #f4f4f4;

    color: #333;

}



header {

    background-color: #005bac;

    color: white;

    padding: 10px 0;

    display: flex;

    justify-content: space-between;

    align-items: center;

}



header .logo {

    margin-left: 20px;

    font-size: 24px;

    font-weight: bold;

}



nav ul {

    list-style: none;

    margin: 0;

    padding: 0;

    display: flex;

}



nav ul li {

    margin-right: 20px;

}



nav ul li a {

    color: white;

    text-decoration: none;

}



.hero {

    text-align: center;

    padding: 50px 20px;

    background-color: #007bff;

    color: white;

}



.hero .btn {

    background-color: white;

    color: #005bac;

    padding: 10px 20px;

    border-radius: 5px;

    text-decoration: none;

}



.shop {

    padding: 20px;

    text-align: center;

}



.shop .products {

    display: flex;

    justify-content: center;

    gap: 20px;

    flex-wrap: wrap;

}



.product {

    background-color: white;

    border: 1px solid #ddd;

    padding: 10px;

    border-radius: 5px;

    text-align: center;

}



footer {

    background-color: #005bac;

    color: white;

    text-align: center;

    padding: 10px 0;

}



.language-switcher {

    display: flex;

    gap: 10px;

    margin-right: 20px;

}



.language-switcher button {

    background: white;

    color: #005bac;

    border: 1px solid #005bac;

    padding: 5px 10px;

    cursor: pointer;

    border-radius: 5px;

    font-size: 14px;

}

"""



js_content = """

const translations = {

    de: {

        home: "Startseite",

        shop: "Shop",

        about: "Über uns",

        contact: "Kontakt",

        cart: "Warenkorb",

    },

    en: {

        home: "Home",

        shop: "Shop",

        about: "About Us",

        contact: "Contact",

        cart: "Cart",

    }

};



function changeLanguage(lang) {

    document.querySelectorAll("nav ul li a").forEach((link, index) => {

        const key = Object.keys(translations[lang])[index];

        link.textContent = translations[lang][key];

    });

    document.getElementById("cart-btn").textContent = translations[lang].cart + " (0)";

}



let cart = [];



function addToCart(productName, price) {

    cart.push({ name: productName, price: price });

    document.getElementById("cart-btn").textContent = `Warenkorb (${cart.length})`;

    console.log(cart);

}



document.querySelectorAll(".product button").forEach((btn, index) => {

    btn.addEventListener("click", () => {

        const productName = document.querySelectorAll(".product h3")[index].textContent;

        const price = document.querySelectorAll(".product p")[index].textContent.replace("€", "");

        addToCart(productName, parseFloat(price));

    });

});

"""



# Create directories

os.makedirs(base_path, exist_ok=True)

for folder in folders:

    os.makedirs(os.path.join(base_path, folder), exist_ok=True)



# Write files

with open(os.path.join(base_path, "index.html"), "w") as f:

    f.write(html_content)

with open(os.path.join(base_path, "css", "styles.css"), "w") as f:

    f.write(css_content)

with open(os.path.join(base_path, "js", "script.js"), "w") as f:

    f.write(js_content)



base_path
