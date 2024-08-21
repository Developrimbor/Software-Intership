# STAJ 0.1

Date: July 22, 2024

- Powertoys Advanced Paste araştırması yapıldı.
- API key ile ilgili aldığım bir hatayı araştırdım ve nedenni öğrendim
- Aşağıda ekran görüntüsü verilen verilen görselde “Welcome CheckBox” kısmının eklenmesi istendi.

![Untitled](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/List.png)

- Bu Welcome kısmı checked olduğunda ilgili sayfanın …/welcome bölümünün açılması gerekiyor.

```html
<div class="container">
  <div class="row">
		<form class="checkboxForm" method="post">
		    <label for="checkbox2" class="non-interactable-label"><b>Welcome</b></label> <!--checkbox2 şeklinde değiştirildi-->
		    <input type="checkbox" id="checkbox2" name="checkbox2" <?php echo isset($_COOKIE['checkbox']) && $_COOKIE['checkbox'] === 'checked' ? 'checked' : ''; 
		    // Çerezde 'checkbox' anahtarı var mı ve değeri 'checked' mi kontrol et, öyleyse 'checked' yazdır, değilse boş bırak.?>>
		 </form>
	 </div>
 </div>
```

- Yukarıdaki kod ile class’ı “checkboxForm” olan yeni bir form oluşturup içine label atayıp içerisine “Welcome” yazdım.

```css
.row {
    display: flex;
}

.container {
    display: flex;
    flex-direction: column;
    align-items: center;
}
```

- Yukarıdaki CSS kodları ile “All Site” ve “Welcome” kısımlarını yanyana ve sayfaya ortaladım.
