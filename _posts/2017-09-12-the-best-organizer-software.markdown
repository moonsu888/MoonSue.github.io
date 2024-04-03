---
layout: post
title: 서울 어디서 여행할까
date: 2017-09-12 00:00:00 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: software.jpg # Add image post (optional)
tags: [Productivity, Software] # add tag
---

## 서울 관광지 혼잡도

데이트 하기 딱좋은 곳은 어디일까

<!-- HTML과 JavaScript 코드 시작 -->
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

<style>
    .card-container {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
    }
    .card {
        width: 250px;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        background: #fff;
    }
    .card img {
        width: 100%;
        height: 150px;
        object-fit: cover;
    }
    .card-info {
        padding: 15px;
    }
    .card-title {
        font-size: 16px;
        font-weight: bold;
        margin: 5px 0;
    }
    .status-label {
        display: inline-block;
        padding: 5px 10px;
        border-radius: 20px;
        color: #fff;
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

<script>
    <script>
        function getData(category) {
            var xhr = new XMLHttpRequest();
            xhr.open("GET", "https://data.seoul.go.kr/SeoulRtd/getCategoryList?page=115&category=" + encodeURIComponent(category) + "&count=115&sort=true", true);
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
<!-- HTML과 JavaScript 코드 끝 -->
