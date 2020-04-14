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
ms.openlocfilehash: bfca799111c83f29924c997218c42f09bff5568a
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224465"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe komut satırı seçenekleri

*VSTest.Console.exe* testleri çalıştırmak için komut satırı aracıdır. Komut satırında herhangi bir sırada birkaç seçenek belirtebilirsiniz. Bu seçenekler [Genel komut satırı seçeneklerinde](#general-command-line-options)listelenir.

> [!NOTE]
> Visual Studio'daki MSTest bağdaştırıcısı da uyumluluk için eski modda *(mstest.exe*ile testler çalıştırmaya eşdeğer) çalışır. Eski modda, TestCaseFilter özelliğinden yararlanamaz. Bağdaştırıcı, *bir test ayarları* dosyası belirtildiğinde, **forcelegacymode** bir *runsettings* dosyasında **doğru** ayarlandığında veya **HostType**gibi öznitelikleri kullanarak eski moda geçiş yapabilir.
>
> ARM mimarisi tabanlı bir makinede otomatik testler çalıştırmak için *VSTest.Console.exe'yi*kullanmanız gerekir.

Komut satırı aracını kullanmak için geliştirici [komut istemini](/dotnet/framework/tools/developer-command-prompt-for-vs) açın veya aracı *%Program Dosyaları(x86)%\Microsoft Visual Studio\\<\> \\ sürümünde bulabilirsiniz<sürümü\>\common7\ide\CommonExtensions\\<Platformu | Microsoft>. *

## <a name="general-command-line-options"></a>Genel komut satırı seçenekleri

Aşağıdaki *tabloda VSTest.Console.exe* için tüm seçenekler ve bunların kısa açıklamaları listeleneb.) Bir komut satırında yazarak `VSTest.Console/?` benzer bir özet görebilirsiniz.

