---
title: Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.FontsAndColors
- VS.ToolsOptionsPages.Environment.Fonts_And_Colors
- VS.Environment.Fonts And Colors
helpviewer_keywords:
- colors, customizing IDE
- Query and View Designer, customizing
- fonts, editors
- menus, customizing
- Table Designer, customizing
- Database Designer, customizing environment
- default colors
- accessibility, options
- editors, customizing
- designers, customizing environment
- defaults, colors
- printers, customizing
ms.assetid: c767d302-51ed-47a8-a527-c07bce2aa485
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d5c9edd47e3db43735d3c6e8f6a4ec1a881214e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595624"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu

**Seçenekler** iletişim kutusunun **Yazı Tipleri ve Renkler** sayfası, tümleşik geliştirme ortamındaki (IDE) çeşitli kullanıcı arabirimi öğeleri için özel bir yazı tipi ve renk düzeni oluşturmanıza olanak tanır. Bu iletişim kutusuna **Araçlar** > **Seçenekleri'ni**tıklayıp **ardından Çevre** > **Yazı Tipleri ve Renkleri'ni**seçerek erişebilirsiniz.

Renk düzeni değişiklikleri yaptığınız oturumsırasında etkili olmaz. Visual Studio'nun başka bir örneğini açarak ve değişikliklerinizin uygulanmasını beklediğiniz koşulları üreterek renk değişikliklerini değerlendirebilirsiniz.

**Ayarları için göster**

Yazı tipini ve renk düzenlerini değiştirebileceğiniz tüm kullanıcı arabirimi öğelerini listeler. Bu listeden bir öğe seçtikten **sonra, Görüntü öğelerinde**seçilen öğenin renk ayarlarını özelleştirebilirsiniz.

- **Metin Editörü**

     Metin Düzenleyicisi için yazı tipi stili, boyutu ve renkli görüntü ayarlarında yapılan değişiklikler varsayılan metin düzenleyicinizdeki metnin görünümünü etkiler. IDE dışında bir metin düzenleyicisinde açılan belgeler bu ayarlardan etkilenmez.

- **Yazıcı**

     Yazıcı için yazı tipi stili, boyutu ve renkli ekran ayarlarında yapılan değişiklikler, yazdırılan belgelerdeki metnin görünümünü etkiler.

    > [!NOTE]
    > Gerektiğinde, yazdırma için metin düzenleyicisinde görüntülenmek için kullanılandan farklı bir varsayılan yazı tipi seçebilirsiniz. Bu, hem tek bayt hem de çift bayt karakter içeren kod yazdırırken yararlı olabilir.

- **Deyim Tamamlama**

     Düzenleyicide deyim tamamlama açılır açılır açılır görünür metin için yazı tipi stili ve boyutunu değiştirir.

- **Düzenleyici Araç İpucu**

     Düzenleyicide görüntülenen Araç İpuçları'nda görünen metnin yazı tipi stilini ve boyutunu değiştirir.

- **Çevre Yazı Tipi**

     Için **göster ayarlarında**zaten ayrı bir seçeneği olmayan tüm IDE kullanıcı arabirimi öğeleri için yazı tipi stilini ve boyutunu değiştirir.

     ::: moniker range="vs-2017"

     Örneğin, bu seçenek Başlangıç **Sayfası** için geçerlidir, ancak **Çıktı** penceresini etkilemez.

     ::: moniker-end

- **[Tüm Metin Aracı Windows]**

     Bu öğenin yazı tipi stili, boyutu ve renkli görüntü ayarlarındaki değişiklikler, IDE'de çıktı bölmeleri bulunan araç pencerelerinde metnin görünümünü etkiler. Örneğin, Çıkış penceresi, Komut penceresi, Hemen penceresi, vb.

    > [!NOTE]
    > **[Tüm Metin Aracı Windows]** öğelerinin metninde yapılan değişiklikler, bunları yaptığınız oturumsırasında etkili olmaz. Bu değişiklikleri Visual Studio'nun başka bir örneğini açarak değerlendirebilirsiniz.

**Varsayılanları kullanma**

