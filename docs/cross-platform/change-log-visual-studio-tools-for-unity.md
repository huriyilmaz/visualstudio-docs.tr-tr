---
title: Günlüğü Değiştir (Unity için Visual Studio Araçları, Windows) | Microsoft Dokümanlar
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0e1810f452f48c95e0c4e8117820be3598b0f139
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74706779"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Günlüğü değiştir (Unity için Visual Studio Tools, Windows)

Unity için Visual Studio Tools değişiklik günlüğü.

## <a name="4420"></a>4.4.2.0

Yayınlanma Aralık 3, 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Kullanıcı tanımlı arabirimlerle sabit tanılama.

  - Hatalı biçimlendirilmiş ifadeleriçeren hızlı araç uçları düzeltildi.

## <a name="4410"></a>4.4.1.0

Yayınlanma Kasım 6, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity arka plan işlemleri için destek eklendi. (Hata ayıklama, alt işlem yerine ana işleme otomatik olarak bağlanabilir).
  
  - İlişkili belgeleri görüntüleyen Birlik iletileri için hızlı bir araç ipucu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Gelişmiş ikili ve `UNT0002` çağırma ifadeleri ile etiket karşılaştırma çözümleyicisi düzeltildi.

### <a name="deprecated-features"></a>Amortismana Küçümsülen Özellikler

- **Entegrasyon:**

  - İleriye dönük olarak, Visual Studio Tools for Unity sadece Visual Studio 2017+'yı destekleyecektir.

## <a name="4400"></a>4.4.0.0

Yayınlanma Tarihi: 15 Ekim 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Tüm Unity iletileri için (kullanılmayan parametre) için `IDE0060` bir bastırıcı eklendi.
  
  - `TooltipAttribute`' ile etiketlenen alanlar için hızlı bir araç ipucu eklendi (Bu da bu alanı kullanarak basit bir erişimci almak için çalışacaktır).

## <a name="4330"></a>4.3.3.0

Yayınlanma Eylül 23, 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Hafif yapılar için hata ve uyarı raporlaması düzeltildi.

## <a name="4320"></a>4.3.2.0

Yayınlanma Eylül 16, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Visual Studio'nun Birlik projelerine özel yeni tanılamalar ekleyerek Birlik projeleri için sahip olduğu anlayışı derinleştirdik. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE, Unity Editor'daki değişkeni değiştirmenizi engelleyecek `readonly` bir denetçi değişkenini değiştirmek için hızlı düzeltme göstermez.
    - `UNT0001`: Birlik iletileri boş olsalar bile çalışma zamanına göre çağrılır, Unity çalışma süresine göre kesintisiz işlemeden kaçınmak için bunları bildirmeyin.
    - `UNT0002`: Dize eşitliği ni kullanarak etiket karşılaştırması yerleşik CompareTag yönteminden daha yavaştır.
    - `UNT0003`: GetComponent'in genel formunun kullanımı tip güvenliği için tercih edilir.
    - `UNT0004`: İletiyi güncelleştirme klitime bağlıdır ve Time.fixedDeltaTime yerine Time.deltaTime'ı kullanmalıdır.
    - `UNT0005`: FixedUpdate iletisi çerçeve hızından bağımsızdır ve Time.deltaTime yerine Time.fixedDeltaTime kullanmalıdır.
    - `UNT0006`: Bu Birlik iletisi için yanlış yöntem imzası algılandı.
    - `UNT0007`: Unity, null coalescing ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecigeçersiz.
    - `UNT0008`: Unity, null yayma ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecigeçersiz kılar.
    - `UNT0009`: InitializeOnLoad özniteliğini bir sınıfa uygularken statik bir oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - `UNT0010`: MonoBehaviours yalnızca AddComponent() kullanılarak oluşturulmalıdır. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - `UNT0011`: ScriptableObject yalnızca CreateInstance() kullanılarak oluşturulmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - `USP0001`için `IDE0029`: Birlik nesneleri null coalescing kullanmamalıdır.
    - `USP0002`for `IDE0031`: Unity nesneleri null yayılımı kullanmamalıdır.
    - `USP0003`for `IDE0051`: Birlik iletileri Birlik çalışma zamanı tarafından çağrılır.
    - `USP0004`for `IDE0044`: SerializeField özniteliği olan alanlar yalnızca okunmamalıdır.

## <a name="4310"></a>4.3.1.0

Yayınlanma Eylül 4, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Daha iyi tür ekranı için destek `List<object>` eklendi, yani `List'1[[System.Object, <corlib...>]]`.

  - İşaretçi üye erişimi için destek `p->data->member`eklendi, yani.

  - Dizi başharflerinde örtük dönüşümler için destek `new byte [] {1,2,3,4}`eklendi, yani .

## <a name="4300"></a>4.3.0.0

Yayınlanma 13 Ağustos 2019

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - MDS protokolü 2.51 için destek eklendi.

- **Entegrasyon:**

  - Sıralama, arama ve yenileme özellikleriyle "Birliğe Ekle örneği" penceresi geliştirildi. PID artık yerel oyuncular için bile görüntülenir (sistemdeki dinleme soketlerini sorgulayarak sahip alma işlemini geri alır).

  - Asmdef dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Unity Players ile iletişim kurarken hatalı biçimlendirilmiş iletilerin sabit kullanımı.

- **Değerlendirme:**

  - İfadelerde ad alanlarının işlenmesi düzeltildi.

  - IntPtr tipleri ile sabit denetim.
  
  - Özel durumlar dışında basamak sorunları düzeltildi.

  - Sözde tanımlayıcıların ($exception gibi) sabit değerlendirilmesi.

  - Geçersiz adresleri derefered ederken kilitlenmeyi önleyin.  

  - Boşaltılan etki alanlarıyla ilgili sorun giderildi.

## <a name="4201"></a>4.2.0.1

Yayınlanma 24 Temmuz 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Unity Project Explorer'dan herhangi bir dosya türü oluşturmak için yeni bir seçenek eklendi.
  
  - Unity projeleri için hızlı yapılar kullanırken tanılama önbelleğe alma geliştirin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Dosya uzantısı tanınmış bir düzenleyici tarafından işlenmediğini zedelediğinde bir sorun giderildi.

  - Unity Project Explorer'da özel uzantılar için sabit destek.

  - Ana iletişim kutusunun dışındaki kaydetme ayarları düzeltildi.

  - Eski Microsoft.VisualStudio.MPF bağımlılığı kaldırıldı.

## <a name="4110"></a>4.1.1.0

Yayınlanma Mayıs 24, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - 2019.1 için Güncelleştirilmiş MonoBehaviour API.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Hafif yapı etkinleştirildiğinde çıktıya raporlama uyarıları ve hataları düzeltildi.

  - Hafif yapı performansı düzeltildi.

## <a name="4100"></a>4.1.0.0

Yayınlanma Mayıs 21, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Projeleri daha hızlı yeniden yüklemek için yeni toplu IŞ API'si için destek eklendi.

  - IntelliSense hatalarını ve uyarılarını kullanmak lehine, Unity projeleri için tam yapıyı devre dışı bıraktı. Nitekim Birlik, Birlik'in dahili olarak ne yaptığını temsil eden sınıf kitaplığı projeleri ile Visual Studio çözümü oluşturur. Bununla birlikte, Visual Studio'daki yapının sonucu, derleme boru hattı kapalı olduğu için Unity tarafından asla kullanılmaz veya alınmaz. Visual Studio'da bina oluşturmak boşuna kaynak tüketmektir. Araçlarınız veya buna bağlı bir kurulumunuz olduğu için tam bir yapıya ihtiyacınız varsa, bu optimizasyonu devre dışı kullanabilirsiniz (Araçlar/Seçenekler/Birlik Araçları/Projelerin tam oluşturmasını devre dışı kullanabilirsiniz).

  - Bir Birlik projesi yüklendiğinde Birlik Proje Gezgini'ni (UPE) otomatik olarak gösterin. UPE, Çözüm Gezgini'nin yanına sabitlenir.

  - Unity 2019.x ile proje adı ayıklama mekanizması güncellendi.

  - UPE'de Birlik paketleri için destek eklendi. Yalnızca Başvurulan paketler `Packages` (klasörde manifest.json kullanılarak) ve `Packages` Yerel paketler (klasöre katıştırılmış) görünür.

