# STAJ 4.2

Date: August 13, 2024

- [ ]  Filter icon larına 2. click işleminden sonra eski style haline geri dönsün

![image.png](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/listFilterIcons.jpg)

```jsx
    function clearActiveClass() {
        buttons.forEach(button => {
            button.classList.remove('active');
            button.style.fontSize = '19.5px'; // Boyutu eski haline döndürür #yenieklendi
            button.style.color = '#000'; // Rengi varsayılan haline döndürür #yenieklendi
        });
    }
...

else {
			clearActiveClass(); // Diğer butonların aktif sınıfını kaldır
			button.classList.add('active'); // Tıklanan butona aktif sınıfını ekle
			button.style.fontSize = '24px'; // boyutu büyütüldü
			button.style.color = '#5A639C'; // rengi değiştirildi
			currentLinks = linksToShow;
			displayResults(currentLinks);
		 }
```

---

- [ ]  list de arama kutusuna girdi olduğunda eğer sonuç sayısı fazla ise yavaş yükleniyor
    - [ ]  bu durum mobilde daha da yavaş

```jsx
function applyOpacityEffect(item, font) { // opaklığın azaltılma işlemini sağlayan fonk. #opaklıkk, opacityy
    debugger;
    let displayText = "";
    let accumulatedWidth = 0; // karakterlerin genişliğini toplayarak metnin toplam genişliğini hesaplar. #genişlikk, metinn
    const maxWidth = 175; // 175 piksel genişlik sınırı

    for (let i = 0; i < item.length; i++) { // metnin genişliğini göre opaklığını azaltma işlemi
      const charWidth = getTextWidth(item[i], font);

      if (accumulatedWidth + charWidth > maxWidth) {
        if (accumulatedWidth + charWidth <= maxWidth + 20) {
          displayText += `<span class="char-opacity-75">${item[i]}</span>`;
        } else if (accumulatedWidth + charWidth <= maxWidth + 35) {
          displayText += `<span class="char-opacity-50">${item[i]}</span>`;
        } else {
            displayText += `<span class="char-opacity-25 hidden">${item[i]}</span>`;
        }
      } else {
        displayText += item[i];
      }

      accumulatedWidth += charWidth;
    }

    return displayText;
  }
```

> bağlantıların belli bir canvas uzunluğunu aştıktan sonra opaklığını azaltmak için kullanılan fonksiyon arama kutusuna girdi yapıldığında özellikle bağlantı sayısının fazla olduğu zamanlarda sonuçların ekrana gelmesini yavaşlatıyor.
> 
- [ ]  opaklık azaltma işlemini kaldırdığımızda hem web de hem de mobilde daha hızlanıyor ama bu sefer de uzantısı çok uzun olan bazı bağlantılar alt satıra taşıyor.
    - [ ]  “*” ⇒ opaklık azaltma işlemi olmadığında mobildeki gecikme yaklaşık olarak 0.40sn, opaklık işlemi yapıldığında ise gecikme süresi yaklaşık olarak 0.60sn
- [ ]  resultContainer a çıkan sonuçların sayısı 10 dan az veya fazla olmasına durumuna göre farklı sonuçlar meydana gelmesi,
- [ ]  bağlantıların sayısı 16 dan fazla ise container ın sağına scroll geliyor,

…

---