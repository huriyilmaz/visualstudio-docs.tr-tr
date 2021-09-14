---
title: Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu
description: IDE'de çeşitli kullanıcı arabirimi öğeleri için özel bir yazı tipi ve renk düzeni oluşturmak üzere Ortam bölümündeki Yazı Tipleri ve Renkler sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 514e07e855299ca7862a393b7f9b576d761ae8f6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725728"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu

Seçenekler **iletişim kutusunun Yazı** Tipleri ve Renkler **sayfası,** tümleşik geliştirme ortamındaki (IDE) çeşitli kullanıcı arabirimi öğeleri için özel bir yazı tipi ve renk düzeni kurmanızı sağlar. Araçlar Seçenekler'e tıklar ve **ardından** Ortam Yazı Tipleri ve  >  Renkler'i **seçerek bu** iletişim  >  **kutusuna erişebilirsiniz.**

Renk düzeni değişiklikleri, bunları yaptığınız oturum sırasında etkili olmaz. Renk değişikliklerini değerlendirmek için başka bir Visual Studio örneği açarak ve değişikliklerinizin geçerli olmasını beklediğiniz koşulları üreterek değerlendirin.

**için ayarları göster**

Yazı tipi ve renk düzenlerini değiştirebilirsiniz tüm kullanıcı arabirimi öğelerini listeler. Bu listeden bir öğe seçtikten sonra Öğeleri görüntüle'de seçilen öğenin renk ayarlarını **özelleştirebilirsiniz.**

- **Metin Düzenleyici**

     Metin Düzenleyici için yazı tipi stili, boyutu ve renk görüntüleme ayarlarında yapılan değişiklikler metnin varsayılan metin düzenleyicinizin görünümünü etkiler. IDE dışında bir metin düzenleyicisinde açılan belgeler bu ayarlardan etkilenmez.

- **Yazıcı**

     Yazıcı için yazı tipi stili, boyutu ve renk görüntüleme ayarlarında yapılan değişiklikler, yazdırılan belgelerde metnin görünümünü etkiler.

    > [!NOTE]
    > Gerektiğinde, yazdırma için metin düzenleyicisinde görüntülemek için kullanılandan farklı bir varsayılan yazı tipi seçebilirsiniz. Bu, hem tek bayt hem de çift bayt karakterleri içeren kod yazdırırken yararlı olabilir.

- **Deyim Tamamlama**

     Düzenleyicide deyim tamamlama açılır menüsünde görüntülenen metnin yazı tipi stilini ve boyutunu değiştirir.

- **Düzenleyici Araç İpucu**

     Düzenleyicide görüntülenen ToolTips içinde görüntülenen metnin yazı tipi stilini ve boyutunu değiştirir.

- **Ortam Yazı Tipi**

     Için ayarları göster'de zaten ayrı bir seçeneği olan tüm IDE kullanıcı arabirimi öğeleri için yazı tipi stilini **ve boyutunu değiştirir.**

     ::: moniker range="vs-2017"

     Örneğin, bu seçenek Başlangıç Sayfası **için geçerlidir** ancak Çıkış penceresini **etkilemez.**

     ::: moniker-end

- **[Tüm Metin Aracı Windows]**

     Bu öğe için yazı tipi stili, boyutu ve renk görüntüleme ayarlarında yapılan değişiklikler, IDE'de çıkış bölmeleri olan araç pencerelerinin metin görünümünü etkiler. Örneğin, Çıkış penceresi, Komut penceresi, Anlık pencere vb.

    > [!NOTE]
    > [Tüm Metin **Aracı Windows]** öğelerinin metninde yapılan değişiklikler, bunları yaptığınız oturum sırasında etkili olmaz. Bu tür değişiklikleri değerlendirmek için başka bir örnek Visual Studio.

**Varsayılanları Kullan**

Için ayarları göster'de seçilen liste öğesinin yazı tipi ve renk **değerlerini sıfırlar.** Diğer **görüntüleme** düzenleri seçim için kullanılabilir olduğunda Kullan düğmesi görünür. Örneğin, Yazıcı için iki düzenden birini seçebilirsiniz.

**Yazı tipi (kalın yazı tipi sabit genişlikli yazı tiplerini gösterir)**

