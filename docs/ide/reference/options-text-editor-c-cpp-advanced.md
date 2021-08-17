---
title: Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş
description: IntelliSense ve gözatma veritabanıyla ilgili davranışı değiştirmek için C/C++ bölümünde Gelişmiş sayfasını nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 9e006a5e1e99c2f1b9a8ad81078553004f2d05c9e0ea1f573a1395c49ef7507d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447473"
---
# <a name="options-text-editor-cc-advanced"></a>Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş

Bu seçenekleri değiştirerek, C veya C++ ' da programlama yaparken IntelliSense ve gözatma veritabanıyla ilgili davranışı değiştirebilirsiniz.

Bu sayfaya erişmek için, **Seçenekler** iletişim kutusunda, sol bölmede, **metin düzenleyici**' yi genişletin, **C/C++**' ı genişletin ve **Gelişmiş**' i seçin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. bkz. [Visual Studio ıde 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="browsingnavigation"></a>Göz atma/gezinme

Bir çözümün veritabanı etkinliğinin kabul edilemez bir sistem kaynağı tükettiği çok büyük olduğu durumlar dışında, bu seçenekleri asla seçemezsiniz.

**Veritabanını devre dışı bırak**

Tüm kod gözatma veritabanı (SDF), diğer tüm gözatma/gezinme seçenekleri ve #include otomatik olarak tamamlanmayı hariç tüm IntelliSense özellikleri devre dışı bırakılır.

**Veritabanı güncelleştirmelerini devre dışı bırak**

Veritabanı salt okunurdur ve dosyalar düzenlenirken hiçbir güncelleştirme gerçekleştirilmez. Özelliklerin çoğu çalışmaya devam edecektir. Ancak, düzenlemeler yapıldıkça veriler eski olur ve hatalı sonuçlar elde edersiniz.

**Veritabanı otomatik güncelleştirmelerini devre dışı bırak**

Kaynak dosyalar değiştirildiğinde, kod gözatma veritabanı otomatik olarak güncelleştirilmeyecek. Ancak **Çözüm Gezgini** açarsanız, proje için kısayol menüsünü açın ve ardından **çözümü yeniden Tara**' yı seçerseniz, tüm güncel dosyalar denetlenir ve veritabanı güncelleştirilir.

**Örtük dosyaları devre dışı bırak**

Kod gözatma veritabanı bir projede belirtilmemiş dosyalar için veri toplamaz. Bir proje, açıkça belirtilen kaynak dosyaları ve üst bilgi dosyalarını içerir. Örtük dosyalar açık dosyalara (örneğin, Afxwin. h, Windows. h ve atlbase. h) dahildir. Normal olarak, sistem bu dosyaları bulur ve ayrıca çeşitli gözatma özellikleri (git dahil) için dizinler. Bu seçeneği belirlerseniz, bu dosyalar dizine alınmamış ve bazı özellikler bunlar için kullanılamaz. Bu seçeneği belirlerseniz, "örtük temizlemeyi devre dışı bırak" ve "dış bağımlılıkları devre dışı bırak" seçeneği de örtük olarak seçilir.

**Örtük temizlemeyi devre dışı bırak**

Kod gözatma veritabanı artık başvurulmayan örtük dosyaları temizleyemiyor. Bu seçenek, artık kullanıldıklarında örtük dosyaların veritabanından kaldırılmasını önler. Örneğin, `#include` kaynak dosyalarından birine MAPI. h ' ye başvuran bir yönerge eklerseniz, MAPI. h bulunur ve dizine alınır. #İnclude kaldırırsanız ve dosyaya başka bir yerde başvurulmazsa, bu seçeneği seçmediğiniz takdirde onunla ilgili bilgiler silinir. ( **Çözüm aralığını yeniden Tara** seçeneğine bakın.) Çözümü açıkça yeniden taradığınızda Bu seçenek göz ardı edilir.

**Dış bağımlılıklar klasörlerini devre dışı bırak**

Her proje için dış bağımlılıklar klasörü oluşturulmaz veya güncelleştirilmedi. **Çözüm Gezgini**, her proje, bu proje için tüm örtük dosyaları Içeren bir dış bağımlılıklar klasörü içerir. Bu seçeneği belirlerseniz, bu klasör görünmez.

**Veritabanını yeniden oluştur**

Çözüm bir sonraki sefer yüklendiğinde kod tarama veritabanını hiçbir şey yeniden oluşturun. Bu seçeneği belirlerseniz, çözümü bir dahaki sefer yüklediğinizde SDF veritabanı dosyası silinir, böylece veritabanının yeniden oluşturulmasına ve tüm dosyaların dizine alınmasını sağlayabilirsiniz.

**Çözüm aralığını yeniden Tara**

