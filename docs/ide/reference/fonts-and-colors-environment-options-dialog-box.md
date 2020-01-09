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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595624"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu

**Seçenekler** Iletişim kutusunun **yazı tipleri ve renkler** sayfası, TÜMLEŞIK geliştirme ortamındaki (IDE) çeşitli kullanıcı arabirimi öğeleri için özel bir yazı tipi ve renk düzeni ayarlamanıza olanak sağlar. Bu iletişim kutusuna **araçlar** > **Seçenekler**' e tıklayıp, ardından **yazı tipleri ve renkler** > **ortam** ' ı seçerek erişebilirsiniz.

Renk şeması değişiklikleri, yaptığınız oturum sırasında etkili olmaz. Visual Studio 'nun başka bir örneğini açarak ve değişikliklerinizin uygulanmasını istediğiniz koşulları üreterek renk değişikliklerini değerlendirebilirsiniz.

**Ayarları göster**

Yazı tipi ve renk düzenlerini değiştirebileceğiniz tüm Kullanıcı arabirimi öğelerini listeler. Bu listeden bir öğe seçtikten sonra, **görüntüleme öğelerinde**seçilen öğenin renk ayarlarını özelleştirebilirsiniz.

- **Metin Düzenleyici**

     Metin Düzenleyicisi için yazı tipi stili, boyutu ve renk görüntüleme ayarlarındaki değişiklikler, varsayılan metin düzenleyicinizdeki metnin görünümünü etkiler. IDE dışında bir metin düzenleyicisinde açılan belgeler bu ayarlardan etkilenmeyecektir.

- **Yazıcıda**

     Yazıcı için yazı tipi stili, boyutu ve renk görüntüleme ayarlarındaki değişiklikler yazdırılan belgelerdeki metnin görünümünü etkiler.

    > [!NOTE]
    > Gerektiğinde, yazdırma için metin düzenleyicisinde görüntülenmek üzere kullanılandan farklı bir varsayılan yazı tipi seçebilirsiniz. Bu, hem tek baytlı hem de çift baytlık karakterler içeren kodu yazdırırken yararlı olabilir.

- **Ekstre tamamlama**

     Düzenleyicide ifade tamamlanma açılır penceresinde görünen metnin yazı tipi stilini ve boyutunu değiştirir.

- **Düzenleyici araç Ipucu**

     Düzenleyicide görüntülenen araç Ipuçlarında görüntülenen metnin yazı tipi stilini ve boyutunu değiştirir.

- **Ortam yazı tipi**

     **Görüntüleme ayarları**' nda ayrı bir seçeneğe sahip olmayan tüm IDE Kullanıcı arabirimi öğelerinin yazı tipi stilini ve boyutunu değiştirir.

     ::: moniker range="vs-2017"

     Örneğin, bu seçenek **Başlangıç sayfası** için geçerlidir ancak **Çıkış** penceresini etkilemez.

     ::: moniker-end

- **[Tüm metin araç pencereleri]**

     Bu öğe için yazı tipi stili, boyutu ve renk görüntüleme ayarlarındaki değişiklikler, IDE 'de çıkış bölmeleri olan araç pencerelerinin metin görünümünü etkiler. Örneğin, çıkış penceresi, Komut penceresi, acil pencere vb.

    > [!NOTE]
    > **[Tüm metin araç pencereleri]** öğelerinin metninde yapılan değişiklikler, bunları yaptığınız oturum sırasında etkili olmaz. Visual Studio 'nun başka bir örneğini açarak, bu değişiklikleri değerlendirebilirsiniz.

**Varsayılanları Kullan**

**Ayarlarını göster**bölümünde seçilen liste öğesinin yazı tipi ve renk değerlerini sıfırlar. Diğer görüntüleme düzenleri seçime uygun olduğunda **kullan** düğmesi görünür. Örneğin, yazıcı için iki düzen arasından seçim yapabilirsiniz.

