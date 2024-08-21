# STAJ 1.3

Date: July 24, 2024

- Kodda birçok düzenleme yapıldı.
- Özellikle Fetch yapısı içerisinde bulunan fonksiyonları ve değişkenleri bu yapının dışına aktardık.
- Bunu yaparak fetch içinde tanımlanan fonkssiyonların dışarıda tekrar tanımlanmasının önüne geçildi.
- Örnek fonksiyonlar;

```jsx
// Arama girdisini temizleyen fonksiyon
function clearSearch() { 
	searchInput.focus(); // Arama girdisine odaklanır
  searchInput.value = ""; // Arama girdisini boşaltır
  showPredefinedLinks(); // Önceden tanımlanmış bağlantıları gösterir
} // Arama girdisini temizleyen fonksiyon

function clearResults() { // Sonuçları temizleyen fonksiyon
  resultsContainer.innerHTML = ''; // Sonuçları içeren konteyneri boşaltır
} // Sonuçları temizleyen fonksiyon

// Her eşleşen öğeyi ekrana gösteren/oluşturan fonksiyon
function displayResults(matchedItems) { // Sonuçları ekrana görüntüler
   matchedItems.forEach(item => { // Eşleşen öğeleri döngü ile işler
     const resultItem = document.createElement('li'); // Yeni bir sonuç öğesi oluşturur
     const resultPatern = document.createElement('div'); // Yeni bir sonuç deseni oluşturur
     resultItem.classList.add('result-item'); // Sonuç öğesine 'result-item' sınıfını ekler
     resultItem.innerHTML = `${item}`; // Sonuç öğesinin içeriğini belirler
            ...
            
            
```