**Için Göster ayarlarında**seçilen liste öğesinin yazı tipini ve renk değerlerini sıfırlar. Diğer ekran düzenleri seçim için kullanılabilir olduğunda **Kullanım** düğmesi görüntülenir. Örneğin, Yazıcı için iki şema arasından seçim yapabilirsiniz.

**Yazı tipi (kalın yazı tipi sabit genişlikli yazı tiplerini gösterir)**

Sisteminizde yüklü tüm yazı tiplerini listeler. Açılan menü ilk göründüğünde, alan **için Göster ayarlarında** seçilen öğenin geçerli yazı tipi vurgulanır. Düzenleyicide hizalaması daha kolay olan sabit yazı tipleri kalın görünür.

**Boyut**

Vurgulanan yazı tipi için kullanılabilir nokta boyutlarını listeler. Yazı tipinin boyutunu değiştirmek, seçim **için Göster ayarları** için tüm **Görüntü öğelerini** etkiler.

**Öğeleri görüntüleme**

Ön plan ve arka plan rengini değiştirebileceğiniz öğeleri listeler.

> [!NOTE]
> **Düz Metin** varsayılan görüntü öğesidir. Bu nedenle, **PlainText'e** atanan özellikler, diğer görüntü öğelerine atanan özellikler tarafından geçersiz kılınacaktır. Örneğin, mavi rengi **PlainText'e,** yeşil rengi **tanımlayıcıya**atarsanız, tüm tanımlayıcılar yeşil renkte görünür. Bu örnekte, **Tanımlayıcı** özellikleri **PlainText** özelliklerini geçersiz kılar.

Görüntü öğelerinden bazıları şunlardır:

|Öğeyi görüntüleme|Açıklama|
|------------------|-----------------|
|**Düz Metin**|Editöre mesaj at.|
|**Seçilen Metin**|Düzenleyici nin odağı olduğunda geçerli seçime dahil edilen metin.|
|**Etkin Olmayan Seçili Metin**|Düzenleyici odağı kaybettiğinde geçerli seçime dahil edilen metin.|
|**Gösterge Marjı**|Kesme noktalarının ve yer imi simgelerinin görüntülendiği Kod Düzenleyicisi'nin solundaki kenar boşluğu.|
|**Çizgi Numaraları**|Her kod satırının yanında görünen isteğe bağlı sayılar|
|**Görünür Beyaz Alan**|Boşluklar, sekmeler ve sözcük kaydırma göstergeleri|
|**Yer işareti**|Yer imleri olan satırlar. **Yer imi** yalnızca gösterge kenar boşluğu devre dışı bırakıldığında görünür.|
|**Ayrayr Eşleştirme (Vurgu)**|Bu genellikle eşleme ayraçları için kalın biçimlendirme olduğunu vurgulayarak.|
|**Ayrayr Eşleştirme (Dikdörtgen)**|Vurgulama genellikle arka planda gri bir dikdörtgen.|
|**Kesme Noktası (Devre Dışı)**|Kullanılmadı.|
|**Kesme Noktası (Etkin)**|Basit kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyi kesme noktaları etkinse veya **Kesme Noktaları için Tüm Kaynak Satırı vurgulanırsa veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Kesme Noktası (Hata)**|Hata durumunda olan kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Yalnızca ekstre düzeyi kesme noktaları etkinse veya **Kesme Noktaları için Tüm Kaynak Satırı veya Geçerli Ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Kesme Noktası (Uyarı)**|Uyarı durumunda olan kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Yalnızca ekstre düzeyi kesme noktaları etkinse veya **Kesme Noktaları için Tüm Kaynak Satırı veya Geçerli Ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Kırılma Noktası - Gelişmiş (Devre Dışı)**|Devre dışı bırakılmış koşullu veya isabet sayılan kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Yalnızca ekstre düzeyi kesme noktaları etkinse veya **Kesme Noktaları için Tüm Kaynak Satırı veya Geçerli Ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Kesme Noktası - Gelişmiş (Etkin)**|Koşullu veya isabet sayılan kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Yalnızca ekstre düzeyi kesme noktaları etkinse veya **Kesme Noktaları için Tüm Kaynak Satırı veya Geçerli Ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Kesme Noktası - Gelişmiş (Hata)**|Hata durumunda olan koşullu veya isabet sayılmış kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Yalnızca ekstre düzeyi kesme noktaları etkinse veya **Kesme Noktaları için Tüm Kaynak Satırı veya Geçerli Ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Kesme Noktası - Gelişmiş (Uyarı)**|Uyarı durumunda olan koşullu veya isabet sayılmış kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Yalnızca ekstre düzeyi kesme noktaları etkinse veya **Kesme Noktaları için Tüm Kaynak Satırı veya Geçerli Ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Kesme Noktası - Eşlenen (Devre Dışı)**|Devre dışı bırakılan kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme Noktası - Eşlenen (Etkin)**|Eşlenen kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme Noktası - Eşlenen (Hata)**|Bir hata durumunda eşlenen kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme Noktası - Eşlenen (Uyarı)**|Uyarı durumunda eşlenen kesme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**C/C++ Kullanıcı Anahtar Kelimeleri**|`#define` Yönerge ile tanımlanan belirli bir kod dosyası içinde sabit.|
|**Çağrı İadesi**|Hata ayıklama yaparken bağlam üstten olmayan yığın çerçevesine geçildiğinde çağrı dönüş noktalarını gösteren kaynak ifadeleri veya satırların vurgu rengini belirtir.|
|**Kod Snippet Bağımlı Alan**|Geçerli düzenlenecek alan değiştirildiğinde güncellenecek bir alan.|
|**Kod Snippet Alanı**|Bir kod parçacığı etkin olduğunda kullanılabilir alan.|
|**Katlanabilir Metin**|Kod Düzenleyicisi içinde görüntüye girip çıkabilen bir metin veya kod bloğu.|
|**Yorum**|Kod açıklamaları.|
|**Derleyici Hatası**|Derleyici hatası belirten editörde mavi dalgalı.|
|**Kapsama Dokunulmaz Alan**|Birim testi kapsamında olmayan kod.|
|**Kapsama Kısmen Dokunulan Alan**|Birim testi tarafından kısmen kapsanan kod.|
|**Kapsama Dokundu Alanı**|Birim testi tarafından tamamen kapsanan kod.|
|**CSS Yorum**|Basamaklı Stil Sayfaları bir yorum. Örnek:<br /><br /> /* yorum\*/|
|**CSS Anahtar Kelime**|Basamaklı Stil Sayfasındaki Anahtar Kelimeler.|
|**CSS Özellik Adı**|Arka Plan gibi bir özelliğin adı.|
|**CSS Özellik Değeri**|Mavi gibi bir özelliğe atanan değer.|
|**CSS Seçici**|Karşılık gelen kuralın hangi öğelere uygulandığını tanımlayan bir dize. Seçici, 'H1' gibi basit bir seçici veya birkaç basit seçiciden oluşan 'H1 B' gibi bağlamsal seçici olabilir.|
|**CSS dize değeri**|Basamaklı Stil Sayfaları'nda bir dize.|
|**Geçerli liste konumu**|Çıkış penceresi veya Sonuçları Bul pencereleri gibi bir liste araç penceresinde gezinilen geçerli satır.|
|**Geçerli Ekstre**|Hata ayıklama yaparken geçerli adım konumunu gösteren kaynak ifade veya satır için vurgu rengini belirtir.|
|**Hata Ayıklama Verileri Değiştirildi**|**Kayıt** ve **Bellek** pencerelerinde değiştirilen verileri görüntülemek için kullanılan metnin rengi.|
|**Tanım Penceresi Arka Planı**|**Kod Tanımı** penceresinin arka plan rengi.|
|**Tanım Penceresi Geçerli Eşleşme**|**Kod Tanımı** penceresindegeçerli tanım.|
|**Dosya Adını Sökme**|**Dosya** adını sökme penceresinin içinde görüntülemek için kullanılan metnin rengi.|
|**Kaynak Sökme**|**Sökme** penceresiiçindeki kaynak çizgileri görüntülemek için kullanılan metnin rengi.|
|**Sökme Simgesi**|**Sökme** penceresinde sembol adlarını görüntülemek için kullanılan metnin rengi.|
|**Metni Sökme**|**Disassembly** penceresi içinde op-kod ve verileri görüntülemek için kullanılan metnin rengi.|
|**Dışlanan Kod**|Derlenmeyecek kod, koşullu bir önişlemci yönergesi başına `#if`.|
|**Tanımlayıcı**|Sınıf adları, yöntem adları ve değişken adları gibi koddaki tanımlayıcılar.|
|**Anahtar kelime**|Verilen dilin anahtar kelimeleri ayrılmıştır. Örneğin: sınıf ve ad alanı.|
|**Bellek Adresi**|Adres sütununu **Bellek** penceresinin içinde görüntülemek için kullanılan metnin rengi.|
|**Bellek Değiştirildi**|Bellek **penceresinde** değiştirilen verileri görüntülemek için kullanılan metnin rengi.|
|**Bellek Verileri**|**Bellek** penceresi içindeki verileri görüntülemek için kullanılan metnin rengi.|
|**Bellek Okunamayan**|**Bellek** penceresinde okunamayan bellek alanlarını görüntülemek için kullanılan metnin rengi.|
|**Numarası**|Gerçek sayısal değeri temsil eden koddaki bir sayı.|
|**Işleç**|+, -ve !=gibi işleçler.|
|**Farklı Bir Hata**|Diğer hata squiggles tarafından kapsanmayan diğer hata türleri. Şu anda, bu Edit ve Continue kaba edit içerir.|
|**Önişlemci Anahtar Kelime**|#include gibi önişlemci tarafından kullanılan anahtar kelimeler.|
|**Salt Okunur Bölge**|Düzenlenemeyen kod. Örneğin Kod Tanımı Görünümü penceresinde görüntülenen kod veya Edit ve Continue sırasında değiştirilemeyen kod.|
|**Arka Planı Yeniden Düzenleme**|**Önizleme Değişiklikleri** iletişim kutusunun arka plan rengi.|
|**Geçerli Alanı Yeniden Düzenleme**|**Önizleme Değişiklikleri** iletişim kutusunda yeniden dizilecek geçerli öğenin arka plan rengi.|
|**Bağımlı Alanı Yeniden Düzenleme**|**Önizleme Değişiklikleri** iletişim kutusunda yeniden dizilecek öğeöğesir öğelendirmek için öğenin başvurularırenk.|
|**Verileri Kaydedin**|**Registers** penceresindeki verileri görüntülemek için kullanılan metnin rengi.|
|**Kayıt NAT**|Tanınmayan verileri ve Nesneleri **Registers** penceresi içinde görüntülemek için kullanılan metnin rengi.|
|**Akıllı Etiket**|Akıllı etiketler çağrıldığınızda anahattı belirtmek için kullanılır.|
|**SQL DML İşaretçisi**|Transact-SQL düzenleyicisi için geçerlidir. Bu düzenleyicideki DML deyimleri varsayılan olarak sınırlayıcı mavi bir kutuyla işaretlenir.|
|**Bayat Kod**|Bir güncelleştirmeyi bekleyen geçersiz kod. Bazı durumlarda, Edit ve Continue kod değişikliklerini hemen uygulayamaz, ancak hata ayıklama devam ettikçe bunları daha sonra uygular. Bu, şu anda yürütülen işlevi çağırması gereken bir işlevi düzenlemeniz veya çağrı yığınında bekleyen bir işleve 64 bayttan fazla yeni değişken eklerseniz oluşur. Bu durumda hata ayıklayıcı bir "Eski Kod Uyarısı" iletişim kutusu görüntüler ve yerine geçen kod, söz konusu işlev bitene ve yeniden çağrılana kadar yürütmeye devam eder. Edit ve Devam, kod değişikliklerini o anda uygular.|
|**Dize**|String literals.|
|**String (C# @ Verbatim)**|C# kelimesi kelimesine yorumlanan string literals. Örnek:<br /><br /> @"x"|
|**Sözdizimi Hatası**|Ayrışdıran hatalar.|
|**Görev Listesi Kısayolu**|Bir satıra **Görev Listesi** kısayolu eklenirse ve gösterge kenar boşluğu devre dışı bırakılırsa, satır vurgulanır.|
|**Tracepoint (Devre Dışı)**|Kullanılmadı.|
|**İzleme Noktası (Etkin)**|Basit izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyinde izleme noktaları etkinse veya **kesme noktaları için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Tracepoint (hata)**|Hata durumunda olan izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyinde izleme noktaları etkinse veya **kesme noktaları için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**İzleme Noktası (Uyarı)**|Uyarı durumunda olan izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyinde izleme noktaları etkinse veya **kesme noktaları için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Tracepoint - Gelişmiş (Devre Dışı)**|Devre dışı bırakılmış koşullu veya isabet sayılan izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyinde izleme noktaları etkinse veya **kesme noktaları için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Tracepoint - Gelişmiş (Etkin)**|Koşullu veya isabet sayılmış izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyinde izleme noktaları etkinse veya **kesme noktaları için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Tracepoint - Gelişmiş (Hata)**|Bir hata durumunda koşullu veya isabet sayılmış izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyinde izleme noktaları etkinse veya **kesme noktaları için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Tracepoint - Gelişmiş (Uyarı)**|Uyarı durumunda olan koşullu veya isabet sayılmış izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Bu seçenek yalnızca ekstre düzeyinde izleme noktaları etkinse veya **kesme noktaları için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse geçerlidir.|
|**Tracepoint - Eşlenen (Devre Dışı)**|Devre dışı bırakılmış izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Tracepoint - Eşlenen (Etkin)**|Eşlenen izleme noktalarını içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Tracepoint - Eşlenen (Hata)**|Bir hata durumunda eşlenen izleme noktaları içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Tracepoint - Eşlenen (Uyarı)**|Uyarı durumunda eşlenen izleme noktalarını içeren ifadeler veya satırlar için vurgu rengini belirtir. Ekstre düzeyi kesme noktaları etkinse VEYA kesme noktaları **için tüm kaynak satırı veya geçerli ekstre** seçeneği [Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda](../../debugger/general-debugging-options-dialog-box.md)seçilirse, ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kaydedin'den sonra Değişiklikleri İzleme**|Dosya açıldığından beri değiştirilen ancak diske kaydedilen kod satırları.|
|**Kaydetmeden önce Değişiklikleri İzleme**|Dosya açıldığından beri değiştirilen ancak diske kaydedilmemiş kod satırları.|
|**Kullanıcı Türleri**|Kullanıcılar tarafından tanımlanan türler.|
|**Kullanıcı Türleri (Temsilciler)**|Temsilciler için renk yazın.|
|**Kullanıcı Türleri (Enums)**|Enumlar için kullanılan rengi yazın.|
|**Kullanıcı Türleri (Arayüzler)**|Arabirimler için renk yazın.|
|**Kullanıcı Türleri (Değer türleri)**|C#'daki yapı türleri gibi değer türleri için renk yazın.|
|**Visual Basic Read Only İşaretleyici**|Özel durumlar, yöntem tanımı ve yapraksız çağrı çerçeveleri gibi EnC'yi atamak için kullanılan Visual Basic'e özgü bir işaretçi.|
|**Uyarı**|Derleyici uyarıları.|
|**Uyarı Satırları Yolu**|Statik Çözümleme uyarı satırları için kullanılır.|
|**XML Öznitelik**|Öznitelik adları.|
|**XML Öznitelik Tırnaklar**|XML öznitelikleri için teklif karakterleri.|
|**XML Öznitelik Değeri**|XML özniteliklerinin içeriği.|
|**XML Cdata Bölümü**|İçindekiler \<! [CDATA[...]] >.|
|**XML Yorum**|!-- --> \<içindekiler.|
|**XML Delimiter**|XML Sözdizimi sınırlayıcılar, < dahil, <?, <!, \<!--, -->, ? \>, \<! [, ]] > ve [, ].|
|**XML Doküman Özniteliği**|Param adı="I"i" >"i" renklendirildiği \<bir xml dokümantasyon özniteliğinin değeri.|
|**XML Doc Yorum**|Xml dokümantasyon yorumlarına ekteki yorumlar.|
|**XML Doküman Etiketi**|XML doküman yorumlarında etiketler, örneğin<br /><br /> /// \<özet>.|
|**XML Anahtar Kelime**|CDATA, IDREF ve NDATA gibi DTD anahtar kelimeler.|
|**XML Adı**|Öğe adları ve İşlem Talimatları hedef adı.|
|**XML İşleme Talimatı**|Hedef ad dahil değil, İşlem talimatlarının içeriği.|
|**XML Metni**|Düz metin öğesi içeriği.|
|**XSLT Anahtar Kelime**|XSLT öğe adları.|