**Yazı tipi (kalın tür sabit genişlikli yazı tiplerini gösterir)**

Sisteminizde yüklü olan tüm yazı tiplerini listeler. Açılan menü ilk göründüğünde, **ayarları göster** alanında seçilen öğenin geçerli yazı tipi vurgulanır. Düzenleyicide daha kolay bir şekilde hizalanmanız gereken sabit yazı tipleri — kalın olarak görünür.

**Boyut**

Vurgulanan yazı tipi için kullanılabilir nokta boyutlarını listeler. Yazı tipinin boyutunu değiştirmek, seçime **yönelik ayarları göster** Için tüm **görüntüleme öğelerini** etkiler.

**Öğeleri görüntüle**

Ön plan ve arka plan rengini değiştirebileceğiniz öğeleri listeler.

> [!NOTE]
> **Düz metin** varsayılan görüntüleme öğesidir. Bu nedenle, **düz metine** atanan özellikler diğer görüntü öğelerine atanan özellikler tarafından geçersiz kılınır. Örneğin, maviyi **düz metin** olarak ve yeşil renkle **tanımlayıcıya**atarsanız, tüm tanımlayıcılar yeşil renkte görünür. Bu örnekte, **tanımlayıcı** özellikleri **düz metin** özelliklerini geçersiz kılar.

Bazı görüntü öğeleri şunlardır:

