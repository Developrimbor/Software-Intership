# STAJ 3.4

Date: August 8, 2024

- [x]  input sonucu çıkan bağlantıların sayısı 10 dan az ise ilk bağlantının small etiketini input a yazdırıyor, ama bağlantı sayısı 10dan az ise ilk bağlantıyı açıyor!!
    - [ ]  Sorun sadece bağlantı sayısında değilmiş soldakinin bağlantı sayısı 6 olmasına rağmen başka bir etiketin içini de dahil ediyor
        - [ ]  Bulunan iki tane sorun var, birincisi eğer bağlantının uzunluğu belli bir canvas uzunluğunu geçiyorsa uygulanan opacity linki açmasına bir şekilde engel oluyor ve bu etiket ile birlikte her şeyi inputa yazdırıyor.
        - [ ]  İkinci sorun ise, eğer bağlantı sayısı 10 dan fazla ise small etiketi içerinde hem bağlantının numarasını hem de bağlantının kendisini yazdırıyor, buna ek olarak eğer canvas size belli bir uzunluğun üstündeyse o bağlantının üzerine uygulanan opacity işlemleri de input da gözüküyor.

![Untitled](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/listBug.jpg)

- [x]  case: ‘Enter’ ın içinde bulunan innerHtml yerine textContent yazıldı ve trim işlemlerine ekstra replace işlemleri de yapılarak linklerin doğru bir şekilde açılması sağlandı.

```jsx
case 'Enter': // Eğer tuş 'Enter' ise #enterr, tuşş, inputt
	event.preventDefault(); // Varsayılan davranışı engeller

		if (selectedIndex >= 0) { // Eğer selectedIndex geçerli ise
			const link = results[selectedIndex].textContent.trim().replace(/^\d+\.\s*/, ''); // Seçili sonucun içeriğini alır
			...
		} else { // Diğer durumlarda
				// Seçili öğe yoksa, ilk öğeyi aç
				const firstResult = results[0]; // İlk sonucu alır
					if (firstResult) { // Eğer ilk sonuç varsa
						const link = firstResult.textContent.trim().replace(/^\d+\.\s*/, ''); // İlk sonucun içeriğini alır	
			...
			}
```