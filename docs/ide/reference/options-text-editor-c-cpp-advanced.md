---
title: Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş
description: IntelliSense ve göz atma veritabanıyla ilgili davranışı değiştirmek için C/C++ bölümündeki Gelişmiş sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: fe69471d231599c6e3eece0b56ff70fca5b6afab
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724926"
---
# <a name="options-text-editor-cc-advanced"></a>Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş

Bu seçenekleri değiştirerek, C veya C++ dilinde programlama yapmak için IntelliSense ve gözatma veritabanıyla ilgili davranışı değiştirebilirsiniz.

Bu sayfaya erişmek için, Seçenekler **iletişim** kutusundaki sol bölmede Metin Düzenleyici'yi **genişletin,** **C/C++ öğesini genişletin** ve gelişmiş'i **seçin.**

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Bkz. [IDE'Visual Studio kişiselleştirme.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="browsingnavigation"></a>Gözatma/Gezinti

Bir çözümün çok büyük olduğu ve veritabanı etkinliğinin kabul edilemez miktarda sistem kaynağı tükettiği nadir durum dışında bu seçenekleri hiçbir zaman seçmeyebilirsiniz.

**Veritabanını Devre Dışı Bırakma**

Koda göz atma veritabanının (SDF), diğer tüm Gözatma/Gezinti seçeneklerinin ve #include Otomatik Tamamlama dışındaki tüm IntelliSense özelliklerinin kullanımı devre dışı bırakılır.

**Veritabanı Güncelleştirmelerini Devre Dışı Bırakma**

Veritabanı salt okunur olarak açılır ve dosyalar düzenlenemezken güncelleştirme gerçekleştirilecek. Çoğu özellik çalışmaya devam ediyor. Ancak, düzenlemeler yapıldı olarak veriler eskir ve yanlış sonuçlar elde olur.

**Veritabanı Otomatik Güncelleştirmelerini Devre Dışı Bırakma**

Kaynak dosyalar değiştirildiğinde koda göz atma veritabanı otomatik olarak güncelleştirilmez. Ancak, **Çözüm Gezgini'yi** açarsanız, projenin kısayol menüsünü açın ve Çözümü YenidenCanla'yı **seçin.** Tüm güncel olmayan dosyalar denetlenir ve veritabanı güncelleştirilir.

**Örtülü Dosyaları Devre Dışı Bırakma**

Koda göz atma veritabanı, projede belirtilmemiş dosyalar için veri toplamaz. Proje, açıkça belirtilen kaynak dosyaları ve üst bilgi dosyalarını içerir. Örtülü dosyalar açık dosyalar (örneğin afxwin.h, windows.h ve atlbase.h) tarafından dahil edilir. Normalde sistem bu dosyaları bulur ve çeşitli göz atma özellikleri (Git dahil) için dizinler. Bu seçeneği kullanırsanız, bu dosyalar dizine ekli değildir ve bazı özellikler bunlar için kullanılamaz. Bu seçeneği seçerseniz, "Örtülü Temizlemeyi Devre Dışı Bırak" ve "Dış Bağımlılıkları Devre Dışı Bırak" da örtülü olarak seçilir.

**Örtülü Temizlemeyi Devre Dışı Bırakma**

Koda göz atma veritabanı artık başvurulmayacak olan örtülü dosyaları temizlemez. Bu seçenek, artık kullanılmadan örtülü dosyaların veritabanından kaldırılmasını önler. Örneğin, kaynak dosyalarınızın biri için mapi.h'ye başvurulan bir yönerge `#include` eklersiniz, mapi.h bulunur ve dizine eklenmiştir. Ardından, #include kaldırırsanız ve dosyaya başka bir yerde başvurulmazsa, bu seçeneği seçmedikçe dosyayla ilgili bilgiler sonunda kaldırılır. **(Bkz. Çözüm Aralığını Yeniden Arala** seçeneği.) Çözümü açıkça yeniden sıyrıyorsanız bu seçenek yoksayılır.

**Dış BağımlılıkLar Klasörlerini Devre Dışı Bırakma**

Her projenin Dış Bağımlılıklar klasörü oluşturulmaz veya güncelleştirilmez. Bu **Çözüm Gezgini,** her proje için tüm örtülü dosyaları içeren bir Dış Bağımlılıklar klasörü içerir. Bu seçeneği seçerseniz bu klasör görünmez.

**Veritabanını Yeniden Oluşturma**

Çözüm bir sonraki yüklemede koda göz atma veritabanını hiçbir şeyden yeniden oluşturun. Bu seçeneği kullanırsanız, çözümü bir sonraki kez yükledikten sonra SDF veritabanı dosyası silinir ve bu da veritabanının yeniden oluşturulmasına ve tüm dosyaların dizine oluşturulmasına neden olur.

**Çözüm Aralığını YenidenCanlama**

Belirttiğiniz aralık için bir 'Çözümü Şimdi Yeniden Arala' işi zamanlandı. 0 ile 5000 dakika arasında bir süre belirtmeniz gerekir. Varsayılan değer 60 dakikadır. Çözüm yenidencannedken, bir dosyanın IDE dışında değiştirilip değiştiril olmadığını belirlemek için dosya zaman damgası denetlenir. (IDE'de yapılan değişiklikler otomatik olarak izlenir ve dosyalar güncelleştirilir.) Örtülü olarak dahil edilen dosyalar, hala başvurulıp başvurulmayacaklarını belirlemek için denetlenir.

## <a name="diagnostic-logging"></a>Tanılama Günlüğü

Microsoft'un bir sorunu tanılamak için gelişmiş bilgi toplamasını isterse bu seçenekler sağlanır. Günlük bilgileri kullanıcılar için kullanışlı değildir ve devre dışı bırakmanız önerilir.

**Günlüğü Etkinleştirme**

Çıkış penceresine tanılama günlüğü kaydını sağlar.

**Günlük Kaydı Düzeyi**

Günlük ayrıntılılığı olarak 0'dan 5'e ayarlayın.

**Günlük Filtresi**

Görüntülenen olay türlerini bit maskesi kullanarak filtreler.

Aşağıdaki seçeneklerden herhangi birini toplamını kullanarak ayarlayın:

- 0 - Yok

- 1 - Genel

- 2 - Boşta

- 4 - WorkItem

- 8 - IntelliSense

- 16 - ACPerf

- 32 - ClassView

## <a name="fallback-location"></a>Geri Dönüş Konumu

Geri dönüş konumu, birincil konum (çözümle aynı dizin) kullanılmadan SDF ve IntelliSense destek dosyalarının (örneğin, iPCH) konma yeridir. Bu durum, kullanıcının çözüm dizinine yazma izninin olmadığını veya çözüm dizininin yavaş bir cihazda olduğunu ortaya çıkabilir. Varsayılan geri dönüş konumu kullanıcının geçici dizinindedir.

**Her zaman Geri Dönüş Konumu Kullan**

Koda göz atma veritabanı ve IntelliSense dosyalarının her zaman .sln dosyasının yanında değil , "Geri Dönüş Konumunuz" olarak belirttiğiniz bir klasörde depolanmış olması gerektiğini gösterir. IDE hiçbir zaman SDF veya iPCH dosyalarını çözüm dizininin yanına koymaya çalışmaz ve her zaman geri dönüş konumunu kullanır.

**Geri dönüş konumu kullanılıyorsa uyarma**

'Geri Dönüş Konumu' kullanılıyorsa size bilgi ve sorulmaz. Normalde, IDE size geri dönüş konumunu kullanmak zorunda olup olamayacaklarını söyler. Bu seçenek bu uyarıyı devre dışıdır.

**Geri Dönüş Konumu**

Bu değer, koda göz atma veritabanı veya IntelliSense dosyalarını depolamak için ikincil konum olarak kullanılır. Varsayılan olarak geçici dizininiz geri dönüş konumunuzdur. IDE, çözümün tam yolunun karmasıyla birlikte çözümün adını içeren belirtilen yol (veya geçici dizin) altında bir alt dizin oluşturacak ve bu da çözüm adlarının aynı olmasıyla ilgili sorunları önler.

## <a name="intellisense"></a>IntelliSense

**Otomatik Hızlı Bilgi**

İşaretçiyi metnin üzerine taşıyabilirsiniz.

**IntelliSense'i devre dışı bırakma**

Tüm IntelliSense özelliklerini devre dışı bırakma. IDE, IntelliSense isteklerine VCPkgSrv.exe işlemler oluşturmaz ve hiçbir IntelliSense özelliği çalışmaz (QuickInfo, Üye Listesi, Otomatik Tamamlama, Param Yardımı). Semantik renklendirme ve başvuru vurgulama da devre dışı bırakılır. Bu seçenek yalnızca veritabanına (Gezinti Çubuğu, ClassView ve Özellik penceresi dahil) bağlı olan göz atma özelliklerini devre dışı bırakmaz.

**Otomatik Güncelleştirmeyi Devre Dışı Bırakma**

IntelliSense güncelleştirmesi, IntelliSense için gerçek bir istek yapılana kadar geciktirilir. Bu gecikme bir dosyada ilk IntelliSense işlemi daha uzun yürütme süresine neden olabilir, ancak çok yavaş veya kaynak kısıtlı makinelerde bu seçeneği ayarlamak yararlı olabilir. Bu seçeneği seçerseniz, "Hata Raporlamayı Devre Dışı Bırak" ve "Geçişleri Devre Dışı Bırak" seçeneklerini de örtülü olarak seçersiniz.

**Hata Raporlamayı Devre Dışı Bırakma**

Geçişler ve Hata Listesi penceresi aracılığıyla IntelliSense hatalarının raporlanması devre dışıdır. Ayrıca hata raporlama ile ilişkili arka plan ayrıştırmayı devre dışı da devre dışı bıraktır. Bu seçeneği seçerseniz, "Geçişleri Devre Dışı Bırak" seçeneğini de örtülü olarak seçersiniz.

**Geçişleri Devre Dışı Bırakma**

IntelliSense hata geçişlerini devre dışı bırakma. Düzenleyici penceresinde kırmızı "geçişler" görünmez, ancak hata Hata Listesi penceresinde görünmeye devam ediyor.

**Önbelleğe Alınan En Fazla Çeviri Birimini Otomatik Ayarlama**

IntelliSense istekleri için herhangi bir anda etkin tutulacak maksimum çeviri birimi sayısı. 2 ile 15 arasında bir değer belirtmeniz gerekir. Bu sayı doğrudan çalıştıracak en fazla VCPkgSrv.exe işlem sayısıyla ilgilidir (verili bir örnek için Visual Studio). Varsayılan değer 2 ' dir, ancak kullanılabilir belleğiniz varsa, bu değeri artırabilir ve IntelliSense üzerinde biraz daha iyi bir performans elde edebilirsiniz.

Çeviri birimleri hakkında daha fazla bilgi için bkz. [Çeviri aşamaları](/cpp/preprocessor/phases-of-translation).

**#İnclude otomatik tamamlamayı devre dışı bırak**

Deyimlerin otomatik tamamlamayı devre dışı bırakır `#include` .

**#İnclude otomatik olarak eğik çizgi kullan**

`#include`"/" Kullanıldığında deyimlerin otomatik tamamlamayı tetikler. Varsayılan sınırlayıcı ters eğik çizgi ' dir \' . Derleyici her ikisini de kabul edebilir, bu nedenle kod tabanınızı kullanıp kullanmadığını belirtmek için bu seçeneği kullanın.

**Agresif üye listesini devre dışı bırak**

Üye listesi, bir tür veya değişkenin adını yazdığınızda görünmez. Liste yalnızca, kayıt karakterlerinden birini yazdığınızda, **üye listesi tamamlama karakterleri** seçeneğinde tanımlandığı şekilde görünür.

**Üye listesi anahtar sözcüklerini devre dışı bırak**

,,,,,,, `void` `class` `switch` Üye listesi önerilerinde görünmüyor.

**Üye listesi kod parçacıklarını devre dışı bırak**

Kod parçacıkları üye listesi önerilerinde görünmez.

**Üye listesi filtre modu**

Eşleşen algoritmanın türünü ayarlar. Benzer ancak özdeş olan eşleşmeleri bulmak için yazım denetimcisine benzer bir algoritma kullandığından **, benzer en olası eşleşmeleri bulur.** **Akıllı filtreleme** bir sözcüğün başlangıcında olmasalar bile alt dizelerdeki eşleşir. **Ön ek** yalnızca sözcüğün başlangıcında başlayan özdeş alt dizeler üzerinde eşleşir.

**Anlam renklendirmeyi devre dışı bırak**

Dil anahtar sözcükleri, dizeler ve açıklamalar hariç tüm kod renklendirmeyi kapatır.

**Üye listesi tamamlama karakterleri**

Vurgulanmış olan üye listesi önerisine neden olan karakterleri belirtir. Bu listeden karakter ekleyebilir veya kaldırabilirsiniz.

**Akıllı üye listesi yürütmesi**

Tam olarak yazılmış bir sözcüğün sonunda Enter tuşunu seçtiğinizde bir satır ekler.

**Üye listesi noktayı Oka Dönüştür**

Üye listesi için uygulanabilir olduğunda '. ' yerine '-> ' koyar.

## <a name="references"></a>Başvurular

**Çözümlemeyi devre dışı bırak**

Performans nedenleriyle, her adayı doğrulamak için IntelliSense kullanmak yerine, ' tüm başvuruları bul ' varsayılan olarak ham metinsel arama sonuçlarını görüntüler. Tüm bulma işlemlerinde daha doğru sonuçlar için bu onay kutusunu temizleyebilirsiniz. Arama başına temelinde filtrelemek için, Sonuç listesinin kısayol menüsünü açın ve "sonuçları çözümle" öğesini seçin.

**Onaylanmamışları gizle**

' Tüm başvuruları bul ' sonuçlarında onaylanmamış öğeleri gizleyin. "Çözümlemeyi devre dışı bırak" seçeneğini ayarlarsanız, sonuçlarda onaylanmamış öğeleri gizlemek için bu seçeneği kullanabilirsiniz.

**Başvuru vurgulamasını devre dışı bırak**

Varsayılan olarak, bazı metinleri seçtiğinizde, aynı metnin tüm örnekleri otomatik olarak geçerli belgede vurgulanır. **Başvuru Vurgulamayı devre dışı bırak** ayarını **true** olarak ayarlayarak bu özelliği devre dışı bırakabilirsiniz.

## <a name="text-editor"></a>Metin Düzenleyici

**Küme ayraçlarıyla çevrelemeyi etkinleştir**

Etkinleştirilirse, metin düzenleyicisine ' {' yazarak seçili metni küme ayraçları ile çevreleyin.

**Parantezlerle çevrelemeyi etkinleştir**

Etkinleştirilirse, metin düzenleyicisine ' (' yazarak seçili metni parantezlerle çevrelemeyi seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
