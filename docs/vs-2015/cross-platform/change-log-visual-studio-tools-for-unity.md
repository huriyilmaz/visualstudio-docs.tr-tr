---
title: Değişiklik günlüğü (Unity için Visual Studio Araçları) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 751faa1d81ca93fce5f8dfa866327cc8787e27ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825965"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Değişiklik Günlüğü (Unity için Visual Studio Araçları)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Unity için Visual Studio Araçları değişiklik günlüğü.

## <a name="23"></a>2.3

Yayınlanan 2016-07-14

### <a name="new-features"></a>Yeni Özellikler

- **Genel**

  - Visual Studio 'nun hata listesindeki Unity konsol günlüklerini devre dışı bırakma seçeneği eklendi.

  - Oluşturulan proje özelliklerinin değiştirilmesine izin veren bir seçenek eklendi.

- **Sý**

  - Metin, XML, HTML ve JSON dize Görselleştiriciler eklendi.

- **'Nı**

  - Eksik Monodavranışlar eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Genel**

  - Visual Studio ayarlarının içindeki denetimlerin görüntülenmesini önleyen ReSharper ile bir çakışma düzeltildi.

  - Bazı durumlarda hata ayıklamayı önleyen Xamarin ile bir çakışma düzeltildi.

- **Sý**

  - Hata ayıklarken Visual Studio 'Nun dondurmasına neden olan bir sorun düzeltildi.

  - Visual Studio 2015 ' de işlev kesme noktaları ile ilgili bir sorun düzeltildi.

  - Birkaç ifade değerlendirme sorunu düzeltildi.

## <a name="22"></a>2.2

Yayınlanan 2016-02-04

### <a name="new-features"></a>Yeni Özellikler

- **'Nı**

  - **Tek davranış uygulama** sihirbazına akıllı arama eklendi.

  - Sihirbazlar bağlamı uyumlu hale getirilir; Örneğin, NetworkBehavior iletileri yalnızca bir NetworkBehavior ile çalışırken kullanılabilir.

  - Sihirbazlardaki NetworkBehavior iletileri için destek eklendi.

