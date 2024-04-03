---
layout: post
title: How I Rest From Work
date: 2024-04-03 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: i-rest.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---

## 서울 관광지 혼잡도

<!DOCTYPE html>
<html lang="kr">
<head>
    <meta charset="UTF-8">
    <title>서울 공공 데이터 UI</title>
    <style>
        .card-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px; /* 카드 사이의 간격 */
        }
        .card {
            width: 250px; /* 카드의 폭 */
            border-radius: 10px; /* 카드의 모서리 둥글기 */
            overflow: hidden; /* 이미지가 모서리 둥글기에 맞춰서 잘림 */
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2); /* 그림자 효과 */
            background: #fff; /* 카드 배경색 */
        }
        .card img {
            width: 100%; /* 이미지가 카드 폭에 맞춰짐 */
            height: 150px; /* 이미지 높이 */
            object-fit: cover; /* 이미지 비율 유지하면서 채움 */
        }
        .card-info {
            padding: 15px;
        }
        .card-title {
            font-size: 16px;
            font-weight: bold;
            margin: 5px 0; /* 제목 위아래 여백 */
        }
        .status-label {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            color: #fff; /* 글자색 */
            text-align: center;
            margin-top: 10px;
        }
        .busy { background: #DD1F3D; }
        .moderate { background: #FF8040; }
        .calm { background: #FFB100; }
        .button-container {
            margin-top: 20px;
            margin-bottom: 30px;
        }
        .button {
            padding: 10px 20px;
            border-radius: 5px;
            background-color: #007bff;
            color: #fff;
            cursor: pointer;
            margin-right: 10px;
            border: none;
            outline: none;
            transition: background-color 0.3s;
        }
        .button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <h1>서울 지역 혼잡도 정보</h1>
    <div class="button-container">
        <button class="button" onclick="getData('전체보기')">전체보기</button>
        <button class="button" onclick="getData('관광특구')">관광특구</button>
        <button class="button" onclick="getData('공원')">공원</button>
        <button class="button" onclick="getData('고궁·문화유산')">고궁·문화유산</button>
        <button class="button" onclick="getData('발달상권')">발달상권</button>
        <button class="button" onclick="getData('인구밀집지역')">인구밀집지역</button>
    </div>

    <div id="cardContainer" class="card-container">
        <!-- 카드들이 여기에 들어갑니다 -->
    </div>

    <script>
        function getData(category) {
            var xhr = new XMLHttpRequest();
            xhr.open("GET", "https://data.seoul.go.kr/SeoulRtd/getCategoryList?page=1&category=" + encodeURIComponent(category) + "&count=115&sort=true", true);
            xhr.onload = function () {
                if (xhr.status >= 200 && xhr.status < 300) {
                    var data = JSON.parse(xhr.responseText);
                    var cardContainer = document.getElementById('cardContainer');
                    cardContainer.innerHTML = ''; // 이전 카드를 모두 지웁니다.

                    data.row.forEach(function(item) {
                        var card = document.createElement('div');
                        card.className = 'card';
                        
                        var img = document.createElement('img');
                    
                        img.src = 'https://cdn.ekw.co.kr/news/photo/202008/10197_10652_4054.jpg';
                        img.alt = item.area_nm; // 접근성을 위한 alt 텍스트

                        var cardInfo = document.createElement('div');
                        cardInfo.className = 'card-info';

                        var title = document.createElement('div');
                        title.className = 'card-title';
                        title.textContent = item.area_nm;

                        var statusLabel = document.createElement('div');
                        statusLabel.className = 'status-label';
                        statusLabel.style.backgroundColor = item.congestion_color;
                        statusLabel.textContent = item.area_congest_lvl;

                        cardInfo.appendChild(title);
                        cardInfo.appendChild(statusLabel);
                        card.appendChild(img); // 이미지 추가
                        card.appendChild(cardInfo);

                        cardContainer.appendChild(card);
                    });
                } else {
                    console.error('The request failed!');
                }
            };
            xhr.send();
        }
    </script>
</body>
</html>


<!-- 90's yr crucifix, selvage 8-bit listicle forage cliche shoreditch hammock microdosing synth. Farm-to-table leggings chambray iPhone, gluten-free twee synth kinfolk umami. Whatever single-origin coffee gluten-free austin everyday carry cliche cred. Plaid ramps kitsch woke pork belly organic. Trust fund whatever coloring book kombucha brooklyn. Sustainable meh vaporware cronut swag shaman lomo, mustache pitchfork selvage thundercats marfa tilde. Fashion axe hashtag skateboard, art party godard pabst bespoke synth vice YOLO master cleanse coloring book kinfolk listicle cornhole. Try-hard mixtape umami fanny pack man bun gastropub franzen tbh. Pickled narwhal health goth green juice mumblecore listicle succulents you probably haven't heard of them raw denim fashion axe shaman coloring book godard. Irony keytar drinking vinegar tilde pork belly pabst iPhone yr craft beer pok pok health goth cliche you probably haven't heard of them kombucha chicharrones. Direct trade hella roof party chia. Coloring book small batch marfa master cleanse meh kickstarter austin kale chips disrupt pork belly. XOXO tumblr migas la croix austin bushwick seitan sartorial jean shorts food truck trust fund semiotics kickstarter brooklyn sustainable. Umami knausgaard mixtape marfa. Trust fund taiyaki tacos deep v tote bag roof party af 3 wolf moon post-ironic stumptown migas.

![I and My friends]({{site.baseurl}}/assets/img/we-in-rest.jpg)

Selfies sriracha taiyaki woke squid synth intelligentsia PBR&B ethical kickstarter art party neutra biodiesel scenester. Health goth kogi VHS fashion axe glossier disrupt, vegan quinoa. Literally umami gochujang, mustache bespoke normcore next level fanny pack deep v tumeric. Shaman vegan affogato chambray. Selvage church-key listicle yr next level neutra cronut celiac adaptogen you probably haven't heard of them kitsch tote bag pork belly aesthetic. Succulents wolf stumptown art party poutine. Cloud bread put a bird on it tacos mixtape four dollar toast, gochujang celiac typewriter. Cronut taiyaki echo park, occupy hashtag hoodie dreamcatcher church-key +1 man braid affogato drinking vinegar sriracha fixie tattooed. Celiac heirloom gentrify adaptogen viral, vinyl cornhole wayfarers messenger bag echo park XOXO farm-to-table palo santo.

>Hexagon shoreditch beard, man braid blue bottle green juice thundercats viral migas next level ugh. Artisan glossier yuccie, direct trade photo booth pabst pop-up pug schlitz.

Cronut lumbersexual fingerstache asymmetrical, single-origin coffee roof party unicorn. Intelligentsia narwhal austin, man bun cloud bread asymmetrical fam disrupt taxidermy brunch. Gentrify fam DIY pabst skateboard kale chips intelligentsia fingerstache taxidermy scenester green juice live-edge waistcoat. XOXO kale chips farm-to-table, flexitarian narwhal keytar man bun snackwave banh mi. Semiotics pickled taiyaki cliche cold-pressed. Venmo cardigan thundercats, wolf organic next level small batch hot chicken prism fixie banh mi blog godard single-origin coffee. Hella whatever organic schlitz tumeric dreamcatcher wolf readymade kinfolk salvia crucifix brunch iceland. Literally meditation four loko trust fund. Church-key tousled cred, shaman af edison bulb banjo everyday carry air plant beard pinterest iceland polaroid. Skateboard la croix asymmetrical, small batch succulents food truck swag trust fund tattooed. Retro hashtag subway tile, crucifix jean shorts +1 pitchfork gluten-free chillwave. Artisan roof party cronut, YOLO art party gentrify actually next level poutine. Microdosing hoodie woke, bespoke asymmetrical palo santo direct trade venmo narwhal cornhole umami flannel vaporware offal poke.

* Hexagon shoreditch beard
* Intelligentsia narwhal austin
* Literally meditation four
* Microdosing hoodie woke

Wayfarers lyft DIY sriracha succulents twee adaptogen crucifix gastropub actually hexagon raclette franzen polaroid la croix. Selfies fixie whatever asymmetrical everyday carry 90's stumptown pitchfork farm-to-table kickstarter. Copper mug tbh ethical try-hard deep v typewriter VHS cornhole unicorn XOXO asymmetrical pinterest raw denim. Skateboard small batch man bun polaroid neutra. Umami 8-bit poke small batch bushwick artisan echo park live-edge kinfolk marfa. Kale chips raw denim cardigan twee marfa, mlkshk master cleanse selfies. Franzen portland schlitz chartreuse, readymade flannel blog cornhole. Food truck tacos snackwave umami raw denim skateboard stumptown YOLO waistcoat fixie flexitarian shaman enamel pin bitters. Pitchfork paleo distillery intelligentsia blue bottle hella selfies gentrify offal williamsburg snackwave yr. Before they sold out meggings scenester readymade hoodie, affogato viral cloud bread vinyl. Thundercats man bun sriracha, neutra swag knausgaard jean shorts. Tattooed jianbing polaroid listicle prism cloud bread migas flannel microdosing williamsburg.

Echo park try-hard irony tbh vegan pok pok. Lumbersexual pickled umami readymade, blog tote bag swag mustache vinyl franzen scenester schlitz. Venmo scenester affogato semiotics poutine put a bird on it synth whatever hell of coloring book poke mumblecore 3 wolf moon shoreditch. Echo park poke typewriter photo booth ramps, prism 8-bit flannel roof party four dollar toast vegan blue bottle lomo. Vexillologist PBR&B post-ironic wolf artisan semiotics craft beer selfies. Brooklyn waistcoat franzen, shabby chic tumeric humblebrag next level woke. Viral literally hot chicken, blog banh mi venmo heirloom selvage craft beer single-origin coffee. Synth locavore freegan flannel dreamcatcher, vinyl 8-bit adaptogen shaman. Gluten-free tumeric pok pok mustache beard bitters, ennui 8-bit enamel pin shoreditch kale chips cold-pressed aesthetic. Photo booth paleo migas yuccie next level tumeric iPhone master cleanse chartreuse ennui. -->
