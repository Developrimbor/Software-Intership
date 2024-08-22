# STAJ 4.4

Date: August 15, 2024

- [x]  CTRL+ B de çıkan Prompts bölümünde Import butonuna tıklandığında PC den ve URL den json uzantılı dosya import işleminin olması için bir context menu oluşturulması istendi
- Burada Import Butonunun Özellikleri Belirlendi
    
    ```jsx
    jsx("div", {
        children: [
            jsx("button", {
                                id: "i_button",
                                title: "Json Dosyasını İçeriye aktar",
                                onClick: () => {
                                    // Context menüyü aç/kapa işlemi
                                    const menu = document.querySelector('#context_menu');
                                    if (menu.style.display === 'block') {
                                        menu.style.display = 'none';
                                    } else {
                                        menu.style.display = 'block';
                                    }
                                },
                                style: {
                                    padding: 5,
                                    height: 40,
                                    backgroundColor: '#333',
                                    color: '#fff',
                                    borderRadius: 5,
                                    cursor: 'pointer',
                                },
                                children: "Import"
                            }),
    ```
    
- Import Butonuna Basıldığında Karşımıza Çıkan Context Menu nun Özellikleri Mevcut PC den ya da URL den JSON uzantılı dosya yükleme Butonları Mevcut
    
    ```jsx
    jsx("div", {
                    id: "context_menu",
                    style: {
                        display: 'none', // Başlangıçta gizli
                        position: 'absolute',
                        backgroundColor: '#fff',
                        border: '1px solid #ccc',
                        padding: '5px',
                        borderRadius: '5px',
                        boxShadow: '0 0 10px rgba(0,0,0,0.1)',
                        marginTop: '5px',
                        width: '100px', // Butonların genişliği için uygun bir genişlik belirledik
                        textAlign: 'center' // Butonların ortalanması için
                    },
                    children: [
                        jsx("div", {
                            onClick: () => {
                                // Bilgisayardan dosya yükleme
                                const input = document.createElement('input');
                                input.type = 'file';
                                input.accept = '.json';
                                input.onchange = (e) => {
                                    const file = e.target.files[0];
                                    if (file) {
                                        const reader = new FileReader();
                                        reader.onload = () => {
                                            const data = JSON.parse(reader.result);
                                            console.log("JSON verisi:", data); // JSON verisini işleyin
                                            // JSON verisiyle ilgili işlemler
                                        };
                                        reader.readAsText(file);
                                    }
                                };
                                input.click();
                            },
                            style: {
                                padding: '10px',
                                marginBottom: '5px',
                                backgroundColor: '#333',
                                color: '#fff',
                                borderRadius: '5px',
                                cursor: 'pointer',
                                width: '100%' // Butonun context menü genişliğini kaplaması için
                            },
                            children: "PC"
                        }),
                        jsx("button", {
                            onClick: () => {
                                // URL'den JSON yükleme kısmını göster
                                const urlInputContainer = document.querySelector('#url_input_container');
                                if (urlInputContainer.style.display === 'block') {
                                    urlInputContainer.style.display = 'none';
                                } else {
                                    urlInputContainer.style.display = 'block';
                                }
                            },
                            style: {
                                padding: '10px',
                                backgroundColor: '#333',
                                color: '#fff',
                                borderRadius: '5px',
                                cursor: 'pointer',
                                width: '100%' // Butonun context menü genişliğini kaplaması için
                            },
                            children: "URL"
                        })
                    ]
                }),
    ```
    
- Burada ise URL den dosya alma işlemleri var
    
    ```jsx
    jsx("div", {
             id: "url_input_container",
             style: {
                 display: 'none', // Başlangıçta gizli
                 position: 'absolute', // Ekranın farklı bir yerinde çıkmasını sağlar
                 top: '120px', // Sayfanın üstünden 100px aşağıda olacak şekilde ayarladık
                 left: '50%', // Ortalanmış şekilde
                 transform: 'translateX(-50%)', // Yatayda tam ortalar
                 padding: '20px',
                 backgroundColor: '#f9f9f9',
                 border: '1px solid #ccc',
                 borderRadius: '5px',
                 width: '300px', // URL girişi için yeterli genişlik
                 boxShadow: '0 0 10px rgba(0,0,0,0.1)' // Hafif bir gölge efekti
             },
             children: [
                 jsx("input", {
                     type: 'text',
                     placeholder: 'URL girin (json uzantılı)',
                     style: {
                         padding: '5px',
                         width: '100%',
                         color: '#000'

                     }
                 }),
                 jsx("button", {
                     onClick: () => {
                         const urlInput = document.querySelector('#url_input_container input').value;
                         if (urlInput && urlInput.endsWith('.json')) {
                             fetch(urlInput)
                             .then(response => {
                                 if (!response.ok) {
                                     throw new Error("URL'den JSON dosyası alınamadı.");
                                 }
                                 return response.json();
                             })
                             .then(data => {
                                 console.log("URL'den alınan JSON verisi:", data); // JSON verisini işleyin
                                 alert("JSON verisi başarıyla alındı!");
                             })
                             .catch(error => {
                                 console.error("Bir hata oluştu:", error);
                                 alert("URL'den JSON dosyası alınamadı.");
                             });
                     } else {
                         alert("Lütfen geçerli bir .json uzantılı URL girin.");
                     }
                 },
                     style: {
                         padding: '10px',
                         marginTop: '10px',
                         backgroundColor: '#333',
                         color: '#fff',
                         borderRadius: '5px',
                         cursor: 'pointer',
                         width: '100%'
                     },
                     children: "Yükle"
                 })
             ]
         })
     ]
})
    ```
    

![image.png](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/contextMenu2.png)

---

<aside>
💡 İşlem belli bir seviyede başarılı oldu ama şöyle bir problemle karşılaştım;

</aside>

![image.png](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/CORSpolicy.png)

> CORS policy nedeniyle karşıdan link yoluyla dosya aktarımı olmuyor. Bu hatanın aynısını AutoCopy özelliği aktif olduğunda “Kopyalandı” bildirimi aldığımızda bildirim sesininin gelmesini istediğimizde almıştık.
> 