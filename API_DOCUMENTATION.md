# Tài Liệu API - Dự Án Website

## Mục Lục
1. [Tổng Quan](#tổng-quan)
2. [Cấu Trúc HTML](#cấu-trúc-html)
3. [Components](#components)
4. [CSS Classes](#css-classes)
5. [Ví Dụ Sử Dụng](#ví-dụ-sử-dụng)
6. [Hướng Dẫn Tùy Chỉnh](#hướng-dẫn-tùy-chỉnh)

---

## Tổng Quan

Dự án website này là một trang HTML tĩnh với bố cục 3 cột, bao gồm header, main content, sidebar trái/phải và footer.

**File chính:**
- `b1.html` - Trang HTML chính
- `b1.css` - File stylesheet (được tham chiếu nhưng chưa có trong dự án)

---

## Cấu Trúc HTML

### Document Structure

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Metadata và CSS -->
  </head>
  <body>
    <!-- Content -->
  </body>
</html>
```

**Đặc điểm:**
- Sử dụng HTML5 DOCTYPE
- Encoding: UTF-8
- Responsive layout sử dụng div-based structure

---

## Components

### 1. Header Component

**Class:** `.header`

**Mô tả:** Component đầu trang chứa tiêu đề chính của website.

**Cấu trúc:**
```html
<div class="header">
    <div class="index">
        <h1>Header...</h1>
    </div>
</div>
```

**Thuộc tính:**
- **Container class:** `header` - Wrapper chính cho header
- **Inner class:** `index` - Container bên trong cho nội dung
- **Heading:** `h1` - Tiêu đề chính

**Ví dụ sử dụng:**
```html
<div class="header">
    <div class="index">
        <h1>Tên Website Của Bạn</h1>
    </div>
</div>
```

---

### 2. Main Content Component

**Class:** `.main`, `.maincontent`

**Mô tả:** Component nội dung chính của trang, chứa phần lớn thông tin.

**Cấu trúc:**
```html
<div class="main">
    <div class="maincontent">
        <div class="index" id="leftText">
            <h1>Heading...</h1>
            <p>Nội dung...</p>
            <h3>Subheading...</h3>
            <p>Nội dung phụ...</p>
        </div>
    </div>
</div>
```

**Thuộc tính:**
- **Container class:** `main` - Wrapper tổng thể
- **Content class:** `maincontent` - Container nội dung chính
- **ID:** `leftText` - Identifier cho styling đặc biệt
- **Headings:** Hỗ trợ `h1` và `h3` tags
- **Paragraphs:** Sử dụng `p` tags cho nội dung văn bản

**API Methods:**
```javascript
// Thêm nội dung động vào main content
function addMainContent(heading, content) {
    const mainContent = document.querySelector('.maincontent .index');
    const newHeading = document.createElement('h3');
    newHeading.textContent = heading;
    const newParagraph = document.createElement('p');
    newParagraph.textContent = content;
    mainContent.appendChild(newHeading);
    mainContent.appendChild(newParagraph);
}
```

**Ví dụ sử dụng:**
```html
<div class="main">
    <div class="maincontent">
        <div class="index" id="leftText">
            <h1>Chào Mừng Đến Website</h1>
            <p>Đây là đoạn giới thiệu về website...</p>
            <h3>Tính Năng Nổi Bật</h3>
            <p>Mô tả các tính năng...</p>
        </div>
    </div>
</div>
```

---

### 3. Left Sidebar Component

**Class:** `.left`

**Mô tả:** Sidebar bên trái chứa thông tin phụ hoặc nội dung bổ sung.

**Cấu trúc:**
```html
<div class="left">
    <div class="index" id="leftText">
        <h2>Heading</h2>
        <p>Nội dung sidebar...</p>
    </div>
</div>
```

**Thuộc tính:**
- **Container class:** `left` - Wrapper cho sidebar trái
- **Inner class:** `index` - Container nội dung
- **ID:** `leftText` - Identifier cho styling
- **Heading:** `h2` - Tiêu đề sidebar

**Ví dụ sử dụng:**
```html
<div class="left">
    <div class="index" id="leftText">
        <h2>Thông Tin</h2>
        <p>Thông tin bổ sung về sản phẩm hoặc dịch vụ...</p>
    </div>
</div>
```

**JavaScript Helper:**
```javascript
// Cập nhật nội dung left sidebar
function updateLeftSidebar(title, content) {
    const leftSidebar = document.querySelector('.left .index');
    leftSidebar.querySelector('h2').textContent = title;
    leftSidebar.querySelector('p').textContent = content;
}
```

---

### 4. Right Sidebar Component

**Class:** `.right`

**Mô tả:** Sidebar bên phải chứa navigation links và menu phụ.

**Cấu trúc:**
```html
<div class="right">
    <div class="index" id="leftText">
        <h2>Right Heading</h2>
        <ul>
            <li><a href="#">Link 1</a></li>
            <li><a href="#">Link 2</a></li>
            <li><a href="#">Link 3</a></li>
        </ul>
    </div>
</div>
```

**Thuộc tính:**
- **Container class:** `right` - Wrapper cho sidebar phải
- **Inner class:** `index` - Container nội dung
- **Navigation:** Sử dụng `ul` và `li` tags
- **Links:** `a` tags với href attributes

**API Functions:**
```javascript
// Thêm link mới vào right sidebar
function addRightSidebarLink(sectionIndex, linkText, linkUrl) {
    const rightSidebar = document.querySelector('.right .index');
    const ulElements = rightSidebar.querySelectorAll('ul');
    
    if (ulElements[sectionIndex]) {
        const newLi = document.createElement('li');
        const newLink = document.createElement('a');
        newLink.href = linkUrl;
        newLink.textContent = linkText;
        newLi.appendChild(newLink);
        ulElements[sectionIndex].appendChild(newLi);
    }
}

// Tạo section navigation mới
function createNavigationSection(title, links) {
    const rightSidebar = document.querySelector('.right .index');
    
    const heading = document.createElement('h3');
    heading.textContent = title;
    
    const ul = document.createElement('ul');
    links.forEach(link => {
        const li = document.createElement('li');
        const a = document.createElement('a');
        a.href = link.url;
        a.textContent = link.text;
        li.appendChild(a);
        ul.appendChild(li);
    });
    
    rightSidebar.appendChild(heading);
    rightSidebar.appendChild(ul);
}
```

**Ví dụ sử dụng:**
```html
<div class="right">
    <div class="index" id="leftText">
        <h2>Menu Điều Hướng</h2>
        <ul>
            <li><a href="#trang-chu">Trang Chủ</a></li>
            <li><a href="#gioi-thieu">Giới Thiệu</a></li>
            <li><a href="#san-pham">Sản Phẩm</a></li>
            <li><a href="#lien-he">Liên Hệ</a></li>
        </ul>
        <h3>Liên Kết Hữu Ích</h3>
        <ul>
            <li><a href="#blog">Blog</a></li>
            <li><a href="#ho-tro">Hỗ Trợ</a></li>
        </ul>
    </div>
</div>
```

---

### 5. Footer Component

**Tag:** `<footer>`

**Class:** `.footer`

**Mô tả:** Component cuối trang chứa thông tin bản quyền và links bổ sung.

**Cấu trúc:**
```html
<footer>
    <div class="footer">
        <h2>Footer...</h2>
    </div>
</footer>
```

**Thuộc tính:**
- **Semantic tag:** `footer` - HTML5 semantic element
- **Container class:** `footer` - Wrapper cho nội dung footer
- **Heading:** `h2` - Tiêu đề footer

**Ví dụ sử dụng:**
```html
<footer>
    <div class="footer">
        <h2>© 2024 Tên Công Ty. All Rights Reserved.</h2>
        <p>Địa chỉ: 123 Đường ABC, Quận XYZ, TP.HCM</p>
        <p>Email: contact@example.com | Phone: (84) 123-456-789</p>
    </div>
</footer>
```

**JavaScript Helper:**
```javascript
// Cập nhật footer content
function updateFooter(copyright, address, contact) {
    const footer = document.querySelector('.footer');
    footer.innerHTML = `
        <h2>${copyright}</h2>
        <p>${address}</p>
        <p>${contact}</p>
    `;
}
```

---

### 6. Clear Component

**Class:** `.clear`

**Mô tả:** Utility component để clear floats trong layout.

**Cấu trúc:**
```html
<div class="clear"></div>
```

**Mục đích:**
- Clear CSS floats
- Đảm bảo layout không bị sập
- Phân tách sections

**CSS Suggestion:**
```css
.clear {
    clear: both;
    height: 0;
    overflow: hidden;
}
```

---

## CSS Classes

### Public CSS Classes API

#### `.header`
**Mô tả:** Class cho header container
**Sử dụng:** Wrapper element cho phần đầu trang
**Liên kết với:** `.index`

#### `.index`
**Mô tả:** Universal inner container class
**Sử dụng:** Được sử dụng trong tất cả các sections để tạo consistent padding/margin
**Áp dụng cho:** Header, Main content, Left sidebar, Right sidebar

#### `.main`
**Mô tả:** Container tổng thể cho main content area
**Sử dụng:** Wrapper cho toàn bộ phần nội dung chính bao gồm cả sidebars

#### `.maincontent`
**Mô tả:** Container cho nội dung chính trung tâm
**Sử dụng:** Chứa nội dung văn bản chính của trang
**Layout:** Thường chiếm phần lớn width, positioned giữa hai sidebars

#### `.left`
**Mô tả:** Container cho left sidebar
**Sử dụng:** Sidebar trái chứa nội dung phụ
**Layout:** Float left hoặc positioned bên trái

#### `.right`
**Mô tả:** Container cho right sidebar
**Sử dụng:** Sidebar phải chứa navigation và links
**Layout:** Float right hoặc positioned bên phải

#### `.footer`
**Mô tả:** Class cho footer content
**Sử dụng:** Styling cho footer area

#### `.clear`
**Mô tả:** Utility class để clear floats
**Sử dụng:** Placed sau floating elements để maintain layout

#### `#leftText`
**Mô tả:** ID selector cho text content
**Sử dụng:** Applied to multiple sections (nên đổi thành class để tránh duplicate ID)
**Ghi chú:** **CẢNH BÁO** - ID này được sử dụng nhiều lần, vi phạm HTML standards. Nên đổi thành class.

---

## Ví Dụ Sử Dụng

### Ví dụ 1: Tạo Trang Đơn Giản

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>My Website</title>
    <link rel="stylesheet" type="text/css" href="b1.css">
</head>
<body>
    <div class="header">
        <div class="index">
            <h1>Welcome to My Website</h1>
        </div>
    </div>
    
    <div class="main">
        <div class="maincontent">
            <div class="index">
                <h1>Main Article</h1>
                <p>Your main content goes here...</p>
            </div>
        </div>
        
        <div class="left">
            <div class="index">
                <h2>About</h2>
                <p>Information about your site...</p>
            </div>
        </div>
        
        <div class="right">
            <div class="index">
                <h2>Navigation</h2>
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </div>
        </div>
    </div>
    
    <div class="clear"></div>
    
    <footer>
        <div class="footer">
            <h2>© 2024 My Website</h2>
        </div>
    </footer>
</body>
</html>
```

### Ví dụ 2: Dynamic Content với JavaScript

```javascript
// Initialize page with dynamic content
document.addEventListener('DOMContentLoaded', function() {
    // Update header
    document.querySelector('.header h1').textContent = 'Dynamic Website';
    
    // Add main content
    addMainContent('Features', 'This website has many great features...');
    
    // Update left sidebar
    updateLeftSidebar('Quick Info', 'Important information here...');
    
    // Add navigation links
    const links = [
        { text: 'Home', url: '#home' },
        { text: 'Services', url: '#services' },
        { text: 'Portfolio', url: '#portfolio' }
    ];
    createNavigationSection('Main Menu', links);
    
    // Update footer
    updateFooter(
        '© 2024 My Company',
        'Address: 123 Main St, City',
        'Email: info@example.com'
    );
});

// Helper functions
function addMainContent(heading, content) {
    const mainContent = document.querySelector('.maincontent .index');
    const h3 = document.createElement('h3');
    h3.textContent = heading;
    const p = document.createElement('p');
    p.textContent = content;
    mainContent.appendChild(h3);
    mainContent.appendChild(p);
}

function updateLeftSidebar(title, content) {
    const leftSidebar = document.querySelector('.left .index');
    leftSidebar.querySelector('h2').textContent = title;
    const p = leftSidebar.querySelector('p') || document.createElement('p');
    p.textContent = content;
    if (!leftSidebar.querySelector('p')) {
        leftSidebar.appendChild(p);
    }
}

function createNavigationSection(title, links) {
    const rightSidebar = document.querySelector('.right .index');
    const h3 = document.createElement('h3');
    h3.textContent = title;
    const ul = document.createElement('ul');
    
    links.forEach(link => {
        const li = document.createElement('li');
        const a = document.createElement('a');
        a.href = link.url;
        a.textContent = link.text;
        li.appendChild(a);
        ul.appendChild(li);
    });
    
    rightSidebar.appendChild(h3);
    rightSidebar.appendChild(ul);
}

function updateFooter(copyright, address, contact) {
    const footer = document.querySelector('.footer');
    footer.innerHTML = `
        <h2>${copyright}</h2>
        <p>${address}</p>
        <p>${contact}</p>
    `;
}
```

### Ví dụ 3: Responsive Adaptation

```javascript
// Make the layout responsive
function makeResponsive() {
    const width = window.innerWidth;
    const main = document.querySelector('.main');
    const left = document.querySelector('.left');
    const right = document.querySelector('.right');
    const mainContent = document.querySelector('.maincontent');
    
    if (width < 768) {
        // Mobile layout - stack vertically
        main.style.flexDirection = 'column';
        left.style.width = '100%';
        right.style.width = '100%';
        mainContent.style.width = '100%';
    } else if (width < 1024) {
        // Tablet layout
        mainContent.style.width = '60%';
        left.style.width = '40%';
        right.style.width = '100%';
    } else {
        // Desktop layout
        mainContent.style.width = '50%';
        left.style.width = '25%';
        right.style.width = '25%';
    }
}

window.addEventListener('resize', makeResponsive);
window.addEventListener('load', makeResponsive);
```

---

## Hướng Dẫn Tùy Chỉnh

### 1. Thay Đổi Layout Structure

**Để thay đổi từ layout 3 cột sang 2 cột:**

```html
<!-- Remove .left or .right div -->
<div class="main">
    <div class="maincontent">
        <!-- Main content -->
    </div>
    <div class="right">
        <!-- Sidebar -->
    </div>
</div>
```

**CSS suggestion:**
```css
.maincontent {
    width: 70%;
    float: left;
}
.right {
    width: 30%;
    float: right;
}
```

### 2. Thêm Styling Classes

**Tạo các variant classes:**

```css
/* Header variants */
.header.dark {
    background-color: #333;
    color: white;
}

.header.transparent {
    background-color: transparent;
}

/* Content variants */
.maincontent.wide {
    width: 80%;
}

.maincontent.narrow {
    width: 60%;
}

/* Sidebar variants */
.left.fixed,
.right.fixed {
    position: fixed;
    top: 100px;
}
```

### 3. Thêm Animation và Transitions

```css
/* Smooth transitions */
.header,
.main,
.footer {
    transition: all 0.3s ease;
}

/* Hover effects */
.right ul li a:hover {
    color: #007bff;
    text-decoration: none;
    padding-left: 10px;
    transition: padding-left 0.2s ease;
}

/* Fade in animation */
@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.maincontent {
    animation: fadeIn 0.5s ease;
}
```

### 4. Accessibility Improvements

**Thêm ARIA labels và semantic HTML:**

```html
<header role="banner" class="header">
    <div class="index">
        <h1>Site Title</h1>
    </div>
</header>

<nav role="navigation" aria-label="Main navigation" class="right">
    <div class="index">
        <h2>Navigation</h2>
        <ul>
            <li><a href="#main">Skip to content</a></li>
            <li><a href="#home">Home</a></li>
        </ul>
    </div>
</nav>

<main role="main" class="main">
    <article class="maincontent">
        <div class="index">
            <h1>Article Title</h1>
            <p>Content...</p>
        </div>
    </article>
    
    <aside role="complementary" class="left">
        <div class="index">
            <h2>Additional Info</h2>
            <p>Side content...</p>
        </div>
    </aside>
</main>

<footer role="contentinfo" class="footer">
    <div class="footer">
        <h2>Footer Information</h2>
    </div>
</footer>
```

### 5. Best Practices

#### ✅ Nên Làm:
- Sử dụng semantic HTML5 tags (`header`, `main`, `footer`, `nav`, `article`)
- Thay thế duplicate ID `leftText` bằng class
- Thêm alt text cho images (nếu có)
- Sử dụng meaningful class names
- Implement responsive design
- Add meta viewport tag cho mobile

#### ❌ Không Nên:
- Sử dụng cùng ID nhiều lần
- Inline styles (nên dùng CSS classes)
- Deep nesting (keep it flat khi có thể)
- Empty divs cho styling (sử dụng pseudo-elements)

### 6. Performance Optimization

```html
<!-- Optimize loading -->
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Your Title</title>
    
    <!-- Preload critical CSS -->
    <link rel="preload" href="b1.css" as="style">
    <link rel="stylesheet" href="b1.css">
    
    <!-- Defer non-critical JavaScript -->
    <script defer src="script.js"></script>
</head>
```

---

## API Reference Quick Guide

### HTML Structure API

| Component | Class/Tag | Purpose | Children |
|-----------|-----------|---------|----------|
| Header | `.header` | Page header | `.index` + `h1` |
| Main | `.main` | Content wrapper | `.maincontent`, `.left`, `.right` |
| Main Content | `.maincontent` | Primary content | `.index` + headings + paragraphs |
| Left Sidebar | `.left` | Secondary content | `.index` + content |
| Right Sidebar | `.right` | Navigation | `.index` + lists |
| Footer | `<footer>` | Page footer | `.footer` + content |
| Clear | `.clear` | Float clear | None |

### JavaScript API Functions

| Function | Parameters | Returns | Description |
|----------|------------|---------|-------------|
| `addMainContent()` | heading, content | void | Thêm section mới vào main content |
| `updateLeftSidebar()` | title, content | void | Cập nhật left sidebar content |
| `addRightSidebarLink()` | sectionIndex, linkText, linkUrl | void | Thêm link mới vào navigation |
| `createNavigationSection()` | title, links[] | void | Tạo section navigation mới |
| `updateFooter()` | copyright, address, contact | void | Cập nhật footer content |

---

## Changelog & Version History

### Version 1.0 (Current)
- Initial structure với 3-column layout
- Basic components: header, main, sidebars, footer
- Static HTML implementation

### Planned Improvements
- [ ] Responsive CSS framework
- [ ] JavaScript interaction library
- [ ] Template system cho dynamic content
- [ ] Accessibility enhancements
- [ ] Performance optimizations
- [ ] Fix duplicate ID issue

---

## Support & Contributing

### Báo Lỗi
Nếu phát hiện lỗi hoặc có suggestions, vui lòng:
1. Document lỗi cụ thể
2. Provide reproduction steps
3. Suggest possible solutions

### Contributing Guidelines
1. Follow existing code structure
2. Maintain consistent naming conventions
3. Test across browsers
4. Update documentation
5. Use semantic HTML

---

## License & Credits

**Author:** Khang Vu  
**Project Type:** Educational/Portfolio Website  
**Last Updated:** 2024

---

*Tài liệu này được tạo tự động dựa trên phân tích codebase. Vui lòng update khi có thay đổi trong structure.*
