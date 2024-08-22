# STAJ 4.5 (YAZILIM STAJI SON GÜN)

Date: August 16, 2024

Kutuda eğer WEB url girmezse,
başını şöyle Tamamlasın:
[https://1a.dslink.co/bookmark/*.json](https://1a.dslink.co/bookmark/*.json)

Örnek:
"bulut" girip enter yaparsam

[https://1a.dslink.co/bookmark/bulut.json](https://1a.dslink.co/bookmark/bulut.json)
olarak işleme alsın

```jsx
jsx("button", {
onClick: () => {
let urlInput = document.querySelector('#url_input_container input').value.trim();

// Eğer uzantı verilmemişse, URL'yi tamamla
if (!urlInput.startsWith('http') && !urlInput.endsWith('.json')) {
urlInput = `https://1a.dslink.co/bookmark/${urlInput}.json`;
}
                                
if (urlInput.endsWith('.json')) {
fetch(urlInput)
...
```

---

- [x]  contextMenu açıkken ekrana click yapıldığında menu kapansın

```jsx
       // Menünün dışında bir yere tıklanıp tıklanmadığını kontrol eden işlev
    function outsideClickListener(event) {
        if (!contextMenu.contains(event.target) && !event.target.matches('span') && !event.target.matches('button')) {
            contextMenu.remove();
            document.removeEventListener("click", outsideClickListener);
        }
    }

    document.addEventListener("click", outsideClickListener);
```
