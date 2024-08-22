# SATJ 3.2

Date: August 6, 2024

- [x]  AutoCopy den iki tane var hala, onu düzeltmeye çalış.
    - [ ]  AutoCopy’nin style özellikleri değiştirilmiyor

```jsx
document.body.appendChild(formGroup);
//bu kodu yorum saatırına alınca sorun çözüldü
```

---

- [x]  Prompter Helper Butonu Düzenlendi

```jsx
showButton.style.right = '37px'; // Sola yaslamak için 'left' kullanılıyor
showButton.style.top = '70px'; // Dikeyde ortala
showButton.title = "Prompter Helper";
```

---

- [x]  buttonClick6 sırasında, ESC ve Space gibi tuşlara basıldığında çıksın

```jsx
document.addEventListener("keydown", function (event) {
    if (event.key === "Escape") {
        contextMenu.remove();
    }
}, { once: true });
```