- **Proje Oluşturma:**

  - Çözüm dosyasını işlerken dış özellikleri koruyun.

- **Değerlendirme:**

  - Takma ad nitelikli adlar için destek eklendi (şimdilik yalnızca genel ad alanı). Yani ifade değerlendiricisi şimdi genel form kullanarak türleri kabul ediyor::namespace.type.

  - İşaretçi `pointer[index]` dereference `*(pointer+index)` formuyla anlamsal olarak aynı olan form için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Microsoft.VisualStudio.MPF ile düzeltme eğitim sorunları.

  - Sabit UWP oynatıcı eklemek, herhangi bir proje yüklü olmadan.

  - Visual Studio henüz bağlı değilken sabit otomatik varlık veritabanı yenileme.

  - Etiketler ve onay kutularıyla ilgili tema sorunları giderildi.

- **Hata ayıklayıcı:**

  - Statik yapıcılar ile sabit adım.

## <a name="4005"></a>4.0.0.5

Yayınlanma Şubat 27, 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Kurulum paketi ile Visual Studio sürüm algılaması düzeltildi.

  - Kullanılmayan derlemeler kurulum paketinden kaldırıldı.

## <a name="4004"></a>4.0.0.4

Yayınlanma Şubat 13, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Yükleme sırasında Unity işlemlerini düzgün bir şekilde algılamak ve kurulum altyapısının dosya kilitlerini daha iyi işlemesine izin vermek için destek eklendi.

  - API'yi `ScriptableObject` güncelleştirildi.

## <a name="4003"></a>4.0.0.3

Yayınlanma Ocak 31, 2019

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - Genel ve serihale alan artık uyarılara neden olmaz. Bu iletileri oluşturan Unity `CS0649` `IDE0051` projelerindeki ve derleyici uyarılarını otomatik olarak bastırdık.

- **Entegrasyon:**

  - Unity düzenleyici ve oyuncu örneklerini görüntülemek için kullanıcı deneyimini geliştirin (windows artık yeniden boyutlandırılabilir, tek tip kenar boşluklarını kullanın ve yeniden boyutlandırma kavramasını görüntüleyin). Unity editörleri için İşlem-Id bilgileri eklendi.

  - API'yi `MonoBehaviour` güncelleştirildi.

- **Değerlendirme:**

  - Yerel işlevler için destek eklendi.

  - Sözde değişkenler (özel durum ve nesne tanımlayıcıları) için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Takma aylak resimleri ve temalarıyla ilgili bir sorun giderildi.

  - Yalnızca hata ayıklama sırasında, otomatik olarak kıymet veritabanını yenilerken Çıkış Penceresi'ne yazın.

  - MonoBehaviour sihirbazı filtreleme ile ui gecikmeleri düzeltildi.

- **Hata ayıklayıcı:**

  - Eski protokol sürümlerini kullanırken adlandırılmış bağımsız değişkenlerde okuma özel özniteliği düzeltildi.

## <a name="4002"></a>4.0.0.2

Yayınlanma Ocak 23, 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Sabit deneysel yapı üretimi.

  - UI iş parçacığı basıncını en aza indirmek için proje dosyası olay işleme sildi.

  - Toplu metin değişiklikleri ile sabit tamamlama sağlayıcısı.

- **Hata ayıklayıcı:**

  - Kullanıcı hata ayıklama iletilerinin görüntülenmesi ekteki hata ayıkcısına düzeltildi.

## <a name="4001"></a>4.0.0.1

Yayınlanma 10 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - İfade değerlendirmesi için Roslyn lehine NRefactory değiştirildi.

  - İşaretçiler için ek destek: dereference, döküm ve işaretçi aritmetik (hem Unity 2018.2+ hem de yeni çalışma süresi gereklidir).

  - Dizi işaretçisi görünümü için destek eklendi (C++'daki gibi). İşaretçi ifadesini alın ve virgül ve görmek istediğiniz öğe sayısını tamamlayın.

  - Async yapıları için destek eklendi.

- **Entegrasyon:**

  - Unity'nin varlık veritabanını otomatik olarak yenilemek için destek eklendi. Bu varsayılan olarak etkinleştirilir ve Visual Studio'da bir komut dosyası kaydederken Unity tarafında bir yeniden derlemetetikletir. Bu özelliği Araçlar\Seçenekler\Birlik Için Araçlar\Unity\Refresh Unity'nin Varlık Veritabanında kaydedebilirsiniz.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Visual Studio tercih edilen dış düzenleyici olarak seçilmediğinde köprü etkinleştirme düzeltildi.

  - Yanlış biçimlendirilmiş veya desteklenmeyen ifadeler ile sabit ifade değerlendirmesi.

## <a name="4000"></a>4.0.0.0

Yayınlanma Tarihi: 4 Aralık 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Visual Studio 2019 için ek destek (Visual Studio 2019'u harici bir komut dosyası editörü olarak kullanabilmek için en azından Unity 2018.3'e ihtiyacınız vardır).

  - HDPI ölçekleme, piksel mükemmel görüntüler ve temalı tam destek ile Visual Studio görüntü hizmeti ve kataloğu benimsenmiştir.

### <a name="deprecated-features"></a>Kullanım dışı bırakılan özellikler

- **Entegrasyon:**

  - İleriye dönük olarak, Visual Studio Tools for Unity yalnızca Unity 5.2+'yı (Unity'nin yerleşik Visual Studio entegrasyonuyla) destekleyecektir.

  - İleriye dönük olarak, Visual Studio Tools for Unity sadece Visual Studio 2015+'ı destekleyecektir.

  - Eski dil hizmeti, hata listesi ve durum çubuğu kaldırıldı.

  - Hızlı Monobehaviour Sihirbazı kaldırıldı (özel intellisense desteği lehine).

## <a name="3903"></a>3.9.0.3

Yayınlanma Kasım 28, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - İlk projede bulunan komut dosyaları eklerken veya kaldırırken proje yeniden yükleme ve intellisense sorunları düzeltildi.

## <a name="3902"></a>3.9.0.2

Yayınlanma Kasım 19, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Unity'nin hata ayıklayıcı motoruyla iletişim kurmak için kullanılan kütüphanedeki bir kilitlenme giderildi ve özellikle 'Birliğe Ekle' tuşuna basarken veya oyunu yeniden başlatırken Visual Studio veya Unity dondurdu.

## <a name="3901"></a>3.9.0.1

Yayınlanma Kasım 15, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Başka bir varsayılan düzenleyici seçildiğinde Unity eklentisi etkinleştirme düzeltildi.

## <a name="3900"></a>3.9.0.0

Yayınlanma Kasım 13, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Unity tarafından düzeltilmiş bir Unity performans hatası için geçici çözüm geri alındı.

## <a name="3807"></a>3.8.0.7

