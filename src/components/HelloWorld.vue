<template>
  <header style="background: #f8f9fa; padding: 15px 0; text-align: center; margin-bottom: 20px;">
    <h1 style="margin: 0; color: #333; font-size: 24px;">我的产品展示站</h1>
    <nav style="margin-top: 15px; padding: 10px 0;">
      <a href="#" class="nav-link" style="margin: 0 15px; text-decoration: none; color: #0099ff;">首页</a>
      <a href="#" class="nav-link" style="margin: 0 15px; text-decoration: none; color: #0099ff;">产品展示</a>
      <a href="#" class="nav-link" style="margin: 0 15px; text-decoration: none; color: #0099ff;">在线留言</a>
    </nav>
  </header>

<main>
<div class="slideshow-container">
  <div class="mySlides">
    <img src="/z1.jpg" alt="作品1" style="width:50%; max-height: 300px; object-fit: contain; display: block; margin: 0 auto; border-radius:8px; transition: all 0.3s ease;">
    <div class="text">第1张图文字</div>
  </div>
  <div class="mySlides">
    <img src="/z2.jpg" alt="作品1" style="width:50%; max-height: 300px; object-fit: contain; display: block; margin: 0 auto; border-radius:8px; transition: all 0.3s ease;">
    <div class="text">第二张图文字</div>
  </div>
  <div class="mySlides">
    <img src="/z3.jpg" alt="作品1" style="width:50%; max-height: 300px; object-fit: contain; display: block; margin: 0 auto; border-radius:8px; transition: all 0.3s ease;">
    <div class="text">第三张图文字</div>
  </div>
  <div class="mySlides">
    <img src="/z4.jpg" alt="作品1" style="width:50%; max-height: 300px; object-fit: contain; display: block; margin: 0 auto; border-radius:8px; transition: all 0.3s ease;">
    <div class="text">第四张图文字</div>
  </div>
  <div class="mySlides">
    <img src="/z5.jpg" alt="作品1" style="width:50%; max-height: 300px; object-fit: contain; display: block; margin: 0 auto; border-radius:8px; transition: all 0.3s ease;">
    <div class="text">第五张图文字</div>
  </div>
  <div class="mySlides">
    <img src="/z6.jpg" alt="作品1" style="width:50%; max-height: 300px; object-fit: contain; display: block; margin: 0 auto; border-radius:8px; transition: all 0.3s ease;">
    <div class="text">第六张图文字</div>
  </div>
  <a class="prev" @click="plusSlides(-1)">&#10094;</a>
  <a class="next" @click="plusSlides(1)">&#10095;</a>
</div>

<div style="text-align:center">
  <span class="dot" @click="currentSlide(1)"></span>
  <span class="dot" @click="currentSlide(2)"></span>
  <span class="dot" @click="currentSlide(3)"></span>
  <span class="dot" @click="currentSlide(4)"></span>
  <span class="dot" @click="currentSlide(5)"></span>
  <span class="dot" @click="currentSlide(6)"></span>
</div>

<div style="max-width: 600px; margin: 40px auto; padding: 0 20px;" class="form-box">
  <h2 style="text-align: center; color: #333; margin-bottom: 25px;">在线留言</h2>
  <form class="contact-form" @submit="handleSubmit(event)" action="https://wj.qq.com/s2/25894031/bba3/" method="GET" target="_blank" style="background: #f8f9fa; padding: 25px; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1);">
    
    <div style="margin-bottom: 18px;" class="form-item">
      <label style="display: block; margin-bottom: 6px; font-weight: bold; color: #444;">姓名：</label>
      <input type="text" name="q1" placeholder="请输入你的姓名" style="width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 4px; font-size: 16px;">
    </div>

    <div style="margin-bottom: 18px;" class="form-item">
      <label style="display: block; margin-bottom: 6px; font-weight: bold; color: #444;">邮箱：</label>
      <input type="email" name="q2" placeholder="请输入你的邮箱" style="width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 4px; font-size: 16px;">
    </div>

    <div style="margin-bottom: 18px;" class="form-item">
      <label style="display: block; margin-bottom: 6px; font-weight: bold; color: #444;">留言内容：</label>
      <textarea name="q3" rows="4" placeholder="请输入你的需求或留言" style="width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 4px; font-size: 16px; resize: vertical;"></textarea>
    </div>

    <button type="submit" style="width: 100%; padding: 12px; background-color: #00cc66; color: white; border: none; border-radius: 4px; font-size: 16px; cursor: pointer;">提交留言</button>
  </form>
</div>
</main>