**Öğe ön planda**

**Görüntü**öğelerinde seçilen öğenin ön planda seçebileceğiniz kullanılabilir renkleri listeler. Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntü düzeni tutması gerektiğinden, metnin ön plan rengini değiştirmek Derleyici Hatası, Anahtar Kelime veya Operatör gibi öğelerin varsayılanlarını da değiştirir.

**Automatic**

Öğeler, ön plan rengini **Düz Metin**gibi diğer görüntü öğelerinden devralabilir. Bu seçeneği kullanarak, devralınan bir görüntü öğesinin rengini değiştirdiğinizde, ilgili görüntü öğelerinin rengi de otomatik olarak değişir. Örneğin, **Derleyici Hatası** için **Otomatik** değeri seçtiyseniz ve daha sonra **Düz Metin** rengini Kırmızı olarak değiştirdiyseniz, **Derleyici Hatası** da otomatik olarak Kırmızı rengi devralır.

**Varsayılan**

Visual Studio'yu ilk açtığınızda öğe için görünen renk. **Varsayılanları Kullan** düğmesini tıklattığınızda bu renk sıfırlanır.

**Özel**

Görüntü öğeleri listesinde seçilen öğe için özel bir renk ayarlamanızı sağlamak için Renk iletişim kutusunu görüntüler.

