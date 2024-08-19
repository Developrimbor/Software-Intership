# STAJ 0.2

Date: July 17, 2024

- Stajımı yapmakta olduğum Dev Secure şirketinde geliştirilen projelerde JS, PHP dilleri hakim. Bu nedenle kendimi bu dillerde geliştirmek için youtube, patikaDev, udemy gibi platformlar üzerinden kendimi geliştirmeye çalışıyorum.
- Geliştirilmiş proje üzerinde anlatım yapılırken bir bug keşfettik ve Seyfettin Bey benden bu bug’u halletmemi istedi.
- Sorunu kısaca anlatıyım: elimizde list.txt adında bir dosya bulunmakta ve bu dosyanın için yaklaşık 700 civarı sitenin linki bulunmakta. Sadece bizim erişim sağlayabildiğimiz bir site üzerinden bu list.txt de bulunan sitelere arama kutusuna “*” işaretini yazdığımızda tüm bu sitelerin ekranda gözükmesi gerekmekte ama sitede sadece bu sitelerin alfateik olarak sıralandığında ortalrından itibaren gözüktüğünü fark ettim.
- Öncelikle sorunu anlayabilmek adına site de “F12” tuşuna basarak siteyi incelemye başladım ve aslında tüm siteleri içeren kodların bulunduğunu fakat tam ortadan itibaren bu sitelerin ilk bölümünün yazdırılması gereken container’a ortalandığını fark ettim.
- Bu bugu çözmek için ise teker teker tüm bu linklerin ait olduğu divleri de kapsayan bir divin düzenlenmesi gerektiğini anladım.
- Koda gelince ilgili bölümde “justify-content: center” seçeneğini kaldırdığımda sorun çözülmüş oldu.

---

```jsx
function openResultLink(matchedItems) {
          console.log(matchedItems);
          console.log(arrayFiltItems);
          matchedItems.slice(0,10).forEach(item => {
            if (checkbox.checked) { // Checkbox işaretli ise
                  openLinkNormal('https://' + normalizeLink(item)) // Normal bağlantıyı açar
                } else if (checkbox2.checked) { //checkbox2 işaretliyse
                  openLinkWelcome('https://' + normalizeLink(item)) // sitelerin Welcome bağlantısını açar
                } else { // Checkbox işaretli değilse
                  openLink('https://' + normalizeLink(item)) // Bağlantıyı açar
                }
          });
          }
        let arrayFiltItems = [];
```

- Burada “matchedItems” adında arama yapılan ve eşlenen sonuçları getirir. Çıkan sonuçların sayısı çok fazla olabileceğinden ilk 10 itemi alması için “slice”ı kullancık ve forEach ile de bu dizi döndürdük. Aynı zamanda 2 tane checkboxumuz bulunuyor. Bunların durumuna göre farklı olaylar gerçekleşiyor.