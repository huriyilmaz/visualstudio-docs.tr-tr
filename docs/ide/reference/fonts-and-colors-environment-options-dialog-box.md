---
title: Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu
description: IDE 'deki çeşitli kullanıcı arabirimi öğeleri için özel bir yazı tipi ve renk şeması oluşturmak üzere ortam bölümündeki yazı tipleri ve renkler sayfasını nasıl kullanacağınızı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101355"
---
# <a name="fonts-and-colors-environment-options-dialog-box"></a>Yazı Tipleri ve Renkler, Ortam, Seçenekler İletişim Kutusu

**Seçenekler** Iletişim kutusunun **yazı tipleri ve renkler** sayfası, TÜMLEŞIK geliştirme ortamındaki (IDE) çeşitli kullanıcı arabirimi öğeleri için özel bir yazı tipi ve renk düzeni ayarlamanıza olanak sağlar. Bu iletişim kutusuna **Araçlar**  >  **Seçenekler**' e ve ardından **ortam**  >  **yazı tipleri ve renkler**' i seçerek erişebilirsiniz.

Renk şeması değişiklikleri, yaptığınız oturum sırasında etkili olmaz. Visual Studio başka bir örneğini açarak ve yaptığınız değişikliklerin uygulanmasını istediğiniz koşulları üreterek renk değişikliklerini değerlendirebilirsiniz.

**Ayarları göster**

Yazı tipi ve renk düzenlerini değiştirebileceğiniz tüm Kullanıcı arabirimi öğelerini listeler. Bu listeden bir öğe seçtikten sonra, **görüntüleme öğelerinde** seçilen öğenin renk ayarlarını özelleştirebilirsiniz.

- **Metin düzenleyici**

     Metin Düzenleyicisi için yazı tipi stili, boyutu ve renk görüntüleme ayarlarındaki değişiklikler, varsayılan metin düzenleyicinizdeki metnin görünümünü etkiler. IDE dışında bir metin düzenleyicisinde açılan belgeler bu ayarlardan etkilenmeyecektir.

- **Yazıcı**

     Yazıcı için yazı tipi stili, boyutu ve renk görüntüleme ayarlarındaki değişiklikler yazdırılan belgelerdeki metnin görünümünü etkiler.

    > [!NOTE]
    > Gerektiğinde, yazdırma için metin düzenleyicisinde görüntülenmek üzere kullanılandan farklı bir varsayılan yazı tipi seçebilirsiniz. Bu, hem tek baytlı hem de çift baytlık karakterler içeren kodu yazdırırken yararlı olabilir.

- **Deyim Tamamlama**

     Düzenleyicide ifade tamamlanma açılır penceresinde görünen metnin yazı tipi stilini ve boyutunu değiştirir.

- **Düzenleyici araç Ipucu**

     Düzenleyicide görüntülenen araç Ipuçlarında görüntülenen metnin yazı tipi stilini ve boyutunu değiştirir.

- **Ortam yazı tipi**

     **Görüntüleme ayarları**' nda ayrı bir seçeneğe sahip olmayan tüm IDE Kullanıcı arabirimi öğelerinin yazı tipi stilini ve boyutunu değiştirir.

     ::: moniker range="vs-2017"

     Örneğin, bu seçenek **Başlangıç sayfası** için geçerlidir ancak **Çıkış** penceresini etkilemez.

     ::: moniker-end

- **[Tüm metin aracı Windows]**

     Bu öğe için yazı tipi stili, boyutu ve renk görüntüleme ayarlarındaki değişiklikler, IDE 'de çıkış bölmeleri olan araç pencerelerinin metin görünümünü etkiler. Örneğin, çıkış penceresi, Komut penceresi, acil pencere vb.

    > [!NOTE]
    > **[tüm metin aracı Windows]** öğelerinin metninde yapılan değişiklikler, bunları yaptığınız oturum sırasında etkili olmaz. Visual Studio başka bir örneğini açarak, bu değişiklikleri değerlendirebilirsiniz.

**Varsayılanları Kullan**

