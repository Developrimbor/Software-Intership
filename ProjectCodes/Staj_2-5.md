# STAJ 2.5

Date: August 2, 2024

- [x]  Test sonrasında şunu yapacağız, AutoCopy etkileşiminde basit bir “Tin” sesi (soundplay) ve sağ alt kısma kaybolan bir notification
    - [ ]  ses gelmiyor!!! İçerik Güvenliği Politikası nı ihlal ettiği için hata alıyoruz!!!
    
    ![Untitled](https://raw.githubusercontent.com/Developrimbor/Software-Intership/main/images/policyError.png)
    
    - [ ]  https://chrome.google.com/webstore/detail/disable-content-security/ieelmcmcagommplceebfedjlakkhpden - Sorunu bu extension ile çözdüm ama geçici bir çözüm

```jsx
audio_notif1.addEventListener('canplaythrough', function() {
            console.log('Ses dosyası başarıyla yüklendi.');
        }, false);

        audio_notif1.addEventListener('error', function() {
            console.error('Ses dosyası yüklenirken bir hata oluştu.');
        }, false);

                // Bildirim göstermek için bir fonksiyon
        function showNotification(message) {
            // Bildirim div'i oluştur
            var notification = document.createElement('div');
            notification.textContent = message;
            notification.style.position = 'fixed';
            notification.style.bottom = '20px';
            notification.style.right = '150px';
            notification.style.padding = '10px 20px';
            notification.style.backgroundColor = 'rgba(0, 0, 0, 0.7)';
            notification.style.color = 'white';
            notification.style.borderRadius = '5px';
            notification.style.fontSize = '14px';
            notification.style.zIndex = '1000';
            notification.style.opacity = '0'; // Başlangıçta görünmez

            // Bildirimi body'e ekle
            document.body.appendChild(notification);

            audio_notif1.play().catch(function(error) {
                console.error('Ses çalınırken bir hata oluştu:', error);
            });

            // Görünürlüğü artırarak bildirim görünsün
            setTimeout(() => {
                notification.style.transition = 'opacity 0.5s';
                notification.style.opacity = '1';
            }, 10);

            // 3 saniye sonra bildirimi kaldır
            setTimeout(() => {
                notification.style.transition = 'opacity 0.5s';
                notification.style.opacity = '0';
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 500);
            }, 3000);
        }
```