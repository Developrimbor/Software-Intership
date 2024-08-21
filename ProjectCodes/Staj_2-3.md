# STAJ 2.3

Date: July 31, 2024

- [x]  Yazılan kodun daha anlaşılır ve düzenli olması için unutulan yerlere comment’ler eklendi.
- [ ]  Telefonda arama kutusuna yazı yazılırken hem yazılar geç geliyor hem de bağlantıların ekrana gelmesi zaman alıyor. Bu sorun PC de yaşaamıyor.
    - [ ]  aynı problemin PC de de yaşandığını fark ettim ama kısa bir süre araştırmaya devam edilebilir
    
    > bunun nedeni genel olarak fonksiyonun içerisinde çok fazla işlem yapılmasından kaynaklı
    > 

> Aşağıdaki fonksiyon da önce sonuçları temizleme işlemi yapıyor, daha sonra matchedItems ile eşlenen itemler eşleniyor, bunların sayısı ekrana yazdırılıyor, bağlantıların sayısının 10 dan fazla olup olmama durumunu kontrol ediliyor, forEach ile döngü oluşturuluyor, ekrana verilen bağlantıların genişliğine bağlı olarak opaklık azaltma işlemi yapılıyor, bağlantıların başına sayı ve nokta ekleniyor, bağlantıların sonuna ise 3 tane aksiyon butonu ekleniyor ve sonuçların sayısına göre container ın büyüklüğü en sağ kısma scroll eklenmesi gibi işlemler de burada yapıldığından belirtilen bu sorunun oluşması normal gibi…
> 

```jsx
 function getTextWidth(text, font) { // text in genişliğini almaya yarayn fonk #textt, genişlikk, widthh
    const canvas = document.createElement('canvas');
    const context = canvas.getContext('2d');
    context.font = font;
    return context.measureText(text).width;
  }
  
  function applyOpacityEffect(item, font) { // opaklığın azaltılma işlemini sağlayan fonk. #opaklıkk, opacityy
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

function displayResults(matchedItems) {
    
    clearResults(); // Sonuçları ekrana görüntüler
    
    arrayFiltItems = matchedItems;
    resultCountElement.textContent = "Çıkan sonuç sayısı: " + matchedItems.length;

    const itemsCount = matchedItems.length > 10; // Bağlantıların sayısının 10'dan fazla olup olmadığını kontrol eder
    const font = "normal 16px Arial"; // Metin için kullanılacak font

    matchedItems.forEach((item, index) => { // Eşleşen öğeleri döngü ile işler
      const resultItem = document.createElement('li'); // Yeni bir sonuç öğesi oluşturur
      const resultPatern = document.createElement('div'); // Yeni bir sonuç deseni oluşturur
      
      resultItem.classList.add('result-item'); // Sonuç öğesine 'result-item' sınıfını ekler
      
      const textWidth = getTextWidth(item, font); // font genişliği için bir değişken

      // 200 pikselden geniş bağlantılar için opaklık efektini uygulama
      let displayText = textWidth > 175 ? applyOpacityEffect(item, font) : item;

      
      // Sonuç öğesinin içeriğini belirler, sayılar yalnızca itemsCount true olduğunda eklenir
      resultItem.innerHTML = itemsCount ? `<small>${index + 1}.</small> ${displayText}` : `${displayText}` ; // Sonuç öğesinin içeriğini belirler #indexx
      
      //İkonları oluşturmak için ve de kutucuk düzeni için 
      ...
    });
```

---