|Öğeyi görüntüle|Açıklama|
|------------------|-----------------|
|**Düz metin**|Düzenleyicideki metin.|
|**Seçili metin**|Düzenleyici odağa sahip olduğunda geçerli seçime dahil edilen metin.|
|**Etkin olmayan seçili metin**|Düzenleyici odağı kaybettiği zaman geçerli seçime dahil edilen metin.|
|**Gösterge kenar boşluğu**|Kod düzenleyicisinin sol tarafındaki kenar boşluğu, kesme noktaları ve yer işareti simgeleri görüntülenir.|
|**Satır numaraları**|Her kod satırının yanında görünen isteğe bağlı sayılar|
|**Görünür boşluk**|Boşluklar, sekmeler ve sözcük kaydırmalı göstergeler|
|**Yer işareti**|Yer işaretleri içeren satırlar. **Yer işareti** yalnızca Gösterge kenar boşluğu devre dışıysa görünür.|
|**Ayraç eşleştirme (vurgula)**|Genellikle eşleşen küme ayraçları için kalın biçimlendirme olan vurgulama.|
|**Ayraç eşleştirme (dikdörtgen)**|Genellikle arka planda gri dikdörtgen olan vurgulama.|
|**Kesme noktası (devre dışı)**|Kullanılmıyor.|
|**Kesme noktası (etkin)**|İfadeler veya basit kesme noktaları içeren çizgiler için vurgu rengi belirtir. Bu seçenek yalnızca, bildirim düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**Kesme noktası (hata)**|Bir hata durumunda olan kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası (uyarı)**|Uyarı durumunda olan kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (devre dışı)**|Devre dışı bırakılmış koşullu veya isabet saymalı kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (etkin)**|Deyim veya koşullu veya isabet saymalı kesme noktaları içeren çizgiler için vurgu rengi belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (hata)**|Bir hata durumunda olan koşullu veya isabet sayılı kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (uyarı)**|Uyarı durumundaki koşullu veya isabet saymalı kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-eşlenmiş (devre dışı)**|Devre dışı eşlenmiş kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme noktası-eşlenmiş (etkin)**|İfadelerin veya eşlenmiş kesme noktaları içeren satırların vurgu rengini belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme noktası-eşlenmiş (hata)**|Bir hata durumunda, eşleşen kesme noktaları içeren deyimlerin veya satırların vurgu rengini belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme noktası-eşlenmiş (uyarı)**|Bir uyarı durumunda eşlenmiş kesme noktaları içeren deyimler veya çizgiler için vurgu rengi belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**C/C++ Kullanıcı anahtar sözcükleri**|`#define` yönergesinin aracılığıyla tanımlanan belirli bir kod dosyası içindeki bir sabit.|
|**Çağrı dönüşü**|Hata ayıklama sırasında bağlam en üst olmayan yığın çerçevesine dönüştürüldüğünde, kaynak deyimleri veya çağrı dönüş noktalarını belirten çizgiler için vurgu rengi belirtir.|
|**Kod parçacığına bağımlı alan**|Geçerli düzenlenebilir alan değiştirildiğinde güncellenecek alan.|
|**Kod parçacığı alanı**|Bir kod parçacığı etkin olduğunda düzenlenebilir alan.|
|**Daraltılabilir metin**|Kod Düzenleyicisi içinde ve görünümün dışına geçiş yapılabilir bir metin veya kod bloğu.|
|**Yorum**|Kod açıklamaları.|
|**Derleyici hatası**|Düzenleyicide bir derleyici hatası gösteren mavi dalgalı çizgiler.|
|**Dokunulmayan kapsam alanı**|Birim testi kapsamında olmayan kod.|
|**Kapsam kısmen dokunulmaz alanı**|Birim testinin kısmen kapsadığı kod.|
|**Kapsam dokunulmaz alanı**|Bir birim testinin tamamen kapsadığı kod.|
|**CSS yorumu**|Geçişli Stil Sayfaları bir yorum. Örneğin:<br /><br /> /* yorum \*/|
|**CSS anahtar sözcüğü**|Basamaklı stil sayfasındaki anahtar sözcükler.|
|**CSS özellik adı**|Arka plan gibi bir özelliğin adı.|
|**CSS özellik değeri**|Mavi gibi bir özelliğe atanan değer.|
|**CSS seçici**|Karşılık gelen kuralın hangi öğelerin uygulanacağını tanımlayan bir dize. Seçici, bir ' H1 ' gibi basit bir seçici ya da birkaç basit seçicisinden oluşan ' H1 B ' gibi bağlamsal seçiciye sahip olabilir.|
|**CSS dize değeri**|Geçişli Stil Sayfaları bir dize.|
|**Geçerli liste konumu**|Geçerli satır, çıkış penceresi veya sonuçları Bul pencereleri gibi bir liste aracı penceresinde gezinilebilir.|
|**Geçerli Ifade**|Hata ayıklarken geçerli adım konumunu gösteren kaynak deyimin veya çizginin vurgu rengini belirtir.|
|**Hata ayıklayıcı verileri değiştirildi**|**Yazmaçların** ve **bellek** pencerelerinin içindeki değiştirilen verileri göstermek için kullanılan metnin rengi.|
|**Tanım penceresi arka planı**|**Kod tanımı** penceresinin arka plan rengi.|
|**Tanım penceresi geçerli eşleşme**|**Kod tanımı** penceresindeki geçerli tanım.|
|**Ayrıştırılmış dosya adı**|**Ayrıştırma** penceresinin içindeki dosya adı sonlarını göstermek için kullanılan metnin rengi.|
|**Ayrıştırılmış kaynak**|**Ayrıştırma** penceresinin içindeki kaynak satırları göstermek için kullanılan metnin rengi.|
|**Ayrıştırılmış kod simgesi**|**Ayrıştırma** penceresinin içindeki sembol adlarını göstermek için kullanılan metin rengi.|
|**Ayrıştırılmış kod metni**|İşlem kodunu ve verileri **ayrıştırma** penceresi içinde göstermek için kullanılan metnin rengi.|
|**Dışlanan kod**|`#if`gibi bir koşullu Önişlemci yönergesine göre derlenmemelidir.|
|**Tanımlayıcısını**|Kod içindeki tanımlayıcılar, sınıf adları, yöntem adları ve değişken adları gibi.|
|**Sözcükle**|Verilen dile ayrılan dil için anahtar sözcükler. Örneğin: sınıf ve ad alanı.|
|**Bellek adresi**|**Bellek** penceresi içindeki adres sütununu göstermek için kullanılan metin rengi.|
|**Bellek değişti**|**Bellek** penceresi içindeki değiştirilen verileri göstermek için kullanılan metnin rengi.|
|**Bellek verileri**|**Bellek** penceresi içindeki verileri göstermek için kullanılan metin rengi.|
|**Bellek okunamaz**|**Bellek** penceresi içindeki okunamaz bellek alanını göstermek için kullanılan metnin rengi.|
|**Sayı**|Kodda gerçek bir sayısal değeri temsil eden bir sayı.|
|**İşleci**|+,-, Ve! = gibi işleçler.|
|**Diğer hata**|Diğer hata türleri diğer hata dalgalı çizgiler kapsamına girmeyen bir hata oluştu. Şu anda, Düzenle ve devam et 'de işlenmemiş düzenlemelerini içerir.|
|**Önişlemci anahtar sözcüğü**|#İnclude gibi Önişlemci tarafından kullanılan anahtar sözcükler.|
|**Salt okuma bölgesi**|Düzenlenemeyen kod. Örneğin, kod tanımı görünümü penceresinde veya Düzenle ve devam et sırasında değiştirilemeyen kodda görüntülenen kod.|
|**Yeniden düzenleme arka planı**|**Değişiklikleri Önizle** iletişim kutusunun arka plan rengi.|
|**Geçerli alanı yeniden düzenleme**|**Değişiklikleri Önizle** iletişim kutusunda yeniden düzenlenmiş olacak geçerli öğenin arka plan rengi.|
|**Bağımlı alanı yeniden düzenleme**|**Değişiklikleri Önizle** iletişim kutusunda yeniden düzenlenmiş olacak öğe başvurularının rengi.|
|**Verileri kaydetme**|**Kayıt** penceresi içindeki verileri göstermek için kullanılan metin rengi.|
|**NAT Kaydet**|**Kayıt** penceresi içindeki tanınmayan verileri ve nesneleri göstermek için kullanılan metin rengi.|
|**Akıllı etiket**|Akıllı etiketler çağrıldığında anahattı göstermek için kullanılır.|
|**SQL DML Işaretçisi**|Transact-SQL Düzenleyicisi için geçerlidir. Bu düzenleyicideki DML deyimleri, varsayılan olarak bir sınırlayıcı mavi kutusuyla işaretlenir.|
|**Eski kod**|Yenisiyle değiştirilen kod bir güncelleştirme bekliyor. Bazı durumlarda, Düzenle ve devam et, kod değişikliklerini hemen uygulayamaz, ancak hata ayıklamaya devam ederken bunları daha sonra uygulayacaktır. Bu, şu anda yürütülmekte olan işlevi çağırması gereken bir işlevi düzenlerseniz veya çağrı yığınında bekleyen bir işleve 64 bayttan fazla yeni değişken eklerseniz oluşur. Bu durumda, hata ayıklayıcı bir "eski kod uyarısı" iletişim kutusu görüntüler ve söz konusu işlev bitene kadar yerine geçilen kod yürütülmeye devam eder ve yeniden çağırılır. Düzenle ve devam et, kod değişikliklerini o zaman uygular.|
|**Dize**|Dize sabit değerleri.|
|**Dize (C# @ harfine)**|İçindeki dize sabit C# değerleri, tam olarak yorumlanır. Örneğin:<br /><br /> @"x"|
|**Söz dizimi hatası**|Ayrıştırma hataları.|
|**Görev Listesi kısayolu**|Bir satıra **görev listesi** kısayolu eklenirse ve gösterge kenar boşluğu devre dışıysa, çizgi vurgulanır.|
|**İzleme noktası (devre dışı)**|Kullanılmıyor.|
|**İzleme noktası (etkin)**|Basit izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası (hata)**|Bir hata durumunda olan izleme noktalarını içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası (uyarı)**|Uyarı durumunda olan izleme noktalarını içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (devre dışı)**|Devre dışı bırakılmış koşullu veya isabet saymalı izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (etkin)**|Koşullu veya isabet saymalı izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (hata)**|Bir hata durumunda olan koşullu veya isabet sayılı izleme noktaları içeren deyimler veya çizgiler için vurgu rengi belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (uyarı)**|Uyarı durumunda olan koşullu veya isabet sayılı izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-eşlenmiş (devre dışı)**|Devre dışı eşlenmiş izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**İzleme noktası-eşlenmiş (etkin)**|Eşlenen izleme noktalarını içeren deyimler veya çizgiler için vurgu rengi belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**İzleme noktası-eşlenmiş (hata)**|Bir hata durumunda, eşlenmiş izleme noktalarını içeren deyimler veya çizgiler için vurgu rengi belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**İzleme noktası-eşlenmiş (uyarı)**|Uyarı durumunda, eşlenmiş izleme noktalarını içeren deyimler veya çizgiler için vurgu rengi belirtir. İfade düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını VURGULA** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kaydettikten sonra değişiklikleri izle**|Dosya açılmadan, ancak diske kaydedildiğinden beri değiştirilen kod satırları.|
|**Kaydetmeden önce değişiklikleri izle**|Dosyanın açıldığı ve diske kaydedilmesinden sonra değiştirilen kod satırları.|
|**Kullanıcı türleri**|Kullanıcılar tarafından tanımlanan türler.|
|**Kullanıcı türleri (Temsilciler)**|Temsilciler için Color yazın.|
|**Kullanıcı türleri (numaralandırmalar)**|Numaralandırmalar için kullanılan renk türü.|
|**Kullanıcı türleri (arabirimler)**|Arabirimler için Color yazın.|
|**Kullanıcı türleri (değer türleri)**|İçindeki C#yapılar gibi değer türleri için Color yazın.|
|**Visual Basic salt okuma Işaretçisi**|Özel durum bölgeleri, yöntem tanımı ve yaprak olmayan çağrı çerçeveleri gibi EnC 'yi belirlemek için kullanılan Visual Basic özgü bir işaretleyici.|
|**Uyarı**|Derleyici uyarıları.|
|**Uyarı satırları yolu**|Statik analiz uyarı satırları için kullanılır.|
|**XML özniteliği**|Öznitelik adları.|
|**XML öznitelik teklifleri**|XML öznitelikleri için tırnak karakterleri.|
|**XML öznitelik değeri**|XML özniteliklerinin içeriği.|
|**XML CDATA bölümü**|\<içeriği! [CDATA [...]] >.|
|**XML açıklaması**|\<!----> içeriği.|
|**XML sınırlayıcısı**|<, <?, <!, \<!--,--> da dahil olmak üzere XML sözdizimi sınırlayıcıları?\>, \<! [, ]] > ve [,].|
|**XML doc özniteliği**|\<param Name = "I" gibi bir XML belgesi özniteliğinin değeri, "I" nin renklendirilme olduğu >.|
|**XML belgesi açıklaması**|XML belgeleri yorumlarına eklenen açıklamalar.|
|**XML belge etiketi**|XML belgesi açıklamalarındaki Etiketler, örneğin<br /><br /> Özet > /// \<.|
|**XML anahtar sözcüğü**|CDATA, ıDREF ve NDATA gibi DTD anahtar sözcükleri.|
|**XML adı**|Öğe adları ve Işleme yönergeleri hedef adı.|
|**XML Işleme yönergesi**|Işleme yönergelerinin içerikleri, hedef adı dahil değildir.|
|**XML metni**|Düz metin öğesi içeriği.|
|**XSLT anahtar sözcüğü**|XSLT öğe adları.|