> [!NOTE]
> Özel renkleri tanımlama yeteneğiniz, bilgisayarınızın ekranının renk ayarlarıyla sınırlı olabilir. Örneğin, bilgisayarınız 256 renk görüntülenecek şekilde ayarlanmışsa ve **Renk** iletişim kutusundan özel bir renk seçerseniz, IDE varsayılan olarak kullanılabilir en yakın **Temel renge** göre dir ve **Renk** önizleme kutusunda siyah rengi görüntüler.

**Öğe arka planı**

**Görüntü öğelerinde**seçilen öğe için bir arka plan rengi seçebileceğiniz bir renk paleti sağlar. Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntü düzeni tutması gerektiğinden, metnin arka plan rengini değiştirmek derleyici hatası, anahtar kelime veya operatör gibi öğelerin varsayılanlarını da değiştirir.

**Automatic**

Öğeler, düz **metin**gibi diğer görüntü öğelerinden arka plan rengini devralabilir. Bu seçeneği kullanarak, devralınan bir görüntü öğesinin rengini değiştirdiğinizde, ilgili görüntü öğelerinin rengi de otomatik olarak değişir. Örneğin, **Derleyici Hatası** için **Otomatik** değeri seçtiyseniz ve daha sonra **Düz Metin** rengini Kırmızı olarak değiştirdiyseniz, **Derleyici Hatası** da otomatik olarak Kırmızı rengi devralır.

**Varsayılan**

Visual Studio'yu ilk açtığınızda öğe için görünen renk. **Varsayılanları Kullan** düğmesini tıklattığınızda bu renk sıfırlanır.

**Özel**

Görüntü öğeleri listesinde seçilen öğe için özel bir renk ayarlamanızı sağlamak için Renk iletişim kutusunu görüntüler.

**Kalın**

Seçili **Ekran öğelerinin** metnini kalın metinde görüntülemek için bu seçeneği belirleyin. Kalın metni editörde tanımlamak daha kolaydır.

**Örnek**

Seçilen öğeleri göster **ve** görüntüleme **ayarları** için yazı tipi stili, boyutu ve renk düzeninin bir örneğini görüntüler. Farklı biçimlendirme seçenekleriyle denemeler yaptığınızda sonuçları önizlemek için bu kutuyu kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler İletişim Kutusu](../../ide/reference/options-dialog-box-visual-studio.md)
- [Nasıl Yapılır: Yazı Tiplerini ve Renkleri Değiştirme](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
