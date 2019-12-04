---
title: Değişiklik günlüğü (Unity için Visual Studio Araçları, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: fe317d446ddc9196df02dfafcf0397f8815574c3
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771549"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Değişiklik Günlüğü (Unity için Visual Studio Araçları, Mac)

Unity için Visual Studio Araçları değişiklik günlüğü.

## <a name="2420"></a>2.4.2.0

Yayın 3 Aralık 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Kullanıcı tanımlı arabirimler ile sabit Tanılamalar.

  - Hatalı biçimlendirilmiş ifadelerle hızlı araç ipuçları düzeltildi.
  
## <a name="2410"></a>2.4.1.0

Yayın tarihi, 6 Kasım 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Unity arka plan işlemlerine yönelik destek eklendi. (Hata ayıklayıcı alt işlem yerine ana işleme otomatik olarak bağlanabilir).

  - Unity iletileri için ilgili belgeleri görüntüleyen bir hızlı araç ipucu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Gelişmiş ikili ve çağırma ifadeleriyle etiket karşılaştırma Çözümleyicisi `UNT0002` düzeltildi.

### <a name="deprecated-features"></a>Kullanım dışı Özellikler

- **Tümleştirme**

  - Unity için Visual Studio Araçları, yalnızca Visual Studio 2017 + desteğine sahip olur.

## <a name="2400"></a>2.4.0.0

Yayımlanma tarihi, 15 Ekim 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Tüm Unity iletileri için `IDE0060` (kullanılmamış parametre) için supprescursor eklendi.

  - `TooltipAttribute`etiketli alanlar için hızlı araç ipucu eklendi. (Bu, bu alanı kullanarak basit bir get erişimcisi için de çalışır).

## <a name="2330"></a>2.3.3.0

Yayın tarihi, 23 Eylül 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - IDE 'nin kullanılmayan parametreleri kaldırmak üzere hızlı bir çözüm göstermesini engellemek için, IDE0060 için yeni bir supprescursor eklendi.
    - `IDE0060`için `USP0005`: Unity iletileri Unity çalışma zamanı tarafından çağrılır.

## <a name="2320"></a>2.3.2.0

Yayın tarihi, 16 Eylül 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Unity 'ye özgü yeni Tanılamalar ekleyerek, Visual Studio 'nun Unity projelerine yönelik olduğunu anlama konusunu sunuyoruz. Unity projeleri için geçerli olmayan genel C# tanılamalarını gizleyerek IDE’yi daha akıllı hale getirdik. Örneğin, IDE, bir Inspector değişkenini `readonly` olarak değiştirmek için bir hızlı onarım göstermez ve bu, değişkenleri Unity düzenleyicisinde değiştirmenize engel olur.
    - `UNT0001`: Unity iletileri, boş olsalar bile çalışma zamanı tarafından çağrılır, Unity çalışma zamanına göre uncesseray işlemesini önlemek için bunları bildirmeyin.
    - `UNT0002`: dize eşitlik kullanılarak etiket karşılaştırması yerleşik CompareTag yönteminden daha yavaştır.
    - `UNT0003`: tür güvenliği için GetComponent 'un genel biçiminin kullanımı tercih edilir.
    - `UNT0004`: güncelleştirme iletisi çerçeve hızına bağımlıdır ve Time. deltaTime yerine Time. fixedDeltaTime kullanın.
    - `UNT0005`: FixedUpdate iletisi çerçeve hızına bağımsızdır ve Time. fixedDeltaTime yerine Time. deltaTime kullanmalıdır.
    - `UNT0006`: Bu Unity iletisi için yanlış bir yöntem imzası algılandı.
    - `UNT0007`: Unity, null birleştirme ile uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - `UNT0008`: Unity, null yayılmayla uyumsuz olan Unity nesneleri için null karşılaştırma işlecini geçersiz kılar.
    - `UNT0009`: bir sınıfa ınitializeonload özniteliği uygulanırken statik bir Oluşturucu sağlamanız gerekir. InitializeOnLoad özniteliği, düzenleyici başlatıldığında bunun çağrılmasını sağlar.
    - `UNT0010`: MonoBehaviours yalnızca AddComponent () kullanılarak oluşturulmalıdır. MonoBehaviour bir bileşendir ve bunun GameObject’e eklenmesi gerekir.
    - `UNT0011`: ScriptableObject yalnızca CreateInstance () kullanılarak oluşturulmalıdır. Unity ileti yöntemlerinin işlenmesi için ScriptableObject’in Unity altyapısı tarafından oluşturulması gerekir.
    - `IDE0029`için `USP0001`: Unity nesneleri null birleştirme kullanmamalıdır.
    - `IDE0031`için `USP0002`: Unity nesneleri null yayma kullanmamalıdır.
    - `IDE0051`için `USP0003`: Unity iletileri Unity çalışma zamanı tarafından çağrılır.
    - `IDE0044`için `USP0004`: SerializeField özniteliğine sahip alanlar ReadOnly yapılmamalıdır.

## <a name="2310"></a>2.3.1.0

Yayımlanma tarihi 4 Eylül 2019

### <a name="new-features"></a>Yeni özellikler

- **Değerlendirmesinin**

  - Daha iyi tür görüntüleme desteği eklendi, örn. `List'1[[System.Object, <corlib...>]]`yerine `List<object>`.

  - İşaretçi üye erişimi için destek eklendi, yani `p->data->member`.

  - Dizi başlatıcılarda örtük dönüştürmeler için destek eklendi, yani `new byte [] {1,2,3,4}`.

  - Bayt dizileri ve dizeleri incelenirken Onaltılı düzenleyici desteği eklendi.

## <a name="2300"></a>2.3.0.0

Yayın tarihi 13 Ağustos 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Özel durumlarla düzeltilen Adımlama sorunları.

  - Sözde tanımlayıcıların ($exception gibi) sabit değerlendirmesi.

  - Geçersiz adreslerin başvurusu kaldırılırken kilitlenmeyi önleyin.  

  - Kaldırılmış AppDomain 'ler ile ilgili sorun düzeltildi.

## <a name="2200"></a>2.2.0.0

Yayın tarihi, 25 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - IntPtr türleriyle düzeltilen İnceleme.

- **Sý**

  - Catch noktaları ve işlev kesme noktalarının sabit işlenmesi.

## <a name="2130"></a>2.1.3.0

Yayın tarihi, 9 Temmuz 2019

### <a name="new-features"></a>Yeni özellikler

- **Sý**

  - Özel durumların yakalamak için destek eklendi.

  - MDS Protokolü 2,51 için destek eklendi.

- **Tümleştirme**

  - Asmdef dosyaları için destek eklendi.

  - Şablondan bir dosya eklendiğinde yeniden adlandırma moduna geçin (Unity Düzenleyicisi davranışını taklit etmek için).

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity oynatıcılarla iletişim kurulurken hatalı biçimlendirilmiş iletilerin işlenmesi düzeltildi.

- **Değerlendirmesinin**

  - İfadelerde ad alanlarını sabit olarak işleme.

## <a name="2120"></a>2.1.2.0

Yayın 2 Temmuz 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Değerlendirmesinin**

  - Ayrıştırılamayan ifadelerle düzeltilen hata raporlaması.

## <a name="2110"></a>2.1.1.0

Yayın tarihi, 27 Haziran 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Monodavranış API 'SI 2019,1 olarak güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit Unity Proje Gezgini performansı.

  - Hafif derleme etkinleştirildiğinde, çıktının düzeltilme uyarıları ve hataları düzeltildi.

  - Sabit basit derleme performansı.

## <a name="2100"></a>2.1.0.0

Yayın tarihi 20 Haziran 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - IntelliSense hatalarının ve uyarılarının kullanımı açısından Unity projelerinin tam derlemesini devre dışı bıraktı. Aslında Unity, dahili olarak hangi Unity 'nin yaptığını temsil eden sınıf kitaplığı projeleri içeren bir Visual Studio çözümü oluşturur. Bu şekilde, Visual Studio 'daki derlemenin sonucu, derleme işlem hattı kapalıyken Unity tarafından hiçbir şekilde kullanılmaz veya alınmaz. Visual Studio 'da oluşturma işlemi yalnızca hiçbir şey için kaynakları tüketiyor. Kendisine bağlı araçlara veya kuruluma sahip olduğunuz için tam bir yapıya ihtiyacınız varsa, bu iyileştirmeyi devre dışı bırakabilirsiniz (Unity için ayarlar/araçlar/projelerin tam derlemesini devre dışı bırak).
  
  - UPE içinde Unity paketleri için destek eklendi. Yalnızca başvurulan paketler (`Packages` klasöründe manifest. JSON kullanılarak) ve yerel paketler (`Packages` klasörüne katıştırılmış) görünür.

## <a name="2021"></a>2.0.2.1

Yayımlanma tarihi 30 Mayıs 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Unity yürütme hedefleri için özel simge eklendi.

## <a name="2020"></a>2.0.2.0

Yayın 2 Nisan 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Kayıt sırasında Unity 'nin varlık veritabanının otomatik olarak yenilenmesi için destek eklendi. Bu, varsayılan olarak etkindir ve Visual Studio 'da bir betiği kaydederken Unity tarafında yeniden derleme tetikleyecektir. Kayıt sırasında Unity 'nin Assetveritabanını yenilemek için Tools\Options\Tools içinde bu özelliği devre dışı bırakabilirsiniz.

  - Çevrimdışı belgeler için tercih edilen Unity yüklemesinin ayarlanmasına yönelik destek eklendi.

  - Yeni düzenleyici için bağlam menüsü eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Boş çerçevelerle sabit derleme filtrelemesi ve çerçeve incelemesi.

## <a name="2011"></a>2.0.1.1
 
 Yayın tarihi 26 Mart 2019

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Yalnızca bu çok özel yayın için mono varsayılan ve yalnızca kullanılabilir hata ayıklayıcı 'yı geçici olarak yapın.

## <a name="2006"></a>2.0.0.6

Yayın tarihi 26 Mart 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - "Unity 'ye Ekle ve Yürüt" desteği eklendi.

## <a name="2005"></a>2.0.0.5

Yayımlanma tarihi, 20 Mart 2019

### <a name="new-features"></a>Yeni özellikler

- **Proje oluşturma:**

  - Çözüm dosyasını işlerken dış özellikleri koruyun.
  
- **Değerlendirmesinin**

  - Diğer ad nitelenmiş adlar için destek eklendi (şimdilik yalnızca genel ad alanı). Bu nedenle, ifade değerlendirici artık genel:: Namespace. Type biçimini kullanarak türleri kabul ediyor.

  - `pointer[index]` form için, işaretçi başvuru `*(pointer+index)` form ile özdeş olan destek eklendi.

## <a name="2004"></a>2.0.0.4

Yayımlanma tarihi, 5 Mart 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - `ScriptableObject` API 'SI güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Ad alanları şablonlardan kaldırıldı.

## <a name="2003"></a>2.0.0.3
 
 Yayımlanma tarihi, 5 Mart 2019

### <a name="new-features"></a>Yeni özellikler

- **Proje oluşturma:**

  - Ortak ve serileştirilmiş alanlar artık uyarılara neden olmaz. Bu iletileri oluşturan Unity projelerinde `CS0649` ve `IDE0051` derleyici uyarılarını otomatik olarak gizliyoruz.

- **Tümleştirme**

  - Bir Unity işlemi çalışıyorsa, belirli bir örneğe İliştirilmek için uyar.

- **Değerlendirmesinin**

  - Yerel işlevler için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Eski protokol sürümleri kullanılırken adlandırılmış bağımsız değişkenlerde özel öznitelik okuma düzeltildi.

## <a name="2002"></a>2.0.0.2

Yayımlanma tarihi 4 Şubat 2019

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Monodavranış API 'SI güncelleştirildi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Hata ayıklayıcıda temel değerler ayarı düzeltildi.

## <a name="2001"></a>2.0.0.1

Yayın tarihi 4 Aralık 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit yükleme paketi kendi kendine kapsama.

## <a name="2000"></a>2.0.0.0
 Yayın tarihi 4 Aralık 2018

### <a name="new-features"></a>Yeni özellikler

- **Sý**

  - Mac üzerindeki Unity hata ayıklayıcı, Windows 'daki aynı Core Unity hata ayıklayıcısıyla değiştirildi.

  - İfade değerlendirmesi için NRefactory 'ın Roslyn tarafından değiştirildiği yer.

  - İşaretçiler için destek eklendi: başvuru, atama ve işaretçi aritmetiği (Bu, hem Unity 2018.2 + hem de yeni çalışma zamanı için gereklidir).

  - Dizi işaretçisi görünümü (içinde C++olduğu gibi) için destek eklendi. Bir işaretçi ifadesi alın, sonra da bir virgül ve görmek istediğiniz öğe sayısını ekleyin.

  - Zaman uyumsuz yapılar için destek eklendi.

  - Sözde değişkenler (özel durum ve nesne tanımlayıcıları) için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Hatalı biçimlendirilmiş veya desteklenmeyen ifadelerle ifade değerlendirmesi düzeltildi.

## <a name="1700"></a>1.7.0.0

Yayın tarihi, 13 Kasım 2018

### <a name="new-features"></a>Yeni özellikler

- **Sý**

  - Ekleme iletişim kutusuna daha fazla istemci bilgisi (IP, makine adı) eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Sý**

  - Unity 'nin hata ayıklayıcı altyapısı ile iletişim kurmak için kullanılan kitaplıkta bir kilitlenme düzeltildi, özellikle ' Unity 'ye Ekle ' veya oyunu yeniden başlatma sırasında, Visual Studio veya Unity dondurma

- **Tümleştirme**

  - Başka bir varsayılan düzenleyici seçildiğinde, sabit Unity eklentisi etkinleştirmesi.

  - Sabit Unity dosya şablonu oluşturma.

## <a name="1602"></a>1.6.0.2

Yayın tarihi, 24 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Unity tarafından düzeltilen bir Unity performans hatası için geçici çözümü geri alındı.

## <a name="1601"></a>1.6.0.1

Yayın tarihi 10 Temmuz 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Sabit gölgelendirici kodu coloration desteği.

## <a name="1600"></a>1.6.0.0

Yayın tarihi 26 Haziran 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **'Nı**

  - OnApplicationFocus iletisi ile sabit yazım hatası.

- **Proje oluşturma:**

  - Unity performans hatası için geçici geçici çözüm: proje oluştururken Cache Monoadaları.

  - Yeni Unity çalışma zamanı kullanılırken taşınabilir pdb 'yi artık mdb 'ye dönüştürmeyin.

## <a name="1502"></a>1.5.0.2

Yayın tarihi 18 Nisan 2018

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Temel gölgelendirici kodu tamamlama desteği eklendi.

  - Gölgelendirici dosyalarında yorumların geçiş için destek eklendi.

## <a name="1501"></a>1.5.0.1

Yayın tarihi, 28 Mart 2018

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Unity proje Gezgininde ek şablonlar için destek eklendi.

## <a name="1500"></a>1.5.0.0

Yayımlanma tarihi 21 Mart 2018

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - USB üzerinden bağlı Android oyuncularını algılama ve ekleme desteği eklendi.

## <a name="1403"></a>1.4.0.3

Yayımlanma tarihi, 5 Mart 2018

### <a name="new-features"></a>Yeni özellikler

- **Proje oluşturma:**

  - Unity 2018,1 ' de yeni proje Oluşturucu desteği eklendi.

- **Tümleştirme**

  - Adanmış ayarlar için seçenek paneli eklendi.

## <a name="1402"></a>1.4.0.2

24 Ocak 2018 ' de yayınlandı

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Sabit mono sürümü algılama.

- **Tümleştirme**

  - 2018,1 ve eklenti etkinleştirme ile ilgili sabit zamanlama sorunları.

  - Yeni bir oynatıcı algılanırken uyarı düzeltildi.

## <a name="1401"></a>1.4.0.1

Yayın tarihi, 23 Ocak 2018

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Çift tıklama üzerinde klasörleri sabit Genişlet/Daralt

## <a name="1400"></a>1.4.0.0

Yayın tarihi, 13 Aralık 2017

### <a name="new-features"></a>Yeni özellikler

- **Proje oluşturma:**

  - .NET Standard için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Otomatik pdb 'den mdb hata ayıklama sembol dönüştürme.

## <a name="1301"></a>1.3.0.1

Yayın tarihi, 12 Aralık 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - EditorPrefs. GetBool öğesine yapılan dolaylı çağrı, dizi boyutunu değiştirmeye çalışırken Inspector 'ı etkiliyor.

- **'Nı**

  - Yöntemi eklemeden önce Roslyn bağlamını yenileyin.

## <a name="1300"></a>1.3.0.0

Yayımlanma tarihi, 20 Kasım 2017

### <a name="new-features"></a>Yeni özellikler

- **'Nı**

  - "Unity iletisi uygulama" Sihirbazı eklendi.

  - Mac 7,4 ' de yeni tamamlanma API 'SI için destek eklendi.

## <a name="1200"></a>1.2.0.0

Yayın tarihi, 23 Ekim 2017

### <a name="new-features"></a>Yeni özellikler

- **Sý**

  - Taşınabilir hata ayıklama sembol dosyaları için destek eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Derleme dosya adına yanlışlıkla eklenmiş ek. dll uzantısı düzeltildi.

  - Varsayılan olarak ' true ' olduğundan AllowAttachedDebuggingOfEditor Unity bayrağını zorlamayın.

## <a name="1103"></a>1.1.0.3

Yayın tarihi, 23 Ekim 2017

### <a name="new-features"></a>Yeni özellikler

- **Proje oluşturma:**

  - .NET 4,6 profili için destek eklendi.

## <a name="1102"></a>1.1.0.2

Yayın tarihi, 8 Ağustos 2017

### <a name="new-features"></a>Yeni özellikler

- **Sý**

  - Hangi Unity 'nin iliştirilemiyor olduğundan emin olmak için işleme İliştir iletişim kutusunu başlatın.

- **Proje oluşturma:**

  - Unity 5,6 kullanıldığında her zaman güvenli olmayan derleme anahtarını etkinleştirin.

## <a name="1101"></a>1.1.0.1

Yayın tarihi 20 Temmuz 2017

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - Yerelleştirilmiş kaynaklar için destek eklendi.

## <a name="1100"></a>1.1.0.0

Yayımlanma tarihi, 12 Temmuz 2017

### <a name="new-features"></a>Yeni özellikler

- **Tümleştirme**

  - İşleme Ekle penceresi aracılığıyla oyunculara ve düzenleyicilere ekleme desteği eklendi.

- **Proje oluşturma:**

  - MCS. rsp dosyalarıyla düzeltilen derleme adı başvuruları.

  - Assembly. JSON derleme birimleri için destek eklendi.

  - API düzeyleriyle düzeltilen tanımlar.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Derlerken düzeltilen gölgelendirici hata iletisi.

## <a name="1001"></a>1.0.0.1

Yayımlanma tarihi 4 Mayıs 2017

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Tümleştirme**

  - Karma ve normal projelerle sabit etkin belge izleme.

## <a name="1000"></a>1.0.0.0

Yayımlanma tarihi 3 Mayıs 2017