| Seçenek | Açıklama |
|---|---|
|**[*test dosyası adları*]**|Belirtilen dosyalardan testleri çalıştırın. Birden çok test dosya adını boşluklarla ayırın.<br />Örnekler: `mytestproject.dll`,`mytestproject.dll myothertestproject.exe`|
|**/Ayarlar:[*dosya adı*]**|Veri toplayıcıları gibi ek ayarlarla testler çalıştırın.<br />Örnek: `/Settings:Local.RunSettings`|
|**/Testler:[*test adı*]**|Sağlanan değerleri içeren adlarla testleri çalıştırın. Birden çok değer sağlamak için, bunları virgülle ayırın.<br />Örnek: `/Tests:TestMethod1,testMethod2`<br />**/Tests** komut satırı seçeneği **/TestCaseFilter** komut satırı seçeneği ile kullanılamaz.|
|**/Paralel**|Testlerin paralel olarak yürütülmesini belirtir. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. Ayarlar dosyasında kullanılacak çekirdek sayısını yapılandırabilirsiniz.|
|**/Enablecodecoverage**|Test çalışmasında veri tanılama bağdaştırıcısı CodeCoverage sağlar.<br />Ayarlar dosyası kullanılarak belirtilmemişse varsayılan ayarlar kullanılır.|
|**/Yalıtım**|Testleri yalıtılmış bir işlemle çalıştırın.<br />Bu *yalıtım, vstest.console.exe* işleminin testlerdeki bir hatada durdurulmasını daha az olası hale getirir, ancak testler daha yavaş çalışabilir.|
|**/UseVsixExtensions**|Bu seçenek, test çalışmasında yüklü vsix uzantılarını (varsa) *vstest.console.exe* işlemini kullanır veya atlar.<br />Bu seçenek amortismana hazırdır. Visual Studio'nun bir sonraki büyük sürümünden itibaren bu seçenek kaldırılabilir. NuGet paketi olarak sunulan tüketen uzantılara geçin.<br />Örnek: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*yol*]**|*vstest.console.exe* işlemini test çalışmasında belirli bir yoldan (varsa) özel test bağdaştırıcılarını kullanmaya zorlar.<br />Örnek: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*platform türü*]**|Test yürütmeiçin kullanılacak hedef platform mimarisi.<br />Geçerli değerler x86, x64 ve ARM'dir.|
|**/Framework: [*framework version*]**|Test yürütmeiçin kullanılacak hedef .NET sürümü.<br />Örnek değerler `Framework35` `Framework40`, `Framework45` `FrameworkUap10`, `.NETCoreApp,Version=v1.1`, , .<br />Hedef çerçeve **Framework35**olarak belirtilirse, testler CLR 4.0 "compatibly modunda" çalıştırılır.<br />Örnek: `/Framework:framework40`|
|**/TestCaseFilter:[*ifade*]**|Verilen ifadeyle eşleşen testler çalıştırın.<br /><\> İfadesi <\>özelliği =\>\|<\>değeri [<Expression ] biçimidir.<br />Örnek: `/TestCaseFilter:"Priority=1"`<br />Örnek: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />**/TestCaseFilter** komut satırı seçeneği **/Tests** komut satırı seçeneği ile kullanılamaz. <br />İfade oluşturma ve kullanma hakkında bilgi için [TestCase filtresine](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)bakın.|
|**/?**|Kullanım bilgilerini görüntüler.|
|**/Logger:[*uri/friendlyname*]**|Test sonuçları için bir logger belirtin.<br />Örnek: Sonuçları Visual Studio Test Sonuçları Dosyasına (TRX) kaydetmek için,<br />**/Logger:trx**<br />**[; LogFileName=\<Benzersiz dosya adı> varsayılandır]**|
|**/ListTests:[*dosya adı*]**|Listeler, verilen test kabından yapılan testleri buldu.|
|**/ListDiscoverers**|Yüklü test keşfederlerini listeler.|
|**/ListExecutors**|Yüklü test uygulayıcılarını listeler.|
|**/ListLoggers**|Yüklü test kaydedicilerini listeler.|
|**/ListSettingsSağlayıcıları**|Yüklü test ayarları sağlayıcılarını listeler.|
|**/Suçlama**|Testler yürütülderken izler ve test ana bilgisayarı işlemi çökerse, çökme sırasında çalışan belirli bir test de dahil olmak üzere, uygulama sıralarına kadar test adlarını yayır. Bu çıktı, rahatsız edici testi yalıtmayı ve daha fazla tanılamayı kolaylaştırır. [Daha fazla bilgi](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*dosya adı*]**|Belirtilen dosyaya tanılama izleme günlükleri yazar.|
|**/ResultsDirectory:[*yol*]**|Test sonuçları dizini yoksa belirtilen yolda oluşturulur.<br />Örnek: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|Geçerli işlemin başlatılmasından sorumlu Üst İşlemin İşlem Kimliği.|
|**/Port:[*bağlantı noktası*]**|Soket bağlantısı ve olay iletilerini almak için Bağlantı Noktası.|
|**/Collect:[*dataCollector friendlyName*]**|Test çalışması için veri toplayıcısını sağlar. [Daha fazla bilgi](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> Seçenekler ve değerler büyük/küçük harf duyarlı değildir.

## <a name="examples"></a>Örnekler

*VSTest.Console.exe* çalıştırmak için sözdizimi:

`Vstest.console.exe [TestFileNames] [Options]`

Aşağıdaki komut test kitaplığı **myTestProject.dll**için *VSTest.Console.exe* çalışır:

```cmd
vstest.console.exe myTestProject.dll
```

Aşağıdaki komut, birden çok test dosyasıyla *VSTest.Console.exe'yi* çalıştırUr. Boşluklarla ayrı test dosyası adları:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Aşağıdaki komut çeşitli seçeneklerle *VSTest.Console.exe* çalışır. Bu yalıtılmış bir işlemde *myTestFile.dll* dosyasında testleri çalışır ve *Local.RunSettings* dosyasında belirtilen ayarları kullanır. Ayrıca, yalnızca "Öncelik=1" işaretli testleri çalıştırır ve sonuçları *bir .trx* dosyasına kaydeder.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
