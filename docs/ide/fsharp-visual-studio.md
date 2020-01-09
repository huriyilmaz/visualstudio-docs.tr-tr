---
title: F# araçları
description: "' De F#hangi Visual Studio özelliklerinin desteklendiğini öğrenin."
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565246"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Visual Studio 'da F# Visual ile geliştirme

Bu makale, geliştirme için F# Visual Studio özellikleri hakkında bilgi içerir.

## <a name="install-f-support"></a>Destek F# yüklemesi

Visual Studio 'da F# ile geliştirme yapmak için, henüz yapmadıysanız **.net masaüstü geliştirme** iş yükünü yüklemeniz gerekir. Araçlar **ve Özellikler al** > **Araçlar** ' ı seçerek açabileceğiniz Visual Studio yükleyicisi aracılığıyla Visual Studio iş yüklerini yüklersiniz.

![Visual Studio 'da .NET masaüstü geliştirme iş yükü](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F#Proje Özellikleri

Visual Studio 'da için F# çeşitli proje ve öğe şablonları mevcuttur. Aşağıdaki görüntüde .NET Core ve .NET Standard için F# bazı proje şablonları gösterilmektedir:

![F#Visual Studio 'da proje şablonları](media/fsharp-project-templates.png)

Aşağıdaki görüntüde bazı F# öğe şablonları gösterilmektedir:

![F#Visual Studio 'da öğe şablonları](media/fsharp-item-templates.png)

Veri erişimi için öğe şablonları hakkında daha fazla bilgi için bkz [ F# . tür sağlayıcıları](/dotnet/fsharp/tutorials/type-providers/index).

Aşağıdaki tablo, için F#proje özelliklerindeki özellikleri özetler:

|Proje ayarı|İçinde F#destekleniyor mu?|Notlar|
|---------------|----------------|-----|
|Kaynak dosyalar|Evet||
|Derleme, hata ayıklama ve başvuru ayarları|Evet||
|Çoklu Sürüm Desteği|Evet||
|Simge ve bildirim|Hayır|Derleyici komut satırı seçenekleriyle kullanılabilir.|
|ASP.NET Istemci Hizmetleri|Hayır||
|ClickOnce|Hayır|Varsa, başka bir .NET dilinde istemci projesi kullanın.|
|Kesin adlandırma|Hayır|Derleyici komut satırı seçenekleriyle kullanılabilir.|
|Derleme yayımlama ve sürüm oluşturma|Hayır||
|Kod analizi|Hayır|Kod analizi araçları el ile veya derleme sonrası bir komutun parçası olarak çalıştırılabilir.|
|Güvenlik (güven düzeylerini değiştir)|Hayır||

## <a name="project-designer"></a>Proje Tasarımcısı

**Proje Tasarımcısı** , ilgili işlevlere göre gruplanmış çeşitli proje özellik sayfalarından oluşur. Projeler için F# kullanılabilen sayfalar çoğunlukla diğer dillerin kullanabildiği bir alt kümesidir ve aşağıdaki tabloda açıklanmıştır. Bağlantılar, ilgili C# **Proje Tasarımcısı** sayfasına sağlanır.

|Proje Tasarımcısı sayfası|İlgili bağlantılar|Açıklama|
| - |-------------|-----------|
|Uygulama|[Uygulama sayfası, proje Tasarımcısı](reference/application-page-project-designer-csharp.md)|Bir kitaplık veya yürütülebilir dosya oluşturma, uygulamanın hedeflediği .NET sürümü ve uygulamanın kullandığı kaynak dosyalarının nerede depolandığı hakkında bilgi gibi uygulama düzeyinde ayarları ve özellikleri belirtmenize olanak sağlar.|
|{1&gt;Yapı (Build)&lt;1}|[Derleme sayfası, proje Tasarımcısı](reference/build-page-project-designer-csharp.md)|Kodun nasıl derlendiğini denetlemenizi sağlar.|
|Derleme olayları|[Derleme olayları sayfası, proje Tasarımcısı](reference/build-events-page-project-designer-csharp.md)|Derlemeden önce veya sonra çalıştırılacak komutları belirtmenize olanak sağlar.|
|Hata ayıklama|[Hata Ayıklama Sayfası, Proje Tasarımcısı](reference/debug-page-project-designer.md)|Hata ayıklama sırasında uygulamanın nasıl çalıştığını denetlemenizi sağlar. Bu, hangi komutların kullanılacağını ve uygulamanızın Başlangıç dizininin ne olduğunu, yerel kod ve SQL gibi özel hata ayıklama modlarını da içerir.|
|Paket (yalnızca .NET SDK)|YOK|NuGet paketi olarak yayımlarken NuGet paketi meta verilerini tanımlamanızı sağlar.|
|Başvuru yolları|[Bir projedeki başvuruları yönetme](managing-references-in-a-project.md)|Kodun bağımlı olduğu derlemelerin nerede aranacağını belirtmenizi sağlar.|
|Kaynaklar (yalnızca .NET SDK)|YOK|Varsayılan bir kaynak dosyası oluşturmanıza ve yönetmenize olanak sağlar.|

### <a name="f-specific-settings"></a>F#-özel ayarlar

Aşağıdaki tablo, öğesine F#özgü ayarları özetler:

|Proje Tasarımcısı sayfası|Ayar|Açıklama|
| - |-------|-----------|
|{1&gt;Yapı (Build)&lt;1}|Kuyruk çağrıları oluştur|Seçilirse, tail Microsoft ara dili (MSIL) yönergesinin kullanımını etkinleştirilir. Bu, yığın çerçevesinin tail Özyinelemeli işlevler için yeniden kullanılmasına neden olur. `--tailcalls` derleyici seçeneğine eşdeğerdir.|
|{1&gt;Yapı (Build)&lt;1}|Diğer bayraklar|Ek derleyici komut satırı seçeneklerini belirtmenizi sağlar.|

## <a name="code-and-text-editor-features"></a>Kod ve metin Düzenleyicisi özellikleri

Visual Studio Code ve metin düzenleyicilerinin aşağıdaki özellikleri içinde F#desteklenir:

|Özellik|Açıklama|İçinde F#destekleniyor mu?|
|-------|-----------|----------------|
|Otomatik olarak açıklama|Kod bölümlerinin açıklamalarını veya açıklama eklemenizi sağlar.|Evet|
|Otomatik olarak Biçimlendir|Standart girintileme ve stille kodu yeniden biçimlendirir.|Hayır|
|Yer İşaretleri|, Düzenleyiciden konumları kaydetmenizi sağlar.|Evet|
|Girintiyi Değiştir|Seçili satırları girintiler veya girintileri geri al.|Evet|
|Akıllı girintileme|, F# Kapsam kurallarına göre imleci otomatik olarak girintiler ve girintiden kaldır.|Evet|
|[Metin bulma ve değiştirme](finding-and-replacing-text.md)|Bir dosya, proje veya çözümde arama yapmanızı ve muhtemelen metin değiştirebilmenizi sağlar.|Evet|
|.NET API tanımına git|İmleç .NET API üzerinde konumlandırıldığında, .NET meta verilerinden oluşturulan kodu gösterir.|Hayır|
|Kullanıcı tanımlı API için tanıma git|İmleç tanımladığınız bir program varlığında olduğunda, imleci kodunuzda varlığın tanımlandığı konuma taşıtır.|Evet|
|Satıra Gitme|Bir dosyada satır numarasına göre belirli bir satıra gitmenizi sağlar.|Evet|
|Dosyanın üstündeki gezinti çubukları|Koddaki konumlara (örneğin, işlev adı) atlamanızı sağlar.|Evet|
|Blok yapısı yönergeleri|Bir önizleme için üzerine F# düşşebilen kapsamları gösteren kılavuzları gösterir.|Evet|
|[Anahat Oluşturma](outlining.md)|Daha kompakt bir görünüm oluşturmak için kodunuzun bölümlerini daraltmanıza olanak sağlar.|Evet|
|Sekmeye Dönüştür|Boşlukları sekmelere dönüştürür.|Evet|
|Tür renklendirme|Tanımlı tür adlarını özel bir renkte gösterir.|Evet|
|Hızlı bul. Bkz. hızlı bul, bul ve Değiştir penceresi.|Bir dosya veya projede arama yapmanızı sağlar.|Evet|
|Tanıma gitmek için **Ctrl**+**tıklayın**|Tanıma Git 'i çağırmak için **CTRL** tuşunu basılı tutarak F# simgeye tıklamenize olanak tanır.|Evet|
|Hızlı bilgilerim tanımına git|ToolTip 'e git çağıran araç ipuçları içinde tıklatılabilir semboller.|Evet|
|Tümüne Git|F# **CTRL**+**t**aracılığıyla tüm yapılar için genel, benzer şekilde eşleşen gezinmeyi mümkün hale sunar.|Evet|
|Satır içi yeniden adlandırma|Bir simgenin tüm oluşumlarını satır içi olarak yeniden adlandırır.|Evet|
|Tüm başvuruları bul|Bir kod tabanında bir sembolün tüm oluşumlarını bulur.|Evet|
|Ad kodu düzeltmesini basitleştirme|Semboller için F# gereksiz niteleyicileri kaldırır.|Evet|
|Kullanılmayan `open` bildiri kodu düzeltmesini kaldır|Belgedeki tüm gereksiz `open` deyimlerini kaldırır.|Evet|
|Kullanılmayan değer kodu onarımı|Alt çizgi için kullanılmamış tanımlayıcıyı yeniden adlandırmayı önerir.|Evet|

Visual Studio 'da kod düzenleme ve metin düzenleyicisinin özellikleri hakkında genel bilgi için bkz. [düzenleyicide kod yazma](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>IntelliSense özellikleri

Aşağıdaki tabloda, desteklenen ve içinde F#desteklenmeyen IntelliSense özellikleri özetlenmektedir:

|Özellik|Açıklama|İçinde F#destekleniyor mu?|
|-------|-----------|----------------|
|Arabirimleri otomatik olarak Uygula|Arabirim yöntemleri için kod saplamaları üretir.|Evet|
|Kod parçacıkları|Ortak kodlama yapıları kitaplığındaki kodu konu başlıkları halinde çıkartır.|Hayır|
|Tam Sözcük|Yazdığınız sözcükleri ve adları tamamlayarak yazma işlemini kaydeder.|Evet|
|Otomatik tamamlama|Etkinleştirildiğinde, sözcüğün tamamlanmasını beklemek yerine, bir tane seçmenizi veya **Ctrl**+**boşluk**tuşlarına basmanız beklenmez.|Evet|
|Açık olmayan ad alanlarında semboller için tamamlama sunma|Otomatik tamamlama ile, açılmamış bir ad alanında bulunan eşleşen bir sembol önerilir ve seçilirken karşılık gelen `open` ifadesiyle tamamlamak için teklif edilir.|Evet|
|Kod öğeleri oluşturma|Çeşitli yapılar için saplama kodu oluşturmanıza olanak sağlar.|Hayır|
|Üyeleri Listeleme|Üye erişim işlecini (.) yazdığınızda, bir türün üyelerini gösterir.|Evet|
|Kullanımlar/açık düzenleme|İçindeki deyimler **kullanılarak** başvurulan ad alanlarını düzenler C# veya içinde F#açık yönergeler.|Hayır|
|Parametre Bilgisi|Bir işlev çağrısı yazarken parametreler hakkındaki yararlı bilgileri gösterir.|Evet|
|Hızlı Bilgi|Kodunuzda herhangi bir tanımlayıcı için bütün bildirimi görüntüler.|Evet|
|Otomatik küme ayracı tamamlama|Küme ayracı F# benzeri sözdizimi yapılarını işlem sırasında otomatik olarak tamamlar.|Evet|

IntelliSense hakkında genel bilgi için bkz. [IntelliSense kullanma](using-intellisense.md).

## <a name="debugging-features"></a>Hata ayıklama özellikleri

Aşağıdaki tabloda, kod hata ayıkladığınızda F# kullanılabilen özellikler özetlenmektedir:

|Özellik|Açıklama|İçinde F#destekleniyor mu?|
|-------|-----------|----------------|
|Otomatik değişkenler penceresi|Otomatik veya geçici değişkenleri gösterir.|Hayır|
|Kesme noktaları|Hata ayıklama sırasında belirli noktalarda kod yürütmeyi duraklatmanızı sağlar.|Evet|
|Koşullu kesme noktaları|Yürütmenin duraklatıp duraklatılmayacağını belirleyen bir koşulu test eden kesme noktalarını sunar.|Evet|
|Düzenle ve Devam Et|Hata ayıklayıcıyı durdurup yeniden başlatmadan çalışan bir programda hata ayıkladığınızda kodun değiştirilmesini ve derlenmesine olanak sağlar.|Hayır|
|İfade değerlendirici|Çalışma zamanında kodu değerlendirir ve yürütür.|Hayır, ancak sözdizimi C# kullanmanız C# gerekir, ancak ifade değerlendirici kullanılabilir.|
|Geçmiş hata ayıklama|Daha önce yürütülen koda adım adım eklemenizi sağlar.|Evet|
|Yerel öğeler penceresi|Yerel olarak tanımlanan değerleri ve değişkenleri gösterir.|Evet|
|İmlece kadar Çalıştır|İmleci içeren satıra ulaşılana kadar kodu çalıştırmanızı sağlar.|Evet|
|Adımla|Yürütmeyi ilerletebilirsiniz ve herhangi bir işlev çağrısına geçiş yapmanızı sağlar.|Evet|
|Üzerinden adımla|Geçerli yığın çerçevesindeki yürütmeyi ilerlemenize ve herhangi bir işlev çağrısını taşımanızı sağlar.|Evet|

Visual Studio hata ayıklayıcısı hakkında genel bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/index.yml).

## <a name="additional-tools"></a>Ek araçlar

Aşağıdaki tabloda Visual Studio araçlarında için F# destek özetlenmektedir.

|Aracı|Açıklama|İçinde F#destekleniyor mu?|
|----|-----------|----------------|
|Çağrı Hiyerarşisi|Kodunuzda işlev çağrılarının iç içe yapısını görüntüler.|Hayır|
|Kod Ölçümleri|Kodunuz hakkında satır sayısı gibi bilgileri toplar.|Hayır|
|Sınıf Görünümü|Projedeki kodun tür tabanlı görünümünü sağlar.|Hayır|
|[Hata Listesi penceresi](reference/error-list-window.md)|Koddaki hataların bir listesini gösterir.|Evet|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Kodu yazmanız (veya kopyalayıp yapıştırmanıza) F# ve projenizin yapısından bağımsız olarak hemen çalıştırmanızı sağlar. F# Etkileşimli pencere bir okuma, değerlendirme, yazdırma döngüsü (REPL).|Evet|
|Nesne Tarayıcısı|Bir derlemedeki türleri görüntülemenize olanak sağlar.|F#derlenmiş derlemelerde göründükleri türler tam olarak yazar olarak görünmez. F# Türlerin derlenmiş gösterimine göz atabilirsiniz, ancak türleri ' den F#göründükleri gibi görüntüleyemezsiniz.|
|[Çıkış penceresi](reference/output-window.md)|Yapı çıkışını görüntüler.|Evet|
|Performans Analizi|Kodunuzun performansını ölçmek için araçlar sağlar.|Evet|
|Özellik penceresi|Odaklı geliştirme ortamındaki nesnenin özelliklerini görüntüler ve düzenlemenizi mümkün.|Evet|
|Server Explorer|Çeşitli sunucu kaynaklarıyla etkileşimde bulunmak için yollar sağlar.|Evet|
|Çözüm Gezgini|Projeleri ve dosyaları görüntülemenize ve yönetmenize olanak sağlar.|Evet|
|Görev Listesi|Kodunuzla ilgili iş öğelerini yönetmenizi sağlar.|Hayır|
|Test projeleri|Kodunuzu test etmenize yardımcı olan özellikler sağlar.|Hayır|
|Araç Kutusu|Metin veya kodun denetimleri ve bölümleri gibi sürüklenebilir nesneleri içeren sekmeleri görüntüler.|Evet|

## <a name="see-also"></a>Ayrıca bkz.

- [F#Kılavuz (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio F# 'da kullanmaya başlayın](/dotnet/fsharp/get-started/get-started-visual-studio)