Belirttiğiniz aralığa göre ' çözümü şimdi yeniden Tara ' işi zamanlandı. 0 ile 5000 dakika arasında bir belirtmeniz gerekir. Varsayılan değer 60 dakikadır. Çözüm yeniden tarandığında, dosya zaman damgaları bir dosyanın IDE dışında değiştirilip değiştirilmediğini belirlemede denetlenir. (IDE 'de yapılan değişiklikler otomatik olarak izlenir ve dosyalar güncelleştirilir.) Örtük olarak eklenen dosyalar, hala başvurulduğunu tespit etmek üzere denetlenir.

## <a name="diagnostic-logging"></a>Tanılama günlüğü

Bu seçenekler, Microsoft 'un bir sorunu tanılamak için gelişmiş bilgi toplamanızı istediğinde sunulmaktadır. Günlüğe kaydetme bilgileri, kullanıcılar için yararlı değildir ve devre dışı bırakmanız önerilir.

**Günlüğe kaydetmeyi etkinleştir**

Çıkış penceresinde tanılama günlüğünü sağlar.

**Günlük Kaydı Düzeyi**

Günlük ayrıntı düzeyini 0 ' dan 5 ' e ayarlayın.

**Günlük kaydı filtresi**

Bir bit maskesi kullanarak, görüntülenmiş olay türlerini filtreler.

Aşağıdaki seçeneklerden herhangi birinin toplamı kullanılarak ayarlanır:

- 0-hiçbiri

- 1-genel

- 2-boşta

- 4-iş öğesi

- 8-IntelliSense

- 16-ACPerf

- 32-ClassView

## <a name="fallback-location"></a>Geri dönüş konumu

Geri dönüş konumu, birincil konum (Çözümle aynı dizin) kullanılmazsa SDF ve IntelliSense destek dosyalarının (örneğin, ıpch) konmasıdır. Bu durum, kullanıcının çözüm dizinine yazma iznine sahip olmaması veya çözüm dizininin yavaş bir cihazda olması olabilir. Varsayılan geri dönüş konumu kullanıcının geçici dizinidir.

**Her zaman geri dönüş konumunu kullan**

Kod gözatma veritabanı ve IntelliSense dosyaları her zaman,. sln dosyasının yanında değil, "temel konumunuz" olarak belirttiğiniz bir klasörde depolanması gerektiğini gösterir. IDE, çözüm dizininin yanına SDF veya ıpch dosyalarını hiçbir zaman almaya çalışmaz ve her zaman geri dönüş konumunu kullanır.

**Geri dönüş konumu kullanılıyorsa uyarma**

Bir ' geri dönüş konumu ' kullanıldığında bilgilendirmez veya uyarılmayacaksınız. Normal olarak, IDE, geri dönüş konumunu kullanmak zorunda olduğunda size bildirir. Bu seçenek, bu uyarıyı kapatır.

**Geri dönüş konumu**

Bu değer, kod tarama veritabanını veya IntelliSense dosyalarını depolamak için ikincil bir konum olarak kullanılır. Varsayılan olarak, geçici dizininiz geri dönüş konumunuzda bulunur. IDE, çözümün adını içeren belirtilen yol (veya geçici dizin) altında bir alt dizin oluşturur ve bu da çözüm adlarının özdeş olan sorunları ortadan kaldırır.

## <a name="intellisense"></a>IntelliSense

**Otomatik hızlı bilgi**

İşaretçiyi metnin üzerine getirdiğinizde hızlı bilgi araç ipuçlarını etkinleştirilir.

**IntelliSense 'i devre dışı bırak**

Tüm IntelliSense özelliklerini devre dışı bırakır. IDE, IntelliSense isteklerine hizmet vermek için VCPkgSrv.exe işlem oluşturmaz ve hiçbir IntelliSense özelliği çalışmaz (hızlı bilgi, üye listesi, otomatik olarak tamamlanan param yardımı). Anlamsal renklendirme ve başvuru vurgulaması de devre dışıdır. Bu seçenek, yalnızca veritabanına (gezinti çubuğu, Sınıfgörünümü ve özellik penceresi dahil) bağlı olan tarama özelliklerini devre dışı bırakır.

**Otomatik güncelleştirmeyi devre dışı bırak**

IntelliSense güncelleştirmesi, IntelliSense için gerçek bir istek yapılıncaya kadar gecikiyor. Bu gecikme, bir dosyadaki ilk IntelliSense işleminin daha uzun bir yürütme süresine neden olabilir, ancak bu seçeneği çok yavaş veya kaynak sınırlamalı makinelerde ayarlamak yararlı olabilir. Bu seçeneği belirlerseniz, "hata raporlamayı devre dışı bırak" ve "dalgalı çizgiler devre dışı bırak" seçeneklerini de örtülü olarak seçersiniz.

**Hata raporlamayı devre dışı bırak**

IntelliSense hatalarının dalgalı çizgiler ve Hata Listesi penceresinden raporlamasını devre dışı bırakır. Ayrıca, hata raporlama ile ilişkili arka plan ayrıştırmayı devre dışı bırakır. Bu seçeneği belirlerseniz, "devre dışı bırak" seçeneğini de örtülü olarak seçersiniz.

**Dalgalı çizgiler devre dışı bırak**

IntelliSense hata dalgalı çizgiler devre dışı bırakır. Kırmızı "dalgalı çizgiler", düzenleyici penceresinde gösterilmez, ancak hata Hata Listesi penceresinde görünmeye devam eder.

**Maksimum önbelleğe alınmış çeviri birimlerini otomatik ayarla**

IntelliSense istekleri için herhangi bir anda etkin tutulacak en fazla çeviri birimi sayısı. 2 ile 15 arasında bir değer belirtmeniz gerekir. Bu numara doğrudan çalıştırılacak VCPkgSrv.exe işlem sayısı üst sınırından (Visual Studio belirli bir örnek için) ilgilidir. Varsayılan değer 2'dir, ancak kullanılabilir belleği varsa bu değeri artırabilir ve IntelliSense'te biraz daha iyi bir performans elde edebilirsiniz.

Çeviri birimleri hakkında daha fazla bilgi için [bkz. Çeviri Aşamaları.](/cpp/preprocessor/phases-of-translation)

**Otomatik #include'yi devre dışı bırakma**

Deyimlerin otomatik tamamlanmasını devre `#include` dışı bırakma.

**Otomatik Tamamlama'da eğik #include eğik çizgi kullanma**

`#include`"/" kullanılırken deyimlerin otomatik tamamlanmasını tetikler. Varsayılan sınırlayıcı ters eğik çizgidir ' \' . Derleyici bu iki seçeneği de kabul eder, bu nedenle kod tabanınızı ne kullandığını belirtmek için bu seçeneği kullanın.

**Devre dışı Agresif Üye Listesi**

Bir tür veya değişkenin adını yazma sırasında üye listesi görünmez. Liste yalnızca, Üye Listesi Yürütme Karakterleri seçeneğinde tanımlandığı gibi işleme karakterlerinden **birini yazmadan sonra** görüntülenir.

**Üye Listesi Anahtar Sözcüklerini Devre Dışı Bırakma**

, gibi dil `void` anahtar sözcükleri üye listesi `class` `switch` önerilerinde görünmez.

**Üye Listesi Kod Parçacıklarını Devre Dışı Bırakma**

Kod parçacıkları üye listesi önerilerinde görünmez.

**Üye Listesi Filtre Modu**

Eşleşen algoritmanın türünü ayarlar. **Fuzzy,** benzer ancak aynı olmayan eşleşmeleri bulmak için yazım denetleyicisine benzer bir algoritma kullandığı için en olası eşleşmeleri bulur. **Akıllı filtreleme,** bir sözcüğün başında değil olsalar bile alt dizeleri eşler. **Ön** ek yalnızca sözcüğün başında başlayan aynı alt dizelerde eşler.

**Semantik Renklendirmeyi Devre Dışı Bırakma**

Dil anahtar sözcükleri, dizeler ve açıklamalar dışında tüm kod renklendirmelerini kapatma.

**Üye Listesi Yürütme Karakterleri**

Şu anda vurgulanan Üye Listesi önerisinin işlendi sinesine neden olan karakterleri belirtir. Bu listeden karakter ekleyebilir veya kaldırabilirsiniz.

**Akıllı Üye Listesi Commit**

Tam olarak türe sahip bir sözcüğün sonuna Enter tuşuna basınca bir satır ekler.

**Üye Listesini Noktalı Okla Etkinleştirme**

Üye Listesi için uygun olduğunda '.' > '->' ile değiştirir.

## <a name="references"></a>Başvurular

**Çözümlemeyi Devre Dışı Bırakma**

Performans nedenleriyle , 'Tüm Başvuruları Bul', her adayı doğrulamak için IntelliSense kullanmak yerine varsayılan olarak ham metin arama sonuçlarını görüntüler. Tüm bulma işlemleriyle ilgili daha doğru sonuçlar için bu onay kutusunu temizebilirsiniz. Arama temelinde filtrelemek için sonuç listesinin kısayol menüsünü açın ve "Sonuçları Çözümle"yi seçin.

**Doğrulanmamış Gizle**

'Tüm Başvuruları Bul' sonuçlarında onaylanmamış öğeleri gizler. "Çözümlemeyi Devre Dışı Bırak" seçeneğinin ayarını geri aldıysanız, sonuçlardaki doğrulanmamış öğeleri gizlemek için bu seçeneği kullanabilirsiniz.

**Başvuru Vurgulamayı Devre Dışı Bırakma**

Varsayılan olarak, bazı metinleri seçerek aynı metnin tüm örnekleri geçerli belgede otomatik olarak vurgulanır. Başvuru Vurgulamayı Devre Dışı Bırak ayarını True **olarak ayarerek bu özelliği devre dışı** **abilirsiniz.**

## <a name="text-editor"></a>Metin Düzenleyici

**Küme Ayraçları ile Çevrele'yi Etkinleştirme**

Etkinleştirilirse, metin düzenleyicisine '{' yazarak seçili metnin küme ayraçları ile çevresini silebilirsiniz.

**Parantezler ile Çevrele'yi Etkinleştirme**

Etkinleştirilirse, metin düzenleyicisine '(' yazarak seçili metnin çevresini parantez içine alın.

## <a name="see-also"></a>Ayrıca bkz.

- [Dile Özgü Düzenleyici Seçeneklerini Ayarlama](../../ide/reference/setting-language-specific-editor-options.md)
