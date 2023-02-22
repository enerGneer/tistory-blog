# tistory-blog

main 커스텀 스킨만
original 오리지널 스킨 변동 체크용



현재 누르고 있는 카테고리와 일치하는 카테고리는 지금 스크립트로도 펼쳐지는데

    const cateLists = document.querySelectorAll(".sub_category_list");
    const currentPageUrl = window.location.href;

    window.addEventListener('load', function() {
      function cateHandler(category) {
        const currentCateUrl = category.parentNode.childNodes[1].getAttribute("href");
        const descriptionUrl = document.querySelector(".description a").getAttribute("href");
        if(currentPageUrl.includes(currentCateUrl)){
          category.parentNode.firstChild.click();
        }
      }
      cateLists.forEach(cateHandler);
    });
이게 단순 url 비교라 현재 글에 속한 건 안펴지는 문제가 있음..

그래서 카테고리명과 일치하는 카테고리를 펴주기. 로 지정하면 어떨지 고민된다.

일단 post-head-category라는 아이디로 글 헤더에 속하는 카테고리만 따로 지정하는 id 만들어줌

이거의 textContent 혹은 innerText와 실제 카테고리 내부 텍스트를 비교하는거지..

이게 약간 난관 같긴 했음 ㅡㅡ 왜냐면 카테고리명이 완벽히 일치하는 건 아님 그래서 아이디 준 post-head-category가 저걸 포함하는.. 을 해야하는데 그전에 문자 슬라이싱을 해야할거같음?!?! 둘다 공백빼버리고 include 비교하면 될거같긴함,,, 지금 여기 (좌우 공백 제거하는 함수가 있대!!!)

만약 이 방법을 쓰면 그냥 이걸로 일원하도 될 거 같음 다른 영역에도 아이디를 주면 되니까..? 근데 걍 href 비교가 젤 빠른가 싶기두 한