Sisteminize yüklenmiş olan tüm yazı tiplerini listeler. Açılan menü ilk kez görüntülendiğinde, Show settings for field (Ayarları göster) alanında seçilen **öğenin geçerli yazı** tipi vurgulanır. Düzenleyicide hizalanması daha kolay olan yazı tipleri kalın olarak görünür.

**Boyut**

Vurgulanan yazı tipi için kullanılabilir nokta boyutlarını listeler. Yazı tipinin boyutunun değiştirilmesi, Seçim **ayarlarını göster** için **tüm Görüntüleme öğelerini** etkiler.

**Öğeleri görüntüleme**

Ön plan ve arka plan rengini değiştirebilirsiniz öğeleri listeler.

> [!NOTE]
> **Düz Metin,** varsayılan görüntüleme öğesidir. Bu nedenle, **PlainText'e atanan** özellikler diğer görüntüleme öğelerine atanan özellikler tarafından geçersiz kılınır. Örneğin, blue rengini **PlainText'e, yeşil** rengi Tanımlayıcı'ya **atarsanız** tüm tanımlayıcılar yeşil renkte görünür. Bu örnekte Tanımlayıcı **özellikleri** **PlainText özelliklerini geçersiz** kılar.

Bazı görüntü öğeleri şunlardır:

|Öğeyi görüntüle|Description|
|------------------|-----------------|
|**Düz Metin**|Düzenleyicide metin.|
|**Seçilen Metin**|Düzenleyici odağında geçerli seçime dahil edilen metin.|
|**Etkin Olmayan Seçili Metin**|Düzenleyici odağı kaybettiğinde geçerli seçime dahil edilen metin.|
|**Gösterge Kenar Boşluğu**|Kod Düzenleyicisi'nin sol tarafından kesme noktaları ve yer işareti simgelerinin görüntüleniyor olduğu kenar boşluğu.|
|**Satır Numaraları**|Her kod satırı yanında görünen isteğe bağlı sayılar|
|**Görünür Boşluk**|Boşluklar, sekmeler ve sözcük kaydırma göstergeleri|
|**Yer işareti**|Yer işaretleri olan satırlar. **Yer** işareti yalnızca gösterge kenar boşluğu devre dışı bırakılmıştır.|
|**Küme Ayracı Eşleştirme (Vurgula)**|Bu, eşleşen ayraçlar için genellikle kalın biçimlendirmedir.|
|**Küme Ayracı Eşleştirme (Dikdörtgen)**|Arka planda genellikle gri bir dikdörtgen olduğunu vurgulama.|
|**Kesme Noktası (Devre Dışı)**|Kullanılmadı.|
|**Kesme Noktası (Etkin)**|Deyimler veya basit kesme noktaları içeren satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde kesme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası (Hata)**|Hata durumuna sahip kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Yalnızca deyim düzeyinde kesme noktaları etkinse veya  Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası (Uyarı)**|Uyarı durumuna sahip kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Yalnızca deyim düzeyinde kesme noktaları etkinse veya  Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası - Gelişmiş (Devre Dışı)**|Devre dışı bırakılmış koşullu veya isabet sayısına sahip kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Yalnızca deyim düzeyinde kesme noktaları etkinse veya  Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası - Gelişmiş (Etkin)**|Koşullu veya isabet sayısına sahip kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Yalnızca deyim düzeyinde kesme noktaları etkinse veya  Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası - Gelişmiş (Hata)**|Hata durumuna sahip koşullu veya isabet sayısına sahip kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Yalnızca deyim düzeyinde kesme noktaları etkinse veya  Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası - Gelişmiş (Uyarı)**|Uyarı durumuna sahip koşullu veya isabet sayısına sahip kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Yalnızca deyim düzeyinde kesme noktaları etkinse veya  Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası - Eşlenmiş (Devre Dışı)**|Devre dışı bırakılmış eşlenmiş kesme noktaları içeren deyimlerin veya satırların vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası - Eşlenmiş (Etkin)**|Eşlenmiş kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme Noktası - Eşlenmiş (Hata)**|Hata durumuna sahip eşlenmiş kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kesme noktası-eşlenmiş (uyarı)**|Bir uyarı durumunda eşlenmiş kesme noktaları içeren deyimler veya çizgiler için vurgu rengi belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**C/C++ Kullanıcı anahtar sözcükleri**|Yönergeyle tanımlanan belirli bir kod dosyası içindeki bir sabit `#define` .|
|**Çağrı dönüşü**|Hata ayıklama sırasında bağlam en üst olmayan yığın çerçevesine dönüştürüldüğünde, kaynak deyimleri veya çağrı dönüş noktalarını belirten çizgiler için vurgu rengi belirtir.|
|**Kod parçacığına bağımlı alan**|Geçerli düzenlenebilir alan değiştirildiğinde güncellenecek alan.|
|**Kod parçacığı alanı**|Bir kod parçacığı etkin olduğunda düzenlenebilir alan.|
|**Daraltılabilir metin**|Kod Düzenleyicisi içinde ve görünümün dışına geçiş yapılabilir bir metin veya kod bloğu.|
|**Yorum**|Kod açıklamaları.|
|**Derleyici hatası**|Düzenleyicide bir derleyici hatası gösteren mavi dalgalı çizgiler.|
|**Dokunulmayan kapsam alanı**|Birim testi kapsamında olmayan kod.|
|**Kapsam kısmen dokunulmaz alanı**|Birim testinin kısmen kapsadığı kod.|
|**Kapsam dokunulmaz alanı**|Bir birim testinin tamamen kapsadığı kod.|
|**CSS yorumu**|Geçişli Stil Sayfaları bir yorum. Örnek:<br /><br /> /* yorum \*/|
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
|**Dışlanan kod**|Bir koşullu ön işlemci yönergesi başına, derlenemediği kod `#if` .|
|**Tanımlayıcı**|Kod içindeki tanımlayıcılar, sınıf adları, yöntem adları ve değişken adları gibi.|
|**Sözcükle**|Verilen dile ayrılan dil için anahtar sözcükler. Örneğin: sınıf ve ad alanı.|
|**Bellek adresi**|**Bellek** penceresi içindeki adres sütununu göstermek için kullanılan metin rengi.|
|**Bellek değişti**|**Bellek** penceresi içindeki değiştirilen verileri göstermek için kullanılan metnin rengi.|
|**Bellek verileri**|**Bellek** penceresi içindeki verileri göstermek için kullanılan metin rengi.|
|**Bellek okunamaz**|**Bellek** penceresi içindeki okunamaz bellek alanını göstermek için kullanılan metnin rengi.|
|**Sayı**|Kodda gerçek bir sayısal değeri temsil eden bir sayı.|
|**Operatör**|+,-, Ve! = gibi işleçler.|
|**Farklı Bir Hata**|Diğer hata türleri diğer hata dalgalı çizgiler kapsamına girmeyen bir hata oluştu. Şu anda, Düzenle ve devam et 'de işlenmemiş düzenlemelerini içerir.|
|**Önişlemci anahtar sözcüğü**|#İnclude gibi Önişlemci tarafından kullanılan anahtar sözcükler.|
|**Salt okuma bölgesi**|Düzenlenemeyen kod. Örneğin, kod tanımı görünümü penceresinde veya Düzenle ve devam et sırasında değiştirilemeyen kodda görüntülenen kod.|
|**Yeniden düzenleme arka planı**|**Değişiklikleri Önizle** iletişim kutusunun arka plan rengi.|
|**Geçerli alanı yeniden düzenleme**|**Değişiklikleri Önizle** iletişim kutusunda yeniden düzenlenmiş olacak geçerli öğenin arka plan rengi.|
|**Bağımlı alanı yeniden düzenleme**|**Değişiklikleri Önizle** iletişim kutusunda yeniden düzenlenmiş olacak öğe başvurularının rengi.|
|**Verileri kaydetme**|**Kayıt** penceresi içindeki verileri göstermek için kullanılan metin rengi.|
|**NAT Kaydet**|**Kayıt** penceresi içindeki tanınmayan verileri ve nesneleri göstermek için kullanılan metin rengi.|
|**Akıllı etiket**|Akıllı etiketler çağrıldığında anahattı göstermek için kullanılır.|
|**SQL DML Işaretçisi**|Transact-SQL düzenleyicisi için geçerlidir. Bu düzenleyicideki DML deyimleri, varsayılan olarak bir sınırlayıcı mavi kutusuyla işaretlenir.|
|**Eski kod**|Yenisiyle değiştirilen kod bir güncelleştirme bekliyor. Bazı durumlarda Düzenle ve Devam Edin kod değişikliklerini hemen uygulayamaz, ancak hata ayıklamaya devam ettiyebilirsiniz. Bu durum, yürütülmektedir olan işlevi çağıracak bir işlevi düzenlerken veya çağrı yığınında bekleyen bir işleve 64 bayttan fazla yeni değişken eklersiniz. Bu durumda, hata ayıklayıcı bir "Eski Kod Uyarısı" iletişim kutusu görüntüler ve yenisi geçen kod, söz konusu işlev bitip yeniden çağrılana kadar yürütülmaya devam eder. Düzenle ve Devam' bu sırada kod değişikliklerini uygular.|
|**Dize**|Dize değişmezleri.|
|**Dize (C# @ Verbatim)**|C# içinde, metin olarak yorumlanır dize değişmezleri. Örnek:<br /><br /> @"x"|
|**Söz Dizimi Hatası**|Hataları ayrıştır.|
|**Görev Listesi Kısayolu**|Bir **Görev Listesi** kısayolu eklenirse ve gösterge kenar boşluğu devre dışı bırakılırsa çizgi vurgulanır.|
|**İzleme Noktası (Devre Dışı)**|Kullanılmadı.|
|**İzleme Noktası (Etkin)**|Deyimler veya basit izleme noktaları içeren satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde izleme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**tracepoint (hata)**|Hata durumuna sahip izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde izleme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**İzleme Noktası (Uyarı)**|Uyarı durumuna sahip izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde izleme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Gelişmiş (Devre Dışı)**|Devre dışı bırakılmış koşullu veya isabet sayısına sahip izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde izleme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Gelişmiş (Etkin)**|Koşullu veya isabet sayısına sahip izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde izleme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Gelişmiş (Hata)**|Hata durumuna sahip koşullu veya isabet sayısına sahip izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde izleme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Gelişmiş (Uyarı)**|Uyarı durumuna sahip koşullu veya isabet sayısına sahip izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Bu seçenek yalnızca deyim düzeyinde izleme noktaları etkinse  veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Eşlenmiş (Devre Dışı)**|Devre dışı bırakılmış eşlenmiş izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Eşlenmiş (Etkin)**|Eşlenmiş izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Eşlenmiş (Hata)**|Hata durumuna sahip eşlenmiş izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Tracepoint - Eşlenmiş (Uyarı)**|Uyarı durumuna sahip eşlenmiş izleme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**Kaydetmeden sonra Değişiklikleri İzle**|Dosya açıldığından beri değiştirilmiş ancak diske kaydedilmiş kod satırları.|
|**Kaydetmeden önce Değişiklikleri izleme**|Dosya açıldığından beri değiştirilmiş olan ancak diske kayıtlı olan kod satırları.|
|**Kullanıcı Türleri**|Kullanıcılar tarafından tanımlanan türler.|
|**Kullanıcı Türleri (Temsilciler)**|Temsilciler için renk yazın.|
|**Kullanıcı Türleri (Numaralar)**|Enum'lar için kullanılan tür rengi.|
|**Kullanıcı Türleri (Arabirimler)**|Arabirimler için renk yazın.|
|**Kullanıcı Türleri (Değer türleri)**|C# içinde yapılar gibi değer türleri için tür rengi.|
|**Visual Basic Salt Okunur İşaretçisi**|Özel durum bölgeleri Visual Basic yöntem tanımı ve yaprak olmayan çağrı çerçeveleri gibi EnC'nin belirtim için kullanılan özel durumlara özgü bir işaretçi.|
|**Uyarı**|Derleyici uyarıları.|
|**Uyarı Satırları Yolu**|Statik Analiz uyarı satırları için kullanılır.|
|**XML Özniteliği**|Öznitelik adları.|
|**XML Öznitelik Teklifleri**|XML öznitelikleri için tırnak karakterleri.|
|**XML Öznitelik Değeri**|XML özniteliklerinin içeriği.|
|**XML Cdata Bölümü**|\<![CDATA[...]]>içeriğinin.|
|**XML Açıklaması**|\<!-- -->içeriğini.|
|**XML Sınırlayıcı**|<, <?, <!, , ? , ve [, ] gibi XML Söz Dizimi \<!--, --> \> \<![, ]]> sınırlayıcıları.|
|**XML Belge Özniteliği**|"I" değerinin renklendirmesi gibi bir xml \<param name="I"> belge özniteliğinin değeri.|
|**XML Belge Açıklaması**|Xml belge açıklamalarında yer alan açıklamalar.|
|**XML Belge Etiketi**|XML belge açıklamalarında yer alan etiketler, örneğin<br /><br /> /// \<summary>.|
|**XML Anahtar Sözcüğü**|CDATA, IDREF ve NDATA gibi DTD anahtar sözcükleri.|
|**XML Adı**|Öğe adları ve İşleme Yönergeleri hedef adı.|
|**XML İşleme Yönergesi**|Hedef adı dahil değil, İşleme Yönergelerinin içeriği.|
|**XML Metni**|Düz metin öğesi içeriği.|
|**XSLT Anahtar Sözcüğü**|XSLT öğe adları.|