Yayınlanma 20 Eylül 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - (3.9.0.2'den itibaren geri alındı) Unity'nin hata ayıklayıcı motoruyla iletişim kurmak için kullanılan kütüphanedeki bir kilitlenme giderildi ve özellikle 'Birliğe Ekle' tuşuna basarken veya oyunu yeniden başlatırken Visual Studio veya Unity dondurdu.

## <a name="3806"></a>3.8.0.6

Yayınlanma Ağustos 27, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Projelerin ve çözümün yeniden yüklenmesi düzeltildi.

## <a name="3805"></a>3.8.0.5

Yayınlanma Tarihi: 20 Ağustos 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Sabit proje izleme abonelik bertaraf.

## <a name="3804"></a>3.8.0.4

Yayınlanma 14 Ağustos 2018

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - İşaretçi değerleri için destek eklendi.

  - Genel yöntemler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Birden çok projeyle akıllı yeniden yükleme değiştirildi.

## <a name="3803"></a>3.8.0.3

Yayınlanma Tarihi: 24 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - (3.9.0.0'dan itibaren geri alındı) Unity tarafından düzeltilmiş bir Unity performans hatası için geçici çözüm geri alındı.

## <a name="3802"></a>3.8.0.2

Yayınlanma 7 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Bir Unity performans hatası için geçici geçici çözüm: proje oluştururken Önbellek MonoIslands.

## <a name="3801"></a>3.8.0.1

Yayınlanma Haziran 26, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklama:**

  - UserLog ve UserBreak komutları için destek eklendi.

  - Tembel tür yükleme desteği eklendi (ağ yükünü ve hata ayıklama yanıt gecikmesini en iyi duruma durumlandırın).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Geliştirilmiş ikili operatör ifade değerlendirmesi ve yöntem arama.

## <a name="3800"></a>3.8.0.0

Yayınlanma Mayıs 30, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklama:**

  - Değişkenleri async yapılarda görüntülemek için destek eklendi.

  - Derleyici yapıları ile uyarıları önlemek için kesme noktaları ayarı yaparken iç içe geçmiş türleri işlemek için destek eklendi.

- **Entegrasyon:**

  - Shaders için metin arkadaşı gramerleri için destek eklendi (Shader kodu renklendirmesi için Artık C++ iş yüküne gerek yok).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Yeni Unity çalışma süresini kullanırken taşınabilir pdb'yi artık mdb'ye dönüştürün.

## <a name="3701"></a>3.7.0.1

Yayınlanma Mayıs 7, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Yükleyici:**

  - Deneysel yapılar kullanırken bağımlılık sorunu düzeltildi.

## <a name="3700"></a>3.7.0.0

Yayınlanma Mayıs 7, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklama:**

  - Düzenlenmiş hata ayıklama (aynı Visual Studio oturumu ile birden fazla oyuncu/editör hata ayıklama) için destek eklendi.

  - Android USB oynatıcı hata ayıklama desteği eklendi.

  - UWP/IL2CPP oy verime için destek eklendi.

- **Değerlendirme:**

  - Hexadecimal belirteçler için destek eklendi.

  - Geliştirilmiş saat penceresi değerlendirme deneyimi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Özel durum ayarlarının sabit kullanımı.

- **Proje Oluşturma:**

  - Paket yöneticisi derleme birimlerini nesilden hariç tut.

## <a name="3605"></a>3.6.0.5

Yayınlanma Mart 13, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - Birlik 2018.1'de yeni proje jeneratörüne destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Özel projelerle bozuk durumları işleme sabit.

- **Hata ayıklayıcı:**

  - Bir sonraki deyimin ayarlanması düzeltildi.

## <a name="3604"></a>3.6.0.4

Yayınlanma Mart 5, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Mono sürüm algılaması düzeltildi.

- **Entegrasyon:**

  - 2018.1 ve eklenti etkinleştirme ile zamanlama sorunları giderildi.

## <a name="3603"></a>3.6.0.3

Yayınlanma Şubat 23, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - .NET Standard için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Birlik hedef çerçeve algılaması düzeltildi.

- **Hata ayıklayıcı:**

  - Kullanıcı kodunun dışına atılan özel durumlar üzerinde kırılma düzeltildi.

## <a name="3602"></a>3.6.0.2

Yayınlanma Şubat 7, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - 2017.3 için UnityMessage API yüzeyini güncelleştirin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Projeleri yalnızca dış değişim (azaltma ile) yeniden yükleyin.

## <a name="3601"></a>3.6.0.1

Yayınlanma Ocak 24, 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - mdb hata ayıklama sembolü dönüştürme için otomatik pdb düzeltildi.

  - Array Boyutunu değiştirmeye çalışırken denetçiyi etkileyen EditorPrefs.GetBool'a dolaylı arama düzeltildi.

## <a name="3600"></a>3.6.0.0

Yayınlanma Ocak 10, 2018

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - 2018.1 MonoIsland referans modeli için destek eklendi.

- **Değerlendirme:**

  - $exception tanımlayıcı için destek eklendi.

- **Hata ayıklayıcı:**

  - Yeni Unity çalışma süresiyle Hata Ayıklama Gizli/DebuggerStepThrough öznitelikleri için destek eklendi.

- **Sihirbaz:**

  - Sihirbazlar için 'En Son' sürümünü tanıtın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Oyuncu projeleri için proje kılavuz hesaplaması düzeltildi.

- **Hata ayıklayıcı:**

  - Kırma olayları nın ele alınmasında bir yarış düzeltildi.

- **Sihirbaz:**

  - Yöntem eklemeden önce roslyn bağlamı yenileyin.

## <a name="3503"></a>3.5.0.3

Yayınlanma Tarihi: 9 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - mdb hata ayıklama sembolü dönüştürme için otomatik pdb düzeltildi.

## <a name="3502"></a>3.5.0.2

Yayınlanma Tarihi: 4 Aralık 2017

### <a name="new-features"></a>Yeni Özellikler

- **Entegrasyon:**

  - Artık Unity'de bir betik eklediğinizde veya kaldırdığınızda Unity projeleri Visual Studio'da otomatik olarak yeniden yükleniyor.

- **Hata ayıklayıcı:**

  - Unity Editor'ı hata ayıklamak için Xamarin ve Visual Studio tarafından Paylaşılan Mono hata ayıklayıcısını Kullanma seçeneği eklendi.

  - Taşınabilir hata ayıklama simgesi dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Entegrasyon:**

  - Sabit kurulum bağımlılıkları sorunları.

  - Unity API yardım menüsü görünmüyor düzeltildi.

- **Proje Oluşturma:**

  - IL2CPP/.NET 4.6 arka uç ile bir UWP oyunu üzerinde çalışırken oyuncu proje oluşturma sabit.

  - Montaj dosya adına yanlış eklenen ekstra .dll uzantısı düzeltildi.

  - Genel proje yerine belirli bir proje API uyumluluk düzeyinin sabit kullanımı.

  - Varsayılan artık 'true' olduğu için AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="3402"></a>3.4.0.2

Yayınlanma 19 Eylül 2017

### <a name="new-features"></a>Yeni Özellikler

- **Proje Oluşturma:**

  - assembly.json derleme birimleri için destek eklendi.

  - Unity derlemelerini proje klasörüne kopyalamayı durdurdu.

- **Hata ayıklayıcı:**

  - Yeni Unity çalışma zamanı ile bir sonraki deyimin ayarlanması için destek eklendi.

  - Yeni Unity çalışma süresiyle ondalık yazı için destek eklendi.

  - Örtülü/açık dönüşümler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - Örtülü boyutta dizi oluşturma düzeltildi.

  - Yerel öğelerle oluşturulan derleyici düzeltildi.

- **Proje Oluşturma:**

  - 4,6 API düzeyi için Microsoft.CSharp'a başvuru düzeltildi.

## <a name="3302"></a>3.3.0.2

Yayınlanma 15 Ağustos 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Unity 5.5 ve önceki sürümlerinde Visual Studio çözüm oluşturma düzeltildi.

## <a name="3300"></a>3.3.0.0

Yayınlanma 14 Ağustos 2017

### <a name="new-features"></a>Yeni Özellikler

- **Değerlendirme:**

  - Yeni Unity çalışma süresiyle yapı oluşturma desteği eklendi.

  - İşaretçiler için minimalist destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirme:**

  - İlkellerüzerinde sabit yöntem çağırma.

  - BeforeFieldInit ile işaretlenmiş türleri ile sabit alan değerlendirmesi.

  - İkili işleçlerle desteklenmeyen çağrılar (çıkarma) düzeltildi.

  - Visual Studio Watch'a öğe eklerken sorunlar giderildi.

- **Proje Oluşturma:**

  - Mcs.rsp dosyaları ile sabit montaj adı başvuruları.

  - Sabit API düzeyleri ile tanımlar.

## <a name="3200"></a>3.2.0.0

Yayınlanma Mayıs 10, 2017

### <a name="new-features"></a>Yeni Özellikler

- **Yükleyici:**

  - MEF önbelleğini temizlemek için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Özel özniteliklerle sabit sınıflandırma/tamamlama.

  - Unity iletileriyle titreme düzeltildi.

## <a name="3100"></a>3.1.0.0

Yayınlanma Nisan 7, 2017

### <a name="new-features"></a>Yeni Özellikler

- **Hata ayıklayıcı:**

  - Yeni Unity çalışma süresi için destek eklendi (.NET 4.6 / C# 6 uyumluluğu ile).

- **Proje Oluşturma:**

  - .NET 4.6 profili için destek eklendi.

  - mcs.rsp dosyaları için destek eklendi.

  - Unity 5.6 kullanıldığında her zaman güvenli olmayan derleme anahtarını etkinleştirin.

  - Windows Mağazası platform ve il2cpp arka uç kullanırken "Player" proje oluşturma desteği eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Otomatik tamamlama ile yöntem ekledikten sonra sabit caret konumu.

- **Proje Oluşturma:**

  - İşlem sonrası derleme sürümü kaldırıldı.

## <a name="3001"></a>3.0.0.1

Yayınlanma 7 Mart 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Bu sürüm, 2.8.x serisi ile tanıtılan tüm yeni özellikleri ve hata düzeltmelerini içerir.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 Önizleme 3
Yayınlanma Ocak 25, 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje Oluşturma:**

  - Plugins'in iki kez başvurulduğu, önce ikili DLL sonra da proje başvurusu olarak çalıştığı regresyon düzeltildi.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 Önizleme 2
Yayınlanma Ocak 23, 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Kod Düzenleyicisi:**

  - Ayraç tamamlanmadan bir öznitelik bildirimi başlatırken bir kilitlenme giderildi.

- **Hata ayıklayıcı:**

  - Yeni Unity derleyicisi/çalışma süresi altında ortak yordamlarla sabit işlev kesme noktaları.

  - Binitilemeyen bir kesme noktası olması durumunda uyarı eklendi (karşılık gelen kaynak konumu bulunamamışsa).

- **Proje Oluşturma:**

  - Özel/lokalize karakterlerle csproj üretimi düzeltildi.

  - Kitaplık (Facebook SDK gibi) gibi Varlıkların dışındaki sabit başvurular.

- **Misc:**

  - Yüklerken veya yüklerken Unity'nin çalışmasını önlemek için denetim eklendi.

  - Uzaktan Birlik belgelerini hedeflemek için https'ye geçildi.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 Önizleme
Yayınlanma Kasım 17, 2016

### <a name="new-features"></a>Yeni Özellikler

- **Genel:**

  - Visual Studio 2017 yükleyici desteği eklendi.

  - Visual Studio 2017 uzantı desteği eklendi.

  - Yerelleştirme desteği eklendi.

- **Kod Düzenleyicisi:**

  - Unity iletileri için C# IntelliSense eklendi.

  - Unity iletileri için C# kodu renklendirmesi eklendi.

- **Hata ayıklayıcı:**

  - , , `is` `as`doğrudan döküm, `default` `new` ifadeler için destek eklendi.

  - String concat ifadeleri için destek eklendi.

  - Tamsayı değerlerinin hexadecimal görüntülenmesi için destek eklendi.

  - Yeni geçici değişkenler (deyimler) oluşturmak için destek eklendi.

  - Örtük ilkel dönüşümler için destek eklendi.

  - Bir tür beklendiğinde veya bulunmadığında daha iyi hata iletileri eklendi.

- **Proje Oluşturma:**

  - CSharp soneki proje adlarından kaldırıldı.

  - Sistem genelinde msbuild hedefleri dosyasına başvuru kaldırıldı.

- **Sihirbaz:**

  - Düzenleyici veya EditorWindow gibi Davranış olmayan türlerde Birlik iletileri için destek eklendi.

  - Unity iletilerini enjekte etmek ve biçimlendirmek için Roslyn'e geçti.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Hata ayıklayıcı:**

  - Genel türleri değerlendirirken Birleşme' yi çükleyen bir hata düzeltildi.

  - Nullable türlerinin sabit işleme.

  - Enumların sabit kullanımı.

  - İç içe geçmemiş üye türlerinin sabit işlemesi.

  - Sabit toplama dizinleyici erişimi.

  - Yeni C# derleyicisi ile hata ayıklama çerçeveleri için sabit destek.

- **Proje Oluşturma:**

  - Unity Web oynatıcısını hedef alırken derlemeyi engelleyen hata düzeltildi.

  - Web kodlanmış bir dosya adı içeren bir komut dosyası derlenirken derlemeyi engelleyen hata düzeltildi.

## <a name="2300"></a>2.3.0.0

Yayınlanma 14 Temmuz 2016

### <a name="new-features"></a>Yeni Özellikler

- **Genel:**

  - Visual Studio'nun hata listesinde Unity konsol günlüklerini devre dışı etme seçeneği eklendi.

  - Oluşturulan proje özelliklerinin değiştirilmesine izin vermek için bir seçenek eklendi.

- **Hata ayıklayıcı:**

  - Metin, XML, HTML ve JSON dize görselleştiricileri eklendi.

- **Sihirbaz:**

  - Eksik MonoBehaviors eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Genel:**

  - Visual Studio ayarlarının içindeki denetimlerin görüntülenmesini engelleyen ReSharper ile çakışma düzeltildi.

  - Bazı durumlarda hata ayıklama engelledi Xamarin ile bir çakışma düzeltildi.

- **Hata ayıklayıcı:**

  - Hata ayıklama yaparken Visual Studio'nun donmasına neden olan bir sorun giderildi.

  - Visual Studio 2015'te işlev kesme noktalarıyla ilgili bir sorun giderildi.

  - Birkaç ifade değerlendirme sorunu düzeltildi.

## <a name="2200"></a>2.2.0.0

Yayınlanma Şubat 4, 2016

### <a name="new-features"></a>Yeni Özellikler

- **Sihirbaz:**

  - **MonoBehavior Uygula** sihirbazında akıllı arama eklendi.

  - Sihirbazlar bağlamı farkında yaptı; örneğin, NetworkBehavior iletileri yalnızca Bir Ağ Davranışı ile çalışırken kullanılabilir.

  - Sihirbazlarda NetworkBehavior iletileri için destek eklendi.

- **Uı:**

  - MonoBehavior iletilerinin görünürlüğünü yapılandırma seçeneği eklendi.

  - Unity projeleri ile ilgili olmayan Visual Studio özellik sayfaları kaldırıldı.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Unity 4.6'da UnityEngine ve UnityEditor'a yapılan başvurular düzeltildi.

  - Unity OSX'te çalışırken proje dosyalarının üretimi düzeltildi.

  - Hashmark (#) karakterleri içeren proje adlarının sabit işleme.

  - Oluşturulan projeleri C# 4 ile sınırlandırır.

- **Hata ayıklayıcı:**

  - Bir Unity coroutine içinde hata ayıklama ifade değerlendirme ile ilgili bir sorun giderildi.

  - Hata ayıklama yaparken Visual Studio'nun donmasına neden olan bir sorun giderildi.

- **Uı:**

  - [Sekler Studio](https://tabsstudio.com/) Visual Studio uzantısı ile uyumsuzluk giderildi.

- **Yükleyici:**

  - HKLM kayıt defteri girişleri oluşturarak VSTU'nun makine çapında kurulumunu (tüm kullanıcılar için yükleme) destekleyin.

  - VsTU'nun aynı sürümü Visual Studio'nun birden çok farklı sürümü için yüklendiğinde VSTU'nun yüklenmemesiyle ilgili sorunlar giderildi. Örneğin, VSTU **2015** 2.1.0.0 ve VSTU **2013** 2.1.0.0 her ikisi de kuruldu.

## <a name="2100"></a>2.1.0.0

Yayınlanma Eylül 8, 2015

### <a name="new-features"></a>Yeni Özellikler

- Birlik Desteği 5.2

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Menü öğelerini Unity < 4.2'de görüntüleme

- Visual Studio XML intellisense dosyalarını kilitlediğinde artık bir hata iletisi görüntülenmez.

- Koşullu \<bağımsız değişken boolean değeri olmadığında, koşullu>> değiştirilen <.

- Windows Mağazası uygulamaları için UnityEngine ve UnityEditor derlemelerine yapılan başvurular düzeltildi.

- Hata ayıklama da adım atıldığında hata düzeltildi: Adım atamayan genel özel durum.

- Visual Studio 2015'te isabet sayısı kesme noktaları düzeltildi.

## <a name="2000"></a>2.0.0.0

Yayınlanma 20 Temmuz 2015

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Birlik Entegrasyonu:**

  - Bir DLL ve hata ayıklama sembollerini (PDB) içe aktarırken Visual Studio 2015 ile oluşturulan hata ayıklama sembollerinin dönüştürülmesi düzeltildi.

  - Bir MDB dosyası da sağlandığı durumlar dışında, bir DLL ve hata ayıklama sembollerini (PDB) içe aktarırken her zaman MDB dosyaları oluşturun.

  - Bir obj dizini ile Birlik proje dizininin sabit kirliliği.

  - System.Xml.Link ve System.Runtime.Serialization başvurularısabit nesil.

  - Proje dosyası oluşturma API kancalarına birden fazla abone için destek eklendi.

  - Oluşturulacak dosyalardan biri kilitlendiğinde bile her zaman proje dosyası oluşturmayı tamamlayın.

  - C# projesine eklenecek dosyaları belirtirken uzantı filtresine * joker karakterler için destek eklendi.

- **Visual Studio entegrasyonu:**

  - Verimlilik Güç Araçları ile uyumluluk sorunu giderildi.

  - Olaylar ve temsilci bildirimleri etrafında MonoBehaviors üreten sabit.

- **Hata ayıklayıcı:**

  - Hata ayıklama yaparken olası bir donma düzeltildi.

  - Yerel lerin belirli yığın çerçevelerinde görüntülenmeyecek bir sorun giderildi.

  - Boş dizileri denetleme düzeltildi.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 Önizleme 2
Yayınlanma Nisan 2, 2015

### <a name="new-features"></a>Yeni özellikler

- **Birlik Proje Explorer:**

  - BirleŞ Project Explorer'da bir dosyayı yeniden adlandırırken sınıfı otomatik olarak yeniden adlandırın **(Bkz. Seçenekler** iletişim kutusu).

  - Unity Project Explorer'da yeni oluşturulan komut dosyalarını otomatik olarak seçin.

  - Birlik Projesi Gezgini'ndeki etkin komut dosyasını izleyin **(Bkz. Seçenekler** iletişim kutusu).

  - Visual Studio Solution Explorer'ı çift eşitleyin **(Seçenekler** iletişim kutusuna bakın).

  - Unity Project Explorer'da Visual Studio simgelerini benimseyin.

- **Hata ayıklayıcı:**

  - Kaydedilmiş veya en son kullanılan hata ayıklama hedefleri listesinden etkin hata ayıklama hedefini seçin **(Bkz. Seçenekler** iletişim kutusu).

  - MonoBehavior yöntemlerinde işlev kesme noktaları oluşturun ve bunları birden çok MonoBehavior sınıfına uygulayın.

  - Destek Hata ayıklamada Nesne Kimliği Yap.

  - Hata ayıklamadaki destek kesme noktası isabet sayısı.

  - Hata ayıklamada (Deneysel) özel durum çığırtmama desteği. Seçenekler **Options** İletişim kutusuna bakın).

  - Hata ayıklamadaki ifadeleri değerlendirirken nesnelerin ve dizilerin oluşturulmasını destekleyin.

  - Hata ayıklamadaki değerlendirme ifadeleri zaman null karşılaştırmasını destekleyin.

  - Hata ayıklama saat pencerelerinde eski üyeleri filtreleyin.

- **Yükleyici:**

  - Birlik uzantısı kaydı için Optimize Edilmiş Visual Studio Araçları.

  - Unity 5 için Unity paketi için Visual Studio Araçları yükleyin.

- **Dokümantasyon:** Dokümantasyon oluşturma performansını artırın.

- **Sihirbazlar:** Unity 4.6 ve Unity 5 için yeni MonoBehavior yöntemlerini destekleyin.

- **Birlik:** Arama güvenli olmayan bayraklar ve özel tanımlar .rsp dosyaları proje dosyası oluşturma sırasında.

- **UI:** Visual Studio'da Birlik **Seçenekleri** için Visual Studio Araçları iletişim kutusu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Birlik Proje Explorer:**

  - Dosyalar Taşındıktan veya Visual Studio Solution Explorer'dan yeniden adlandırıldıktan sonra Unity Project Explorer'ı yenileyin.

  - Birbirle Project Explorer'daki dosyaları yeniden adlandırırken seçimleri koruyun.

  - Unity Project Explorer'da dosyalar çift tıklandığında otomatik olarak genişletmeyi ve daraltmalarını önleyin.

  - Yeni seçilen dosyaların Unity Project Explorer'da görünür olduğundan emin olun.

- **Hata ayıklayıcı:**

  - Hata ayıklamadaki ifadeleri değerlendirirken olası bir Visual Studio donmasını önleyin.

  - Yöntem çağrılarının hata ayıklamadaki uygun etki alanında gerçekleştiğinden emin olun.

- **Birlik:**

  - UnityVS.OpenFile'ın konumunu Unity 5 ile düzeltin.

  - Unity 5 ile pdb2mdb'nin yerini düzeltin.

  - Proje dosyası oluşturma sırasında olası bir özel durumu önleyin.

  - OSX'te Unity çalıştırırken olası bir donma masını önleyin.

  - İç özel durumları ele alın.

  - Unity konsol günlüklerini VS hata listesine gönderin.

- **Dokümantasyon:** Yeni birlik belgeleri için doğru belge oluşturma.

- **Proje:** Gerektiğinde klasörlerde bile Unity .meta dosyalarını taşıyın ve yeniden adlandırın.

- **Sihirbazlar:** Kod oluştururken MonoBehavior yöntem parametrelerinin sırasını düzeltin.

- **UI:** Bağlam menüsü ve simgeler için Visual Studio temalarını destekleyin.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 Önizleme
Yayınlanma Kasım 12, 2014

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2015 desteği.

- Visual Studio 2015'te Unity shaders için Kod Renklendirmesi.

- Hata ayıklama yaparken değerlerin geliştirilmiş görselleştirmesi:

  - ArrayLists, Listeler, Karma Tablolar ve Sözlükler için daha iyi görselleştirme.

  - Genel Olmayan üyeleri ve Statik üyeleri saat ve yerel görünümlerde kategoriler olarak gösterin.

  - Yalnızca özellik için geçerli olan değer alanını değerlendirmek için Unity's SerializedProperty'in geliştirilmiş görüntüsü.

  - Sınıflar ve structs için DebuggerDisplayAttribute desteği.

  - DebuggerTypeProxyAttribute desteği.

- Kullanıcı kodlama kurallarına saygı göstermek için sihirbazlarımızı kullanarak MonoBehaviour yöntemlerinin eklenmesini yapın.

- UnityVS oluşturulan projelerde Zaman Metin Şablonlarını Derle için destek uygulayın.

- UnityVS oluşturulan projelerde ResX kaynakları için destek uygulayın.

- Unity'den Visual Studio'da shaders'ı destekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Attach and Play'den sonra Unity oyununda oyuna başlamadan önce yuvaları temizleme, Visual Studio'da tetiklendi. Bu, Ekle ve Oynat'ı kullanırken Unity ve VS arasındaki bağlantının kararlılığıyla ilgili bazı sorunları giderir.

- Unity'nin komut dosyası altyapısı hata ayıklama arabiriminde, Unity'yi dondurmaya meyilli arama yöntemlerinden kaçının. Bu, hata ayıklamayı eklerken Birlik dondurmasını düzeltir.

- Sembol yoksa çağrı yığınlarının görüntülenmesini düzeltin.

- Gerekirse günlük geri aramasını kaydetmeyin.

## <a name="1920"></a>1.9.2.0

Yayınlanma Tarihi: 9 Ekim 2014

### <a name="new-features"></a>Yeni özellikler

- Unity oyuncularının algılanmasını geliştirin.

- Dosya açacağımızı kullanırken, Unity'nin dosya adının yanı sıra satır numarasını da geçmesini sağlar.

- Yerel belge yoksa çevrimiçi Unity belgelerine varsayılan olarak.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Etki alanı yeniden yükledikten sonra bir kesme noktasına çarptığında olası Unity çökmesini düzeltin.

- Bir etki alanı yeniden yükledikten sonra Yapılandırmamızı veya Windows Hakkında'mızı kapatırken Unity konsolunda gösterilen özel durumları düzeltin.

- Yerel olarak çalışan 64bitUnity algılamadüzeltin.

- Sihirbazlarda Unity sürümü başına MonoBehaviours filtreleme düzeltme.

- Uzantı filtresi boşsa, tüm varlıkların proje dosyalarına dahil edildiği hatayı düzeltin.

## <a name="1910"></a>1.9.1.0

Yayınlanma Eylül 22, 2014

### <a name="new-features"></a>Yeni özellikler

- Bağlama kesme noktasını kaynak konumlara en iyi duruma getirin.

- Hata ayıklamanın İfade Değerlendirmesinde aşırı yüklenen yöntemlerin desteği.

- Hata ayıklamanın İfade Değerlendirmesinde ilkelve değer türlerinin kutulatını destekleme.

- Anonim yöntemlerin hata ayıklanmasında C# yerel değişkenler ortamını yeniden oluşturmayı destekleyin.

- Visual Studio'daki dosyaları silerken veya yeniden adlandırırken .meta dosyalarını silin ve yeniden adlandırın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio temalarının işlenmesini düzeltin. Daha önce, siyah temalar üzerinde iletişim boş görünebilir.

- Unity yeniden derlenirken hata ayıklamayı bağlarken Unity dondur'u düzeltin.

- Uzaktan editörleri veya başka bir sistemde derlenen oyuncuları hata ayıklarken kesme noktalarını düzeltin.

- Bir kesme noktası vurulduğunda olası bir Visual Studio çökmesini düzeltin.

- Boş olarak gösterilen kesme noktalarını önlemek için kesme noktalarını bağlamayı düzeltin.

- Kapsam dışında görünen canlı değişkenleri önlemek için hata ayıklamadaki değişken kapsamın işlenmesini düzeltin.

- Hata ayıklamanın İfade Değerlendirmesinde statik üyelerin aramasını düzeltin.

- Statik alanları ve özellikleri göstermek için hata ayıklamanın İfade Değerlendirmesi'ndeki türlerin görüntülenmesini düzeltin.

- Unity proje adları Visual Studio'nun yasakladığı özel karakterler içeriyorsa çözüm oluşturmayı düzeltin (Bağlantı sorunu #948666).

- Seçenek işaretlendikten sonra konsol etkinliklerini göndermeyi derhal durdurmak için Visual Studio Tools Unity paketini düzeltin (Bağlantı sorunu #933357).

- UnityVS oluşturulan projelerde UnityEngine.UI gibi yeni API'lere yapılan başvuruların doğru şekilde yeniden oluşturulmasına yapılan başvuruların algılanması düzeltin.

- Bozuk yüklemeleri önlemek için Visual Studio'nun yüklemeden önce kapatılmasını gerektirecek şekilde yükleyiciyi düzeltin.

- VsTU'nun tüm sürümleri arasında paylaşılan uygun bağımsız bir bileşen olarak Birlik Başvuru Derlemelerini yüklemek için yükleyiciyi düzeltin.

- Unity'nin 64 bit sürümlerinde VSTU ile açılış komut dosyalarını düzeltin.

## <a name="1900"></a>1.9.0.0

Yayınlanma Temmuz 29, 2014

### <a name="new-features"></a>Yeni özellikler

- Unity Debugger Ekle penceresinde, hata ayıklamak için özel bir IP ve bağlantı noktası girme özelliğini ekleyin.

- Arka planda çalışacak veya çalışmamak için Birlik'i ayarlamak için yapılandırma seçeneği ekleyin.

- Yalnızca çözüm oluşturmak ve dosyaları veya proje dosyalarını yansıtmak için yapılandırma seçeneği ekleyin.

- Başlangıç hedefi: Birliğe Ekle'yi seçin veya Birlik ve Oynat'a ekleyi seçin.

- Hata ayıklamada çok boyutlu dizilerin görüntülenmesi.

- Yeni Unity Player hata ayıklama bağlantı noktalarını ele alın.

- Unity'nin 4.6 GUI derlemeleri gibi yeni Birlik derlemelerine atıfta bulunulmasını tamamla.

- Hata ayıklama yaparken yerel değişkenleri düzgün bir şekilde görüntülemek için kapatmaları deconstructs.

- Deconstructs hata ayıklama bağımsız değişkenler içine yineleme değişkenleri oluşturdu.

- Proje yeniden yükledikten sonra Birlik Projesi Gezgini'nin durumunu koruyun.

- Birbirle Project Explorer'ı geçerli belgeyle eşitlemek için bir komut ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hata ayıklayıcıya başlamadan önce koşulları ayarlanan koşullu kesme noktalarını düzeltin.

- Uyarılardan kaçınmak için UnityEngine'e yapılan başvuruları düzeltin.

- Unity betaları için ayrıştma sürümlerini düzeltin.

- Kesme noktasına veya adımatmaya bastığında yerel değişkenler penceresinde değişkenlerin görünmediği sorunu düzeltin.

- Visual Studio 2013'te değişkenleri düzeltin araç ipuçları.

- Unity 4.5 için IntelliSense belgelerinin neslini düzeltin.

- Bir etki alanı yeniden yükledikten sonra Unity / Visual Studio iletişimini düzeltin (Unity'de oyna/durdurun).

- Visual Studio temalarının bölümlerinin işlenmesini düzeltin.

> [!IMPORTANT]
> C# Birlik ekosisteminde baskın dil olmak - yeni Örnek Varlıklar C# bulunmaktadır, Birlik belgeleri C# varsayılan olacak - C# deneyimine daha iyi odaklanmak için UnityScript ve Boo için temel desteğimizi kaldırdık. Sonuç olarak, VSTU çözümleri artık sadece C# ve yüklenmesi çok daha hızlıdır.

## <a name="1820"></a>1.8.2.0

Yayınlanma Ocak 7, 2014

### <a name="new-features"></a>Yeni özellikler

- Editörlerin uzaktan keşfi için Unity'nin Komut Dosyası altyapısının Mavericks'teki ağ katmanındaki bir sorunu çözmeyi çalışın.

- Uzaktan Unity oyuncularını keşfetmek için yeni bağlantı noktalarını işleyebilir.

- Geçerli yapı hedefine özgü UnityEngine tertibatına başvurun.

- Oluşturulan projelere eklemek için dosyaları filtrelemek için ayar ekleyin.

- Visual Studio hata listesine konsol günlüklerini göndermeyi devre dışı katmak için ayar ekleyin. Bu, Konsol günlüklerini almak için Unity'de kayıtlı yalnızca bir geri arama olabileceğinden PlayMaker veya Console Pro kullanıyorsanız kullanışlıdır.

- MDB hata ayıklama sembollerinin oluşumunu devre dışı katmak için ayar ekleyin. Bu, mdb'yi kendiniz üretiyorsanız yararlıdır.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity >= 4.2'den VS'de açılan dosyalar IntelliSense'i kaybedince bir gerilemeyi düzeltin.

- Özel temaları işlemek için VS iletişim formlarımızı düzeltin.

- UPE'nin bağlam menüsünü kapatmayı düzeltin.

- Eşitlenmemişse, sürüme özgü oluşturulan derleme de Unity'de çökmesini önleyin.

## <a name="1810"></a>1.8.1.0

Yayınlanma Kasım 21, 2013

### <a name="new-features"></a>Yeni özellikler

- Unity 4.3 API'leri ile MonoBehaviour sihirbazları ayarlandı.

- MonoBehaviour sihirbazları, kullandığınız sürüme bağlı olarak Unity API'leri filtreler.

- Unity > 4.1 projelerine System.Xml.Linq'e referans ekleyin.

- İletiye yığın izinin başlangıcını eklememek için Debug.Log çağrılarımızı prettify.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio'daki JavaScript dosyalarının varsayılan olarak işlenmesine müdahale edebileceğimiz bir hata düzeltildi.

- Bu sefer vs'de görünen beyaz bir piksel düzeltildi.

- Yalnızca Bir SCM tarafından okunan olarak işaretlenmişse UnityVS.VersionSpecific derlemesinin silinmesi düzeltildi.

- UnityVS paketinde soket oluştururken özel durumlar düzeltildi.

- Visual Studio montajlarından stok görüntüleri yüklerken Visual Studio'da bir çökme giderildi.

- Unity'nin kaynak yapılaşması için UnityVS.VersionSpecific'in oluşumundaki bir hata düzeltildi.

- Unity paketinde bir soket açarken olası bir donma düzeltildi.

- Unity projesinin kendi adlarına bir tire (-) ile işlenmesi düzeltildi.

- Unity 4.2 ve üzeri için ALT+TAB sırasını karıştırmamak için Unity komut dosyaları düzeltildi.

## <a name="1800"></a>1.8.0.0

Yayınlanma Eylül 24, 2013

### <a name="new-features"></a>Yeni özellikler

- Büyük ölçüde geliştirilmiş hata ayıklama bağlantı hızı.

- Unity 4.2 ve üzeri dosya ve satıra gezinmeyi otomatik olarak işleyebilir.

- Koşullu kesme noktaları.

- Proje dosya oluşturucusu artık T4 şablonlarını işler.

- MonBehavior sihirbazlarını yeni API'lerle güncelleştirin.

- Unity türleri için C# intelliSense belgeleri.

- Aritmetik ve mantıksal ifadeler değerlendirme.

- Uzaktan hata ayıklama önizlemesi için uzak düzenleyicilerin daha iyi keşfi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hata ayıklamaişlemini kestikten sonra VS'de bir iş parçacığı sızdırabileceğimiz bir hata düzeltildi.

- VS'de görünen beyaz bir piksel düzeltildi.

- Durum çubuğu simgesindeki tıklamaların işlenmesi düzeltildi.

- Eklentiler klasörlerinde derlemeler ile başvuru ların üretimi düzeltildi.

- Özel durumlar durumunda UnityVS paketinden soketlerin oluşturulması düzeltildi.

- UnityVS'nin yeni sürümlerinin algılanması düzeltildi.

- Lisansın süresi dolduğunda lisans yöneticisinin istemleri düzeltildi.

- İşlem listesini ekle hata ayıklamada boş hale getirebilecek bir hata DÜZELTILDI VS'nin işlem penceresi.

- Yerel görünümde Booleans'ın değişen değerleri düzeltildi.

## <a name="1220"></a>1.2.2.0

Yayınlanma Temmuz 9, 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- İfade değerlendiricisinde tam nitelikli adları ele alın.

- Unity komut dosyası altyapısının bize yanlış yığın çerçevesi verileri gönderdiği özel durum işlemeyle ilgili bir donma düzeltildi.

- Web hedefleri için düzeltilen yapı işlemi.

- Visual Studio başlatıldığında ve silinen bir dosyanın başlangıçta açılacak dosyalar listesinde olması durumunda ortaya çıkan bir hata düzeltildi.

- Derlenmiş gölgeleyiciler gibi komut dosyası olmayan dosyaları işlemek için UnityVS.OpenFile düzeltildi.

- Şimdi tüm C# projelerinden Boo.Lang ve UnityScript.Lang referans.

- Projeözel karakterlere sahipse projelerdeki başvuruların sabit üretimi.

- Elden çıkarılan projelere yapılan yöntem çağrılarının birden çok NullReferenceException MessageBox'ı tetiklediği bir VS sorunu yla geçici çözüm.

- Unity 4.2 Beta derlemelerinin sabit kullanımı.

## <a name="1210"></a>1.2.1.0

Yayınlanma Nisan 9, 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- IO hatası durumunda kod tamamlanması için Unity derlemelerinin yerel dağıtımı düzeltildi (salt okunur dosyalar veya Visual Studio tarafından kilitlenmiş dosyalar gibi).

- Visual Studio'da zaten açılmışsa, Unity'den bir komut dosyasının açılmasının dosyaya odaklanmayacağı bir gerileme düzeltildi.

- Yeni özel durum işlemenin düzeltildi performans sorunu.

- Bazı harici DL'lerde kesme noktalarının bağlanması düzeltildi.

## <a name="1200"></a>1.2.0.0

Yayınlanma Mart 25, 2013

### <a name="new-features"></a>Yeni özellikler

- Büyük ölçüde geliştirilmiş hata ayıklama bağlantı hızı.

- Daha büyük projeler için Optimize Edilmiş Birlik Proje Gezgini.

- İşlenmemiş özel durumlarüzerinde Visual Studio ayarlarını kırmak (veya bozmamak) için Visual Studio ayarlarını onurlandırın.

- Yerel değişkenler üzerinde ToString aramak için Visual Studio ayarı onur.

- Unity oyuncularını hata ayıklamak için kullanabileceğiniz unity hata ayıklama > yeni menü hata ayıklama ekleyin.

- Çözüm dosyası oluşturma da UnityVS çözümüne eklenen özel projeleri koruyun.

- Unity işlevi veya üyenin unity belgelerini caret konumunda görüntülemek için ctrl+ALT+M -> CTRL+H'ye yeni klavye kısayolu ekleyin.

- Visual Studio'dan derleyici yanıt dosyalarını (rsp) hesaba katın.

- Deconstruct derleyici, jeneratör yöntemlerini hata ayıklarken değişkenleri göstermek için türleri oluşturdu.

- Paylaşılan bir klasörü Unity olarak yapılandırma gereksinimini kaldırarak uzaktan hata ayıklamayı basitleştirin. Artık Windows'tan Unity projenize erişmeniz gerekiyor.

- Standart bir .net hedef profili olarak özel bir Unity profili yükleyin. Bu, ReSharper'ın gösterebileceği tüm yanlış pozitif leri düzeltir.

- Bir Unity komut dosyası komut dosyası altyapısı hatası etrafında çalışın, böylece hata ayıklama düzgün kayıtlı olmayan iş parçacığı kırılmaz.

- Dosya açık isteği üzerinde çökmesini yaparken, dosyaları açabildiğini iddia ettiği VS'de bir yarış koşulundan kaçınmak için dosya açıcıyı yeniden çalışın.

- UnityVS şimdi VS proje yi oluştururken yapıyı yenilemek istiyor ve artık dosya kaydetmede değil.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özel .net profilimiz düzeltildi

- Temalı tümleştirme düzeltildi, bu VS 2012 karanlık tema ile sorunlarımızı giderir.

- VS 2012'de hızlı davranış kısayolu düzeltildi.

- Hata ayıklama ve ana olmayan bir iş parçacığı bir kesme noktasına çarptığında meydana gelebilecek bir atlama sorunu düzeltildi.

- Int gibi tür takma adlarının UnityScript ve Boo tamamlanması düzeltildi.

- Yeni bir UnityScript veya Boo dizesi yazarken özel durum düzeltildi.

- Çözüm yüklenmediğinde Birlik menülerinde özel durumlar düzeltildi.

- Hata UVS-48 sabit: çift teklif yazarak bazen hata üretmek ve tüm işlevi (kod tamamlama, sözdizimi vurgulamak vb) kırmak.

- Hata UVS-46 sabit: Visual Studio Hata Listesi'ne tıkladığınızda yinelenen açılan komut dosyası dosyası dosyası (UnityScript).

- Hata UVS-42 sabit: Durum çubuğundaki unity bağlantı logosu VS 2012'deki fare olaylarını işlemez.

- Sabit hata UVS-44: CTRL+SHIFT+Q, Hızlı MonoBehaviours için VS 2012'de kullanılamaz.

- Hata UVS-40: Unity Project Explorer'da seçilen öğeler, PENCERE VS2012 "karanlık" temasında etkin olmadığında okunamaz.

- Hata UVS-39 sabit: Sorun tokenizing kaçan dizeleri.

- Hata UVS-35 sabit: Değişkenleri incelerken nesneler üzerinde ToString çağırın.

- Hata UVS-27 sabit: VS2012 "karanlık" tema ile Goto Symbol pencere tutarsızlığı.

- Hata UVS-11 sabit: Coroutines yerliler.

## <a name="1100---beta-release"></a>1.1.0.0 - Beta sürümü
Yayınlanma Mart 9, 2013

## <a name="10130"></a>1.0.13.0
Yayınlanma Ocak 21, 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hedef hata ayıklama geçersiz iş parçacığı olayları gönderiyorsa gerçekleşebilecek bir Visual Studio kilitlemesi düzeltildi. Bu genellikle OSX uzak bir Birlik hata ayıklama olur.

- Bir özel durum hata ayıklamayı kapatırsa gerçekleşebilecek bir Visual Studio kilidi düzeltildi.

- Bir C# MonoBehavior ad alanında olduğunda MonoBehavior yardımcılarımız düzeltildi.

- Visual Studio 2012'de UnityScript için hata ayıklama araç ipuçları düzeltildi.

- Yalnızca hata ayıklama sabitleri Unity'den değiştirildiğinde proje oluşturma düzeltildi.

- Unity Project Explorer'da klavye gezintisi düzeltildi.

- Kaçan dizeleri için UnityScript renklendirmesi düzeltildi.

- Unity dışında kullanıldığında proje adını daha iyi tahmin etmek için dosya açAcağımızı düzeltildi. Bu, kullanıcı UnityVS'ye temsilci veren Unity'de üçüncü bir parça dosya açAcağı kullandığında gereklidir.

- Unity'den UnityVS'ye gönderilen uzun iletilerin sabit kullanımı. Bundan önce, uzun mesajlar UnityVS bizim mesajlaşma parçası çökmesine olabilir. Sonuç olarak, bazen UnityVS Unity'den bir dosya açmaz.

## <a name="10120"></a>1.0.12.0
Yayınlanma Ocak 3, 2013

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio bir kesme noktasını serken meydana gelebilecek Visual Studio kilitlemesi düzeltildi.

- Unity oyun komut dosyalarını yeniden derledikten sonra bazı kesme noktalarının isabet edilmeyeceğini zedilen bir hata düzeltildi.

- Kesme noktaları bağlanmamışken Visual Studio'yu düzgün bir şekilde bildirmek için hata ayıklayıcı düzeltildi.

- Visual Studio hata ayıklamanın yerel programları hata ayıklamasını engelleyebilecek bir kayıt sorunu düzeltildi.

- UnityScript ve Boo ifadelerini değerlendirirken olabilecek bir özel durum düzeltildi.

- Unity'deki .net API düzeyini değiştirmenin proje dosyalarının güncelliğini tetiklemeyeceğinin bir gerileme düzeltildi.

- Kullanıcı kodunun günlük geri arama işleyicisi katılamadı bir API hatası düzeltildi.

## <a name="10110"></a>1.0.11.0
Yayınlanma Kasım 28, 2012

### <a name="new-features"></a>Yeni özellikler

- Birlik 4'ün resmi desteği.

- Unity Project Explorer'dan komut dosyalarının manipülasyonu.

- Visual Studio'nun Gezinme penceresine entegrasyon.

- Bilgi konsolu iletisinin ayrışması, böylece Hata Listesi'nde tıklatma sembolleri ile ilk yığın çerçevesine götürür.

- Kullanıcının proje oluşturma çalışmalarına katılmasını sağlamak için bir [API](../cross-platform/customize-project-files-created-by-vstu.md) ekleyin.

- Kullanıcının LogCallback'e katılmasını sağlamak için bir [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 2012'deki Unity Project Explorer'ın arka planında gerileme düzeltildi.

- Tam .net profili kullanıcıları için sabit proje oluşturma.

- Web hedefi kullanıcıları için sabit proje oluşturma.

- Unity gibi HATA VE TRACE derleme sembollerini içerecek şekilde proje oluşturma sabitlenmiştir.

- Goto Symbol penceremizde özel karakterler kullanılırken kilitlenme düzeltildi.

- Visual Studio'nun durum çubuğuna simgemizi enjekte edemezsek kaza düzeltildi.

## <a name="10100"></a>1.0.10.0
Yayınlanma Tarihi: 9 Ekim 2012

### <a name="bug-fixes"></a>Hata Düzeltmeleri

- Visual Studio 2010'daki Unity Project Explorer'ın arka planı düzeltildi.

- UnityVS hata ayıklama daha önce çöktü bir Unity için hata ayıklama eklemeye çalışırsa meydana gelebilecek bir Visual Studio dondurma düzeltildi.

- Bir kesme noktası ayarlandığında ve AppDomain yeniden yüklemesi meydana geldiğinde gerçekleşebilecek bir Visual Studio dondurması düzeltildi.

- Dosyaları kilitlememek ve Unity yapı işlemini karıştırmak için derlemelerin Unity'den nasıl alındığı düzeltildi.

## <a name="1090"></a>1.0.9.0

Yayınlanma Ekim 3, 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity projesi gerçek JavaScript varlıklarını içerdiğinde proje oluşturma sabitlenir.

- İfade değerlendirmesinde hata işleme düzeltildi.

- Değer türleri alanlarına yeni değerler ayarı düzeltildi.

- Kod düzenleyicisinin ifadelerinin üzerinde gezinirken olası yan etkiler düzeltildi.

- İfade değerlendirmesi için yüklü derlemelerde türlerin nasıl arandığı düzeltildi.

- Hata UVS-21 sabit: Unity nesneleri üzerinde atama değerlendirilmesi hiçbir etkisi yoktur.

- Hata UVS-21 sabit: Unity Math API için bir yöntem çağırma değerlendirirken geçersiz işaretçi.

## <a name="1080"></a>1.0.8.0

Yayınlanma Eylül 26, 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hem Visual Studio'yu hem de senaryoları açabilmek için senaryo açıcımızın projeye giden yolu edindiği yol düzeltildi.

- Hata ayıklama oturumu çalışırken oluşturulan kesme noktalarıyla görsel stüdyonun kilitlenmesine neden olabilecek bir hata düzeltildi.

- UnityVS'nin Visual Studio 2010'da nasıl kaydolduğu düzeltildi.

## <a name="1070"></a>1.0.7.0

Yayınlanma Eylül 14, 2012

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2012 desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Düzenleyici ve Eklentilerin sabit nesli, Unity'nin davranışıyla eşleşecek şekilde dosyaları yansıtTı.

- Unity 4'teki .pdb sembollerinin çevirisi düzeltildi.

> [!IMPORTANT]
> Visual Studio 2012 desteği nedeniyle, birkaç dosyayı yeniden adlandırmak ve başka bir dosyayı taşımak zorunda kaldık. UnityVS paketi birlik almak için şimdi ya UnityVS 2010 veya UnityVS 2012, sırasıyla Visual Studio 2010 ve Visual Studio 2012 için adlandırılır. Bu sürüm, UnityVS proje dosyalarının yeniden oluşturulmasını da gerektirir.

## <a name="1060---internal-build"></a>1.0.6.0 - Dahili yapı
Yayınlanma Eylül 12, 2012

## <a name="1050"></a>1.0.5.0

Yayınlanma Eylül 10, 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Komut dosyaları veya gölgeli geçersiz bir xml karakteri olduğunda proje dosyalarının sabit nesil.

- Unity, Varlık sunucusuna bağlandığında Birlik örneklerinin sabit algılanması. Bu, Unity'den gelen dosyaların açılmasında başarısızlığa ve Visual Studio hata ayıkıcısının otomatik bağlantısını tetikledi.

## <a name="1040"></a>1.0.4.0

Yayınlanma Eylül 5, 2012

### <a name="new-features"></a>Yeni özellikler

- Unity'de hata ayıklama sembollerinin otomatik olarak dönüştürülmesi.

    Varlık klasörünüzde ilişkili .pdb ile bir .NET .dll derlemeniz varsa, derlemeyi yeniden içe aktarmanız ve UnityVS .pdb'yi Unity'nin komut dosyası oluşturma motorunun anladığı hata ayıklama sembolleri dosyasına dönüştürür ve .NET derlemelerinize UnityVS.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- UnityVS'nin çökmesi, Unity içindeki yöntemler veya özellikler tarafından atılan özel durumlar nedeniyle hata ayıklama sırasında kilitlenir.

## <a name="1030"></a>1.0.3.0

Yayınlanma Eylül 4, 2012

### <a name="new-features"></a>Yeni özellikler

- Unity'den dosyaları açmak için UnityVS kullanımını devre dışı kalınan yeni yapılandırma seçeneği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Editör olmayan projeler için UnityEditor'a yapılan başvuruların sabit nesli.

- Editör olmayan projeler için UNITY_EDITOR sembolünün sabit tanımı.

- Özel durum çubuğumuzun neden olduğu rastgele VS çökmesi düzeltildi.

## <a name="1020"></a>1.0.2.0

Yayınlanma Ağustos 30, 2012

### <a name="bug-fixes"></a>Hata düzeltmeleri

- PythonTools hata ayıklayıcısı ile çakışma düzeltildi.

- Mono.Cecil'e yapılan başvurular düzeltildi.

- Komut dosyası derlemelerinin Unity with Unity 4 b7'den nasıl alındığı nasıI hata düzeltildi.

## <a name="1010"></a>1.0.1.0

Yayınlanma Ağustos 28, 2012

### <a name="new-features"></a>Yeni özellikler

- Unity 4.0 Beta için önizleme desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özel durumlar atan özelliklerin denetimi düzeltildi.

- Nesneleri incelerken temel nesnelere inme düzeltildi.

- MonoBehavior sihirbazındaki ekleme noktası için boş açılır liste düzeltildi.

- UnityScript ve Boo için Varlık klasöründe dll için sabit tamamlama.

## <a name="1000---initial-release"></a>1.0.0.0 - İlk sürüm
Yayınlanma Ağustos 22, 2012
