<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8" />
    <title>Продажа виртуальных ресурсов</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: #ffffff; /* Белый фон */
            color: #000; /* Черный текст */
            opacity: 0; /* Начинаем с невидимости */
            animation: fadeInBody 1s forwards; /* Анимация появления тела страницы */
        }

        @keyframes fadeInBody {
            to {
                opacity: 1;
            }
        }

        header {
            background-color: #000; /* Черный */
            color: #fff; /* Белый текст */
            text-align: center;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            opacity: 0;
            transform: translateY(-20px);
            animation: fadeInUp 1s forwards;
            animation-delay: 0.2s;
            flex-wrap: wrap;
        }

        /* Размер логотипа 100x100, перемещен за текст */
        .logo-img {
            width: 100px;
            height: 100px;
            object-fit: contain;
            order: 2; /* После текста */
        }

        /* Заголовок с очень медленным плавным переливом зеленый-золотой */
        .site-title {
            display: flex;
            align-items: center;
            font-size: 2em;
            font-weight: bold;
            background: linear-gradient(
                270deg,
                #008000, /* Зеленый */
                #ffd700, /* Золотой */
                #008000  /* Зеленый (повтор для плавности) */
            );
            background-size: 1400% 1400%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: gradientShift 30s linear infinite; /* Медленная анимация */
            padding: 10px 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.3);
            margin: 10px 0;
            order: 1; /* Перед изображением */
        }

        @keyframes gradientShift {
            0% {
                background-position: 0% 50%;
            }
            100% {
                background-position: 1400% 50%;
            }
        }

        nav {
            background-color: #222; /* Темно-серый, почти черный */
            display: flex;
            gap: 15px;
            padding: 10px 20px;
            justify-content: center;
            flex-wrap: wrap;
            opacity: 0;
            transform: translateY(-20px);
            animation: fadeInUp 1s forwards;
            animation-delay: 0.4s;
        }

        nav a {
            text-decoration: none;
            color: #fff; /* Белый */
            font-weight: bold;
            padding: 8px 12px;
            border-radius: 5px;
            transition: background 0.3s, color 0.3s;
        }

        nav a:hover {
            background-color: #fff; /* Белый фон при наведении */
            color: #000; /* Черный текст */
        }

        main {
            padding: 20px;
            max-width: 1200px;
            margin: auto;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s forwards;
            animation-delay: 0.6s;
        }

        section {
            margin-top: 30px;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s forwards;
            animation-delay: 0.8s;
        }

        h2 {
            margin-bottom: 15px;
            color: #000;
        }

        .product {
            border: 1px solid #000; /* Черная рамка */
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            background: #fff; /* Белый фон */
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s forwards;
        }

        .product:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
        }

        #cart {
            border: 1px solid #000; /* Черная рамка */
            border-radius: 12px;
            padding: 15px;
            min-height: 50px;
            background: #fff;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: box-shadow 0.3s, transform 0.3s;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s forwards;
            animation-delay: 1.2s;
        }

        #cart:hover {
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            transform: translateY(-2px);
        }

        /* Анимация для отзывов */
        #review-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            padding: 10px;
        }

        .review {
            background: #222; /* Темно-серый фон */
            color: #fff; /* Белый текст */
            border-radius: 12px;
            padding: 15px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.5s forwards;
            animation-delay: 1.4s;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .review:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.4);
        }

        .review strong {
            display: block;
            margin-bottom: 8px;
            font-size: 1.1em;
            color: #fff;
        }

        /* Форма отзывов */
        #review-form {
            display: flex;
            flex-direction: column;
            max-width: 400px;
            margin-top: 20px;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeIn 1s forwards;
            animation-delay: 1.6s;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        #review-form input,
        #review-form textarea {
            padding: 10px;
            border-radius: 8px;
            border: 1px solid #000; /* Черная граница */
            font-size: 1em;
            margin-bottom: 10px;
        }

        /* Обновленные стили кнопок */
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 8px;
            font-size: 1em;
            cursor: pointer;
            margin-top: 10px;
            transition: all 0.3s ease;
            font-family: Arial, sans-serif;
        }

        /* Кнопка "Купить" зеленая как деньги */
        .btn-buy {
            background: linear-gradient(135deg, #28a745, #218838);
            color: #fff;
            font-weight: bold;
        }
        .btn-buy:hover {
            background: linear-gradient(135deg, #34d399, #22c55e);
            transform: scale(1.02);
        }

        /* Кнопка "Очистить корзину" - красная */
        .btn-secondary {
            background: linear-gradient(135deg, #dc3545, #a71d2a);
            color: #fff;
        }
        .btn-secondary:hover {
            background: linear-gradient(135deg, #e3342f, #cc1f2a);
            transform: scale(1.02);
        }

        /* Кнопка "Перейти к оплате" — зеленая как кнопка "Купить" */
        .btn-pay {
            background: linear-gradient(135deg, #28a745, #218838);
            color: #fff;
            font-weight: bold;
        }
        .btn-pay:hover {
            background: linear-gradient(135deg, #34d399, #22c55e);
            transform: scale(1.02);
        }

        /* Для кнопки отправки отзыва — использовать общий класс */
        .btn-submit {
            background: linear-gradient(135deg, #000, #222);
            color: #fff;
            font-weight: bold;
        }
        .btn-submit:hover {
            background: linear-gradient(135deg, #222, #000);
            transform: scale(1.02);
        }
    </style>
</head>
<body>

<header>
    <!-- Текст "FlopShop" -->
    <div class="site-title">FlopShop</div>
    <!-- Логотип 100x100, за текстом -->
    <img src="https://media.discordapp.net/attachments/1178438610500980747/1418274429858877511/flopshop.png?ex=68cd867e&is=68cc34fe&hm=fc95eb8ef5c54436a68be806fb8dca9612ba0ec5a604c3f7ff2a5705f3a87354&=&format=webp&quality=lossless&width=1604&height=902" alt="Логотип" class="logo-img"/>
</header>

<nav>
    <a href="#resources">Ресурсы</a>
    <a href="#cart-section">Корзина</a>
    <a href="#contacts">Наши контакты</a>
    <a href="#reviews">Отзывы</a>
</nav>

<main>
    <!-- Раздел ресурсов -->
    <section id="resources">
        <h2>Доступные ресурсы</h2>
        <div class="product">
            <h3>✏️Pakrahmatmamat✏️</h3>
            <p>Описание: 1.5m/s.</p>
            <p>Цена: 250 рублей</p>
            <button class="btn btn-buy" onclick="addToCart('✏️Pakrahmatmamat✏️', 250)">Добавить в корзину</button>
        </div>
        <div class="product">
            <h3>🎩Los Matteos🎩</h3>
            <p>Описание: +1 mutations, 1.3m/s.</p>
            <p>Цена: 500 рублей</p>
            <button class="btn btn-buy" onclick="addToCart('🎩Los Matteos🎩', 500)">Добавить в корзину</button>
        </div>
        <div class="product">
            <h3>🐋Orcalero Orcala🐋</h3>
            <p>Описание: +1 mutations, 1.3m/s.</p>
            <p>Цена: 500 рублей</p>
            <button class="btn btn-buy" onclick="addToCart('🐋Orcalero Orcala🐋', 500)">Добавить в корзину</button>
        </div>
    </section>

    <!-- Раздел корзины -->
    <section id="cart-section">
        <h2>Корзина</h2>
        <div id="cart"></div>
        <p><strong>Общая сумма: </strong><span id="total">0</span> рублей</p>
        <button class="btn btn-secondary" onclick="clearCart()">Очистить корзину</button>
        <button class="btn btn-pay" onclick="goToPayment()">Перейти к оплате</button>
    </section>

    <!-- Контакты -->
    <section id="contacts">
        <h2>Наши контакты</h2>
        <p>Discord: </p>
        <p>FunPay: </p>
    </section>

    <!-- Отзывы -->
    <section id="reviews" class="reviews">
        <h2>Отзывы</h2>
        <div id="review-list"></div>
        <h3>Оставить отзыв</h3>
        <form id="review-form" onsubmit="submitReview(event)">
            <input type="text" id="name" placeholder="Ваше имя" required />
            <textarea id="review-text" placeholder="Ваш отзыв" required></textarea>
            <button type="submit" class="btn-submit">Отправить отзыв</button>
        </form>
    </section>
</main>

<footer>
    <p>&copy; FlopShop - Доверься нам</p>
</footer>

<script>
    const cart = [];
    const reviewList = [];

    function addToCart(name, price) {
        cart.push({name, price});
        updateCart();
    }

    function updateCart() {
        const cartDiv = document.getElementById('cart');
        cartDiv.innerHTML = '';
        let total = 0;
        cart.forEach((item, index) => {
            total += item.price;
            const container = document.createElement('div');
            container.style.display='flex'; 
            container.style.justifyContent='space-between'; 
            container.style.alignItems='center'; 
            container.style.marginBottom='8px';

            const textSpan = document.createElement('span');
            textSpan.textContent = `${item.name} - ${item.price} рублей`;

            const removeBtn = document.createElement('button');
            removeBtn.textContent='Удалить';
            removeBtn.style.background='#000';
            removeBtn.style.color='white';
            removeBtn.style.border='none';
            removeBtn.style.borderRadius='4px';
            removeBtn.style.padding='5px 10px';
            removeBtn.style.cursor='pointer';
            removeBtn.onclick = () => {
                cart.splice(index,1);
                updateCart();
            };

            container.appendChild(textSpan);
            container.appendChild(removeBtn);
            cartDiv.appendChild(container);
        });
        document.getElementById('total').textContent = total;
    }

    function clearCart() {
        cart.length=0;
        updateCart();
    }

    function submitReview(event) {
        event.preventDefault();
        const name = document.getElementById('name').value;
        const reviewText = document.getElementById('review-text').value;
        const review = {name, reviewText};
        reviewList.push(review);
        saveReviews();
        displayReviews();
        document.getElementById('review-form').reset();
    }

    function displayReviews() {
        const reviewContainer = document.getElementById('review-list');
        reviewContainer.innerHTML = '';
        reviewList.forEach(r => {
            const div = document.createElement('div');
            div.className='review';
            div.innerHTML = `<strong>${r.name}</strong><p>${r.reviewText}</p>`;
            reviewContainer.appendChild(div);
        });
    }

    function saveReviews() {
        localStorage.setItem('reviews', JSON.stringify(reviewList));
    }

    function goToPayment() {
        const total = document.getElementById('total').textContent;
        if (parseInt(total) > 0) {
            const paymentUrl = `https://example.com/payment?amount=${total}`;
            window.location.href = paymentUrl;
        } else {
            alert('Корзина пуста');
        }
    }

    // Инициализация отзывов
    window.onload=() => {
        const savedReviews = localStorage.getItem('reviews');
        if (savedReviews) {
            reviewList.push(...JSON.parse(savedReviews));
        }
        displayReviews();
    };
</script>

</body>
</html>
