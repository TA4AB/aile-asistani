# Aile Asistanı Gizlilik Politikası

**Yürürlük tarihi: 10 Ekim 2026**

Bu politika, Aile Asistanı Android uygulamasının hangi bilgilere eriştiğini, bunları nasıl kullandığını ve kullanıcıların seçimlerini açıklar.

## Veri sorumlusu ve iletişim

- **Geliştirici:** Arif Onur Bütün (Ar-Se Soft Technology)
- **E-posta:** [info@arsesoft.com](mailto:info@arsesoft.com)

Gizlilik veya kişisel verilerinizle ilgili talepleriniz için bu adrese başvurabilirsiniz.

## Uygulamanın işlevi

Aile Asistanı, kullanıcının belirlediği saatlerde bir iyi olma kontrolü başlatır. Kullanıcı, kontrol ekranındaki **İYİYİM** düğmesine basarak yanıt verebilir. Yanıt, yapılandırılmış sesli uyarı tekrarları tamamlanana kadar gelmezse uygulama, gerekli izinler varsa kayıtlı acil durum kişisine konum bilgisini içerebilecek bir SMS göndermeyi dener.

Uygulama acil servislerin, profesyonel bakımın veya tıbbi hizmetlerin yerine geçmez. Alarmın çalışacağı, konumun alınacağı veya SMS'in iletileceği garanti edilmez.

## Erişilen ve saklanan bilgiler

Kullanıcının girmesi veya uygulamanın çalışmasıyla aşağıdaki bilgiler işlenebilir:

- **Profil:** ad, yaş ve isteğe bağlı kişi notları.
- **Acil durum kişisi:** kullanıcının girdiği kişinin adı ve telefon numarası.
- **Kontrol ayarları:** alarm saatleri, uyarı tekrar sayısı, titreşim tercihi ve SMS şablonu.
- **Yerel istatistikler:** toplam kontroller, başarılı yanıt sayısı ve son kontrol zamanı.
- **Konum:** yanıt alınmadığında ve konum izni verildiğinde, cihazın mevcut veya son bilinen konumu.

Profil, ayarlar ve istatistikler Android uygulamasının özel depolamasında tutulur (`SharedPreferences`). Uygulama tarafından işletilen bir sunucuya veya analiz/ reklam hizmetine bu bilgilerin gönderildiği bir işlev mevcut kodda bulunmuyor. Uygulama kaynak manifestinde internet izni tanımlı değildir. Bununla birlikte Android cihazın sistem yedekleme özelliği uygulama verilerini cihaz dışına yedekleyebilir; bu davranış kullanıcının cihaz/hesap ayarlarına ve uygulamanın yedekleme kurallarına bağlıdır.

Kişi notları alanı isteğe bağlıdır. Bu notlar acil durum SMS'ine eklenmez. Bu alana gereğinden fazla hassas bilgi yazmayın.

## İzinler ve kullanım amaçları

- **SMS gönderme (`SEND_SMS`):** Tüm kontrol tekrarlarından sonra yanıt alınmazsa, uygulamada kayıtlı acil durum kişisine uyarı mesajı göndermeyi denemek için kullanılır. Mesaj, SMS şablonuna ve bulunabilen konuma bağlı olarak acil durum kişisinin adını ve harita bağlantısını içerebilir. Profildeki yaş ve isteğe bağlı sağlık notu SMS'e eklenmez. Mobil operatör tarifesi uygulanabilir.
- **Konum (`ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION`):** Yanıt alınmadığında SMS'e konum eklemek amacıyla kullanılır. Uygulama son bilinen konumu kullanabilir; bu konum güncel olmayabilir. Konum alınamazsa SMS konum bilgisi olmadan gönderilebilir.
- **Bildirim (`POST_NOTIFICATIONS`) ve tam ekran bildirim (`USE_FULL_SCREEN_INTENT`):** Kontrol zamanı uyarısını ve yanıt ekranını kullanıcıya göstermek için kullanılır. Tam ekran izni/özelliği cihaz veya Play politikası nedeniyle kullanılamazsa bildirim davranışı değişebilir.
- **Kesin alarm (`SCHEDULE_EXACT_ALARM`, `USE_EXACT_ALARM`) ve yeniden başlatma (`RECEIVE_BOOT_COMPLETED`):** Kullanıcının planladığı kontrol saatlerini zamanında çalıştırmak ve yeniden başlatma sonrasında etkin alarmları yeniden planlamak için kullanılır.
- **Titreşim (`VIBRATE`):** Kullanıcı titreşimi etkinleştirmişse alarm uyarısını desteklemek için kullanılır.
- **Ön plan hizmeti ve uyanık tutma (`FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_MEDIA_PLAYBACK`, `WAKE_LOCK`):** Alarm uyarısı sırasında ses/titreşim işlevini yürütmek için kullanılır.