**Öğe ön planı**

Öğeleri görüntüle'de seçilen öğenin ön planı için seçebilirsiniz kullanılabilir **renkleri listeler.** Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntü düzeni sürdürmesi gerektiği için, metnin ön plan rengini değiştirmek Derleyici Hatası, Anahtar Sözcük veya İşleç gibi öğelerin varsayılanlarını da değiştirir.

**Otomatik**

Öğeler, **düz metin** gibi diğer görüntüleme öğelerinden ön plan rengini alabilir. Bu seçeneği kullanarak, devralınan bir görüntüleme öğesinin rengini değiştirdiğinizde ilgili görüntü öğelerinin rengi de otomatik olarak değişir. Örneğin, **derleyici hatası** için **Otomatik** değeri seçtiyseniz ve daha sonra **düz metnin** rengini kırmızı olarak değiştirdiyseniz, **derleyici hatası** da otomatik olarak kırmızı rengi miras alır.

**Varsayılanını**

Visual Studio ilk kez açtığınızda öğe için görüntülenen renk. **Varsayılanları Kullan** düğmesine tıklamak bu renge sıfırlanır.

**Özel**

Görüntüleme öğeleri listesinde seçilen öğe için özel bir renk ayarlamanıza olanak tanımak üzere renk iletişim kutusunu görüntüler.

