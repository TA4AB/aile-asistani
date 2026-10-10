# Aile Asistanı

Aile Asistanı, kullanıcının belirlediği saatlerde iyi olma kontrolü yapan bir Android uygulamasıdır. Yanıt ekranında **İYİYİM** düğmesine basılabilir. Yanıt gelmezse uygulama, ayarlanmış sayıda sesli uyarı tekrarından sonra izin verilmişse kayıtlı acil durum kişisine SMS göndermeyi dener.

> Uygulama acil servislerin, profesyonel bakımın veya tıbbi cihazların yerine geçmez. Alarm, konum ve SMS işlevleri cihaz ayarlarına, izinlere, ağ/GPS durumuna ve mobil operatöre bağlıdır; kritik güvenlik hizmeti olarak tek başına kullanılmamalıdır.

## Özellikler

- Günlük kontrol alarmları oluşturma ve yönetme
- Gerçek alarm sesi/tekrar akışını SMS göndermeden deneyen test alarmı
- SMS, konum, bildirim, kesin alarm ve tam ekran alarm izinleri için durum kontrolü
- Kayıtlı acil durum kişisine ücret uyarısı içeren, kullanıcı onaylı test SMS'i
- Yanıt ekranını açan sesli alarm
- Ayarlardan 1–10 arasında seçilebilen uyarı tekrarı; varsayılan olarak her uyarı 1 dakika çalar ve uyarılar arasında 10 saniye beklenir
- Yanıt verilmezse kayıtlı acil durum kişisine konum bağlantısı içeren SMS gönderme denemesi
- İsteğe bağlı titreşim, SMS şablonu, yerel istatistikler ve test alarmı
- Profil, alarm ve uygulama tercihlerinin cihazda saklanması

## Gerekenler

- Android Studio ve Android SDK
- Mevcut proje yapılandırmasıyla derleme için Android SDK Platform 36
- Android 7.0 (API 24) veya üzeri bir cihaz

Android Studio'da projeyi açıp **Build > Make Project** seçin. Makinede Gradle kuruluysa debug APK şu komutla üretilebilir:

```sh
gradle :app:assembleDebug
```

Windows'ta depoda bulunan Gradle başlatıcısı kullanılabilir:

```bat
gradlew.bat :app:assembleDebug
```

Çıktı: `app/build/outputs/apk/debug/app-debug.apk`

## İlk kullanım

1. Profil bilgilerini girin; kişi için not alanı isteğe bağlıdır.
2. Ana ekranda acil durum kişisinin adını ve telefon numarasını kaydedin.
3. Günlük kontrol saatlerini ekleyin.
4. Ayarlar'da uyarı tekrarı sayısını ve titreşimi seçin; isterseniz test alarmını çalıştırın.
5. Android'in istediği SMS, konum, bildirim ve kesin alarm izinlerini, ilgili özellikleri kullanmak için verin.

SMS, yalnızca yanıt süresi ve tüm uyarı tekrarları tamamlandıktan sonra gönderilmeye çalışılır. SMS/konum izni yoksa, SMS gönderimi başarısız olursa veya cihaz/operatör mesajı iletemezse yakına haber verilemeyebilir. Konum bulunamaması halinde uygulama SMS'i konum bilgisi olmadan gönderebilir. Standart operatör ücretleri uygulanabilir.

## İzinler ve veri kullanımı

Uygulama; alarm planlama, bildirim ve kilit ekranında kontrol uyarısı gösterebilme, titreşim, acil durum SMS'i gönderme ve yanıt alınmadığında konum ekleme amaçlarıyla Android izinleri ister. İzinleri vermemek ilgili özelliği devre dışı bırakabilir.

Profil adı, yaş, isteğe bağlı kişi notları, acil durum kişisi adı/telefonu, alarm saatleri, tercih edilen tekrar sayısı, SMS şablonu ve yerel istatistikler uygulamanın özel depolamasında tutulur. Uygulama kendi sunucusuna bu bilgileri göndermez; ancak Android'in cihaz yedekleme özelliği uygulama verilerini cihaz dışına yedekleyebilir. Yanıt verilmediğinde, izin varsa cihazın konumu SMS içeriğine eklenebilir ve SMS mobil operatör üzerinden kayıtlı kişiye iletilir.