Kullanıcı Android ayarlarından izinleri reddedebilir veya sonradan geri alabilir. İlgili izin olmadan konum/SMS/tam ekran uyarı işlevi çalışmayabilir.

## SMS ve üçüncü taraflarla paylaşım

Yanıt alınmadığında ve SMS izni mevcut olduğunda SMS, cihazın mobil şebekesi üzerinden kullanıcının kaydettiği acil durum kişisine gönderilir. Bu paylaşım uygulamanın temel acil durum uyarısı işlevini yerine getirmek içindir. SMS içeriğinde acil durum kişisinin adı, konum koordinatları veya harita bağlantısı bulunabilir. Profildeki yaş ve sağlık notu SMS'e eklenmez. SMS gönderimi mobil operatörün altyapısına tabidir; ücret alınabilir. Uygulama mesajın teslim edildiğini doğrulamaz ve mesaj gönderildikten sonra onu geri alamaz.

Uygulama içindeki harita bağlantısı alıcı tarafından açılırsa, bağlantı ilgili harita hizmetinin sağlayıcısına gider ve o hizmetin kendi gizlilik koşulları geçerli olur. Geliştirici, bu bağlantıyla ilgili üçüncü taraf hizmetlerin veri uygulamalarını kontrol etmez.

Uygulama kodunda reklam veya analitik SDK'sı kullanımı bulunmamaktadır. Bu durum yeni bir SDK eklenmesiyle değişirse bu politika güncellenmelidir.

## Saklama ve silme

Uygulamanın yerel verileri siz uygulama ayarlarından değiştirmediğiniz, Android uygulama verisini temizlemediğiniz veya uygulamayı kaldırmadığınız sürece cihazda tutulur. Profil verilerini, acil durum kişisini ve ayarları uygulama içinden değiştirebilirsiniz. Tüm yerel verileri silmek için Android **Uygulama bilgisi > Depolama > Verileri temizle** seçeneğini kullanın veya uygulamayı kaldırın. Sistem yedeğine alınmış veriler, cihaz/hesap yedekleme ayarları kapsamında ayrıca yönetilebilir. Daha önce gönderilmiş SMS'i alıcının cihazından uygulama silemez.

## Güvenlik

Veriler Android'in uygulama özel depolama alanında tutulur. Uygulama, yerel verileri ayrıca şifrelediğini iddia etmez. Cihaz kilidi kullanmanız, Android'i güncel tutmanız ve SMS/konum izinlerini yalnızca gerekli olduğunda vermeniz önerilir.

## Çocukların gizliliği

Uygulama, aile üyeleri ve bakım verenler tarafından kullanılmak üzere tasarlanmıştır; çocuklara yönelik bir hizmet olarak tasarlanmamıştır. Profil yaş alanı kullanıcı tarafından doldurulur. Çocukların bilgileri girilecekse bunu yalnızca yasal veli/vasinin bilgisi ve geçerli mevzuata uygun biçimde yapın.

## Politika değişiklikleri

Uygulama işlevleri, veri akışı veya yürürlükteki gereksinimler değiştiğinde bu politika güncellenebilir. Güncel metin, uygulamanın herkese açık GitHub deposunda bu dosyada yayımlanır. Önemli değişikliklerde uygun uygulama içi bilgilendirme yapılmalıdır.
