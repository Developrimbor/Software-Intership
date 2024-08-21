# STAJ 2.1

Date: July 29, 2024

- Bug tespiti ve çözüm süreçleri ile geçti.
- bir önceki gün yapılan bağlantıların belli bir karater uzunluğundan sonra opaklığının azaltılması yerine metin genişilğinin belli bir uzunluğu geçtikten sonra opaklık azaltılması olarak değiştirildi.

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
	  ...
	  const itemsCount = matchedItems.length > 10; // Bağlantıların sayısının 10'dan fazla olup olmadığını kontrol eder
    const font = "normal 16px Arial"; // Metin için kullanılacak font
		const textWidth = getTextWidth(item, font); // font genişliği için bir değişken
    // 200 pikselden geniş bağlantılar için opaklık efektini uygulama
    let displayText = textWidth > 175 ? applyOpacityEffect(item, font) : item;
	  ...
  }
```