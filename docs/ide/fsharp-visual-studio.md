---
title: F# araçları
description: Visual Studio'nun hangi özelliklerinin F# ile destekleniyi öğrenin.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 75ebee68bf76a4dd5419942f79a3207c29673134
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565246"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Visual Studio'da Visual F# ile geliştirin

Bu makale, F# geliştirme için Visual Studio özellikleri hakkında bilgi içerir.

## <a name="install-f-support"></a>F# desteğini yükleme

Visual Studio'da F# ile geliştirmek için önce **.NET masaüstü geliştirme** iş yükünü yükleyin. **Araçlar** > **Al Araçları ve Özellikleri**seçerek açabileceğiniz Visual Studio Installer aracılığıyla Visual Studio iş yüklerini yüklersiniz.

![.NET masaüstü geliştirme iş yükü Visual Studio'da](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F# proje özellikleri

Visual Studio'da F# için çeşitli proje ve öğe şablonları mevcuttur. Aşağıdaki resimde .NET Core ve .NET Standard için F# proje şablonlarından bazıları gösterilmektedir:

![Visual Studio'da F# proje şablonları](media/fsharp-project-templates.png)

Aşağıdaki resim, F# öğe şablonlarından bazılarını gösterir:

![Visual Studio'da F# öğe şablonları](media/fsharp-item-templates.png)

Veri erişimi için madde şablonları hakkında daha fazla bilgi için [F# türü sağlayıcılarına](/dotnet/fsharp/tutorials/type-providers/index)bakın.

Aşağıdaki tabloda F#'ın proje özellikleri özetlenebilir:

|Proje ayarı|F# ile mi desteklenir?|Notlar|
|---------------|----------------|-----|
|Kaynak dosyalar|Evet||
|Oluşturma, hata ayıklama ve başvuru ayarları|Evet||
|Çoklu Sürüm Desteği|Evet||
|Simge ve bildirim|Hayır|Derleyici komut satırı seçenekleri ile kullanılabilir.|
|ASP.NET Müşteri Hizmetleri|Hayır||
|ClickOnce|Hayır|Varsa başka bir .NET dilinde istemci proje kullanın.|
|Kesin adlandırma|Hayır|Derleyici komut satırı seçenekleri ile kullanılabilir.|
|Montaj yayımlama ve sürüm|Hayır||
|Kod analizi|Hayır|Kod çözümleme araçları el ile veya yapı sonrası komutun bir parçası olarak çalıştırılabilir.|
|Güvenlik (güven düzeylerini değiştirme)|Hayır||

## <a name="project-designer"></a>Proje Tasarımcısı

**Project Designer,** ilgili işlevselliğe göre gruplanmış birkaç proje özelliği sayfalarından oluşur. F# projeleri için kullanılabilen sayfalar çoğunlukla diğer diller için kullanılabilenlerin bir alt kümesidir ve aşağıdaki tabloda açıklanmıştır. Bağlantılar ilgili C# **Project Designer** sayfasına verilir.

|Proje Tasarımcısı sayfası|İlgili bağlantılar|Açıklama|
| - |-------------|-----------|
|Uygulama|[Uygulama Sayfası, Proje Tasarımcısı](reference/application-page-project-designer-csharp.md)|Kitaplık veya çalıştırılabilir dosya oluşturup oluşturmadığınız, .NET'in hangi sürümünün uygulama hedeflerini ve uygulamanın kullandığı kaynak dosyalarının nerede depolandığı hakkında bilgi gibi uygulama düzeyindeki ayarları ve özellikleri belirtmenizi sağlar.|
|Oluşturma|[Yapı Sayfası, Proje Tasarımcısı](reference/build-page-project-designer-csharp.md)|Kodun nasıl derlenilet edildiğini denetlemenizi sağlar.|
|Etkinlikler Oluşturun|[Etkinlik Oluşturma Sayfası, Proje Tasarımcısı](reference/build-events-page-project-designer-csharp.md)|Derlemeden önce veya sonra çalışacak komutları belirtmenizi sağlar.|
|Hata ayıklama|[Hata Ayıklama Sayfası, Proje Tasarımcısı](reference/debug-page-project-designer.md)|Hata ayıklama sırasında uygulamanın nasıl çalıştığını denetlemenizi sağlar. Buna, hangi komutların kullanılacağı ve uygulamanızın başlangıç dizininin ne olduğu ve yerel kod ve SQL gibi etkinleştirmek istediğiniz özel hata ayıklama modları dahildir.|
|Paket (sadece.NET SDK)|Yok|NuGet paketi olarak yayımlarken NuGet Paketi meta verilerini tanımlamanızı sağlar.|
|Başvuru Yolları|[Bir projedeki başvuruları yönetme](managing-references-in-a-project.md)|Kodun bağlı olduğu derlemeleri nerede arayacağınızı belirtmenizi sağlar.|
|Kaynaklar (sadece.NET SDK)|Yok|Varsayılan kaynaklar dosyası oluşturmanızı ve yönetmeniz sağlar.|

### <a name="f-specific-settings"></a>F#'a özel ayarlar

Aşağıdaki tabloda F#'a özgü ayarlar özetlenir:

|Proje Tasarımcısı sayfası|Ayar|Açıklama|
| - |-------|-----------|
|Oluşturma|Kuyruk çağrıları oluşturma|Seçilirse, kuyruk Microsoft Ara Dili (MSIL) yönergesinin kullanılmasını sağlar. Bu, yığın çerçevesinin kuyruk özyinelemeli işlevleri için yeniden kullanılmasına neden olur. Derleyici `--tailcalls` seçeneğine eşdeğerdir.|
|Oluşturma|Diğer bayraklar|Ek derleyici komut satırı seçenekleri belirtmenizi sağlar.|

## <a name="code-and-text-editor-features"></a>Kod ve metin düzenleyiciözellikleri

Visual Studio kodunun ve metin editörlerinin aşağıdaki özellikleri F#'da desteklenir:

|Özellik|Açıklama|F# ile mi desteklenir?|
|-------|-----------|----------------|
|Otomatik olarak yorum|Kodun yorum bölümlerini yorumlamanızı veya açıklamadışı etmenizi sağlar.|Evet|
|Otomatik biçimlendirme|Standart girintiyle ve stiliyle kodu yeniden biçimlendirmez.|Hayır|
|Yer İşaretleri|Editördeki yerleri kaydetmenizi sağlar.|Evet|
|Girintiyi değiştir|Seçili satırları girintisi veya girintisi olmayan lar.|Evet|
|Akıllı girintinasyon|İmleci F# kapsam kurallarına göre otomatik olarak girintiler ve girintiler.|Evet|
|[Metin bulma ve değiştirme](finding-and-replacing-text.md)|Bir dosyada, projede veya çözümde arama yapmanızı ve metni değiştirmenizi sağlar.|Evet|
|.NET API için tanıma git|İmleç bir .NET API'ye yerleştirildiğinde,.NET meta verilerinden oluşturulan kodu gösterir.|Hayır|
|Kullanıcı tanımlı API için tanıma gitme|İmleç sizin tanımladığınız bir program varlığı nda olduğunda, imleci kodundaki varlığın tanımlandığı konuma taşır.|Evet|
|Satıra Gitme|Bir dosyadaki belirli bir satıra satır numarasıyla gitmenizi sağlar.|Evet|
|Dosyanın üst kısmında gezinme çubukları|Örneğin, işlev adı ile kod içinde konumlara atlamanızı sağlar.|Evet|
|Blok Yapı Yönergeleri|Bir önizleme için üzerinde gezinilebilen F# kapsamlarını gösteren yönergeler gösterir.|Evet|
|[Anahat](outlining.md)|Daha kompakt bir görünüm oluşturmak için kodlarınızın bölümlerini daraltmanızı sağlar.|Evet|
|Tabify|Boşlukları sekmeye dönüştürür.|Evet|
|Tür renklendirme|Tanımlı tür adlarını özel bir renkte gösterir.|Evet|
|Çabuk bul. Bkz. Pencereyi Hızlı Bul, Bul ve Değiştir.|Bir dosyada veya projede arama yapmanızı sağlar.|Evet|
|**Ctrl'yi**+**tıklatın** Tanıma Gitmek|**Ctrl'yi** basılı tutmanızı ve Tanıma Git'i çağırmak için F# simgesine tıklamanızı sağlar.|Evet|
|QuickInfo'dan Tanıma Git|Tanıma Git'i çağıran araç ipuçlarının içindeki tıklatılabilir semboller.|Evet|
|Tümüne Git|**Ctrl**+**T**ile tüm F# yapıları için küresel, bulanık eşleşen gezinmeyi sağlar.|Evet|
|Satır Ara Yeniden Adlandırma|Bir simgenin tüm oluşumlarını satır satır olarak yeniden adlandırır.|Evet|
|Tüm Referansları Bul|Kod tabanındabir sembolün tüm oluşumlarını bulur.|Evet|
|Ad kodu düzeltmesini basitleştir|F# sembolleri için gereksiz elemeleri kaldırır.|Evet|
|Kullanılmayan `open` ifade kodu düzeltmesini kaldırma|Belgedeki tüm `open` gereksiz ifadeleri kaldırır.|Evet|
|Kullanılmayan değer kodu düzeltmesi|Alt vurgulamak için kullanılmayan bir tanımlayıcıyı yeniden adlandırmayı önerir.|Evet|

Visual Studio'da kod düzenleme hakkında genel bilgiler ve metin düzenleyicisinin özellikleri için [editörde kod yaz'a](writing-code-in-the-code-and-text-editor.md)bakın.

## <a name="intellisense-features"></a>IntelliSense özellikleri

Aşağıdaki tablo, F#'da desteklenen ve desteklenmeyen IntelliSense özelliklerini özetler:

|Özellik|Açıklama|F# ile mi desteklenir?|
|-------|-----------|----------------|
|Arabirimleri otomatik olarak uygulayın|Arabirim yöntemleri için kod saplamaları oluşturur.|Evet|
|Kod parçacıkları|Ortak kodlama yapılarından oluşan bir kitaplıktan konulara kod enjekte eder.|Hayır|
|Tam Sözcük|Yazarken sözcükleri ve adları tamamlayarak yazmayı kaydeder.|Evet|
|Otomatik tamamlama|Etkinleştirildiğinde, bir tane seçmeni veya **Ctrl**+**Space**tuşuna basmanızı beklemek yerine, kelime tamamlamanın siz yazarken ilk eşleşmeyi seçmesine neden olur.|Evet|
|Açılmamış ad alanlarındaki semboller için teklif tamamlama|Otomatik tamamlama ile, açılmamış bir ad alanında bulunan eşleşen bir simge önerilir `open` ve seçildiğinde ilgili deyimle tamamlanmayı teklif eder.|Evet|
|Kod öğeleri oluşturma|Çeşitli yapılar için saplama kodu oluşturmanıza olanak tanır.|Hayır|
|Üyeleri Listeleme|Üye erişim işleci (.) yazdığınızda, bir tür için üyeleri gösterir.|Evet|
|Kullanımı Düzenle/Aç|C# veya F#'daki **açık** yönergeler **ifadeleri kullanılarak** başvurulan ad alanlarını düzenler.|Hayır|
|Parametre Bilgisi|Bir işlev çağrısı yazarken parametreler hakkında yararlı bilgiler gösterir.|Evet|
|Hızlı Bilgi|Kodunuzdaherhangi bir tanımlayıcı için tam bildirimi görüntüler.|Evet|
|Otomatik ayraç tamamlama|F# ayraç benzeri sözdizimi yapılarını işlemsel bir şekilde otomatik olarak tamamlar.|Evet|

IntelliSense hakkında genel bilgi için Bkz. [IntelliSense'i kullan.](using-intellisense.md)

## <a name="debugging-features"></a>Hata ayıklama özellikleri

Aşağıdaki tablo, F# kodunu hata ayıklamada kullanılabilen özellikleri özetley:

|Özellik|Açıklama|F# ile mi desteklenir?|
|-------|-----------|----------------|
|Otomatik değişkenler penceresi|Otomatik veya geçici değişkenleri gösterir.|Hayır|
|Kesme Noktaları|Hata ayıklama sırasında belirli noktalarda kod yürütmeyi duraklatmanızı sağlar.|Evet|
|Koşullu kesme noktaları|Yürütmenin duraklatılıp duraklatılmayacağını belirleyen bir koşulu sınayan kesme noktalarını etkinleştirin.|Evet|
|Düzenle ve Devam Et|Hata ayıklayıcıyı durdurmadan ve yeniden başlatmadan çalışan bir programı hata ayıklama olarak kodun değiştirilmesini ve derlenmesine olanak tanır.|Hayır|
|İfade değerlendiricisi|Kodu çalışma zamanında değerlendirir ve yürütür.|Hayır, ancak C# ifade değerlendiricisi kullanılabilir, ancak C# sözdizimini kullanmanız gerekir.|
|Geçmiş hata ayıklama|Daha önce yürütülmüş koda adım atmanızı sağlar.|Evet|
|Yerel öğeler penceresi|Yerel olarak tanımlanmış değerleri ve değişkenleri gösterir.|Evet|
|İmlec'e Çalıştır|İmleci içeren satıra ulaşılıncaya kadar kodu yürütmenizi sağlar.|Evet|
|Adım Adım|Yürütmeyi ilerletmenizi ve herhangi bir işlev çağrısına geçmenizi sağlar.|Evet|
|Adım Adım|Geçerli yığın çerçevesinde yürütmeyi ilerletmenizi ve herhangi bir işlev çağrısını geçmenizi sağlar.|Evet|

Visual Studio hata ayıklama hakkında genel bilgi için [Visual Studio'da Hata Ayıklama](../debugger/index.yml)bölümüne bakın.

## <a name="additional-tools"></a>Ek araçlar

Aşağıdaki tablo, Visual Studio araçlarında F# desteğini özetleyilmiştir.

|Araç|Açıklama|F# ile mi desteklenir?|
|----|-----------|----------------|
|Çağrı Hiyerarşisi|Kodunuzda işlev çağrılarının iç içe olan yapısını görüntüler.|Hayır|
|Kod Ölçümleri|Satır sayıları gibi kodunuz la ilgili bilgileri toplar.|Hayır|
|Sınıf Görünümü|Projedeki kodun tür tabanlı görünümünü sağlar.|Hayır|
|[Hata Listesi penceresi](reference/error-list-window.md)|Koddaki hataların listesini gösterir.|Evet|
|[F# İnteraktif](/dotnet/fsharp/tutorials/fsharp-interactive/)|F# kodunu yazmanızı (veya kopyalayıp yapıştırmanızı) ve projenizin binasından bağımsız olarak hemen çalıştırmanızı sağlar. F# Interactive penceresi Okuma, Değerlendirme, Yazdırma Döngüsü (REPL) penceredir.|Evet|
|Nesne Tarayıcısı|Bir derlemedeki türleri görüntülemenizi sağlar.|Derlenmiş derlemelerde göründükleri gibi F# türleri tam olarak sizin yazdığınız gibi görünmez. F# türlerinin derlenmiş gösterimine göz atabilirsiniz, ancak türleri F#'dan göründükleri gibi görüntüleyemezsiniz.|
|[Çıktı penceresi](reference/output-window.md)|Yapı çıktısını görüntüler.|Evet|
|Performans analizi|Kodunuzu ölçmek için araçlar sağlar.|Evet|
|Özellik penceresi|Odak noktası olan geliştirme ortamında nesnenin özelliklerini görüntüler ve düzenlemeyi sağlar.|Evet|
|Sunucu Gezgini|Çeşitli sunucu kaynaklarıyla etkileşim kurmanın yollarını sağlar.|Evet|
|Çözüm Gezgini|Projeleri ve dosyaları görüntülemenizi ve yönetmenizsağlar.|Evet|
|Görev Listesi|Kodunuzla ilgili iş öğelerini yönetmenize olanak tanır.|Hayır|
|Test projeleri|Kodunuzu sınamamanıza yardımcı olan özellikler sağlar.|Hayır|
|Araç Kutusu|Denetimler ve metin veya kod bölümleri gibi sürülebilir nesneleri içeren sekmeleri görüntüler.|Evet|

## <a name="see-also"></a>Ayrıca bkz.

- [F# kılavuzu (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio'da F# ile başlayın](/dotnet/fsharp/get-started/get-started-visual-studio)