- **'SıNı**

  - Tek davranış iletilerinin görünürlüğünü yapılandırmak için bir seçenek eklenmiştir.

  - Unity projelerine yeniden yol açan Visual Studio özellik sayfaları kaldırıldı.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Proje oluşturma:**

  - Unity 4,6 ' de UnityEngine ve UnityEditor 'a yönelik sabit başvurular.

  - Unity, OSX üzerinde çalışırken proje dosyalarının sabit üretimi düzeltildi.

  - Diyez işareti (#) karakteri içeren proje adlarının sabit işlenmesi.

  - Kısıtlanmış oluşturulan projeler C# 4 ' e.

- **Sý**

  - Unity eş içinde hata ayıklanırken ifade değerlendirmesiyle ilgili bir sorun düzeltildi.

  - Hata ayıklarken Visual Studio 'Nun dondurmasına neden olan bir sorun düzeltildi.

- **'SıNı**

  - [Sekmeler Studio](https://tabsstudio.com/) Visual Studio uzantısıyla uyumsuzluk düzeltildi.

- **Yükleyicinin**

  - HKLM Kayıt defteri girişleri oluşturarak, bir VSTU (tüm kullanıcılar için yükleme) makine genelinde yüklemesini destekler.

  - Aynı VSTU sürümü Visual Studio 'nun birden çok farklı sürümüne yüklendiğinde, VSTU 'nin kaldırılmasıyla ilgili sorunlar düzeltildi. Örneğin, VSTU **2015** 2.1.0.0 ve vstu **2013** 2.1.0.0 her ikisi de yüklüyse.

## <a name="21"></a>2.1

Yayınlanan 2015-09-08

### <a name="new-features"></a>Yeni Özellikler

- Unity 5,2 için destek

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity < 4,2 ' de menü öğelerini görüntüle

- Visual Studio XML IntelliSense dosyalarını kilitlediğinde bir hata iletisi artık görüntülenmez.

- \<When Changed>Koşullu bağımsız değişken bir Boole değeri olmadığında, koşullu kesme noktaları> <tanıtıcısı.

- Windows Mağazası uygulamaları için UnityEngine ve UnityEditor Derlemeleriyle ilgili sabit başvurular.

- Hata ayıklayıcıda adımla düzeltilen hata: adım, genel özel durum.

- Visual Studio 2015 ' de sabit isabet sayısı kesme noktaları.

## <a name="20"></a>2.0

Yayınlanan 2015-07-20

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity tümleştirmesi:**

  - DLL ve hata ayıklama sembolleri (PDB) içeri aktarılırken Visual Studio 2015 ile oluşturulan hata ayıklama simgelerinin dönüştürülmesi düzeltildi.

  - Bir MDB dosyası da sağlanmasının dışında, bir DLL ve hata ayıklama sembolleri (PDB) içeri aktarırken her zaman MDB dosyaları oluştur.

  - Bir obj diziniyle Unity proje dizininin sabit bir şekilde kirmi düzeltildi.

  - System.Xml başvuruların sabit üretimi. LINK ve System. Runtime. Serialization.

  - Proje dosyası oluşturma API kancalarına birden çok abone desteği eklendi.

  - Oluşturulacak dosyalardan biri kilitlendiğinde bile proje dosya oluşturmayı her zaman doldurun.

  - C# projesine dahil edilecek dosyaları belirtirken uzantı filtresinde * joker karakterleri için destek eklendi.

- **Visual Studio tümleştirmesi:**

  - Üretkenlik güç araçlarıyla bir uyumluluk sorunu düzeltildi.

  - Olaylar ve temsilciler bildirimlerinin etrafında Monodavranışlar üretme düzeltildi.

- **Sý**

  - Hata ayıklanırken olası dondurma düzeltildi.

  - Belirli yığın çerçevelerinde Yerellerden görüntülenmeyen bir sorun düzeltildi.

  - Boş dizileri inceliyor düzeltildi.

## <a name="20-preview-2"></a>2,0 Preview 2
Yayınlanan 2015-04-02

### <a name="new-features"></a>Yeni özellikler

- **Unity Proje Gezgini:**

  - Unity proje Gezgininde bir dosyayı yeniden adlandırırken otomatik olarak sınıfı yeniden adlandır (bkz. **Seçenekler** iletişim kutusu).

  - Unity proje Gezgininde yeni oluşturulan betikleri otomatik olarak seçin.

  - Unity proje Gezgininde etkin betiği izleyin (bkz. **Seçenekler** iletişim kutusu).

  - Visual Studio Çözüm Gezgini ikili olarak eşitler (bkz. **Seçenekler** iletişim kutusu).

  - Unity proje Gezgininde Visual Studio simgelerini benimseyin.

- **Sý**

  - Kaydedilmiş veya son kullanılan hata ayıklama hedefleri listesinden etkin hata ayıklama hedefini seçin (bkz. **Seçenekler** iletişim kutusu).

  - Tek davranış yöntemlerinde işlev kesme noktaları oluşturun ve bunları birden çok MonoBehavior sınıfına uygulayın.

  - Hata ayıklayıcıda nesne KIMLIĞI oluşturma desteği.

  - Hata ayıklayıcıda destek kesme noktası isabet sayısı.

  - Hata ayıklayıcıda kesme özel durumunu destekle (deneysel. Bkz. **Seçenekler** iletişim kutusu).

  - Hata ayıklayıcıda ifadeler değerlendirilirken nesne ve dizi oluşturulmasını destekler.

  - Hata ayıklayıcıda değerlendirme ifadeleri olduğunda null karşılaştırmayı destekler.

  - Hata ayıklayıcı 'da eski üyeleri filtrele Windows izleme.

- **Yükleyicinin**

  - En iyi duruma getirilmiş Unity için Visual Studio Araçları uzantısı kaydı.

  - Unity 5 için Unity için Visual Studio Araçları paketini yükler.

- **Belgeler:** Belge oluşturma performansını geliştirir.

- **Sihirbazlar:** Unity 4,6 ve Unity 5 için yeni MonoBehavior yöntemlerini destekler.

- **Unity:** Proje dosyası oluşturma sırasında. rsp dosyalarında güvenli olmayan bayraklar ve özel tanımlar arama yapın.

- **Kullanıcı arabirimi:** Visual Studio 'da Unity için Visual Studio Araçları **seçenekleri** iletişim kutusu eklendi.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- **Unity Proje Gezgini:**

  - Dosyalar taşındıktan veya Visual Studio Çözüm Gezgini yeniden adlandırıldıktan sonra Unity proje Gezginini yenileyin.

  - Unity proje Gezgininde dosyaları yeniden adlandırırken seçimleri koru.

  - Unity proje Gezgininde dosyalar çift tıklandığında otomatik genişletmeyi önleyin ve daraltın.

  - Yeni seçilen dosyaların Unity proje Gezgininde göründüğünden emin olun.

- **Sý**

  - Hata ayıklayıcıda ifadeler değerlendirilirken olası bir Visual Studio donmasını önleyin.

  - Yöntem etkinleştirmeleri hata ayıklayıcıda doğru etki alanında gerçekleşdiğinden emin olun.

- **'Yi**

  - UnityVS. OpenFile konumunu Unity 5 ile düzeltin.

  - Pdb2mdb konumunu Unity 5 ile düzeltin.

  - Proje dosyası oluşturma sırasında olası bir özel durumu önleyin.

  - OSX üzerinde Unity çalıştırırken olası dondurma önleme.

  - İç özel durumları işleyin.

  - Unity konsol günlüklerini VS hata listesine gönderin.

- **Belgeler:** Yeni Unity belgeleri için doğru belge oluşturma.

- **Proje:** Gerektiğinde de Unity. meta dosyalarını taşıyın ve yeniden adlandırın.

- **Sihirbazlar:** Kod oluştururken MonoBehavior yöntem parametrelerinin sırasını düzeltin.

- **Kullanıcı arabirimi:** Bağlam menüsü ve simgeler için Visual Studio temalarını destekleme.

## <a name="20-preview"></a>2,0 Önizleme
Yayınlanan 2014-11-12

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2015 için destek.

- Visual Studio 2015 ' de Unity gölgelendiriciler için kod renklendirme.

- Hata ayıklama sırasında değerlerin görselleştirilmesi geliştirildi:

  - ArrayLists, listeler, hashtables ve sözlükler için daha iyi görselleştirme.

  - Genel olmayan üyeleri ve statik üyeleri, izleme ve yerel görünümlerde kategori olarak gösterin.

  - Unity 'nin SerializedProperty özelliğinin yalnızca özellik için geçerli olan değer alanını değerlendirmek için iyileştirilmiş görünümü.

  - Sınıflar ve yapılar için DebuggerDisplayAttribute desteği.

  - DebuggerTypeProxyAttribute desteği.

- Kullanıcı kodlama kurallarına göre sihirbazları kullanarak Monodavranış yöntemlerinin eklenmesini sağlayın.

- UnityVS tarafından oluşturulan projelerde derleme zamanı metin şablonları için destek uygulayın.

- UnityVS tarafından oluşturulan projelerde ResX kaynakları için destek uygulayın.

- Unity 'den Visual Studio 'da gölgelendiriciler açmayı destekler.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 'da Iliştirme ve yürütme tetiklendikten sonra Unity 'de oyunu başlatmadan önce Yuvaları Temizleme. Bu, Attach ve Play kullanılırken Unity ile VS arasındaki bağlantının kararlılığı ile ilgili bazı sorunları düzeltir.

- Unity 'nin betik altyapısı hata ayıklayıcısı arabirimindeki, Unity 'nin donmasına engel olan yöntemlerin çağrılmasını önleyin. Bu, hata ayıklayıcı eklenirken Unity dondurma 'yı düzeltir.

- Kullanılabilir sembol olmadığında çağrı yığınlarının görüntülenmesini düzeltir.

- Gerekmiyorsa, günlük geri aramayı kaydedin.

## <a name="192"></a>1.9.2

Yayınlanan 2014-10-09

### <a name="new-features"></a>Yeni özellikler

- Unity oynatıcıların algılanmasını geliştirme.

- Dosya openmizi kullanırken, Unity 'yi dosya adının yanı sıra satır numarası olarak geçirin.

- Yerel belge yoksa, çevrimiçi Unity belgeleri için varsayılan değer.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Bir etki alanı yeniden yüklendikten sonra bir kesme noktasına gelindiğinde olası Unity kilitlenmeyi düzeltir.

- Bir etki alanı yeniden yüklendikten sonra, konfigürasyonumuzu veya Windows 'u kapatırken Unity konsolunda gösterilen özel durumları düzeltir.

- Yerel olarak çalışan 64bit Unity algılama işlemini düzeltir.

- Sihirbazlardaki Unity sürümü başına MonoBehaviours filtrelemesini onarın.

- Uzantı filtresi boşsa tüm varlıkların proje dosyalarına dahil edildiği hatayı düzeltir.

## <a name="191"></a>1.9.1

Yayınlanan 2014-09-22

### <a name="new-features"></a>Yeni özellikler

- Bağlama kesme noktasını kaynak konumlarına iyileştirin.

- Hata ayıklayıcının Ifade değerlendirmesinde aşırı yüklenmiş yöntemler için destek.

- Hata ayıklayıcının Ifade değerlendirmesinde paketleme temelleri ve değer türleri için destek.

- Anonim yöntemlerde hata ayıklarken C# yerel değişkenleri ortamını yeniden oluşturmayı destekler.

- Visual Studio 'dan dosyaları silerken veya yeniden adlandırırken. meta dosyalarını silin ve yeniden adlandırın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio temalarını işlemeyi çözme. Daha önce, siyah temalardaki iletişim kutuları boş görünebilir.

- Unity yeniden derlenirken hata ayıklayıcıyı bağlarken Unity donması 'nı düzeltemedi.

- Başka bir sistemde derlenen uzak düzenleyicilerde veya yürütücülerde hata ayıklarken kesme noktalarını düzeltme.

- Kesme noktası isabet edildiğinde olası bir Visual Studio kilitlenmesine çözüm.

- Kesme noktaları bağlantısını, bellekten kaldırılmamasına engel olmak için düzeltir.

- Kapsam dışında görünen canlı değişkenlerin önüne geçmek için hata ayıklayıcıda değişken kapsamının işlenmesini düzeltir.

- Hata ayıklayıcının Ifade değerlendirmesi içindeki statik üyelerin aramasını düzeltir.

- Statik alanları ve özellikleri göstermek için hata ayıklayıcının Ifade değerlendirmesinde türlerin görüntülenmesini düzeltir.

- Unity proje adları, Visual Studio yasaklıyor (Connect sorun #948666) özel karakterler içerdiğinde çözüm üretimini düzeltir.

- Seçenek işaretlendikten sonra konsol olaylarının gönderilmesini hemen durdurmak için Visual Studio Araçları Unity paketini onarın (bağlantı verme #933357).

- UnityEngine. UI gibi yeni API 'Lerin başvurularını doğru şekilde yeniden oluşturmak için başvuruları algılamayı, UnityVS tarafından oluşturulan projelerde düzeltir.

- Yükleyici, bozulan yüklemeleri önlemek için yüklemeden önce Visual Studio 'Nun kapatılmasını gerektirecek şekilde düzeltilir.

- Unity başvuru derlemelerini, tüm VSTU sürümleri arasında paylaşılan, uygun bir bağımsız bileşen olarak yüklemek için yükleyiciyi onarın.

- Unity 'nin 64 bit sürümlerinde VSTU ile betikleri açmayı onarma.

## <a name="19"></a>1.9

Yayınlanan 2014-07-29

### <a name="new-features"></a>Yeni özellikler

- Unity hata ayıklayıcısı Ekle penceresinde, hata ayıklama için özel bir IP ve bağlantı noktası girme özelliğini ekleyin.

- Unity 'yi arka planda çalışacak şekilde ayarlamak için yapılandırma seçeneği ekleyin.

- Yalnızca çözüm ve proje dosyaları ya da proje dosyaları oluşturmak için yapılandırma seçeneği ekleyin.

- Başlangıç hedefi: Unity 'ye eklemek veya Unity 'ye eklemek ve oynatmak için seçin.

- Hata ayıklayıcıda çok boyutlu dizileri görüntüleme.

- Yeni Unity oynatıcı hata ayıklama bağlantı noktalarını işleyin.

- Unity 'nin 4,6 GUI derlemeleri gibi yeni Unity derlemelerine başvuruları işleyin.

- Hata ayıklarken yerel değişkenleri düzgün şekilde göstermek için kapanışları kaldırır.

- Hata ayıklarken oluşturulan yineleyiciler değişkenlerini bağımsız değişkenlerle kaldırır.

- Proje yeniden yüklendikten sonra Unity Proje Gezgini 'nin durumunu koru.

- Unity proje Gezginini geçerli belgeyle eşitleyecek bir komut ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Koşulu hata ayıklayıcıya başlamadan önce ayarlanan koşullu kesme noktalarını düzeltir.

- Uyarıları önlemek için UnityEngine başvurularını onarın.

- Unity betas için ayrıştırma sürümlerini onarma.

- Bir kesme noktasına veya adımlamayı vurarak değişkenlerin yerel değişkenler penceresinde gözükmesine neden olan sorunu giderme.

- Visual Studio 2013 değişkenleri araç ipuçlarını düzeltir.

- Unity 4,5 için IntelliSense belgelerinin oluşturulmasını düzeltir.

- Bir etki alanı yeniden yüklendikten sonra Unity/Visual Studio iletişimini onarın (Unity 'de Oynat/Durdur).

- Visual Studio temalarının parçalarını işlemeyi çözme.

> [!IMPORTANT]
> C#, Unity ekosisteminde önceden baskın bir dil olmasını sağlar. yeni örnek varlıklar C# ' ta, Unity belgelerinin varsayılan değeri C# ' dir; C# deneyimine daha iyi odaklanmak için, Unityscrıpt ve Boo 'nun temel desteğini kaldırdık. Sonuç olarak, VSTU çözümleri artık C# ' dir ve yükleme için çok daha hızlıdır.

## <a name="182"></a>1.8.2

Yayınlanan 2014-01-07

### <a name="new-features"></a>Yeni özellikler

- , Düzenleyicilerin uzaktan keşfi için Mavericks adresindeki Ağ katmanında bir sorunu geçici olarak çözmek.

- Uzak Unity oynatıcılarını keşfetmeye yönelik yeni bağlantı noktalarını işleyin.

- Geçerli derleme hedefine özel UnityEngine derlemesine başvur.

- Oluşturulan projelere dahil edilecek dosyaları filtrelemek için ayar ekleyin.

- Konsol günlüklerinin Visual Studio hata listesine gönderilmesini devre dışı bırakmak için ayar ekleyin. Konsol günlüklerini almak için Unity 'de kayıtlı yalnızca bir geri çağırma işlemi olduğu için, PlayMaker veya Console Pro kullanıyorsanız bu faydalıdır.

- MDB hata ayıklama sembolleri oluşturmayı devre dışı bırakmak için ayar ekleyin. Bu, mdb 'yi kendiniz oluşturuyorsanız yararlı olur.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity 'den VS >= 4,2 ' de açılan dosyalar IntelliSense 'i kaybedecektir.

- Özel temaları işlemek için VS iletişim kutusumuzu düzeltir.

- UPE öğesinin bağlam menüsünü kapatmayı düzeltir.

- Sürüme özgü oluşturulan derleme eşitleme dışı olduğunda Unity 'de kilitlenmeyi önleyin.

## <a name="181"></a>1.8.1

Yayınlanan 2013-11-21

### <a name="new-features"></a>Yeni özellikler

- Unity 4,3 API 'Leri ile Monodavranış sihirbazları ayarlandı.

- Tek davranış sihirbazları, kullandığınız sürüme bağlı olarak Unity API 'Larını filtrelemedir.

- System.Xml bir başvuru ekleyin. Unity > 4,1 için projelere LINQ.

- İletiye StackTrace 'in başlangıcını dahil etmek için hata ayıklama. log çağrılarımızın önmizi yapın.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 'da JavaScript dosyalarının varsayılan işlemesini etkileyebilecek bir hata düzeltildi.

- Bu kez, gerçek zamanlı olarak VS. olarak görünen beyaz bir piksel düzeltildi.

- Bir SCM tarafından ReadOnly olarak işaretlenmişse UnityVS. VersionSpecific derlemesini silme işlemi düzeltildi.

- UnityVS paketinde yuva oluşturulurken oluşan özel durumlar düzeltildi.

- Visual Studio derlemelerinden hisse senedi görüntüleri yüklenirken Visual Studio 'da kilitlenme düzeltildi.

- Unity 'nin kaynak yapıları için UnityVS. VersionSpecific 'ın oluşturulmasında hata düzeltildi.

- Unity paketinde bir yuva açılırken olası bir dondurma düzeltildi.

- Unity projesinin adında bir tire (-) ile işlenmesi düzeltildi.

- Unity 'de betikler 4,2 ve üzeri için ALT + sekme sırasını karıştırmayın.

## <a name="180"></a>1.8.0

Yayınlanan 2013-09-24

### <a name="new-features"></a>Yeni özellikler

- Büyük ölçüde geliştirilmiş hata ayıklayıcı bağlantı hızı.

- Unity 4,2 ve üzeri üzerine dosya ve satıra gezintiyi otomatik olarak işler.

- Koşullu kesme noktaları.

- Proje dosya üreticisi artık T4 şablonlarını işler.

- Yeni API 'lerle MonBehavior sihirbazları ' nı güncelleştirin.

- Unity türleri Için C# ' de IntelliSense belgeleri.

- Aritmetik ve mantıksal ifadeler değerlendirmesi.

- Uzaktan hata ayıklama önizlemesi için uzak düzenleyicilerin daha iyi bulunması.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hata ayıklayıcının bağlantısını kestikten sonra VS 'deki bir iş parçacığını sızdığımız bir hata düzeltildi.

- VS 'de görünen beyaz piksel düzeltildi.

- Durum çubuğu simgesinde tıklamaların işlenmesi düzeltildi.

- Eklentiler klasörlerinde Derlemelerle başvuruların üretimi düzeltildi.

- Özel durumlar söz konusu olduğunda UnityVS paketinden yuvaların oluşturulması düzeltildi.

- Yeni bir UnityVS sürümünün algılanması düzeltildi.

- Lisansın süre dolduğunda Lisans Yöneticisi istemi düzeltildi.

- VS 'nin işlem hata ayıklayıcısına karşılık gelen işlem listesini içeren bir hata düzeltildi.

- Yerel görünümde Boole değerleri değiştirme değeri düzeltildi.

## <a name="122"></a>1.2.2

Yayınlanan 2013-07-09

### <a name="bug-fixes"></a>Hata düzeltmeleri

- İfade değerlendirici içinde tam nitelikli adları işleyin.

- Unity betik altyapısının yanlış StackFrame verileri gönderdiği özel durum işlemeyle ilgili bir dondurma düzeltildi.

- Web hedefleri için düzeltilen derleme işlemi.

- Visual Studio başlatıldığında ve silinen bir dosyanın başlangıçta açılacak dosya listesinde olması durumunda oluşabilecek bir hata düzeltildi.

- Derlenmiş gölgelendiriciler gibi betik olmayan dosyaları işlemek için fixed UnityVS. OpenFile.

- Şimdi tüm C# projelerinden Boo. lang ve UnityScript. lang başvurduk.

- Projede özel karakterler varsa, projelerdeki başvuruların sabit üretimi.

- Geçici çözüm, yöntemin atılmış projelere çağrı yaptığı bir VS sorunu, birden çok NullReferenceException MessageBox tetikleyecektir.

- Unity 4,2 Beta derlemelerinin sabit işlenmesi.

## <a name="121"></a>1.2.1

Yayınlanan 2013-04-09

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Bir GÇ hatası (salt okuma dosyaları veya Visual Studio tarafından kilitlenen dosyalar gibi) durumunda kod tamamlama için Unity derlemelerinin sabit yerel dağıtımı.

- Unity 'den bir betik açmak, Visual Studio 'da zaten açılırsa dosyayı odaklanmaz.

- Yeni özel durum işlemenin sabit performans sorunu.

- Bazı dış dll 'lerde kesme noktalarının sabit bağlaması.

## <a name="12"></a>1.2

Yayınlanan 2013-03-25

### <a name="new-features"></a>Yeni özellikler

- Büyük ölçüde geliştirilmiş hata ayıklayıcı bağlantı hızı.

- Daha büyük projeler için iyileştirilmiş Unity Proje Gezgini.

- İşlenmiş ve işlenmemiş özel durumların üzerine kesmek (veya not etmek) için Visual Studio ayarlarını dikkate alır.

- Yerel değişkenlerde ToString çağrısı yapmak için Visual Studio ayarını dikkate alır.

- Yeni menü hata ayıklama-> Unity oynatıcısında hata ayıklamak için kullanabileceğiniz Unity hata ayıklayıcısı ekleyin.

- Çözüm dosyası oluşturma sırasında UnityVS çözümüne eklenen özel projeleri koruma.

- Yeni klavye kısayolu Ekle CTRL + ALT + M->, CTRL + H tuşlarına basarak Unity işlevine veya üyesine yönelik Unity belgelerini giriş işareti konumunda görüntüleyin.

- Visual Studio 'dan derlerken derleyici yanıt dosyalarını (rsp) hesaba alın.

- Oluşturucu metotlarında hata ayıklama sırasında değişkenleri göstermek için derleyicinin ürettiği türler kaldırılıyor.

- Paylaşılan bir klasörü Unity 'ye yapılandırma gereksinimini kaldırarak uzaktan hata ayıklamayı kolaylaştırın. Artık yalnızca Windows 'da Unity projenize erişiminizin olması gerekir.

- Özel bir Unity profilini standart .net hedef profili olarak yükler. Bu, ReSharper tarafından gösterebilecek tüm hatalı pozitif durumları düzeltir.

- Bir Unity betik altyapısı hatasına geçici olarak çalışın, bu nedenle hata ayıklayıcı düzgün şekilde kaydedilmemiş iş parçacıklarında kesintiye uğramaz.

- Dosya açma isteği üzerinde kilitlenme sırasında dosyaları açmak için gereken yerde bir yarış durumu oluşmasını önlemek için dosyayı Opener 'da yeniden çalışın.

- UnityVS, artık projeyi oluştururken ve artık dosya Kaydet 'de değil derlemeyi yenilemeyi istiyor.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özel .net profiliniz düzeltildi

- Tema tümleştirmesi düzeltildi, bu, VS 2012 koyu temasıyla ilgili sorunlarımızı düzeltir.

- VS 2012 ' de sabit hızlı davranış kısayolu.

- Hata ayıklama ve ana olmayan iş parçacığı bir kesme noktasına isabet edildiğinde oluşabilecek bir Adımlama sorunu düzeltildi.

- İnt gibi tür diğer adların sabit Unityscrıpt ve Boo 'un tamamlanması.

- Yeni bir UnityScript veya Boo dizesi yazılırken düzeltilen özel durum.

- Bir çözüm yüklenmediği zaman Unity menülerindeki özel durumlar düzeltildi.

- Düzeltilen hata UVS-48: çift tırnak yazıldığında bazen hata oluşur ve tüm işlev kesilir (kod tamamlama, sözdizimi vurgusu vb.).

- Düzeltilen hata UVS-46: Visual Studio 'nun Hata Listesi tıklandığında yinelenen açık betik dosyası (UnityScript).

- Düzeltilen hata UVS-42: durum çubuğundaki Unity bağlantı logosu, VS 2012 ' de fare olaylarını işlemez.

- Sabit hata UVS-44: CTRL + SHIFT + Q, VS 2012 ' de hızlı MonoBehaviours için kullanılamaz.

- Düzeltilen hata UVS-40: Unity proje Gezgininde seçili öğeler, VS2012 "koyu" teması içinde pencere etkin olmadığında okunamaz.

- Düzeltilen hata UVS-39: atlanan dizeleri simgeleştirirken sorun.

- Düzeltilen hata UVS-35: değişkenleri incelerken nesnelerde ToString çağrısı yapın.

- Düzeltilen hata UVS-27: VS2012 içinde "koyu" temayla sembol penceresine git.

- Sabit hata UVS-11: eş öğelerdeki Yereller.

## <a name="11--beta-release"></a>1,1 – Beta sürümü
Yayınlanan 2014-10-09

## <a name="1013"></a>1.0.13
Yayınlanan 2013-01-21

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Hedef hata ayıklananın geçersiz iş parçacığı olayları göndermesi durumunda oluşabilecek bir Visual Studio kilitleniyor düzeltildi. Bu, genellikle OSX üzerinde Uzak Unity hata ayıklaması yapılırken meydana gelir.

- Bir özel durum hata ayıklayıcıyı kapdığı takdirde oluşabilecek bir Visual Studio kilitleniyor düzeltildi.

- C# MonoBehavior bir ad alanında olduğunda MonoBehavior yardımcılarımız düzeltildi.

- Visual Studio 2012 ' de Unityscrıpt için düzeltilen hata ayıklayıcı araç ipuçları.

- Unity 'den yalnızca hata ayıklama sabitleri değiştirildiğinde düzeltilen proje oluşturma.

- Unity proje Gezgininde sabit klavye gezintisi.

- Atlanan dizeler için kod renklendirme düzeltildi.

- Unity dışında kullanıldığında proje adını daha iyi tahmin etmek için dosya Openme düzeltildi. Bu, Kullanıcı Unity 'de UnityVS 'ye temsilci olarak üçüncü bir bölüm dosyası kullandığında gereklidir.

- Unity 'den UnityVS 'e gönderilen uzun mesajların sabit işlenmesi. Bundan önce, uzun iletiler ileti alımızın bir parçası olan mesajlaşma bölümünü çökebilir. Sonuç olarak, bazen Unity 'den bir dosya açılmaz.

## <a name="1012"></a>1.0.12
Yayınlanan 2013-01-03

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio bir kesme noktasını sildiğinde oluşabilecek sabit Visual Studio kilitleniyor.

- Unity 'nin oyun betiklerini yeniden derlendikten sonra bazı kesme noktaları isabet ettirilmeyen bir hata düzeltildi.

- Kesme noktaları ilişkisiz olduğunda Visual Studio 'Yu düzgün şekilde bilgilendirmek için hata ayıklayıcı düzeltildi.

- Visual Studio hata ayıklayıcının yerel programlarda hata ayıklamasına engel olabilecek bir kayıt sorunu düzeltildi.

- UnityScript ve Boo ifadeleri değerlendirilirken oluşabilecek bir özel durum düzeltildi.

- Unity 'de .NET API düzeyinin değiştirilmesinin proje dosyalarının güncelleştirilmesini tetikleyemediğinde bir gerileme düzeltildi.

- Kullanıcı kodunun günlük geri çağırma işleyicisine katılabileceği bir API hatası düzeltildi.

## <a name="1011"></a>1.0.11
Yayınlanan 2012-11-28

### <a name="new-features"></a>Yeni özellikler

- Unity 4 için resmi destek.

- Unity Proje Gezgini 'nden betikleri düzenleme.

- Visual Studio 'da tümleştirme, pencereye git.

- Bilgi konsolu iletisini ayrıştırma, Hata Listesi tıklamak, simgeleri olan ilk StackFrame 'e götürür.

- Kullanıcının proje üretimine katılmasını sağlamak için bir [API](../cross-platform/customize-project-files-created-by-vstu.md) ekleyin.

- Kullanıcının LogCallback 'a katılmasını sağlamak için bir [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) ekleyin.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Visual Studio 2012 ' de Unity Proje Gezgini 'nin arka planında düzeltilen gerileme.

- Tam .net profilinin kullanıcıları için sabit proje üretimi.

- Web hedefinin kullanıcıları için sabit proje üretimi.

- Unity olarak hata ayıklama ve Izleme derleme sembolleri dahil olmak üzere sabit proje üretimi.

- Goto symbol penceremizdeki özel karakterler kullanılırken oluşan kilitlenme düzeltildi.

- Visual Studio 'nun durum çubuğunda simgemizi ekleyeemiz için çökme düzeltildi.

## <a name="1010"></a>1.0.10
Yayınlanan 2012-10-09

### <a name="bug-fixes"></a>Hata Düzeltmeleri

- Visual Studio 2010 ' de Unity Proje Gezgini 'nin arka planı düzeltildi.

- Hata ayıklayıcı arabirimi daha önce kilitlenen bir Unity 'ye hata ayıklayıcı eklemesi denenirse bir Visual Studio donması düzeltildi.

- Bir kesme noktası ayarlandığında ve bir AppDomain yeniden yüklemesi gerçekleştiğinde ortaya çıkabilecek bir Visual Studio donması düzeltildi.

- Dosyaları kilitlemenin ve Unity oluşturma işleminin karışmasını önlemek için derlemelerin Unity 'den nasıl alındığı düzeltildi.

## <a name="109"></a>1.0.9

Yayınlanan 2012-10-03

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity projesi gerçek JavaScript varlıklarını içerdiğinde, sabit proje üretimi.

- İfade değerlendirmesinde düzeltilen hata işleme.

- Değer türlerinin alanlarına yeni değerleri ayarlama düzeltildi.

- Kod düzenleyicisinden ifadelerin üzerine gelindiğinde olası yan etkiler düzeltildi.

- İfade değerlendirmesi için yüklü derlemelerde türlerin nasıl arandığı düzeltildi.

- Düzeltilen hata UVS-21: Unity nesnelerinde atamanın değerlendirmesi etkisizdir.

- Düzeltilen hata UVS-21: Unity matematik API 'sine bir yöntem çağrısı değerlendirilirken geçersiz işaretçi.

## <a name="108"></a>1.0.8

Yayınlanan 2012-09-26

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Betiğimizin, hem Visual Studio hem de betikleri açabildiğinden emin olmak için, projenin yolunu elde ettiği şekilde düzeltildi.

- Hata ayıklama oturumu çalıştırılırken oluşturulan kesme noktalarıyla bir hata düzeltildi ve bu, Visual Studio 'Nun kilitlenmesini istiyor olabilir.

- Visual Studio 2010 ' de UnityVS 'in nasıl kaydedildiği düzeltildi.

## <a name="107"></a>1.0.7

Yayınlanan 2012-09-14

### <a name="new-features"></a>Yeni özellikler

- Visual Studio 2012 desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity 'nin davranışını eşleştirmek için, düzenleyici ve eklenti proje dosyalarının sabit üretimi.

- Unity 4 ' te. pdb sembolleri çevirisi düzeltildi.

> [!IMPORTANT]
> Visual Studio 2012 desteği nedeniyle, birkaç dosyayı yeniden adlandırdık ve başka bir süre içinde taşınacak. Unity 'yi içeri aktarmaya yönelik UnityVS paketi, sırasıyla Visual Studio 2010 ve Visual Studio 2012 için UnityVS 2010 ya da UnityVS 2012 olarak adlandırılmaktadır. Bu sürüm ayrıca, UnityVS proje dosyalarının yeniden oluşturulmasını gerektirir.

## <a name="106---internal-build"></a>1.0.6-iç derleme
Yayınlanan 2012-09-12

## <a name="105"></a>1.0.5

Yayınlanan 2012-09-10

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Betiklerin veya gölgelendiricilerin geçersiz bir XML karakteri olduğunda proje dosyalarının sabit üretimi düzeltildi.

- Unity varlık sunucusuna bağlıyken Unity örneklerinin sabit algılanması. Bu, Unity 'den dosyaları açmak ve Visual Studio hata ayıklayıcının otomatik bağlantısı için hata tetikledi.

## <a name="104"></a>1.0.4

Yayınlanan 2012-09-05

### <a name="new-features"></a>Yeni özellikler

- Unity 'de hata ayıklama sembollerini otomatik dönüştürme.

    Varlık klasörünüzde ilişkili. pdb ile bir .NET. dll derlemesi varsa, derlemeyi yeniden içeri aktarmanız yeterlidir ve UnityVS,. pdb 'yi Unity 'nin betik altyapısının anladığı bir hata ayıklama sembolleri dosyasına dönüştürür.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Unity içindeki metotlar veya özellikler tarafından oluşturulan özel durumlar nedeniyle hata ayıklamada hata ayıklama sırasında sabit Unıvs kilitlenmesi

## <a name="103"></a>1.0.3

Yayınlanan 2012-09-04

### <a name="new-features"></a>Yeni özellikler

- Unity 'den dosya açmaya yönelik UnityVS kullanımını devre dışı bırakmak için yeni yapılandırma seçeneği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Düzenleyici olmayan projeler için UnityEditor başvuruları düzeltildi.

- Düzenleyici olmayan projeler için UNITY_EDITOR sembolün sabit tanımı.

- Özel durum çubuğumuzdan kaynaklanan sabit rastgele VS kilitlenmesi.

## <a name="102"></a>1.0.2

Yayınlanan 2012-08-30

### <a name="bug-fixes"></a>Hata düzeltmeleri

- PythonTools hata ayıklayıcı ile çakışma düzeltildi.

- Mono. CECIL 'e yönelik sabit başvurular.

- Unity 4 B7 ile Unity 'den komut dosyası derlemelerinin nasıl alındığı ile ilgili hata düzeltildi.

## <a name="101"></a>1.0.1

Yayınlanan 2012-08-28

### <a name="new-features"></a>Yeni özellikler

- Unity 4,0 Beta için Önizleme desteği.

### <a name="bug-fixes"></a>Hata düzeltmeleri

- Özelliklerin özel durum atma denetimi düzeltildi.

- Nesneler incelenirken temel nesnelerde azalan şekilde düzeltildi.

- Tek davranış sihirbazında ekleme noktası için boş açılan liste.

- UnityScript ve Boo 'un varlık klasörü içindeki dll için sabit tamamlama.

## <a name="10--initial-release"></a>1,0 – ilk sürüm
Yayınlanan 2012-08-22
