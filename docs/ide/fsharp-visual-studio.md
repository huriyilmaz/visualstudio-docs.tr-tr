---
title: F# araçları
description: F# ile desteklenen Visual Studio özelliklerini öğrenin.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
f1_keywords:
- fs.ProjectPropertiesDebug
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 71b18226be9a9609269a6619f2524c3099610eb1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086189"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Visual Studio'Visual F# Visual Studio

Bu makale, F# Visual Studio özellikleri hakkında bilgi içerir.

## <a name="install-f-support"></a>F# desteğini yükleme

Visual Studio'da F# ile geliştirmek için, önce **.NET masaüstü geliştirme** iş yükünü yükleyin (henüz yüklemediyebilirsiniz). Araçları Visual Studio Özellikler'i Visual Studio Yükleyicisi seçerek açabilirsiniz.   >  

![Visual Studio'de .NET masaüstü geliştirme iş Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F# proje özellikleri

F# için farklı proje ve öğe şablonları Visual Studio. Aşağıdaki görüntüde .NET Core ve .NET Standard için F# proje şablonlarının bazıları .NET Standard:

![Visual Studio'de F# proje şablonları](media/fsharp-project-templates.png)

Aşağıdaki görüntüde F# öğesi şablonlarının bazıları yer almaktadır:

![Visual Studio'da F# öğe şablonları](media/fsharp-item-templates.png)

Veri erişimine ilişkin öğe şablonları hakkında daha fazla bilgi için bkz. [F# tür sağlayıcıları.](/dotnet/fsharp/tutorials/type-providers/index)

Aşağıdaki tabloda F# için proje özellikleri özetlenmiştir:

|Project ayarı|F# ile desteklensin mi?|Notlar|
|---------------|----------------|-----|
|Kaynak dosyalar|Yes||
|Derleme, hata ayıklama ve başvuru ayarları|Yes||
|Çoklu Sürüm Desteği|Yes||
|Simge ve bildirim|Hayır|Derleyici komut satırı seçenekleri aracılığıyla kullanılabilir.|
|ASP.NET İstemci Hizmetleri|Hayır||
|ClickOnce|Hayır|Varsa, başka bir .NET dilinde bir istemci projesi kullanın.|
|Kesin adlandırma|Hayır|Derleyici komut satırı seçenekleri aracılığıyla kullanılabilir.|
|Derleme yayımlama ve sürüm derleme|Hayır||
|Kod analizi|Hayır|Kod analizi araçları el ile veya derleme sonrası komutun bir parçası olarak çalıştırılabilir.|
|Güvenlik (güven düzeylerini değiştirme)|Hayır||

## <a name="project-designer"></a>Proje Tasarımcısı

**Project Designer,** ilgili işlevlere göre gruplu çeşitli proje özellik sayfalarından oluşur. F# projeleri için kullanılabilen sayfalar çoğunlukla diğer dillerde kullanılabilenlerin bir alt kümesidir ve aşağıdaki tabloda açıklanmıştır. Bağlantılar, ilgili C# Project **Sağlanır.**

|Project Tasarımcı sayfası|İlgili bağlantılar|Açıklama|
| - |-------------|-----------|
|Uygulama|[Uygulama Sayfası, Project Tasarımcısı](reference/application-page-project-designer-csharp.md)|Bir kitaplık mı yoksa yürütülebilir dosya mı oluşturuyorsanız, uygulamanın hangi sürümünü hedeflemektedir ve uygulamanın kullandığı kaynak dosyalarının nerede depolandığı hakkında bilgiler gibi uygulama düzeyinde ayarlar ve özellikler belirtmenize olanak sağlar.|
|Oluşturma|[Derleme Sayfası, Project Tasarımcısı](reference/build-page-project-designer-csharp.md)|Kodun nasıl derlenmiş olduğunu denetlemeyi sağlar.|
|Derleme Olayları|[Derleme Olayları Sayfası, Project Tasarımcısı](reference/build-events-page-project-designer-csharp.md)|Derlemeden önce veya sonra çalıştıracak komutları belirtmenizi sağlar.|
|Hata Ayıklama|[Hata Ayıklama Sayfası, Proje Tasarımcısı](reference/debug-page-project-designer.md)|Hata ayıklama sırasında uygulamanın nasıl çalıştırılır denetlemenizi sağlar. Bu, hangi komutların ve uygulamanın başlangıç dizininin ne olduğunu ve yerel kod ve yerel kod gibi etkinleştirmek istediğiniz özel hata ayıklama modlarını SQL.|
|Paket (yalnızca.NET SDK)|Yok|Paket meta verilerini NuGet paket olarak yayımlarken tanımlama NuGet sağlar.|
|Başvuru Yolları|[Bir projedeki başvuruları yönetme](managing-references-in-a-project.md)|Kodun bağlı olduğu derlemelerin nerede aranabilir olduğunu belirtmenizi sağlar.|
|Kaynaklar (yalnızca.NET SDK)|Yok|Varsayılan kaynaklar dosyası oluşturma ve yönetmenizi sağlar.|

### <a name="f-specific-settings"></a>F#'a özgü ayarlar

Aşağıdaki tabloda F# için özel ayarlar özetlenmiştir:

|Project Tasarımcı sayfası|Ayar|Açıklama|
| - |-------|-----------|
|Oluşturma|Kuyruk çağrıları oluşturma|Seçilirse, Kuyruk Microsoft Ara Dil (MSIL) yönergesi kullanımını sağlar. Bu, yığın çerçevesinin kuyruk tekrarlayıcı işlevler için yeniden kullanılmasına neden olur. Derleyici `--tailcalls` seçeneğine eşdeğerdir.|
|Oluşturma|Diğer bayraklar|Ek derleyici komut satırı seçenekleri belirtmenize olanak sağlar.|

## <a name="code-and-text-editor-features"></a>Kod ve metin düzenleyici özellikleri

Kod ve metin düzenleyicilerinin Visual Studio özellikleri F# ile de desteklene sahiptir:

|Özellik|Açıklama|F# ile desteklensin mi?|
|-------|-----------|----------------|
|Otomatik olarak açıklama|Kodun bölümlerini açıklama veya açıklamadan alma özelliğine olanak sağlar.|Yes|
|Otomatik olarak biçimlendirme|Standart girintileme ve stil ile kodu yeniden biçimlendirin.|Hayır|
|Yer işaretleri|Düzenleyicide yer kaydetmenizi sağlar.|Yes|
|Girintiyi değiştirme|Seçili satırları girintiler veya girintilerini geri alar.|Yes|
|Akıllı girintileme|F# sınır kurallarına göre imleci otomatik olarak girintiler ve girintilerini siler.|Yes|
|[Metin bulma ve değiştirme](finding-and-replacing-text.md)|Bir dosya, proje veya çözümde aramanızı ve potansiyel olarak metni değiştirmenizi sağlar.|Yes|
|.NET API'si için tanıma gidin|İmleç bir .NET API'sini üzerine yerleştirerek .NET meta verilerinden oluşturulan kodu gösterir.|Hayır|
|Kullanıcı tanımlı API için tanıma git|İmleç tanımlandığı bir program varlığı üzerinde olduğunda imleci kodunda varlığın tanımlandığı konuma taşır.|Yes|
|Satıra Gitme|Bir dosyada satır numarasına göre belirli bir satıra gitmene olanak sağlar.|Yes|
|Dosyanın üst kısmında gezinti çubukları|İşlev adı gibi kodlarda konumlara atlama sağlar.|Yes|
|Blok Yapısı Yönergeleri|Önizleme için üzerine gelinen F# kapsamlarını gösteren yönergeleri gösterir.|Yes|
|[Anahat Oluşturma](outlining.md)|Daha küçük bir görünüm oluşturmak için kodunuzun bölümlerini daraltabilirsiniz.|Yes|
|Tabify|Boşlukları sekmelere dönüştürür.|Yes|
|Tür renklendirme|Tanımlı tür adlarını özel bir renkle gösterir.|Yes|
|Hızlı Bul. Bkz. Hızlı Bulma, Bulma ve Değiştirme Penceresi.|Bir dosya veya projede aramanızı sağlar.|Yes|
|**Ctrl tuşunu basılı tutarak** + **Tanıma** Git'e tıklayın|Tanıma Git'i **çağırmak için Ctrl** tuşunu basılı tutarak bir F# simgesine tıklamayı sağlar.|Yes|
|QuickInfo'dan Tanıma Git|Tanıma Git'i çağıran araç ipucu içinde tıklanabilir semboller.|Yes|
|Tamam'a gidin|**Ctrl** T aracılığıyla tüm F# yapıları için genel, belirsiz eşleşen gezintiyi + **sağlar.**|Yes|
|Satır Içi Yeniden Adlandırma|Bir sembolün satır içi tüm oluşumlarını yeniden adlandırıyor.|Yes|
|Tüm Başvuruları Bul|Bir kod tabanındaki bir sembolün tüm oluşumlarını bulur.|Yes|
|Ad kodu düzeltmeyi basitleştirme|F# sembolleri için gereksiz niteleyicileri kaldırır.|Yes|
|Kullanılmayan deyim `open` kodu düzeltmeyi kaldırma|Belgede yer alan `open` tüm gereksiz deyimleri kaldırır.|Yes|
|Kullanılmayan değer kodu düzeltmesi|Alt çizgi için kullanılmayan bir tanımlayıcının yeniden adlandırılacağı önerildi.|Yes|

Düzenleyicide kodu düzenleme ve Visual Studio özellikleri hakkında genel bilgi için [bkz. Düzenleyicide kod yazma.](writing-code-in-the-code-and-text-editor.md)

## <a name="intellisense-features"></a>IntelliSense özellikleri

Aşağıdaki tabloda, F# ile desteklenen ve desteklen IntelliSense özellikleri özetlenmiştir:

|Özellik|Açıklama|F# ile desteklensin mi?|
|-------|-----------|----------------|
|Arabirimleri otomatik olarak uygulama|Arabirim yöntemleri için kod saplamaları üretir.|Yes|
|Kod parçacıkları|Ortak kodlama yapılarından bir kitaplıktan konulara kodlar.|Hayır|
|Tam Sözcük|Siz yazarken sözcükleri ve adları tamamlayarak yazmayı kaydeder.|Yes|
|Otomatik tamamlama|Etkinleştirildiğinde, sözcük tamamlamanın siz yazarak ilk eşleşmeyi seçmesine neden olur. Bunun yerine, bir eşleşme seçmenizi beklemek veya **Ctrl Ara** Çubuğuna + **basabilirsiniz.**|Yes|
|Açılmamış ad alanlarındaki semboller için teklif tamamlama|Otomatik tamamlama ile, açılmamış bir ad alanı içinde bulunan eşleşen bir simge önerilir ve seçildiğinde ilgili deyimle `open` tamamlanması önerilir.|Yes|
|Kod öğeleri oluşturma|Çeşitli yapılar için saplama kodu oluşturmana olanak sağlar.|Hayır|
|Üyeleri Listeleme|Üye erişim işleci (.) yazarak bir türün üyelerini gösterir.|Yes|
|Kullanımı Düzenleme/Açma|C# içinde deyimleri **veya** F# içinde açık yönergeler **kullanılarak** başvurulan ad alanlarını düzenleyebilir.|Hayır|
|Parametre Bilgisi|Bir işlev çağrısı yazarak parametreler hakkında yararlı bilgiler gösterir.|Yes|
|Hızlı Bilgi|Kodundaki herhangi bir tanımlayıcının eksiksiz bildirimini görüntüler.|Yes|
|Otomatik küme ayracı tamamlama|F# ayraç gibi söz dizimi yapılarını işlemsel bir şekilde otomatik olarak tamamlar.|Yes|

IntelliSense hakkında genel bilgi için [bkz. IntelliSense kullanma.](using-intellisense.md)

## <a name="debugging-features"></a>Hata ayıklama özellikleri

Aşağıdaki tabloda, F# kodunda hata ayıklarken kullanılabilen özellikler özetlenmiştir:

|Özellik|Açıklama|F# ile desteklensin mi?|
|-------|-----------|----------------|
|Otomatik değişkenler penceresi|Otomatik veya geçici değişkenleri gösterir.|Hayır|
|Kesme noktaları|Hata ayıklama sırasında belirli noktalarda kod yürütmeyi duraklatmanizi sağlar.|Yes|
|Koşullu kesme noktaları|Yürütmenin duraklatıp duraklatmayacaklarını belirleyen bir koşulu test etmek için kesme noktaları sağlar.|Yes|
|Düzenle ve Devam Et|Hata ayıklayıcıyı durdurmadan ve yeniden başlatmadan çalışan bir programda hata ayıklarken kodun değiştirilmelerini ve derlerini sağlar.|Hayır|
|İfade değerlendirici|Çalışma zamanında kodu değerlendirir ve yürütür.|Hayır, ancak C# ifade değerlendiricisi kullanılabilir, ancak C# söz dizimi kullan gerekir.|
|Geçmiş hata ayıklama|Daha önce yürütülen koda adım adım çalışmana olanak sağlar.|Yes|
|Yerel öğeler penceresi|Yerel olarak tanımlanan değerleri ve değişkenleri gösterir.|Yes|
|İmleçe Çalıştır|İmleci içeren satıra ulaşıncaya kadar kodu yürütmenizi sağlar.|Yes|
|Adımla|Yürütmeyi ilerletin ve herhangi bir işlev çağrısına taşımayı sağlar.|Yes|
|Adım At|Geçerli yığın çerçevesinde yürütmeyi ilerletin ve herhangi bir işlev çağrısının gerisini taşımayı sağlar.|Yes|

Hata ayıklayıcısı hakkında genel Visual Studio için [bkz.](../debugger/index.yml)Visual Studio.

## <a name="additional-tools"></a>Ek araçlar

Aşağıdaki tabloda, Visual Studio araçları için F# desteği özetlenmiştir.

|Araç|Açıklama|F# ile desteklensin mi?|
|----|-----------|----------------|
|Çağrı Hiyerarşisi|Kodundaki işlev çağrılarının iç içe geçmiş yapısını görüntüler.|Hayır|
|Kod Ölçümleri|Kodunuz hakkında satır sayıları gibi bilgiler toplar.|Hayır|
|Sınıf Görünümü|Bir proje içinde kodun tür tabanlı bir görünümünü sağlar.|Hayır|
|[Hata Listesi penceresi](reference/error-list-window.md)|Kodda hataların listesini gösterir.|Yes|
|[F# Etkileşimli](/dotnet/fsharp/tutorials/fsharp-interactive/)|F# kodu yazmanızı (veya kopyalayıp yapıştırmanızı) ve projenizin binadan bağımsız olarak hemen çalıştırmanızı sağlar. Bu F# Etkileşimli Okuma, Değerlendirme, Yazdırma Döngüsü (REPL) penceresidir.|Yes|
|Nesne Tarayıcısı|Bir derlemede türleri görüntülemeye olanak sağlar.|Derlenmiş derlemelerde görünen F# türleri, tam olarak siz yazar gibi görünmez. F# türlerinin derlenmiş gösterimine göz atabilirsiniz, ancak türleri F# içinden görünen şekilde görüntü olamaz.|
|[Çıktı penceresi](reference/output-window.md)|Derleme çıkışını görüntüler.|Yes|
|Performans analizi|Kodunuzun performansını ölçmek için araçlar sağlar.|Yes|
|Özellik penceresi|Odak noktası olan geliştirme ortamında nesnenin özelliklerini görüntüler ve düzenlemeyi sağlar.|Yes|
|Sunucu Gezgini|Çeşitli sunucu kaynaklarıyla etkileşim kurmanın yollarını sağlar.|Yes|
|Çözüm Gezgini|Projeleri ve dosyaları görüntülemenizi ve yönetmenizi sağlar.|Yes|
|Görev Listesi|Kodunuzla ilgili iş öğelerini yönetmenizi sağlar.|Hayır|
|Projeleri test etmek|Kodunuzu test etmeye yardımcı olan özellikler sağlar.|Hayır|
|Araç Kutusu|Denetimler ve metin veya kod bölümleri gibi sürüklenebilir nesneler içeren sekmeleri görüntüler.|Yes|

## <a name="see-also"></a>Ayrıca bkz.

- [F# kılavuzu (.NET Framework)](/dotnet/fsharp/)
- [Kullanmaya başlayın F# ile Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)
