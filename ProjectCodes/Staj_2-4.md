# STAJ 2.4

Date: August 1, 2024

> Chatgpt ye entegre edilmiş birkaç butonumuz var bunlarla ilgili bazı yenilemeler yapılması istendi.
> 
- [ ]  UX hataları var, kontrol et…

![Untitled](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/Buttons.png)

![Untitled](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/enterKey.png)

Bütün inputlarda sağında geniş click alanlı yapıştır butonu
Altında enter ile gönder (Default aktif) bilgi seçeneği. Her iki objede de "Hint".
—-
AYM algoritması.

Eğer kutu boş iken onaylarsa (Send)>
Yapıştır butonu eylemi gerçekleşecek. (Pano içeriğini yapıştıracak.)

---

- [x]  sağ üste paste butonu eklendi

```jsx
// paste clipboard #pastee, yapıştır
const pasteClipboardButton = document.createElement("button");
//pasteClipboardButton.style.marginBottom = "15px";
pasteClipboardButton.style.marginRight = "25px";
pasteClipboardButton.style.padding = "5px 10px";
pasteClipboardButton.style.cursor = "pointer";
pasteClipboardButton.style.float = "right";
pasteClipboardButton.style.backgroundColor = "linear-gradient(-45deg, #ffae00, #7e03aa, #00fffb)"; // Buton arkaplan rengi
pasteClipboardButton.style.borderRadius = "3px"; // Buton kenarını oval yaptım
pasteClipboardButton.style.border = "1px solid #ccc"; // Buton kenar çizgisi
pasteClipboardButton.style.fontFamily = "Arial, sans-serif"; // Yazı tipini Arial yaptım
pasteClipboardButton.style.fontSize = "14px";
pasteClipboardButton.textContent = "paste"; // Placeholder metni ayarla #hintt,placee,Placeholderr
pasteClipboardButton.title = "Panoyu Yapıştırma İşlemi";
pasteClipboardButton.addEventListener("click",  () => {
	navigator.clipboard.readText().then(value => inputElement.value = value);
});
inputContainer.appendChild(pasteClipboardButton);
```

---

- [x]  sol alta checkbox ve text eklendi

```jsx
// checkbox oluşturma #checkboxx, enterr
const checkboxEnter = document.createElement("input");
checkboxEnter.style.float = "left";
checkboxEnter.style.margin = "10px 10px 10px 0px";
checkboxEnter.style.cursor = "pointer";
checkboxEnter.style.border = "1px solid #ccc"; // Buton kenar çizgisi
checkboxEnter.type = "checkbox";
checkboxEnter.title = "Enter ile Gönder";
checkboxEnter.textContent = "Enter ile Gönder";
checkboxEnter.checked = true;

inputContainer.appendChild(checkboxEnter);
 
// Enter ile Gönder #enterr
const checkboxLabel = document.createElement("label");
checkboxLabel.innerText = "Enter ile Gönder";
checkboxLabel.style.marginTop = "5px";
checkboxLabel.style.float = "left";

inputContainer.appendChild(checkboxLabel);
```

---

- [x]  enter eventi düzenlendi

```jsx
if (index === buttonArray.length - 1) {
	inputElement.addEventListener("keydown", (event) => {
		if (event.key === "Enter" && checkboxEnter.checked) {                         
			if (inputElement.value === "" ) {
				pasteClipboardButton.click();
      }
      setTimeout(() => {
	      buttonElement.click();
      },100)
    }
	});
}
```