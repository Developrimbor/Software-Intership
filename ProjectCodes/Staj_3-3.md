# STAJ 3.3

Date: August 7, 2024

- [x]  Enter ile gönder checkboxunu cookie ile takip et son actiounu hatırlasın

```jsx
// Cookie ayarlama  #enterr,cookiee
function setCookie(name, value, days) {
	const date = new Date();
	date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
	const expires = "expires=" + date.toUTCString();
	document.cookie = name + "=" + value + ";" + expires + ";path=/";
}

// Cookie okuma fonksiyonu
function getCookie(name) {
	const nameEQ = name + "=";
	const ca = document.cookie.split(';');
		for (let i = 0; i < ca.length; i++) {
			let c = ca[i];
			while (c.charAt(0) === ' ') c = c.substring(1, c.length);
			if (c.indexOf(nameEQ) === 0) return c.substring(nameEQ.length, c.length);
		}
	return null;
}

// Son durumunu cookie'den al
const savedState = getCookie("checkboxEnterState");
checkboxEnter.checked = savedState === "true"; // Eğer cookie "true" ise checked yap

// Checkbox durumunu kaydetme
checkboxEnter.addEventListener("change", function () {
    setCookie("checkboxEnterState", checkboxEnter.checked, 365);
});
```

---

- [x]  [list.dslink.co](http://list.dslink.co) TR karakter fix
    - [x]  arama kısmına “ğ,ç,ö...” vb. karakter girildiğinde bunların “g,c,o…” olması gerek
        - [ ]  Büyük “İ” Harfi Dışındakiler Düzeltildi

```jsx
.replace(/[üÜ]/g, 'u') // Ü harflerini u'ye dönüştürür
.replace(/[öÖ]/g, 'o') // Ö harflerini o'ye dönüştürür
.replace(/[çÇ]/g, 'c') // Ç harflerini c'ye dönüştürür
```

---

- [ ]  ~~pano boş ise notification gelsin “pano boş” şeklinde~~
    - [ ]  ~~ilerleme kaydedilemedi~~

---

- [ ]  ~~List dslink logo olsun,
Mobil de masaüstü kısayolu oluştur dene logo gözükecekmi, gözükürse başarılı~~