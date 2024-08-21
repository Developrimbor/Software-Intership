# STAJ 1.5

Date: July 26, 2024

- [x]  buglar var tespit edip düzelt
    - [x]  Sol butonlara basıldığında buton rengi değişiyor ve 2.kez basıldığında eski haline dönmesi gerekirken ekranda herhangi bir yere basıldığında eski haline dönüyor bunu düzelt
        - [ ]  ilerleme var ama tam olarak düzelmedi

```css
.result-item:hover {
    text-decoration: underline; /* Metni altını çizme */
    text-decoration: none; /* Metni altını çizmeme */
    font-weight: normal;
    color: #FF6347; /* Yazı rengi */
}
```

---

- [x]  arama kutusuna yazılan ifade sonucunda gelen bağlantıların başında bulunan sayıların CSS düzenlemesi yapıldı

```css
.result-item small {
    color: #808080;
    justify-content: space-between;
    font-size: 0.9em; /* İstediğiniz boyuta göre ayarlayabilirsiniz */
    margin-left: -7px;
    margin-right: -4px;
}
```

---

- [x]  ekrana gelen bu bağlantıların başına sayılardan sonra “.” işaaretinin gelmesi sağlandı.

```jsx
resultItem.innerHTML = itemsCount ? `<small>${index + 1}.</small> ${displayText}` : `${displayText}` ;
```

---

- [x]  bağlantıların sağında bulunan ilk butona bastığımızda o bağlantıyı kopyalama işlmei yapıyordu, “ctrl” ile click işlemi yapıldığında ise “…/welcome” uzantısının kopyalanması isteniyor.

```jsx
function handleClick(event, url) { // ctrl tuşu ile basıldığında welcome uzantısı kopyalama #ctrll,kopyalamaa
    if (event.ctrlKey) {
      url += '/welcome'; // Ctrl tuşuna basılıysa URL'yi günceller
      //Örnek: https://bigmammas.dslink.co/welcome
    }
    copyToClipboard(url); // URL'yi kopyalar
  }
```