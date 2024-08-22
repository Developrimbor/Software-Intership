# !STAJ 3.1

Date: August 5, 2024

- [x]  “paste” yazısı yerine icon ile yer değiştirildi

```jsx
// FontAwesome stil dosyasını sayfaya ekle
const link = document.createElement("link");
link.rel = "stylesheet";
link.href = "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css";
document.head.appendChild(link);

// İkonu ekle
const icon = document.createElement("i");
icon.className = "fas fa-file"; // FontAwesome ikon sınıfı
icon.style.fontSize = "18px"; // İkon boyutu
icon.style.color = "#fff"; // İkon rengi
pasteClipboardButton.appendChild(icon);
```
<div class="row">
  
<img src = 'https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/pasteText.png' height = '400px' >
<img src = 'https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/pasteIcon.png' height = '400px' >

</div>
---

- [x]  Bu butonlar tıklama içeriği oluşturulacak. CTRL + B kutusunda Promptlar var.
- [x]  AYM kontrolü yap (Akıllı yazılım mimarisi / UX)

<img src = 'https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/contextMenu.png' height = '400px' >

```jsx
var promptInput = "Aşağıda sana vermiş olduğum bu kodu kısa ve öz olacak şekilde özetlemeni istiyorum.\n------- \n[input: Özetle]";
-----------------
var promptInput = "Sana vermiş olduğum aşağıdaki kodu düzenlemeni -Tidy Yapmanı- istiyorum. Mesela fonksiyon parametreleri arasında boşluk bırakmak, gövdenin içinde her iki mantıksal kısım arasında boşluk bırakmak vb.\n---------\n[input:Tidy Yap]";
-----------------
var promptInput = "Yazılan her satır kodun en sağından itibaren yorum satırı koyup o satırdaki kodun ne işe yaradaığını yazmanı istiyorum.\n------------\n[input:Hashtag]";
```