**Ayarlarını göster** bölümünde seçilen liste öğesinin yazı tipi ve renk değerlerini sıfırlar. Diğer görüntüleme düzenleri seçime uygun olduğunda **kullan** düğmesi görünür. Örneğin, yazıcı için iki düzen arasından seçim yapabilirsiniz.

**Yazı tipi (kalın tür sabit genişlikli yazı tiplerini gösterir)**

Sisteminizde yüklü olan tüm yazı tiplerini listeler. Açılan menü ilk göründüğünde, **ayarları göster** alanında seçilen öğenin geçerli yazı tipi vurgulanır. Düzenleyicide daha kolay bir şekilde hizalanmanız gereken sabit yazı tipleri — kalın olarak görünür.

**Boyut**

Vurgulanan yazı tipi için kullanılabilir nokta boyutlarını listeler. Yazı tipinin boyutunu değiştirmek, seçime **yönelik ayarları göster** Için tüm **görüntüleme öğelerini** etkiler.

**Öğeleri görüntüle**

Ön plan ve arka plan rengini değiştirebileceğiniz öğeleri listeler.

> [!NOTE]
> **Düz metin** varsayılan görüntüleme öğesidir. Bu nedenle, **düz metine** atanan özellikler diğer görüntü öğelerine atanan özellikler tarafından geçersiz kılınır. Örneğin, maviyi **düz metin** olarak ve yeşil renkle **tanımlayıcıya** atarsanız, tüm tanımlayıcılar yeşil renkte görünür. Bu örnekte, **tanımlayıcı** özellikleri **düz metin** özelliklerini geçersiz kılar.

Bazı görüntü öğeleri şunlardır:

|Öğeyi görüntüle|Açıklama|
|------------------|-----------------|
|**Düz Metin**|Düzenleyicideki metin.|
|**Seçilen Metin**|Düzenleyici odağa sahip olduğunda geçerli seçime dahil edilen metin.|
|**Etkin olmayan seçili metin**|Düzenleyici odağı kaybettiği zaman geçerli seçime dahil edilen metin.|
|**Gösterge kenar boşluğu**|Kod düzenleyicisinin sol tarafındaki kenar boşluğu, kesme noktaları ve yer işareti simgeleri görüntülenir.|
|**Satır numaraları**|Her kod satırının yanında görünen isteğe bağlı sayılar|
|**Görünür boşluk**|Boşluklar, sekmeler ve sözcük kaydırmalı göstergeler|
|**Yer işareti**|Yer işaretleri içeren satırlar. **Yer işareti** yalnızca Gösterge kenar boşluğu devre dışıysa görünür.|
|**Ayraç eşleştirme (vurgula)**|Genellikle eşleşen küme ayraçları için kalın biçimlendirme olan vurgulama.|
|**Ayraç eşleştirme (dikdörtgen)**|Genellikle arka planda gri dikdörtgen olan vurgulama.|
|**Kesme noktası (devre dışı)**|Kullanılmadı.|
|**Kesme noktası (etkin)**|İfadeler veya basit kesme noktaları içeren çizgiler için vurgu rengi belirtir. Bu seçenek yalnızca, bildirim düzeyi kesme noktaları etkinse veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**Kesme noktası (hata)**|Bir hata durumunda olan kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası (uyarı)**|Uyarı durumunda olan kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (devre dışı)**|Devre dışı bırakılmış koşullu veya isabet saymalı kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (etkin)**|Deyim veya koşullu veya isabet saymalı kesme noktaları içeren çizgiler için vurgu rengi belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (hata)**|Bir hata durumunda olan koşullu veya isabet sayılı kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-Gelişmiş (uyarı)**|Uyarı durumundaki koşullu veya isabet saymalı kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Yalnızca ifade düzeyi kesme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneği belirlenmişse geçerlidir.|
|**Kesme noktası-eşlenmiş (devre dışı)**|Devre dışı eşlenmiş kesme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme noktası-eşlenmiş (etkin)**|İfadelerin veya eşlenmiş kesme noktaları içeren satırların vurgu rengini belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme noktası-eşlenmiş (hata)**|Bir hata durumunda, eşleşen kesme noktaları içeren deyimlerin veya satırların vurgu rengini belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kesme Noktası - Eşlenmiş (Uyarı)**|Uyarı durumuna sahip eşlenmiş kesme noktaları içeren deyimler veya satırlar için vurgulama rengini belirtir. Deyim düzeyinde kesme noktaları etkinse asp veya ASP.NET hata ayıklaması  için geçerlidir veya Genel, Hata Ayıklama, Seçenekler İletişim Kutusu'nda Kesme noktaları veya geçerli deyim için tüm kaynak satırı vurgula seçeneği [seçiliyse geçerlidir.](../../debugger/general-debugging-options-dialog-box.md)|
|**C/C++ Kullanıcı Anahtar Sözcükleri**|Yönergesi ile tanımlanan belirli bir kod dosyasındaki `#define` sabit.|
|**Çağrı İadesi**|Kaynak deyimleri veya satırlar için bağlam hata ayıklama sırasında üst yığın olmayan bir çerçeveye geçiş olduğunda çağrı dönüş noktalarını gösteren vurgulama rengini belirtir.|
|**Kod Parçacığı Bağımlı Alanı**|Geçerli düzenlenebilir alan değiştirildiğinde güncelleştirilecek bir alan.|
|**Kod Parçacığı Alanı**|Kod parçacığı etkin olduğunda düzenlenebilir alan.|
|**Daraltılabilir Metin**|Kod Düzenleyicisi'nde görünümü açıp kapatan bir metin veya kod bloğu.|
|**Yorum**|Kod yorumları.|
|**Derleyici Hatası**|Düzenleyicide derleyici hatasını gösteren mavi geçişler.|
|**Kapsama Dokunmadı Alanı**|Birim testi kapsamında yer alan kod.|
|**Kısmen Dokunmuş Kapsam Alanı**|Birim testinin kapsamında olan kod.|
|**Kapsam Dokunma Alanı**|Birim testi kapsamındaki kod.|
|**CSS Açıklaması**|Geçişli Stil Sayfaları. Örnek:<br /><br /> /* açıklama \*/|
|**CSS Anahtar Sözcüğü**|Basamaklı Stil Sayfası'nın Anahtar Sözcükleri.|
|**CSS Özellik Adı**|Background gibi bir özelliğin adı.|
|**CSS Özellik Değeri**|Mavi gibi bir özelle atanan değer.|
|**CSS Seçici**|İlgili kuralın geçerli olduğu öğeleri tanımlayan bir dize. Seçici , 'H1' gibi basit bir seçici veya birkaç basit seçiciden oluşan 'H1 B' gibi bağlamsal seçici olabilir.|
|**CSS Dize Değeri**|dizesinde bir Geçişli Stil Sayfaları.|
|**Geçerli liste konumu**|Çıkış penceresi veya Sonuçları Bul pencereleri gibi bir liste aracı penceresinde gezinilen geçerli satır.|
|**Geçerli Deyim**|Hata ayıklama sırasında geçerli adım konumunu gösteren kaynak deyiminin veya satırın vurgulama rengini belirtir.|
|**Hata Ayıklayıcı Verileri Değiştirildi**|Yazmazlar ve Bellek pencerelerinin içinde değiştirilen verileri görüntülemek **için** **kullanılan metnin** rengi.|
|**Tanım Penceresi Arka Planı**|Kod Tanımı penceresinin **arka plan** rengi.|
|**Tanım Penceresi Geçerli Eşleşmesi**|Kod Tanımı **penceresindeki geçerli** tanım.|
|**Dosya Adını Parçalara Ayır**|**Disassembly** penceresinde dosya adı sonlarını görüntülemek için kullanılan metnin rengi.|
|**Kaynağı Parçalara Ayır**|**Disassembly** penceresinde kaynak satırları görüntülemek için kullanılan metnin rengi.|
|**Parçalara Ayır Simgesi**|**Disassembly** penceresinde sembol adlarını görüntülemek için kullanılan metnin rengi.|
|**Metni Parçalara Ayır**|**Disassembly** penceresinde op-code ve data görüntülemek için kullanılan metnin rengi.|
|**Dışlanan Kod**|Gibi bir koşullu önişlemci yönergesi başına derlenmez `#if` kod.|
|**Tanımlayıcı**|Kodda sınıf adları, yöntem adları ve değişken adları gibi tanımlayıcılar.|
|**Anahtar kelime**|Ayrılmış olan dilin anahtar sözcükleri. Örneğin: sınıf ve ad alanı.|
|**Bellek Adresi**|Bellek penceresinde adres sütununu görüntülemek için kullanılan **metnin** rengi.|
|**Bellek Değiştirildi**|Değiştirilen verileri Bellek penceresinde görüntülemek için kullanılan **metnin** rengi.|
|**Bellek Verileri**|Bellek penceresindeki verileri görüntülemek için **kullanılan** metnin rengi.|
|**Bellek Okunamaz**|Bellek penceresinde okunamaz bellek alanlarını görüntülemek için kullanılan **metnin** rengi.|
|**Sayı**|Gerçek bir sayısal değeri temsil eden kodda bir sayı.|
|**Operatör**|+, -ve != gibi işleçler.|
|**Farklı Bir Hata**|Diğer hata geçişlerinin kapsamına alınan diğer hata türleri. Şu anda, Düzenle ve Devam Etme'de kaba düzenlemeler de buna dahildir.|
|**Önişlemci Anahtar Sözcüğü**|Ön işlemci tarafından kullanılan anahtar sözcükler (örneğin, #include.|
|**Salt Okunur Bölge**|Düzenlenemez kod. Örneğin, Kod Tanımı Görünümü penceresinde görüntülenen kod veya Düzenle ve Devam Sırasında değiştiril değiştirilebilir kod.|
|**Arka Planı Yeniden Düzenleme**|Değişiklikleri Önizle **iletişim kutusunun arka plan** rengi.|
|**Geçerli Alanı Yeniden Düzenleme**|Değişiklikleri Önizle iletişim kutusunda yeniden düzenlemeye devam etmek için **geçerli öğenin arka** plan rengi.|
|**Bağımlı Alanı Yeniden Düzenleme**|Önizleme Değişiklikleri iletişim kutusunda yeniden düzenlemesi gereken öğe **başvurularının** rengi.|
|**Verileri Kaydetme**|Yazmanlar penceresindeki verileri görüntülemek için **kullanılan metnin** rengi.|
|**NAT'yi kaydetme**|Yazmaçlar penceresinde tanınmayan verileri ve nesneleri görüntülemek için **kullanılan metnin** rengi.|
|**Akıllı Etiket**|Akıllı etiketler çağrıldığında ana hatlarını ifade etmek için kullanılır.|
|**SQL DML İşaretçisi**|Transact-SQL için geçerlidir. Bu düzenleyicide DML deyimleri varsayılan olarak sınırlayıcı mavi bir kutuyla işaretlenir.|
|**Eski Kod**|Güncelleştirme bekleyen yeni kod. Bazı durumlarda, Düzenle ve devam et, kod değişikliklerini hemen uygulayamaz, ancak hata ayıklamaya devam ederken bunları daha sonra uygulayacaktır. Bu, şu anda yürütülmekte olan işlevi çağırması gereken bir işlevi düzenlerseniz veya çağrı yığınında bekleyen bir işleve 64 bayttan fazla yeni değişken eklerseniz oluşur. Bu durumda, hata ayıklayıcı bir "eski kod uyarısı" iletişim kutusu görüntüler ve söz konusu işlev bitene kadar yerine geçilen kod yürütülmeye devam eder ve yeniden çağırılır. Düzenle ve devam et, kod değişikliklerini o zaman uygular.|
|**Dize**|Dize sabit değerleri.|
|**Dize (C# @ tam)**|C# dilinde, harfine yorumlanan dize sabit değerleri. Örnek:<br /><br /> @"x"|
|**Söz dizimi hatası**|Ayrıştırma hataları.|
|**Görev Listesi kısayolu**|Bir satıra **görev listesi** kısayolu eklenirse ve gösterge kenar boşluğu devre dışıysa, çizgi vurgulanır.|
|**İzleme noktası (devre dışı)**|Kullanılmadı.|
|**İzleme noktası (etkin)**|Basit izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası (hata)**|Bir hata durumunda olan izleme noktalarını içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası (uyarı)**|Uyarı durumunda olan izleme noktalarını içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (devre dışı)**|Devre dışı bırakılmış koşullu veya isabet saymalı izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (etkin)**|Koşullu veya isabet saymalı izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (hata)**|Bir hata durumunda olan koşullu veya isabet sayılı izleme noktaları içeren deyimler veya çizgiler için vurgu rengi belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-Gelişmiş (uyarı)**|Uyarı durumunda olan koşullu veya isabet sayılı izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. Bu seçenek yalnızca, ekstre düzeyi izleme noktaları etkin olduğunda veya [Genel, hata ayıklama, Seçenekler Iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını Vurgula** seçeneğinin seçili olması durumunda geçerlidir.|
|**İzleme noktası-eşlenmiş (devre dışı)**|Devre dışı eşlenmiş izleme noktaları içeren deyimlerin veya çizgilerin vurgu rengini belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**İzleme noktası-eşlenmiş (etkin)**|Eşlenen izleme noktalarını içeren deyimler veya çizgiler için vurgu rengi belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**İzleme noktası-eşlenmiş (hata)**|Bir hata durumunda, eşlenmiş izleme noktalarını içeren deyimler veya çizgiler için vurgu rengi belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**İzleme noktası-eşlenmiş (uyarı)**|Uyarı durumunda, eşlenmiş izleme noktalarını içeren deyimler veya çizgiler için vurgu rengi belirtir. ifade düzeyi kesme noktaları etkinse veya [genel, hata ayıklama, seçenekler iletişim kutusunda](../../debugger/general-debugging-options-dialog-box.md) **kesme noktaları veya geçerli ifade için tüm kaynak satırını vurgula** seçeneği belirlenmişse ASP veya ASP.NET hata ayıklama için geçerlidir.|
|**Kaydettikten sonra değişiklikleri izle**|Dosya açılmadan, ancak diske kaydedildiğinden beri değiştirilen kod satırları.|
|**Kaydetmeden önce değişiklikleri izle**|Dosyanın açıldığı ve diske kaydedilmesinden sonra değiştirilen kod satırları.|
|**Kullanıcı türleri**|Kullanıcılar tarafından tanımlanan türler.|
|**Kullanıcı türleri (Temsilciler)**|Temsilciler için Color yazın.|
|**Kullanıcı türleri (numaralandırmalar)**|Numaralandırmalar için kullanılan renk türü.|
|**Kullanıcı türleri (arabirimler)**|Arabirimler için Color yazın.|
|**Kullanıcı türleri (değer türleri)**|C# içindeki yapılar gibi değer türleri için Color yazın.|
|**Visual Basic Salt okuma Işaretçisi**|özel durum bölgeleri, yöntem tanımı ve yaprak olmayan çağrı çerçeveleri gibi EnC 'yi belirlemek için kullanılan Visual Basic özgü bir işaretleyici.|
|**Uyarı**|Derleyici uyarıları.|
|**Uyarı satırları yolu**|Statik analiz uyarı satırları için kullanılır.|
|**XML özniteliği**|Öznitelik adları.|
|**XML öznitelik teklifleri**|XML öznitelikleri için tırnak karakterleri.|
|**XML öznitelik değeri**|XML özniteliklerinin içeriği.|
|**XML CDATA bölümü**|İçeriği \<![CDATA[...]]> .|
|**XML açıklaması**|İçeriği \<!-- --> .|
|**XML sınırlayıcısı**|<, <?, <!, \<!--, --> ,? \> , \<![, ]]> , ve [,] dahil olmak üzere XML sözdizimi sınırlayıcıları.|
|**XML doc özniteliği**|\<param name="I">"İ" nin renklendirilme gibi bir XML belgesi özniteliği değeri.|
|**XML belgesi açıklaması**|XML belgeleri yorumlarına eklenen açıklamalar.|
|**XML belge etiketi**|XML belgesi açıklamalarındaki Etiketler, örneğin<br /><br /> /// \<summary>.|
|**XML anahtar sözcüğü**|CDATA, ıDREF ve NDATA gibi DTD anahtar sözcükleri.|
|**XML adı**|Öğe adları ve Işleme yönergeleri hedef adı.|
|**XML Işleme yönergesi**|Işleme yönergelerinin içerikleri, hedef adı dahil değildir.|
|**XML metni**|Düz metin öğesi içeriği.|
|**XSLT anahtar sözcüğü**|XSLT öğe adları.|

**Öğe ön planı**

**Görüntüleme öğelerinde** seçilen öğenin ön planı için seçebileceğiniz kullanılabilir renkleri listeler. Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntüleme düzenini koruduğundan, metnin ön plan rengini değiştirmek de derleyici hatası, anahtar sözcük veya Işleç gibi öğelerin varsayılan değerlerini değiştirir.

**Otomatik**

Öğeler, Düz Metin gibi diğer görünen öğelerden ön plan **rengini devralabilir.** Bu seçeneği kullanarak, devralınan bir görüntüleme öğesinin rengini değiştirseniz ilgili görüntüleme öğelerinin rengi de otomatik olarak değişir. Örneğin, Derleyici Hatası  için Otomatik  değerini seçtiy ve daha sonra **Düz** Metin rengini Kırmızı olarak değiştirirse, **Derleyici** Hatası otomatik olarak Kırmızı rengini devralır.

**Varsayılan**

İlk kez öğe için görüntülenen renk, Visual Studio. Varsayılanları **Kullan düğmesine** tıklamak bu renge sıfırlanır.

**Özel**

Öğeleri görüntüle listesinde seçilen öğe için özel bir renk ayarlamanızı sağlayan Renk iletişim kutusunu görüntüler.

> [!NOTE]
> Özel renkler tanımlama yeteneğiniz, bilgisayarınızın görüntüsü için renk ayarlarıyla sınırlı olabilir. Örneğin, bilgisayarınız 256 renk görüntüleniyorsa ve Renk iletişim kutusundan özel bir renk seçerek, IDE varsayılan olarak kullanılabilir en  yakın **Temel** renge ayarlanır ve Renk önizleme kutusunda siyah rengi görüntüler. 

**Öğe arka planı**

Öğeleri görüntüle'de seçilen öğe için bir arka plan rengi seçen bir renk **paleti sağlar.** Bazı öğeler ilişkili olduğundan ve bu nedenle tutarlı bir görüntü düzeni sürdürmesi gerektiği için, metnin arka plan rengini değiştirmek Derleyici Hatası, Anahtar Sözcük veya İşleç gibi öğelerin varsayılanlarını da değiştirir.

**Otomatik**

Öğeler, Düz Metin gibi diğer görünen öğelerden arka plan **rengini devralabilir.** Bu seçeneği kullanarak, devralınan bir görüntüleme öğesinin rengini değiştirseniz ilgili görüntüleme öğelerinin rengi de otomatik olarak değişir. Örneğin, Derleyici Hatası  için Otomatik  değerini seçtiy ve daha sonra **Düz** Metin rengini Kırmızı olarak değiştirirse, **Derleyici** Hatası otomatik olarak Kırmızı rengini devralır.

**Varsayılan**

İlk kez öğe için görüntülenen renk, Visual Studio. Varsayılanları **Kullan düğmesine** tıklamak bu renge sıfırlanır.

**Özel**

Öğeleri görüntüle listesinde seçilen öğe için özel bir renk ayarlamanızı sağlayan Renk iletişim kutusunu görüntüler.

**Kalın**

Seçili Öğeleri kalın metin olarak görüntüle metnini **görüntülemek için bu** seçeneği belirleyin. Düzenleyicide kalın metin tanımlamak daha kolaydır.

**Örnek**

Ayarları göster ve Seçili öğeleri görüntüle için yazı tipi stilinin, boyutunun **ve renk düzeninin** **bir örneğini** görüntüler. Farklı biçimlendirme seçenekleriyle denemeler sırasında sonuçları önizlemek için bu kutuyu kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler İletişim Kutusu](../../ide/reference/options-dialog-box-visual-studio.md)
- [Nasıl Yapılır: Yazı Tiplerini ve Renkleri Değiştirme](../../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
