---
title: Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş
description: IntelliSense ve gözatma veritabanıyla ilgili davranışı değiştirmek için C/C++ bölümünde Gelişmiş sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/08/2021
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
ms.openlocfilehash: 1e301de225f65c4a625939b8158d8d4a8cdefeb7
ms.sourcegitcommit: 5f1e0171626e13bb2c5a6825e28dde48061208a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2021
ms.locfileid: "129704402"
---
# <a name="options-text-editor-cc-advanced"></a>Seçenekler, Metin Düzenleyici, C/C++, Gelişmiş

Bu seçenekleri değiştirerek, C veya C++ ' da programlama yaparken IntelliSense ve gözatma veritabanıyla ilgili davranışı değiştirebilirsiniz.

Bu sayfaya erişmek için, **Seçenekler** iletişim kutusunda, sol bölmede, **metin düzenleyici**' yi genişletin, **C/C++**' ı genişletin ve **Gelişmiş**' i seçin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. bkz. [Visual Studio ıde 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="brace-completion"></a>Küme ayracı tamamlama

**Türler için noktalı virgül Ekle**

Türler için küme ayraçları kapatıldıktan sonra noktalı virgül eklenecektir.

**Ham dize değişmez değerlerinde parantez Tamam**

Ham dize sabit değerinde açık bir parantez yazılmışsa, bir kapanış ayracı ile tamamlanır.

**Çok satırlı açıklamaları doldurun**

Çok satırlı açıklamalar (ile başlayan açıklamalar `/*` ) tamamlanır.

## <a name="browsing-database-fallback"></a>Veritabanı geri dönüşü göz atma

Geri dönüş konumu, birincil konum (Çözümle aynı dizin) kullanılmazsa SDF ve IntelliSense destek dosyalarının (örneğin, ıpch) konmasıdır. Bu durum, kullanıcının çözüm dizinine yazma iznine sahip olmaması veya çözüm dizininin yavaş bir cihazda olması olabilir. Varsayılan geri dönüş konumu kullanıcının geçici dizinidir.

**Her zaman geri dönüş konumunu kullan**

Kod gözatma veritabanı ve IntelliSense dosyaları her zaman,. sln dosyasının yanında değil, "temel konumunuz" olarak belirttiğiniz bir klasörde depolanması gerektiğini gösterir. IDE, çözüm dizininin yanına SDF veya ıpch dosyalarını hiçbir zaman almaya çalışmaz ve her zaman geri dönüş konumunu kullanır.

**Geri dönüş konumu kullanılıyorsa uyarma**

Bir ' geri dönüş konumu ' kullanıldığında bilgilendirmez veya uyarılmayacaksınız. Normal olarak, IDE, geri dönüş konumunu kullanmak zorunda olduğunda size bildirir. Bu seçenek, bu uyarıyı kapatır.

**Geri dönüş konumu**

Bu değer, kod tarama veritabanını veya IntelliSense dosyalarını depolamak için ikincil bir konum olarak kullanılır. Varsayılan olarak, geçici dizininiz geri dönüş konumunuzda bulunur. IDE, çözümün adını içeren belirtilen yol (veya geçici dizin) altında bir alt dizin oluşturur ve bu da çözüm adlarının özdeş olan sorunları ortadan kaldırır.

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

**Güncel denetimi taramayı devre dışı bırak**

, Gözatma işlemlerini yürütürken kod gözatma veritabanının güncel olmasını beklemeyi devre dışı bırakır.

**Geçerli öğe seçimini devre dışı bırak**

Özellikler araç penceresinde ve başka bir yerde seçili kod öğesinin görselleştirmesini devre dışı bırakır.

**Dış dosyalar için Atlanan bölgeleri görüntüle**

Gözatma veritabanı hatalarını görüntülerken, dış dosyalardaki atlanan bölgeleri dahil edin.

## <a name="code-analysis"></a>Kod Çözümleme

**C++ Code Analysis deneyimini devre dışı bırak**

Code analysis dalgalı çizgiler, background Code Analysis ve c++ dosyaları için diğer özellikler için destek sağlayan c++ Code Analysis deneyimini devre dışı bırakın.

**Arka plan Code Analysis devre dışı bırak**

dosyalar açıldığında veya kaydedildiğinde arka planda C++ Code Analysis çalıştırmayı devre dışı bırakın.

**Code Analysis dalgalı çizgiler devre dışı bırak**

C++ Code Analysis uyarıları için dalgalı çizgiler devre dışı bırakın. Hatalar hata listesinde gösterilmeye devam edecektir. Yalnızca yeni açılan pencereleri etkiler.

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