**Öğe ön planı**

**Görüntüleme öğelerinde**seçilen öğenin ön planı için seçebileceğiniz kullanılabilir renkleri listeler. Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntüleme düzenini koruduğundan, metnin ön plan rengini değiştirmek de derleyici hatası, anahtar sözcük veya Işleç gibi öğelerin varsayılan değerlerini değiştirir.

**Otomatik**

Öğeler, **düz metin**gibi diğer görüntüleme öğelerinden ön plan rengini alabilir. Bu seçeneği kullanarak, devralınan bir görüntüleme öğesinin rengini değiştirdiğinizde ilgili görüntü öğelerinin rengi de otomatik olarak değişir. Örneğin, **derleyici hatası** için **Otomatik** değeri seçtiyseniz ve daha sonra **düz metnin** rengini kırmızı olarak değiştirdiyseniz, **derleyici hatası** da otomatik olarak kırmızı rengi miras alır.

**Default**

Visual Studio 'Yu ilk kez açtığınızda öğe için görüntülenen renk. **Varsayılanları Kullan** düğmesine tıklamak bu renge sıfırlanır.

**Özel**

Görüntüleme öğeleri listesinde seçilen öğe için özel bir renk ayarlamanıza olanak tanımak üzere renk iletişim kutusunu görüntüler.

