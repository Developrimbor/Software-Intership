# STAJ 1.5

Date: July 26, 2024

- [x]  ekrana gelen bağlantıların sayısı 10 dan az ise numaralar gözükmesin.

```jsx
  function itemsCount(matchedItems) {
    const itemsCount = matchedItems.length > 10; // Bağlantıların sayısının 10'dan fazla olup olmadığını kontrol eder
    
    matchedItems.forEach((item, index) => { // Eşleşen öğeleri döngü ile işler
    // Sonuç öğesinin içeriğini belirler, sayılar yalnızca itemsCount true olduğunda eklenir
		  resultItem.innerHTML = itemsCount? `<small>${index + 1}.</small> ${item}` : `${item}` ; // Sonuç öğesinin içeriğini belirler #indexx
	  }
}
// itemsCount koşulu ile bağalntıların sayısına göre işlem yapılır
```

---

- [x]  responsive bir tasarım gerekiyor mobile uygun olmalı video var
- [x]  bağlantıların sağ butonlarla arsında kalan boşluk azalsın
- [x]  bazı bağlantıların uzantıları çok uzun bu yüzden bir alt satıra geçiyor linkler bunu çözmek için bir karekter sınırı koymamız lazım, bu sınır aşıldığında “…” ile uzantı tamamlanmalı
    - [x]  “…” yerine son 3 harfin opaklığını kısarak linkin devam ettiğini belirten kod yazıldı.

```css
.char-opacity-75 {
   opacity: 0.75;
  }.char-opacity-50 {
   opacity: 0.50;
  }.char-opacity-25 {
   opacity: 0.25;
  }.hidden {
   display: none;
  }
```

```jsx
let displayText = "";
      if (item.length > 25) {
        for (let i = 0; i < item.length; i++) {
          if (i < 22) {
            displayText += item[i];
          } else if (i == 22) {
            displayText += `<span class="char-opacity-75">${item[i]}</span>`;
          } else if (i == 23) {
            displayText += `<span class="char-opacity-50">${item[i]}</span>`;
          } else if (i == 24) {
            displayText += `<span class="char-opacity-25">${item[i]}</span>`;
          } else {
            displayText += `<span class="char-opacity-25 hidden">${item[i]}</span>`;
          }
        }
      } else {
        displayText = item;
      }
```

---