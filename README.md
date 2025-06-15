# 한원석 - 개발자 포트폴리오 웹사이트

컴퓨터공학을 전공하며 정보 교사를 꿈꾸는 대학생의 개인 포트폴리오 웹사이트입니다. 다양한 프로그래밍 프로젝트와 기술 스킬, 그리고 미래 비전을 소개합니다.

## 🌐 웹사이트 소개

이 웹사이트는 순수 HTML, CSS, JavaScript로 제작된 반응형 포트폴리오입니다. 현대적인 디자인과 부드러운 애니메이션을 통해 사용자 경험을 향상시켰으며, 모바일과 데스크톱 모든 환경에서 최적화되어 작동합니다.

**GitHub 주소**: [https://github.com/nunuragu](https://github.com/nunuragu)

## ✨ 주요 기능

### 1. 반응형 네비게이션 바
**설명**: 스크롤에 따라 배경이 변경되고, 부드러운 스크롤 효과를 제공하는 고정 네비게이션

**코드 위치**: 
- HTML: `index.html` (10-19줄)
- CSS: `style.css` (13-51줄)
- JavaScript: `script.js` (39-48줄)

**코드 설명**:
```html
<!-- 네비게이션 구조 -->
<nav>
    <div class="nav-container">
        <div class="logo">포트폴리오</div>
        <ul class="nav-links">
            <li><a href="#home">홈</a></li>
            <!-- ... 기타 메뉴 항목들 -->
        </ul>
    </div>
</nav>
```
- CSS로 고정 위치(`position: fixed`)와 블러 효과(`backdrop-filter: blur`) 적용
- JavaScript로 스크롤 시 배경색과 그림자 동적 변경

### 2. 히어로 섹션 애니메이션
**설명**: 그라데이션 배경과 페이드인 애니메이션이 적용된 메인 화면

**코드 위치**:
- HTML: `index.html` (21-28줄)
- CSS: `style.css` (53-120줄)

**코드 설명**:
```css
.hero {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    /* 그라데이션 배경 */
}

@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
}
```
- CSS 그라데이션으로 시각적 임팩트 제공
- `fadeInUp` 애니메이션을 통한 텍스트 등장 효과

### 3. 부드러운 스크롤 효과
**설명**: 네비게이션 메뉴 클릭 시 해당 섹션으로 부드럽게 이동

**코드 위치**: `script.js` (1-11줄)

**코드 설명**:
```javascript
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        target.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
        });
    });
});
```
- 앵커 링크 클릭 시 기본 동작 방지
- `scrollIntoView()`의 `smooth` 옵션으로 부드러운 스크롤 구현

### 4. 인터섹션 옵저버를 활용한 스크롤 애니메이션
**설명**: 스크롤 시 요소가 화면에 나타날 때 페이드인 효과 적용

**코드 위치**: 
- JavaScript: `script.js` (13-28줄)
- CSS: `style.css` (386-399줄)

**코드 설명**:
```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('visible');
        }
    });
}, observerOptions);

document.querySelectorAll('.fade-in').forEach(el => {
    observer.observe(el);
});
```
- IntersectionObserver API로 요소의 가시성 감지
- 화면에 나타나는 순간 `visible` 클래스 추가로 애니메이션 트리거

### 5. 그리드 레이아웃 시스템
**설명**: CSS Grid를 활용한 반응형 카드 레이아웃

**코드 위치**: 
- 스킬 섹션: `style.css` (172-175줄)
- 프로젝트 섹션: `style.css` (210-215줄)

**코드 설명**:
```css
.skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
}
```
- `auto-fit`과 `minmax()`로 반응형 그리드 구현
- 화면 크기에 따라 자동으로 열 개수 조정

### 6. 호버 효과 및 트랜지션
**설명**: 카드와 버튼에 마우스 호버 시 부드러운 변화 효과

**코드 위치**: `style.css` (183-187줄, 224-226줄)

**코드 설명**:
```css
.skill-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
}
```
- `transform`으로 카드가 위로 이동하는 효과
- `box-shadow`로 그림자 깊이 증가

### 7. 미디어 쿼리를 통한 반응형 디자인
**설명**: 모바일 기기에서의 최적화된 레이아웃

**코드 위치**: `style.css` (358-383줄)

**코드 설명**:
```css
@media (max-width: 768px) {
    .nav-links { display: none; }
    .hero h1 { font-size: 2.5rem; }
    .about-content { grid-template-columns: 1fr; }
}
```
- 768px 이하에서 네비게이션 메뉴 숨김
- 텍스트 크기와 레이아웃 구조 조정

## 🛠 기술 스택

- **HTML5**: 시맨틱 마크업
- **CSS3**: Flexbox, Grid, 애니메이션, 미디어 쿼리
- **JavaScript (ES6+)**: DOM 조작, IntersectionObserver API

## 📁 파일 구조

```
├── index.html          # 메인 HTML 파일
├── css/
│   └── style.css      # 스타일시트
├── js/
│   └── script.js      # JavaScript 파일
└── pic/               # 이미지 파일들
    ├── profile.jpg
    ├── baseballnumber.png
    ├── genesis.png
    ├── catsoup.png
    ├── chap.png
    └── bass.jpg


**GitHub**: [github.com/nunuragu](https://github.com/nunuragu)

---

*이 포트폴리오는 정보 교사를 꿈꾸는 컴퓨터공학과 학생 한원석의 기술적 역량과 교육에 대한 열정을 보여줍니다.*
