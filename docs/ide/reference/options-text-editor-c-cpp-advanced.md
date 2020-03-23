---
title: Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş
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
ms.openlocfilehash: 2e7e031836c9762d9666a5624e78ecc7c8cc7dd9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275204"
---
# <a name="options-text-editor-cc-advanced"></a>Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş

Bu seçenekleri değiştirerek, C veya C++'da programlama yaparken IntelliSense ve tarama veritabanıyla ilgili davranışı değiştirebilirsiniz.

Bu sayfaya erişmek için, Sol bölmedeki **Seçenekler** iletişim kutusunda, Metin Düzenleyicisi'ni genişletin, **C/C++** genişletin ve gelişmiş **seçeneğini**seçin. **Text Editor**

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. [Bkz. Visual Studio IDE'yi Kişiselleştirin.](../../ide/personalizing-the-visual-studio-ide.md)

## <a name="browsingnavigation"></a>Tarama/Gezinme

Veritabanı etkinliği kabul edilemez miktarda sistem kaynakları tüketir, bir çözüm çok büyük olduğu nadir durumlar dışında bu seçenekleri asla seçmemelisiniz.

**Veritabanını Devre Dışı**

Kod tarama veritabanının (SDF), diğer tüm Tarama/Gezinme seçeneklerinin ve #include Otomatik Tamamlama dışındaki tüm IntelliSense özelliklerinin tüm kullanımı devre dışı bırakılır.

**Veritabanı Güncelleştirmelerini Devre Dışı**

Veritabanı salt okunur olarak açılır ve dosyalar düzenlenirken güncelleştirme yapılmaz. Çoğu özellik çalışmaya devam edecektir. Ancak, yapılan lar gibi, veriler bayatlanır ve yanlış sonuçlar alırsınız.

**Veritabanı Otomatik Güncelleştirmelerini Devre Dışı**

Kaynak dosyalar değiştirildiğinde kod tarama veritabanı otomatik olarak güncelleştirilmez. Ancak, Solution **Explorer'ı**açarsanız, proje için kısayol menüsünü açın ve ardından **Rescan Solution'ı**seçin, güncel olmayan tüm dosyalar denetlenir ve veritabanı güncelleştirilir.

**Örtülü Dosyaları Devre Dışı**

Kod tarama veritabanı, projede belirtilmeyen dosyalar için veri toplamaz. Proje, açıkça belirtilen kaynak dosyaları ve üstbilgi dosyaları içerir. Örtük dosyalar açık dosyalar (örneğin, afxwin.h, windows.h ve atlbase.h) tarafından eklenmiştir. Normalde, sistem bu dosyaları bulur ve çeşitli tarama özellikleri (Gezinme dahil) için dizinler. Bu seçeneği seçerseniz, bu dosyalar dizine eklenmez ve bazı özellikler bunlar için kullanılamaz. Bu seçeneği seçerseniz, "Örtülü Temizlemeyi Devre Dışı" ve "Dış Bağımlılıkları Devre Dışı" da dolaylı olarak seçilir.

**Örtülü Temizlemeyi Devre Dışı**

Kod tarama veritabanı artık başvurulan örtük dosyaları temizlemez. Bu seçenek, örtük dosyaların artık kullanılmadığında veritabanından kaldırılmasını önler. Örneğin, mapi.h'ye kaynak dosyalarınızdan birine başvuran bir `#include` yönerge eklerseniz, mapi.h bulunur ve dizine eklenir. Daha sonra #include kaldırırsanız ve dosya başka bir yerde başvurulmuyorsa, bu seçeneği seçmediğiniz sürece dosyayla ilgili bilgiler sonunda kaldırılacaktır. **(Bkz. Rescan Çözüm Aralığı** seçeneği.) Çözümü açıkça rescan zaman bu seçenek yoksayılır.

**DışBağımlılık Klasörlerini Devre Dışı**

Her proje için Dışa Bağımlılıklar klasörü oluşturulmaz veya güncelleştirilemiyor. **Çözüm Gezgini'nde,** her proje, o proje için tüm örtük dosyaları içeren bir Dışa Bağımlılıklar klasörü içerir. Bu seçeneği seçerseniz, bu klasör görünmez.

**Veritabanını Yeniden Oluşturma**

Çözüm yüklenirse bir dahaki sefere kod tarama veritabanını hiçbir şeyden yeniden oluşturun. Bu seçeneği seçerseniz, çözümü bir sonraki yüklediğinizde SDF veritabanı dosyası silinir ve böylece veritabanının yeniden oluşturulmasına ve tüm dosyaların dizine alınmasına neden olur.

**Rescan Çözüm Aralığı**

Belirttiğiniz aralık için bir 'Rescan Solution Now' işi zamanlanır. 0 ile 5000 dakika arasında belirtmeniz gerekir. Varsayılan değer 60 dakikadır. Çözüm yeniden taranırken, dosyanın IDE dışında değiştirilip değiştirilmediğini belirlemek için dosya zaman damgaları denetlenir. (IDE'de yapılan değişiklikler otomatik olarak izlenir ve dosyalar güncelleştirilir.) Örtülü olarak eklenmiş dosyalar, hepsinin hala başvurulup başvurulmadığını belirlemek için denetlenir.

## <a name="diagnostic-logging"></a>Tanılama Günlüğü

Bu seçenekler, Microsoft'un bir sorunu tanılamak için gelişmiş bilgiler toplamanızı istemesi durumunda sağlanır. Günlük bilgileri kullanıcılar için yararlı değildir ve bu bilgileri devre dışı bırakmanızı öneririz.

**Günlük Atamasını Etkinleştir**

Çıkış penceresine tanılama günlüğe kaydetmeyi sağlar.

**Günlük Kaydı Düzeyi**

Günlük ayrıntılılığını 0'dan 5'e ayarlayın.

**Günlük Filtresi**

Filtreler bir bitmask kullanarak olay türleri görüntülenir.

Aşağıdaki seçeneklerden herhangi birinin toplamını kullanarak ayarlayın:

- 0 - Yok

- 1 - Genel

- 2 - Boşta

- 4 - İş Öğesi

- 8 - IntelliSense

- 16 - ACPerf

- 32 - ClassView

## <a name="fallback-location"></a>Geri Dönüş Konumu

Geri dönüş konumu, birincil konum (çözümle aynı dizin) kullanılmadığında SDF ve IntelliSense destek dosyalarının (örneğin, iPCH) konulduğu yerdir. Bu durum, kullanıcının çözüm dizinine yazma izinlerine sahip olmaması veya çözüm dizininin yavaş bir aygıtta olması durumunda oluşabilir. Varsayılan geri dönüş konumu kullanıcının geçici dizinindedir.

**Her Zaman Geri Dönüş Konumunu Kullan**

Kod tarama veritabanı nın ve IntelliSense dosyalarının her zaman .sln dosyasının yanında değil, "Fallback Location" olarak belirttiğiniz bir klasörde depolanması gerektiğini belirtir. IDE, SDF veya iPCH dosyalarını çözüm dizininin yanına koymaya asla çalışmaz ve her zaman geri dönüş konumunu kullanır.

**Geri Dönüş Konumu Kullanılırsa Uyarmayın**

'Geri Dönüş Konumu' kullanılırsa bilgilendirilmediğiniz veya istenmediğiniz. Normalde, IDE geri dönüş konumunu kullanmak zorunda olup olmadığını size söyleyecektir. Bu seçenek bu uyarıyı kapatır.

**Geri Dönüş Konumu**

Bu değer, kod tarama veritabanını veya IntelliSense dosyalarını depolamak için ikincil bir konum olarak kullanılır. Varsayılan olarak, geçici dizininiz geri dönüş konumunuzdur. IDE, çözüme giden yolun bir karmasıyla birlikte çözümün adını içeren belirtilen yolun (veya geçici dizinin) altında çözüm adlarının aynı olmasıyla ilgili sorunları önleyen bir alt dizini oluşturur.

## <a name="intellisense"></a>IntelliSense

**Otomatik Hızlı Bilgi**

İşaretçiyi metin üzerinde hareket ettirdiğinizde QuickInfo araç ipuçlarını etkinleştirir.

**IntelliSense'i devre dışı**

Tüm IntelliSense özelliklerini devre dışı kılabilir. IDE, IntelliSense isteklerini yerine getirmek için VCPkgSrv.exe süreçleri oluşturmaz ve Hiçbir IntelliSense özelliği çalışmaz (QuickInfo, Üye Listesi, Otomatik Tamamlama, Param Yardımı). Anlamsal renklendirme ve referans vurgulama da devre dışı bırakılır. Bu seçenek, yalnızca veritabanına (Gezinti Çubuğu, ClassView ve Özellik penceresi dahil) dayanan tarama özelliklerini devre dışı almaz.

**Otomatik Güncellemeyi Devre Dışı**

IntelliSense güncelleme, IntelliSense için gerçek bir istek yapılana kadar geciktirilir. Bu gecikme, bir dosyadaki ilk IntelliSense işleminin daha uzun bir yürütme süresine neden olabilir, ancak bu seçeneği çok yavaş veya kaynak kısıtlı makinelerde ayarlamak yararlı olabilir. Bu seçeneği seçerseniz, "Hata Raporlamasını Devre Dışı" ve "Squiggles'ı devre dışı" seçeneklerini de dolaylı olarak seçersiniz.

**Hata Bildirimini Devre Dışı**

Squiggles ve Hata Listesi penceresi aracılığıyla IntelliSense hataları raporlama devre dışı kalmaktadır. Ayrıca, hata raporlamasıyla ilişkili arka plan ayrıştırmasını da devre dışı kılabilir. Bu seçeneği seçerseniz, "Squiggles'ı devre dışı" seçeneğini de zımni olarak seçersiniz.

**Squiggles devre dışı**

IntelliSense hata squiggles devre dışı kalmaktadır. Kırmızı "dalgalı" düzenleyici penceresinde görünmüyor, ancak hata yine de Hata Listesi penceresinde görünür.

**Otomatik Tune Max Önbelleğe Alınmış Çeviri Birimleri**

IntelliSense istekleri için herhangi bir anda etkin tutulacak maksimum çeviri birimi sayısı. 2 ile 15 arasında bir değer belirtmeniz gerekir. Bu sayı doğrudan çalışacak vcpkgSrv.exe süreçlerinin maksimum sayısı ile ilgilidir (Visual Studio belirli bir örnek için). Varsayılan değer 2'dir, ancak kullanılabilir belleğe sahipseniz, bu değeri artırabilir ve intelliSense'de biraz daha iyi performans elde edebilirsiniz.

Çeviri birimleri hakkında daha fazla bilgi için çeviri [aşamalarına](/cpp/preprocessor/phases-of-translation)bakın.

**Otomatik Tamamlama #include devre dışı**

İfadelerin otomatik olarak tamamlanmasını `#include` devre dışı kılmaktadır.

**Otomatik Tamamlama #include'da İleri Yele'yi Kullanma**

"/" kullanıldığında `#include` ifadelerin otomatik olarak tamamlanmasını tetikler. Varsayılan delimiter backslash\'' olduğunu. Derleyici her ikisini de kabul edebilir, bu nedenle kod tabanınızın ne kullandığını belirtmek için bu seçeneği kullanın.

**Agresif Üye Listesini Devre Dışı**

Bir türün veya değişkenin adını yazarken üye listesi görünmez. Liste, **yalnızca Üye Listesi Karakterleri İşleme** seçeneğinde tanımlandığı gibi, işleme karakterlerinden birini yazdıktan sonra görüntülenir.

**Üye Listesi Anahtar Kelimelerini Devre Dışı**

`void`, , `class` `switch` üye listesi önerilerinde görünmez.

**Üye Liste Kodu Parçacıklarını Devre Dışı**

Kod parçacıkları üye listesi önerilerinde görünmez.

**Üye Listesi Filtre Modu**

Eşleşen algoritma türünü ayarlar. **Bulanık,** benzer ancak aynı olmayan eşleşmeleri bulmak için yazım denetleyicisine benzer bir algoritma kullandığından mümkün olan en olası eşleşmeleri bulur. **Akıllı filtreleme,** bir sözcüğün başında olmasalar bile alt dizeleri eşleşir. **Önek** yalnızca sözcüğün başında başlayan aynı alt dizeleri eşleşir.

**Anlamsal Renklendirmeyi Devre Dışı**

Dil anahtar kelimeleri, dizeleri ve açıklamalar dışında tüm kod renklendirmesini kapatır.

**Üye Listesi Karakterleri Commit**

Şu anda vurgulanan Üye Listesi önerisinin işlenmesine neden olan karakterleri belirtir. Bu listeden karakter ekleyebilir veya kaldırabilirsiniz.

**Akıllı Üye Listesi Commit**

Tam olarak yazılan bir sözcüğün sonunda Enter tuşunu seçtiğinizde bir satır ekler.

**Üye Listesini Etkinleştir Nokta-To-Ok**

Üye Listesi için geçerli olduğunda '.' ile '.' yerine '->' alır.

## <a name="references"></a>Başvurular

**Çözmeyi Devre Dışı**

Performans nedenleriyle ,'Tüm Başvuruları Bul' her adayı doğrulamak için IntelliSense kullanmak yerine varsayılan olarak ham metin arama sonuçlarını görüntüler. Tüm bulma işlemlerinde daha doğru sonuçlar elde etmek için bu onay kutusunu temizleyebilirsiniz. Arama başına filtre uygulayabilmek için, sonuç listesinin kısayol menüsünü açın ve ardından "Sonuçları Çözümle"yi seçin.

**Onaylanmamış Gizle**

Onaylanmamış öğeleri 'Tüm Başvuruları Bul' sonuçlarında gizleyin. "Çözmeyi Devre Dışı Bırak" seçeneğini ayarlarsanız, sonuçlarda onaylanmamış öğeleri gizlemek için bu seçeneği kullanabilirsiniz.

**Başvuru Vurgulamayı devre dışı**

Varsayılan olarak, bazı metni seçtiğinizde, geçerli belgede aynı metnin tüm örnekleri otomatik olarak vurgulanır. **Başvuru Vurgulamasını** **True'ya**devre dışı katarak bu özelliği devre dışı kullanabilirsiniz.

## <a name="text-editor"></a>Metin Düzenleyici

**Ayraçlarla Surround'u Etkinleştir**

Etkinse, metin düzenleyicisine '{' yazarak seçili metni kıvırcık ayraçlarla çevreleyebilirsiniz.

**Parantezle Surround'u Etkinleştir**

Etkinleştirilirse, metin düzenleyicisine '(' yazarak seçili metni parantez içinde çevreleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
