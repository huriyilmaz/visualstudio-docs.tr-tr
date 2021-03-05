---
title: VSTest.Console.exe komut satırı seçenekleri
description: Testleri çalıştıran VSTest.Console.exe komut satırı aracı hakkında bilgi edinin. Bu makalede genel komut satırı seçenekleri bulunur.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86544ad36874ec2a99fac0f8505b24548e83c7c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168367"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe komut satırı seçenekleri

*VSTest.Console.exe* , testleri çalıştırmak için komut satırı aracıdır. Komut satırında herhangi bir sırada birkaç seçenek belirtebilirsiniz. Bu seçenekler [genel komut satırı seçeneklerinde](#general-command-line-options)listelenmiştir.

> [!NOTE]
> Visual Studio 'daki MSTest bağdaştırıcısı, uyumluluk için eski modda da ( *mstest.exe* ile testleri çalıştırmaya eşdeğerdir) çalışır. Eski modda, TestCaseFilter özelliğinden faydalanabilirsiniz. Bir *testsettings* dosyası belirtildiğinde, bağdaştırıcı eski moda geçebilir, **forcelegacymode** bir *runsettings* dosyasında **true** olarak ayarlanır veya **HostType** gibi öznitelikler kullanılarak.
>
> ARM mimarisi tabanlı bir makinede otomatikleştirilmiş testler çalıştırmak için *VSTest.Console.exe* kullanmanız gerekir.

Komut satırı aracını kullanmak için [Geliştirici komut istemi](../ide/reference/command-prompt-powershell.md) açın veya aracı *% Program Files (x86)% \ Microsoft Visual Studio \\<sürüm \> \\<Edition \> \common7\ide\CommonExtensions \\<platformunda bulabilirsiniz | Microsoft>*.

## <a name="general-command-line-options"></a>Genel komut satırı seçenekleri

Aşağıdaki tabloda *VSTest.Console.exe* ve bunların kısa açıklamaları için tüm seçenekler listelenmektedir. Benzer bir özeti, komut satırına yazarak görebilirsiniz `VSTest.Console/?` .

| Seçenek | Açıklama |
|---|---|
|**[*test dosyası adları*]**|Belirtilen dosyalardan testleri çalıştırın. Birden çok test dosyası adını boşluklarla ayırın.<br />Örnekler: `mytestproject.dll` , `mytestproject.dll myothertestproject.exe`|
|**/Settings: [*dosya adı*]**|Testleri veri toplayıcılar gibi ek ayarlarla çalıştırın. Daha fazla bilgi için bkz [.. runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)<br />Örnek: `/Settings:local.runsettings`|
|**/TESTS: [*Test adı*]**|Testleri, belirtilen değerleri içeren adlarla çalıştırın. Birden çok değer sağlamak için bunları virgülle ayırın.<br />Örnek: `/Tests:TestMethod1,testMethod2`<br />**/Tests** komut satırı seçeneği, **/TestCaseFilter** komut satırı seçeneğiyle birlikte kullanılamaz.|
|**/Parallel**|Testlerin paralel olarak yürütüleceğini belirtir. Varsayılan olarak, makinedeki tüm kullanılabilir çekirdekler kullanılabilir. Bir ayar dosyasında kullanılacak çekirdek sayısını yapılandırabilirsiniz.|
|**/Enablecodecoverage**|Test çalıştırmasında veri tanılama bağdaştırıcısı CodeCoverage öğesine izin vermez.<br />Ayarlar dosyası kullanılarak belirtilmemişse varsayılan ayarlar kullanılır.|
|**/Inısolation**|Testleri yalıtılmış bir işlemde çalıştırır.<br />Bu yalıtım, testlerin bir hata üzerinde *vstest.console.exe* işlemini daha düşük bir hale getirir, ancak testler daha yavaş çalışabilir.|
|**/UseVsixExtensions**|Bu seçenek, *vstest.console.exe* işleminin Test çalıştırmasında yüklü olan (varsa) VSIX uzantılarını kullanmasını veya atlamasını sağlar.<br />Bu seçenek kullanım dışıdır. Visual Studio 'nun bir sonraki ana sürümünden itibaren bu seçenek kaldırılabilir. NuGet paketi olarak kullanılabilir hale getirilen genişletme uzantılarına taşıyın.<br />Örnek: `/UseVsixExtensions:true`|
|**/TestAdapterPath: [*yol*]**|*vstest.console.exe* işlemini, Test çalıştırmasında belirtilen yoldan (varsa) özel test bağdaştırıcılarını kullanacak şekilde zorlar.<br />Örnek: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform: [*Platform türü*]**|, Geçerli çalışma zamanından belirlenen platform yerine, verilen platformu kullanmak üzere zorlar. Bu seçenek Windows üzerinde yalnızca x86 ve x64 platformları zorlayabilir. ARM seçeneği bozulur ve çoğu sistemde x64 ile sonuçlanır.<br />ARM64 gibi geçerli değerler listesinde olmayan çalışma zamanları üzerinde çalıştırmak için bu seçeneği belirtmeyin.<br />Geçerli değerler x86, x64 ve ARM 'dir.<br /> 
|**/Framework: [*Framework sürümü*]**|Test yürütmesi için kullanılacak hedef .NET sürümü.<br />Örnek değerler şunlardır,,, `Framework35` `Framework40` `Framework45` `FrameworkUap10` , `.NETCoreApp,Version=v1.1` .<br />TargetFrameworkAttribute, bu seçeneği derlemeinizden otomatik olarak algılamak için kullanılır ve özniteliği mevcut olmadığında varsayılan olarak öğesine ayarlanır `Framework40` . [TargetFrameworkAttribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) 'Yi .NET Core derlemelerinden kaldırırsanız bu seçeneği açıkça belirtmeniz gerekir.<br />Hedef çerçeve **Framework35** olarak belirtilmişse, testler CLR 4,0 "uyumluluk modunda" çalışır.<br />Örnek: `/Framework:framework40`|
|**/TestCaseFilter: [*ifade*]**|Verilen ifadeyle eşleşen testleri çalıştırın.<br /><Ifade \> <özellik \> =<değer \> [ \|<ifadesi \> ] biçimindedir.<br />Örnek: `/TestCaseFilter:"Priority=1"`<br />Örnek: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />**/TestCaseFilter** komut satırı seçeneği **/Tests** komut satırı seçeneğiyle birlikte kullanılamaz. <br />İfadeleri oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [TestCase filtresi](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Kullanım bilgilerini görüntüler.|
|**/Günlükçü: [*Uri/FriendlyName*]**|Test sonuçları için bir günlükçü belirtin. Birden çok günlüğü etkinleştirmek için parametreyi birden çok kez belirtin.<br />Örnek: sonuçları bir Visual Studio Test Sonuçları dosyasına (TRX) kaydetmek Için, şunu kullanın:<br />**/Günlükçü: TRX**<br />**[; LogFileName = \<Defaults to unique file name> ]**|
|**/ListTests: [*dosya adı*]**|Verilen test kapsayıcısından bulunan testleri listeler.|
|**/ListDiscoverers**|Yüklü test discoverers listeler.|
|**/ListExecutors**|Yüklü test yürüticileri listeler.|
|**/Listlogger**|Yüklü test Günlükçüleri listeler.|
|**/ListSettingsProviders**|Yüklü test ayarları sağlayıcılarını listeler.|
|**/Blame**|Testleri sorumluyu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesine neden olan sorunlu testleri yalıtmak için yararlıdır. Kilitlenme algılandığında, `TestResults/<Guid>/<Guid>_Sequence.xml` çökmeden önce çalıştırılan testlerin sırasını yakalayan bir sıra dosyası oluşturur. Daha fazla bilgi için bkz. [Blame veri toplayıcısı](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag: [*dosya adı*]**|Tanılama izleme günlüklerini belirtilen dosyaya yazar.|
|**/ResultsDirectory: [*yol*]**|Mevcut değilse, belirtilen yolda test sonuçları dizini oluşturulur.<br />Örnek: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId: [*ParentProcessId*]**|Geçerli işlemi başlatmaktan sorumlu üst Işlemin işlem KIMLIĞI.|
|**/Port: [*bağlantı noktası*]**|Yuva bağlantısı için bağlantı noktası ve olay iletilerini alma.|
|**/Collect: [*DataCollector FriendlyName*]**|Test çalıştırması için veri toplayıcıyı etkinleştirilir. [Daha fazla bilgi](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> Seçenekler ve değerler büyük/küçük harfe duyarlı değildir.

## <a name="examples"></a>Örnekler

*vstest.console.exe* çalıştırmak için sözdizimi şöyledir:

`vstest.console.exe [TestFileNames] [Options]`

Aşağıdaki komut, test Kitaplığı *myTestProject.dll* için *vstest.console.exe* çalıştırır:

```cmd
vstest.console.exe myTestProject.dll
```

Aşağıdaki komut birden çok test dosyası ile *vstest.console.exe* çalıştırır. Test dosyası adlarını boşluklarla ayır:

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Aşağıdaki komut birkaç seçenekten *vstest.console.exe* çalışır. *myTestFile.dll* dosyadaki testleri yalıtılmış bir işlemde çalıştırır ve *Local. runsettings* dosyasında belirtilen ayarları kullanır. Ayrıca, yalnızca "Priority = 1" olarak işaretlenmiş testleri çalıştırır ve sonuçları bir *. trx* dosyasına kaydeder.

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

Aşağıdaki komut,  `/blame` Test kitaplığı *myTestProject.dll* seçeneğiylevstest.console.exeçalışır:

```cmd
vstest.console.exe myTestFile.dll /blame
```

Bir test ana bilgisayarı kilitlentiyse, *sequence.xml* dosyası oluşturulur. Dosya yürütme sırasında yürütülen test sırasındaki testlerin tam adlarını içerir ve kilitlenme sırasında çalışan belirli bir testi dahil eder.

Test ana bilgisayar kilitlenmesi yoksa *sequence.xml* dosyası oluşturulmaz.

Oluşturulan bir *sequence.xml* dosyası örneği: 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