Kullanılabilir sistem RAM 'ine göre, IntelliSense istekleri için herhangi bir anda etkin tutulacak en fazla çeviri birimi sayısını mümkün olur.

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

**Üye Listesi kayıt agresif**

' Üye listesi tamamlama karakterleri ' ' kararlılık ' üye listesi sırasında etkin.

**Otomatik üye listesi için agresif üye listesini kullan**

Etkin ve otomatik üye listesi gösterildiğinde, üye listesi tamamlama karakterlerini kullanarak tamamlanmaz.

**Agresif üye listesinde yürütmek için sekmeyi kullanın**

Etkin ve agresif üye listesi gösterildiğinde, sekme tuşunu üye listesi Işleme karakteri olarak değerlendirin.

**Kod parçacığı eklemek için Tab kullanın**

Etkinleştirildiğinde, `Edit.InvokeSnippetFromShortcut` üye listesinin gösterilip gösterilmediğine bakılmaksızın sekme basıldığında parçacık anahtar sözcüğü genişletilir (kısayol tuşu şuna atanmamışsa).

**Modülleri devre dışı bırak**

IntelliSense için gereken modülleri otomatik oluşturma gibi çeşitli C++ 20 modülleri IDE özelliklerini devre dışı bırakın.

**Üye listesi filtresine erişilemiyor**

Üye listelerinde erişilemeyen öğeleri gösterme.

**Etkin olmayan platformlar için IntelliSense 'i devre dışı bırak**

Klasörlerdeki ve paylaşılan varlıklar projelerindeki etkin olmayan platformlar için tüm IntelliSense özelliklerini devre dışı bırakın.

**Üye listesi noktayı Oka Dönüştür**

Üye listesi için uygulanabilir olduğunda '. ' yerine '-> ' koyar.

**HLSL IntelliSense 'i devre dışı bırak**

Tüm HLSL IntelliSense özelliklerini devre dışı bırakın.

**Otomatik önceden derlenmiş üstbilgiyi devre dışı bırak**

Otomatik önceden derlenmiş üstbilgi, bazı IntelliSense işlemlerini, çözüm başına sabit sürücü önbelleğinin masrafına göre hızlandırabilir.

**Otomatik önceden derlenmiş üst bilgi önbelleği kotası**

Çözüm başına önbelleğin megabayt cinsinden en büyük boyutu; gerçek kullanım bu değerin etrafında dalgalanmaya başlayabilir.

**Etkin olmayan platform IntelliSense sınırı**

IntelliSense için işlenecek, etkin olmayan en fazla platform sayısı.  Değer 1 ile 16 arasında olmalıdır.

**Şablon IntelliSense 'i etkinleştir**

İmleç bir şablon gövdesinde etkin olduğunda, şablonun IntelliSense 'i yapılandırmak için düzenleyicide bir çubuk görüntüler.

**Hızlı bilgiyle yardım bağlantısını etkinleştir**

Hızlı Bilgi ipucu çevrimiçi aramalara bağlantıyı sağlar.

**Hızlı bilgi yardım bağlantısında Web Araması kullan**

Hızlı Bilgi ipucu çevrimiçi aramalar için eylem olarak belirtilen arama sağlayıcısıyla bir Web araması başlatır. Devre dışı bırakıldığında F1 yardımı kullanır.

**IntelliSense hata araç Ipuçlarında yardım bağlantısını etkinleştir**

IntelliSense hata araç ipuçlarında çevrimiçi aramalara bağlantıyı sağlar.

**Arama sağlayıcısı**

Hatalarda çevrimiçi yardım bulmak için kullanılan URL, {0} hata ile değiştiriliyor

## <a name="intellisense-and-browsing-for-non-project-files"></a>Project olmayan dosyalar için ıntellisense ve gözatma

**Gelişmiş Tek Dosya etkinleştir**

Var olan bir projenin parçası olmayan tek başına dosyalar için IntelliSense, gözatma ve diğer özellikleri sunar.

**IntelliSense dalgalı çizgiler etkinleştir**

Gelişmiş Tek Dosya modundaki tek başına dosyalar için dalgalı çizgiler 'ı sunar.

**IntelliSense hatalarını Hata Listesi göster**

Tek başına dosyalardaki IntelliSense hatalarının Hata Listesi görüntülenip görüntülenmediğini denetler.

**Hata ayıklama sırasında yeni dosyaları askıya al**

Hata ayıklama sırasında yeni açılan dosyalar için IntelliSense 'i etkinleştirmeyi askıya alın.

## <a name="refactoring"></a>Yeniden Düzenle

**Bildirim/tanım oluşturma hafif Bult'leri devre dışı bırak**

Eksik bir işlev bildirimi veya tanımı oluşturmak için öneriler sunmaz.

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