> [!NOTE]
> Özel renkler tanımlama olanağınız, bilgisayarınızın görüntüsüne ait renk ayarlarıyla sınırlı olabilir. Örneğin, Bilgisayarınız 256 renk görüntüleyecek şekilde ayarlandıysa ve **renk** iletişim kutusundan özel bir renk SEÇTIĞINIZDE, IDE varsayılan olarak en yakın kullanılabilir **Temel renge** sahiptir ve **renk önizleme kutusunda siyah rengi görüntüler** .

**Öğe arka planı**

, **Görüntüleme öğelerinde**seçilen öğe için bir arka plan rengi seçebileceğiniz bir renk paleti sağlar. Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntüleme düzenini koruduğundan, metnin arka plan rengini değiştirmek de derleyici hatası, anahtar sözcük veya Işleç gibi öğelerin varsayılan değerlerini değiştirir.

**Otomatik**

Öğeler **düz metin**gibi diğer görüntüleme öğelerinden arka plan rengini alabilir. Bu seçeneği kullanarak, devralınan bir görüntüleme öğesinin rengini değiştirdiğinizde ilgili görüntü öğelerinin rengi de otomatik olarak değişir. Örneğin, **derleyici hatası** için **Otomatik** değeri seçtiyseniz ve daha sonra **düz metnin** rengini kırmızı olarak değiştirdiyseniz, **derleyici hatası** da otomatik olarak kırmızı rengi miras alır.

**Default**

Visual Studio 'Yu ilk kez açtığınızda öğe için görüntülenen renk. **Varsayılanları Kullan** düğmesine tıklamak bu renge sıfırlanır.

**Özel**

Görüntüleme öğeleri listesinde seçilen öğe için özel bir renk ayarlamanıza olanak tanımak üzere renk iletişim kutusunu görüntüler.

**Kalın**

Seçilen **görüntüleme öğelerinin** metnini kalın metinde göstermek için bu seçeneği belirleyin. Kalın metin, düzenleyicide tanımlanması daha kolaydır.

**Örnek**

**Ayarları göster** ve seçili **öğeleri görüntüle** için yazı tipi stili, boyutu ve renk şemasının bir örneğini görüntüler. Farklı biçimlendirme seçenekleriyle denemeler yaparken sonuçları önizlemek için bu kutuyu kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler İletişim Kutusu](../../ide/reference/options-dialog-box-visual-studio.md)
- [Nasıl Yapılır: Yazı Tiplerini ve Renkleri Değiştirme](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
