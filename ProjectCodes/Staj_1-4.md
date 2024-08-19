# STAJ 1.2

Date: July 23, 2024

- [x]  Bağlantıların solundaki numaralardan sonra nokta eklendi
- [x]  “*” a basıldığında çıkan bağlantılardan bazıları ekrana tam sığmıyordu bunun için bağalntının üzerine gelindiğinde metnin font-size ı küçültüldü.

```css
.result-item:hover {
		text-decoration: underline;
		text-decoration: none;
		font-weight: bold;
		color: #000;
		font-size: 15.5px;
}
```

- [x]  All Site ile Welcome yer değiştirilmeli
- [x]  All Site seçili olduğunda Welcome seçilemez olsun, aynısı tam tersi içinde geçerli
    - [x]  BUG ⇒ All Site seçili iken F5 lediğimizde All Site checked geliyor.
    - [x]  Bu kısmı radio button mantığı ile yap yani birine tıklandığında diğeri disabled olmasın biri checked olduğunda diğeri unchecked olarak kalsın

```jsx
 	var checkbox = document.getElementById('checkbox'); // "checkbox" id'li öğeyi seç ve checkbox değişkenine ata.
  var checkbox2 = document.getElementById('checkbox2');
  var form = document.getElementById('checkboxForm');

  function updateCheckboxes(checkedCheckbox) { // checkbox checked ise checkbox2 yi, checkbox2 checked ise checkbox ı unchecked yap.
    if (checkedCheckbox === 'checkbox') {
      checkbox2.checked = false; // Diğer checkbox'ı işaretsiz yap
    } else if (checkedCheckbox === 'checkbox2') {
      checkbox.checked = false; // Diğer checkbox'ı işaretsiz yap
    }
  }

  function sendCheckboxState() { // checkboxların durumunu gönderen fonksiyon
    var formData = new FormData(form);
    fetch(window.location.href, {
      method: 'POST',
      body: formData
    }).catch(error => console.error('Error:', error));
  }

  checkbox.addEventListener('change', function () {
    if (this.checked) {
      updateCheckboxes('checkbox');
    }
    sendCheckboxState(); // Checkbox durumunu gönder
  });

  checkbox2.addEventListener('change', function () {
    if (this.checked) {
      updateCheckboxes('checkbox2');
    }
    sendCheckboxState(); // Checkbox durumunu gönder
  });

  // Sayfa yüklendiğinde çerez durumuna göre checkboxları ayarla
  window.addEventListener('load', function () {
    var cookieCheckbox = document.cookie.indexOf('checkbox=checked') !== -1;
    var cookieCheckbox2 = document.cookie.indexOf('checkbox2=checked') !== -1;

    checkbox.checked = cookieCheckbox;
    checkbox2.checked = cookieCheckbox2;

    updateCheckboxes(cookieCheckbox ? 'checkbox' : (cookieCheckbox2 ? 'checkbox2' : '')); // Çerezlere göre durumları güncelle
  });
```

---

- [x]  ekrana gelen bağlantıların sayısı 10 dan az ise numaralar gözükmesin.

```jsx
const itemsCount = matchedItems.length > 10;
```

- [x]  bağlantıların başında yer alan numaralar ile linkler arasındaki boşluğu biraz artır.
- [x]  2 tane görsel verildi bunları PS de birleştirip tasarım yap
- [x]  responsive bir tasarım gerekiyor mobile uygun olmalı video var
- [x]  bağlantıların sağ butonlarla arsında kalan boşluk azalsın
    - [x]  bu yapıldığında linkler bir alt satıra taşıyor