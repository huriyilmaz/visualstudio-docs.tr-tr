---
title: VSTest.Console.exe komut satırı seçenekleri
ms.date: 07/12/2018
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d4c44719854714658c1c15bf7059e49f4e668bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590429"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe komut satırı seçenekleri

*VSTest. Console. exe* , testleri çalıştırmak için komut satırı aracıdır. Komut satırında herhangi bir sırada birkaç seçenek belirtebilirsiniz. Bu seçenekler [genel komut satırı seçeneklerinde](#general-command-line-options)listelenmiştir.

> [!NOTE]
> Visual Studio 'daki MSTest bağdaştırıcı ayrıca uyumluluk için eski modda ( *MSTest. exe*ile testleri çalıştırmaya eşdeğerdir) çalışır. Eski modda, TestCaseFilter özelliğinden faydalanabilirsiniz. Bir *testsettings* dosyası belirtildiğinde, bağdaştırıcı eski moda geçebilir, **forcelegacymode** bir *runsettings* dosyasında **true** olarak ayarlanır veya **HostType**gibi öznitelikler kullanılarak.
>
> ARM mimarisi tabanlı bir makinede otomatikleştirilmiş testler çalıştırmak için *VSTest. Console. exe*kullanmanız gerekir.

## <a name="general-command-line-options"></a>Genel komut satırı seçenekleri

Aşağıdaki tabloda *VSTest. Console. exe* için tüm seçenekler ve bunların kısa açıklamaları listelenmektedir. Bir komut satırına `VSTest.Console/?` yazarak benzer bir Özet görebilirsiniz.

| Seçenek | Açıklama |
|---|---|
|**[*test dosyası adları*]**|Belirtilen dosyalardan testleri çalıştırın. Birden çok test dosyası adını boşluklarla ayırın.<br />Örnekler: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings: [*dosya adı*]**|Testleri veri toplayıcılar gibi ek ayarlarla çalıştırın.<br />Örnek: `/Settings:Local.RunSettings`|
|**/TESTS: [*Test adı*]**|Testleri, belirtilen değerleri içeren adlarla çalıştırın. Birden çok değer sağlamak için bunları virgülle ayırın.<br />Örnek: `/Tests:TestMethod1,testMethod2`<br />**/Tests** komut satırı seçeneği, **/TestCaseFilter** komut satırı seçeneğiyle birlikte kullanılamaz.|
|**/Parallel**|Testlerin paralel olarak yürütüleceğini belirtir. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. Bir ayar dosyasında kullanılacak çekirdek sayısını yapılandırabilirsiniz.|
|**/Enablecodecoverage**|Test çalıştırmasında veri tanılama bağdaştırıcısı CodeCoverage öğesine izin vermez.<br />Ayarlar dosyası kullanılarak belirtilmemişse varsayılan ayarlar kullanılır.|
|**/Inısolation**|Testleri yalıtılmış bir işlemde çalıştırır.<br />Bu yalıtım, *VSTest. Console. exe* işleminin testlerin bir hata üzerinde durdurulması olasılığını azaltır, ancak testler daha yavaş çalışabilir.|
|**/UseVsixExtensions**|Bu seçenek, *VSTest. Console. exe* işleminin Test çalıştırmasında yüklü olan (varsa) VSIX uzantılarını kullanmasını veya atlamasını sağlar.<br />Bu seçenek kullanım dışıdır. Visual Studio 'nun bir sonraki ana sürümünden itibaren bu seçenek kaldırılabilir. NuGet paketi olarak kullanılabilir hale getirilen genişletme uzantılarına taşıyın.<br />Örnek: `/UseVsixExtensions:true`|
|**/TestAdapterPath: [*yol*]**|*VSTest. Console. exe* işlemini, Test çalıştırmasında belirtilen yoldan (varsa) özel test bağdaştırıcılarını kullanacak şekilde zorlar.<br />Örnek: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform: [*Platform türü*]**|Test yürütmesi için kullanılacak hedef platform mimarisi.<br />Geçerli değerler x86, x64 ve ARM 'dir.|
|**/Framework: [*Framework sürümü*]**|Test yürütmesi için kullanılacak hedef .NET sürümü.<br />Örnek değerler `Framework35`, `Framework40`, `Framework45`, `FrameworkUap10`, `.NETCoreApp,Version=v1.1`.<br />Hedef çerçeve **Framework35**olarak belirtilmişse, testler CLR 4,0 "uyumluluk modunda" çalışır.<br />Örnek: `/Framework:framework40`|
|**/TestCaseFilter: [*ifade*]**|Verilen ifadeyle eşleşen testleri çalıştırın.<br />< Ifade\> biçim < Özellik\>= < değer\>[\|< expression\>].<br />Örnek: `/TestCaseFilter:"Priority=1"`<br />Örnek: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />**/TestCaseFilter** komut satırı seçeneği **/Tests** komut satırı seçeneğiyle birlikte kullanılamaz. <br />İfadeleri oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Kullanım bilgilerini görüntüler.|
|**/Günlükçü: [*Uri/FriendlyName*]**|Test sonuçları için bir günlükçü belirtin.<br />Örnek: sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek Için **/günlükçü: TRX**komutunu kullanın.<br />Örnek: Team Foundation Server test sonuçlarını yayınlamak Için TfsPublisher kullanın:<br />**/günlükçü: TfsPublisher;**<br />**Koleksiyon = < projesi URL 'si\>;**<br />**BuildName = < derleme adı\>;**<br />**TeamProject = < proje adı\>;**<br />**[; Platform =\<varsayılan olarak "Any CPU" >]**<br />**[; Flavor =\<varsayılan olarak "Debug" >]**<br />**[; RunTitle = < başlık\>]**|
|**/ListTests: [*dosya adı*]**|Verilen test kapsayıcısından bulunan testleri listeler.|
|**/ListDiscoverers**|Yüklü test discoverers listeler.|
|**/ListExecutors**|Yüklü test yürüticileri listeler.|
|**/Listlogger**|Yüklü test Günlükçüleri listeler.|
|**/ListSettingsProviders**|Yüklü test ayarları sağlayıcılarını listeler.|
|**/Blame**|Testleri yürütülmekte olduğu gibi izler ve test ana bilgisayar işlemi kilitlenirse, yürütme sırasında çalışmakta olan belirli bir test dahil olmak üzere, testlerin adlarını yürütme sırasıyla yayar. Bu çıktı, sorunlu testi yalıtmak ve daha fazla tanılama yapmayı kolaylaştırır. [Daha fazla bilgi](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag: [*dosya adı*]**|Tanılama izleme günlüklerini belirtilen dosyaya yazar.|
|**/ResultsDirectory: [*yol*]**|Mevcut değilse, belirtilen yolda test sonuçları dizini oluşturulur.<br />Örnek: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId: [*ParentProcessId*]**|Geçerli işlemi başlatmaktan sorumlu üst Işlemin işlem KIMLIĞI.|
|**/Port: [*bağlantı noktası*]**|Yuva bağlantısı için bağlantı noktası ve olay iletilerini alma.|
|**/Collect: [*DataCollector FriendlyName*]**|Test çalıştırması için veri toplayıcıyı etkinleştirilir. [Daha fazla bilgi](https://aka.ms/vstest-collect).|

> [!TIP]
> Seçenekler ve değerler büyük/küçük harfe duyarlı değildir.

## <a name="examples"></a>Örnekler

*VSTest. Console. exe* ' yi çalıştırmak için sözdizimi şöyledir:

`Vstest.console.exe [TestFileNames] [Options]`

Aşağıdaki komut, **MyTestProject. dll**test Kitaplığı Için *VSTest. Console. exe* ' yi çalıştırır:

```cmd
vstest.console.exe myTestProject.dll
```

Aşağıdaki komut, *VSTest. Console. exe* ' yi birden çok test dosyası ile çalıştırır. Test dosyası adlarını boşluklarla ayır:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Aşağıdaki komut *VSTest. Console. exe* ' yi çeşitli seçeneklerle çalıştırır. Bir yalıtılmış işlemdeki *myTestFile. dll* dosyasındaki testleri çalıştırır ve *Local. runsettings* dosyasında belirtilen ayarları kullanır. Ayrıca, yalnızca "Priority = 1" olarak işaretlenmiş testleri çalıştırır ve sonuçları bir *. trx* dosyasına kaydeder.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
