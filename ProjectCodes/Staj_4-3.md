# STAJ 4.3

Date: August 14, 2024

- [ ]  AutoCopy den iki tane var ve üstteki checked olduğunda, bu işlem çalışıyor ama üsttekki default olarak checked gelmiyor ve alttaki checked olarak geliyor yani alttakinin büyük ihtimalle bir işlevi yok. Alttakini bi türlü yok edemedim.

![Untitled](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/autoCopy1.png)

```jsx
toggleCheckbox.addEventListener("change", function(){
            if (toggleCheckbox.checked) { 
                copyCode(); // Checkbox işaretliyse kodu panoya kopyala
            }
        });
```

---

- [ ]  “scriptGT.dt” adında bir dosya daha var ve bu script “GPT_Prompter.dt” ye etki ediyor

- [ ]  AutoCopy nin style özellikleri “scriptGT.dt” dosyasında değiştirildi

```jsx
    formGroup.style.top = "56px";
    formGroup.style.right = "90px";
```

![image.png](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/autoCopy2.png)