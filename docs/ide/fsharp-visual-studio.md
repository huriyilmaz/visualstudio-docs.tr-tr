---
title: F# araçları
description: "F # ' da hangi Visual Studio özelliklerinin desteklendiğini öğrenin."
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
f1_keywords:
- fs.ProjectPropertiesDebug
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c0ce6e68fa36f3b13474306ddd1d8304d640c0ec
ms.sourcegitcommit: e359b93c93c6ca316c0d8b86c2b6e566171fd1ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507982"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Visual Studio 'da Visual F# ile geliştirme

Bu makale, F # geliştirme için Visual Studio özellikleri hakkında bilgi içerir.

## <a name="install-f-support"></a>F # desteğini yükler

Visual Studio 'da F # ile geliştirme yapmak için, henüz yapmadıysanız **.net masaüstü geliştirme** iş yükünü yüklemeniz gerekir. **Araçlar**  >  **ve Özellikler al**' ı seçerek açabileceğiniz Visual Studio yükleyicisi aracılığıyla Visual Studio iş yüklerini yüklersiniz.

![Visual Studio 'da .NET masaüstü geliştirme iş yükü](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F # proje özellikleri

Visual Studio 'da F # için çeşitli proje ve öğe şablonları mevcuttur. Aşağıdaki görüntüde .NET Core ve .NET Standard için bazı F # proje şablonları gösterilmektedir:

![Visual Studio 'da F # proje şablonları](media/fsharp-project-templates.png)

Aşağıdaki görüntüde bazı F # öğe şablonları gösterilmektedir:

![Visual Studio 'da F # öğe şablonları](media/fsharp-item-templates.png)

Veri erişimi için öğe şablonları hakkında daha fazla bilgi için bkz. [F # tür sağlayıcıları](/dotnet/fsharp/tutorials/type-providers/index).

Aşağıdaki tabloda F # için proje özelliklerindeki Özellikler özetlenmektedir:

|Proje ayarı|F # içinde destekleniyor mu?|Notlar|
|---------------|----------------|-----|
|Kaynak dosyalar|Yes||
|Derleme, hata ayıklama ve başvuru ayarları|Yes||
|Çoklu Sürüm Desteği|Yes||
|Simge ve bildirim|Hayır|Derleyici komut satırı seçenekleriyle kullanılabilir.|
|ASP.NET Istemci Hizmetleri|Hayır||
|ClickOnce|Hayır|Varsa, başka bir .NET dilinde istemci projesi kullanın.|
|Kesin adlandırma|Hayır|Derleyici komut satırı seçenekleriyle kullanılabilir.|
|Derleme yayımlama ve sürüm oluşturma|Hayır||
|Kod analizi|Hayır|Kod analizi araçları el ile veya derleme sonrası bir komutun parçası olarak çalıştırılabilir.|
|Güvenlik (güven düzeylerini değiştir)|Hayır||

## <a name="project-designer"></a>Proje Tasarımcısı

**Proje Tasarımcısı** , ilgili işlevlere göre gruplanmış çeşitli proje özellik sayfalarından oluşur. F # projeleri için kullanılabilen sayfalar çoğunlukla diğer dillerin kullanabildiği bir alt kümesidir ve aşağıdaki tabloda açıklanmıştır. Bağlantılar, karşılık gelen C# **Proje Tasarımcısı** sayfasına sağlanır.

|Proje Tasarımcısı sayfası|İlgili bağlantılar|Açıklama|
| - |-------------|-----------|
|Uygulama|[Uygulama sayfası, proje Tasarımcısı](reference/application-page-project-designer-csharp.md)|Bir kitaplık veya yürütülebilir dosya oluşturma, uygulamanın hedeflediği .NET sürümü ve uygulamanın kullandığı kaynak dosyalarının nerede depolandığı hakkında bilgi gibi uygulama düzeyinde ayarları ve özellikleri belirtmenize olanak sağlar.|
|Yapı|[Derleme sayfası, proje Tasarımcısı](reference/build-page-project-designer-csharp.md)|Kodun nasıl derlendiğini denetlemenizi sağlar.|
|Derleme olayları|[Derleme olayları sayfası, proje Tasarımcısı](reference/build-events-page-project-designer-csharp.md)|Derlemeden önce veya sonra çalıştırılacak komutları belirtmenize olanak sağlar.|
|Hata ayıklama|[Hata Ayıklama Sayfası, Proje Tasarımcısı](reference/debug-page-project-designer.md)|Hata ayıklama sırasında uygulamanın nasıl çalıştığını denetlemenizi sağlar. Bu, hangi komutların kullanılacağını ve uygulamanızın Başlangıç dizininin ne olduğunu, yerel kod ve SQL gibi özel hata ayıklama modlarını da içerir.|
|Paket (yalnızca .NET SDK)|YOK|NuGet paketi olarak yayımlarken NuGet paketi meta verilerini tanımlamanızı sağlar.|
|Başvuru yolları|[Bir projedeki başvuruları yönetme](managing-references-in-a-project.md)|Kodun bağımlı olduğu derlemelerin nerede aranacağını belirtmenizi sağlar.|
|Kaynaklar (yalnızca .NET SDK)|YOK|Varsayılan bir kaynak dosyası oluşturmanıza ve yönetmenize olanak sağlar.|

### <a name="f-specific-settings"></a>F #-özel ayarlar

Aşağıdaki tablo, F # ' a özel ayarları özetler:

|Proje Tasarımcısı sayfası|Ayar|Açıklama|
| - |-------|-----------|
|Yapı|Kuyruk çağrıları oluştur|Seçilirse, tail Microsoft ara dili (MSIL) yönergesinin kullanımını etkinleştirilir. Bu, yığın çerçevesinin tail Özyinelemeli işlevler için yeniden kullanılmasına neden olur. `--tailcalls`Derleyici seçeneğine eşdeğerdir.|
|Yapı|Diğer bayraklar|Ek derleyici komut satırı seçeneklerini belirtmenizi sağlar.|

## <a name="code-and-text-editor-features"></a>Kod ve metin Düzenleyicisi özellikleri

Visual Studio Code ve metin düzenleyicilerinin aşağıdaki özellikleri F # içinde desteklenir:

|Özellik|Açıklama|F # içinde destekleniyor mu?|
|-------|-----------|----------------|
|Otomatik olarak açıklama|Kod bölümlerinin açıklamalarını veya açıklama eklemenizi sağlar.|Yes|
|Otomatik olarak Biçimlendir|Standart girintileme ve stille kodu yeniden biçimlendirir.|Hayır|
|Yer işaretleri|, Düzenleyiciden konumları kaydetmenizi sağlar.|Yes|
|Girintiyi Değiştir|Seçili satırları girintiler veya girintileri geri al.|Yes|
|Akıllı girintileme|İmleci F # kapsam kurallarına göre otomatik olarak girintiler ve girintiden kaldır.|Yes|
|[Metin bulma ve değiştirme](finding-and-replacing-text.md)|Bir dosya, proje veya çözümde arama yapmanızı ve muhtemelen metin değiştirebilmenizi sağlar.|Yes|
|.NET API tanımına git|İmleç .NET API üzerinde konumlandırıldığında, .NET meta verilerinden oluşturulan kodu gösterir.|Hayır|
|Kullanıcı tanımlı API için tanıma git|İmleç tanımladığınız bir program varlığında olduğunda, imleci kodunuzda varlığın tanımlandığı konuma taşıtır.|Yes|
|Satıra Gitme|Bir dosyada satır numarasına göre belirli bir satıra gitmenizi sağlar.|Yes|
|Dosyanın üstündeki gezinti çubukları|Koddaki konumlara (örneğin, işlev adı) atlamanızı sağlar.|Yes|
|Blok yapısı yönergeleri|Bir önizleme için üzerine düşen, F # kapsamlarını belirten yönergeleri gösterir.|Yes|
|[Anahat Oluşturma](outlining.md)|Daha kompakt bir görünüm oluşturmak için kodunuzun bölümlerini daraltmanıza olanak sağlar.|Yes|
|Sekmeye Dönüştür|Boşlukları sekmelere dönüştürür.|Yes|
|Tür renklendirme|Tanımlı tür adlarını özel bir renkte gösterir.|Yes|
|Hızlı bul. Bkz. hızlı bul, bul ve Değiştir penceresi.|Bir dosya veya projede arama yapmanızı sağlar.|Yes|
|**CTRL** + Tanıma gitmek için **tıklayın**|Tanıma Git 'i çağırmak için **CTRL** tuşunu basılı tutup bir F # simgesine tıklamenize olanak tanır.|Yes|
|Hızlı bilgilerim tanımına git|ToolTip 'e git çağıran araç ipuçları içinde tıklatılabilir semboller.|Yes|
|Tümüne git|**CTRL**T aracılığıyla tüm F # yapıları için genel, belirsiz eşleştirme gezintisini mümkün hale sunar + **T**.|Yes|
|Satır içi yeniden adlandırma|Bir simgenin tüm oluşumlarını satır içi olarak yeniden adlandırır.|Yes|
|Tüm başvuruları bul|Bir kod tabanında bir sembolün tüm oluşumlarını bulur.|Yes|
|Ad kodu düzeltmesini basitleştirme|F # sembolleri için gereksiz niteleyicileri kaldırır.|Yes|
|Kullanılmayan `open` beyan kodu düzeltmesini kaldır|Belgedeki tüm gereksiz `open` deyimleri kaldırır.|Yes|
|Kullanılmayan değer kodu onarımı|Alt çizgi için kullanılmamış tanımlayıcıyı yeniden adlandırmayı önerir.|Yes|

Visual Studio 'da kod düzenleme ve metin düzenleyicisinin özellikleri hakkında genel bilgi için bkz. [düzenleyicide kod yazma](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>IntelliSense özellikleri

Aşağıdaki tabloda, F # ' da desteklenen ve desteklenmeyen IntelliSense özellikleri özetlenmektedir:

|Özellik|Açıklama|F # içinde destekleniyor mu?|
|-------|-----------|----------------|
|Arabirimleri otomatik olarak Uygula|Arabirim yöntemleri için kod saplamaları üretir.|Yes|
|Kod parçacıkları|Ortak kodlama yapıları kitaplığındaki kodu konu başlıkları halinde çıkartır.|Hayır|
|Tam Sözcük|Yazdığınız sözcükleri ve adları tamamlayarak yazma işlemini kaydeder.|Yes|
|Otomatik tamamlama|Etkin olduğunda, bir tane seçmenizi veya **CTRL**Space 'e basmanız beklenmeden, sözcük tamamlamada yazarken ilk eşleşmeyi seçmesini sağlar + **Space**.|Yes|
|Açık olmayan ad alanlarında semboller için tamamlama sunma|Otomatik tamamlama ile, açılmamış bir ad alanında bulunan eşleşen bir sembol önerilir ve seçilirken karşılık gelen deyimle tamamlamak için teklif edilir `open` .|Yes|
|Kod öğeleri oluşturma|Çeşitli yapılar için saplama kodu oluşturmanıza olanak sağlar.|Hayır|
|Üyeleri Listeleme|Üye erişim işlecini (.) yazdığınızda, bir türün üyelerini gösterir.|Yes|
|Kullanımlar/açık düzenleme|C# ' deki deyimler **kullanılarak** başvurulan ad alanlarını veya F # içinde **Açık** yönergeleri düzenler.|Hayır|
|Parametre Bilgisi|Bir işlev çağrısı yazarken parametreler hakkındaki yararlı bilgileri gösterir.|Yes|
|Hızlı Bilgi|Kodunuzda herhangi bir tanımlayıcı için bütün bildirimi görüntüler.|Yes|
|Otomatik küme ayracı tamamlama|F # küme ayracı benzeri sözdizimi yapılarını işlem sırasında otomatik olarak tamamlar.|Yes|

IntelliSense hakkında genel bilgi için bkz. [IntelliSense kullanma](using-intellisense.md).

## <a name="debugging-features"></a>Hata ayıklama özellikleri

Aşağıdaki tabloda, F # kodunda hata ayıklarken kullanılabilen özellikler özetlenmektedir:

|Özellik|Açıklama|F # içinde destekleniyor mu?|
|-------|-----------|----------------|
|Otomatik değişkenler penceresi|Otomatik veya geçici değişkenleri gösterir.|Hayır|
|Kesme noktaları|Hata ayıklama sırasında belirli noktalarda kod yürütmeyi duraklatmanızı sağlar.|Yes|
|Koşullu kesme noktaları|Yürütmenin duraklatıp duraklatılmayacağını belirleyen bir koşulu test eden kesme noktalarını sunar.|Yes|
|Düzenle ve Devam Et|Hata ayıklayıcıyı durdurup yeniden başlatmadan çalışan bir programda hata ayıkladığınızda kodun değiştirilmesini ve derlenmesine olanak sağlar.|Hayır|
|İfade değerlendirici|Çalışma zamanında kodu değerlendirir ve yürütür.|Hayır, ancak C# sözdizimi kullanmak zorunda olsanız da C# ifade değerlendiricisi kullanılabilir.|
|Geçmiş hata ayıklama|Daha önce yürütülen koda adım adım eklemenizi sağlar.|Yes|
|Yerel öğeler penceresi|Yerel olarak tanımlanan değerleri ve değişkenleri gösterir.|Yes|
|Imlece kadar Çalıştır|İmleci içeren satıra ulaşılana kadar kodu çalıştırmanızı sağlar.|Yes|
|Adımla|Yürütmeyi ilerletebilirsiniz ve herhangi bir işlev çağrısına geçiş yapmanızı sağlar.|Yes|
|Adımla|Geçerli yığın çerçevesindeki yürütmeyi ilerlemenize ve herhangi bir işlev çağrısını taşımanızı sağlar.|Yes|

Visual Studio hata ayıklayıcısı hakkında genel bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/index.yml).

## <a name="additional-tools"></a>Ek araçlar

Aşağıdaki tabloda, Visual Studio araçlarında F # desteği özetlenmektedir.

|Araç|Açıklama|F # içinde destekleniyor mu?|
|----|-----------|----------------|
|Çağrı Hiyerarşisi|Kodunuzda işlev çağrılarının iç içe yapısını görüntüler.|Hayır|
|Kod Ölçümleri|Kodunuz hakkında satır sayısı gibi bilgileri toplar.|Hayır|
|Sınıf Görünümü|Projedeki kodun tür tabanlı görünümünü sağlar.|Hayır|
|[Hata Listesi penceresi](reference/error-list-window.md)|Koddaki hataların bir listesini gösterir.|Yes|
|[F# Etkileşimli](/dotnet/fsharp/tutorials/fsharp-interactive/)|, F # kodunu yazmanız (veya kopyalayıp yapıştırmanızı) ve bunu projenizin yapısından bağımsız olarak hemen çalıştırmanızı sağlar. F# Etkileşimli pencere bir okuma, değerlendirme, yazdırma döngüsü (REPL).|Yes|
|Nesne Tarayıcısı|Bir derlemedeki türleri görüntülemenize olanak sağlar.|Derlenmiş derlemelerde göründükleri gibi F # türleri tam olarak yazar olarak görünmez. F # türlerinin derlenmiş gösterimine göz atabilirsiniz, ancak türleri F # ' dan göründükleri gibi görüntüleyemezsiniz.|
|[Çıktı penceresi](reference/output-window.md)|Yapı çıkışını görüntüler.|Yes|
|Performans Analizi|Kodunuzun performansını ölçmek için araçlar sağlar.|Yes|
|Özellik penceresi|Odaklı geliştirme ortamındaki nesnenin özelliklerini görüntüler ve düzenlemenizi mümkün.|Yes|
|Sunucu Gezgini|Çeşitli sunucu kaynaklarıyla etkileşimde bulunmak için yollar sağlar.|Yes|
|Çözüm Gezgini|Projeleri ve dosyaları görüntülemenize ve yönetmenize olanak sağlar.|Yes|
|Görev Listesi|Kodunuzla ilgili iş öğelerini yönetmenizi sağlar.|Hayır|
|Test projeleri|Kodunuzu test etmenize yardımcı olan özellikler sağlar.|Hayır|
|Araç Kutusu|Metin veya kodun denetimleri ve bölümleri gibi sürüklenebilir nesneleri içeren sekmeleri görüntüler.|Yes|

## <a name="see-also"></a>Ayrıca bkz.

- [F # Kılavuzu (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio 'da F # ile çalışmaya başlama](/dotnet/fsharp/get-started/get-started-visual-studio)