<footer style="background: #f8f9fa; padding: 20px 0; text-align: center; margin-top: 30px; font-size: 14px; color: #666;">
  <p>© 2026 我的产品展示站 | 联系方式：your_email@163.com</p>
</footer>
</template>

<script setup>
import { onMounted } from 'vue'
let slideIndex = 1;

function plusSlides(n) {
  showSlides(slideIndex += n);
}

function currentSlide(n) {
  showSlides(slideIndex = n);
}

function showSlides(n) {
  let i;
  let slides = document.getElementsByClassName("mySlides");
  let dots = document.getElementsByClassName("dot");
  if (n > slides.length) {slideIndex = 1}
  if (n < 1) {slideIndex = slides.length}
  for (i = 0; i < slides.length; i++) {
    slides[i].style.display = "none";
  }
  for (i = 0; i < dots.length; i++) {
    dots[i].className = dots[i].className.replace(" active", "");
  }
  if (slides.length > 0) slides[slideIndex-1].style.display = "block";
  if (dots.length > 0) dots[slideIndex-1].className += " active";
}

function autoSlide() {
  plusSlides(1);
  setTimeout(autoSlide, 3000);
}

function handleSubmit(event) {
  event.preventDefault();
  const form = event.target;
  const name = form.q1.value;
  const email = form.q2.value;
  const message = form.q3.value;

  if (!name || !email || !message) {
    alert("姓名、邮箱、留言都要填哦！");
    return;
  }

  const wjUrl = "https://wj.qq.com/s2/25894031/bba3/";
  const fullUrl = wjUrl + "?q1=" + encodeURIComponent(name) + "&q2=" + encodeURIComponent(email) + "&q3=" + encodeURIComponent(message);

  alert("即将跳转到问卷页面，提交后数据会保存到后台！");
  const newWindow = window.open("https://wj.qq.com/s2/25894031/bba3/", "_blank");
  setTimeout(() => {
    newWindow.location.href = fullUrl;
  }, 500);
  form.reset();
}

onMounted(() => {
  showSlides(slideIndex);
  autoSlide();

  const navLinks = document.querySelectorAll('.nav-link');
  navLinks.forEach(link => {
    link.addEventListener('click', (e) => {
      navLinks.forEach(l => l.classList.remove('active'));
      e.target.classList.add('active');
    });
  });
  navLinks[0].classList.add('active');
});
</script>

<style scoped>
.mySlides {
  display: none;
  animation: fade 0.8s;
}

@keyframes fade {
  from { opacity: 0.4 }
  to { opacity: 1 }
}

.slideshow-container {
  max-width: 800px;
  position: relative;
  margin: 30px auto;
}

.mySlides img:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.prev, .next {
  display: block;
  cursor: pointer;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  background: rgba(0,0,0,0.3);
  border-radius: 4px;
  user-select: none;
}

.next {
  right: 0;
}

.prev:hover, .next:hover {
  background: rgba(0,0,0,0.8);
}

.text {
  color: white;
  font-size: 15px;
  padding: 8px 12px;
  position: absolute;
  bottom: 8px;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.5);
  border-radius: 4px;
}

.dot {
  cursor: pointer;
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background: #bbb;
  border-radius: 50%;
  display: inline-block;
}

.active, .dot:hover {
  background: #717171;
}

.nav-link {
  margin: 0 15px;
  text-decoration: none;
  color: #0099ff;
  padding: 8px 12px;
  border-radius: 6px;
  transition: 0.3s;
  font-weight: bold;  /* 文字加粗 */
font-size: 16px;    /* 字号变大 */
}

.nav-link:hover {
  background: #0099ff;
  color:#ffffff!important;
}

.nav-link.active {
  background: #0077cc;
  color: white;
}

.form-box {
  max-width: 550px;
  margin: 40px auto;
  padding: 30px;
  background: #f9f9f9;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.form-item input,
.form-item textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 15px;
}

button[type="submit"] {
  width: 100%;
  padding: 12px;
  background: #0099ff;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  cursor: pointer;
  margin-top: 8px;
}

button[type="submit"]:hover {
  background: #0077cc;
}
/* 手机端适配 - 粘贴到style最后 */
@media (max-width: 768px) {
  .slideshow-container {
    max-width: 100%;
    margin: 15px auto;
  }
  .mySlides img {
    width: 90% !important;
    max-height: 250px;
  }
  .nav-link {
    padding: 6px 10px;
    font-size: 14px;
    margin: 0 8px;
  }
  .form-box {
    padding: 20px;
    margin: 20px auto;
  }
  header h1 {
    font-size: 20px;
  }
}
</style>