> [!NOTE]
> Özel renkler tanımlama olanağınız, bilgisayarınızın görüntüsüne ait renk ayarlarıyla sınırlı olabilir. Örneğin, Bilgisayarınız 256 renk görüntüleyecek şekilde ayarlandıysa ve **renk** iletişim kutusundan özel bir renk SEÇTIĞINIZDE, IDE varsayılan olarak en yakın kullanılabilir **Temel renge** sahiptir ve **renk önizleme kutusunda siyah rengi görüntüler** .

**Öğe arka planı**

, **Görüntüleme öğelerinde** seçilen öğe için bir arka plan rengi seçebileceğiniz bir renk paleti sağlar. Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntüleme düzenini koruduğundan, metnin arka plan rengini değiştirmek de derleyici hatası, anahtar sözcük veya Işleç gibi öğelerin varsayılan değerlerini değiştirir.

**Otomatik**

Öğeler **düz metin** gibi diğer görüntüleme öğelerinden arka plan rengini alabilir. Bu seçeneği kullanarak, devralınan bir görüntüleme öğesinin rengini değiştirdiğinizde ilgili görüntü öğelerinin rengi de otomatik olarak değişir. Örneğin, **derleyici hatası** için **Otomatik** değeri seçtiyseniz ve daha sonra **düz metnin** rengini kırmızı olarak değiştirdiyseniz, **derleyici hatası** da otomatik olarak kırmızı rengi miras alır.

**Varsayılanını**

Visual Studio ilk kez açtığınızda öğe için görüntülenen renk. **Varsayılanları Kullan** düğmesine tıklamak bu renge sıfırlanır.

**Özel**

Görüntüleme öğeleri listesinde seçilen öğe için özel bir renk ayarlamanıza olanak tanımak üzere renk iletişim kutusunu görüntüler.

**Kalın**

Seçilen **görüntüleme öğelerinin** metnini kalın metinde göstermek için bu seçeneği belirleyin. Kalın metin, düzenleyicide tanımlanması daha kolaydır.

**Örnek**

**Ayarları göster** ve seçili **öğeleri görüntüle** için yazı tipi stili, boyutu ve renk şemasının bir örneğini görüntüler. Farklı biçimlendirme seçenekleriyle denemeler yaparken sonuçları önizlemek için bu kutuyu kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler Iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md)
- [Nasıl Yapılır: Yazı Tiplerini ve Renkleri Değiştirme](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