Ayrıntılar ve güncel iletişim bilgisi için [Gizlilik Politikası](PRIVACY_POLICY.md) sayfasına bakın.

## Google Play'e gönderim durumu

Bu depo, yayına hazır olduğu veya Google Play tarafından onaylandığı anlamına gelmez. **10 Ekim 2026 itibarıyla** proje `targetSdk = 36` ve `compileSdk = 36` kullanır; bu, yeni mobil uygulama gönderimleri için 31 Ağustos 2026'da yürürlüğe giren minimum Android 16 / API 36 hedefini karşılar. Daha yeni Play şartları veya uygulamaya özgü politika incelemesi ayrıca geçerli olabilir.

API 36 hedefi tek başına Play onayı garantilemez. Yayından önce Android 16 cihazında sistem çubukları/ekran yerleşimi ve alarm akışlarını test edin; aşağıdaki Play Console beyanları ve izin incelemeleri yine tamamlanmalıdır.

Ek yayın öncesi işler:

- `SEND_SMS` hassas izni için Play Console'da izin beyanı ve inceleme gereksinimini değerlendirin. Google Play, fiziksel güvenlik/acil durum SMS kullanımını listeler; bu, uygulamanın otomatik onay alacağı anlamına gelmez. Uygulama incelemesi için izin kullanımını gösteren video ve test adımları hazırlayın.
- `USE_FULL_SCREEN_INTENT` beyanını tamamlayın ve bu uygulamanın kontrol alarmı kullanımının uygunluğunu Play Console'da doğrulayın. İzin reddedilirse uygulama tam ekranı zorla açmak yerine bildirimle işlevini sürdürebilmelidir.
- `USE_EXACT_ALARM` kısıtlı kullanım izninin uygulamanın temel işlevine uygunluğunu doğrulayın. Uygun değilse kaldırıp kullanıcı tarafından verilebilen `SCHEDULE_EXACT_ALARM` akışını kullanmayı değerlendirin.
- `mediaPlayback` foreground service türünü, kullanım gerekçesini ve inceleme videosunu Play Console'da beyan edin; hedef API yükseltmesinin gerektirdiği manifest/çalışma zamanı değişikliklerini uygulayın.
- SMS ve konum izin pencerelerinden önce, verinin ne zaman, kime ve hangi amaçla kullanılacağını açıklayan belirgin bir uygulama içi bildirim ve kullanıcı onayı ekleyin.
- Google Play **Data safety** formunu gerçek veri akışına göre doldurun ve GitHub'da barındırılan gizlilik politikası bağlantısını mağaza kaydına ekleyin.
- Google Play'de yayımlanacak uygulamalar için **Health apps declaration** formunu tamamlayın. Uygulama sağlık özelliği sunmadığı sonucuna varılsa bile Play Console formu bunu beyan etmenizi ister; isteğe bağlı sağlık notu alanı ve yaşlı bakımı amacı için doğru kategoriyi seçin.
- Gizlilik metnindeki veri yedekleme, saklama, silme ve iletişim bilgilerini kontrol edin; Android yedekleme davranışını uygulama ayarlarıyla tutarlı hale getirin.
- Hedef kitle/yaş beyanı, mağaza açıklaması, ekran görüntüleri ve uygulama davranışını birbiriyle tutarlı hazırlayın.

Resmî başvuru kaynakları:

- [Google Play hedef API seviyesi şartı](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en)
- [SMS ve Arama Kaydı izin politikası](https://support.google.com/googleplay/android-developer/answer/10208820?hl=en)
- [İzin beyanı ve inceleme süreci](https://support.google.com/googleplay/android-developer/answer/9214102?hl=en)
- [Foreground service ve tam ekran bildirim gereksinimleri](https://support.google.com/googleplay/android-developer/answer/13392821?hl=en)
- [Kesin alarm izni için Android kılavuzu](https://developer.android.com/about/versions/14/changes/schedule-exact-alarms)
- [Google Play kullanıcı verisi politikası](https://support.google.com/googleplay/android-developer/answer/9888076?hl=en)
- [Google Play Health apps declaration](https://support.google.com/googleplay/android-developer/answer/14738291?hl=en)

## Lisans

Bu depoda bir lisans dosyası bulunmuyor. Kodun kullanım, değiştirme ve dağıtım koşulları için hak sahibinden izin alın.
