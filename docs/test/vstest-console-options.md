---
title: VSTest.Console.exe komut satırı seçenekleri
description: Testleri çalıştıran VSTest.Console.exe komut satırı aracı hakkında bilgi edinebilirsiniz. Bu makale Genel komut satırı seçeneklerini içerir.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 9af275fe53925c2814c1c43a72ec4512d1e2c1b2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634198"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe komut satırı seçenekleri

*VSTest.Console.exe* çalıştıracak komut satırı aracıdır. Komut satırına istediğiniz sırada birkaç seçenek belirtebilirsiniz. Bu seçenekler Genel komut [satırı seçeneklerinde listelenir.](#general-command-line-options)

> [!NOTE]
> Visual Studio'daki MSTest bağdaştırıcısı, uyumluluk için eski modda da çalışır (mstest.exe *ile* test çalıştırmaya eşdeğerdir). Eski modda TestCaseFilter özelliği kullanılabilir. Bağdaştırıcı, bir *testsettings* dosyası belirtilirken, **forcelegacymode** bir *runsettings* dosyasında **true** olarak veya HostType gibi öznitelikler kullanılarak eski moda **geçilebilir.**
>
> ARM mimarisi tabanlı bir makinede otomatikleştirilmiş testler çalıştırmak için *VSTest.Console.exe.*

Komut [Geliştirici Komut İstemi](../ide/reference/command-prompt-powershell.md) aracını kullanmak için Geliştirici Komut İstemi'ı açın veya *aracı %Program Files(x86)%\Microsoft Visual Studio \\<version \> \\<edition \> \common7\ide\CommonExtensions \\<Platform | Microsoft>.*

## <a name="general-command-line-options"></a>Genel komut satırı seçenekleri

Aşağıdaki tabloda, tümVSTest.Console.exe *seçenekleri* ve bunların kısa açıklamaları listele. Komut satırına yazarak benzer `VSTest.Console/?` bir özete bakabilirsiniz.

| Seçenek | Açıklama |
|---|---|
|**[*test dosyası adları*]**|Belirtilen dosyalardan testleri çalıştırın. Birden çok test dosyası adını boşluklarla ayırma.<br />Örnekler: `mytestproject.dll` , `mytestproject.dll myothertestproject.exe`|
|**/Ayarlar:[ dosya *adı*]**|Testleri veri toplayıcıları gibi ek ayarlarla çalıştırın. Daha fazla bilgi için [bkz. .runsettings dosyası kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)<br />Örnek: `/Settings:local.runsettings`|
|**/Tests:[*test adı*]**|Sağlanan değerleri içeren adlarla testleri çalıştırın. Birden çok değer sağlamak için bunları virgülle ayırabilirsiniz.<br />Örnek: `/Tests:TestMethod1,testMethod2`<br />**/Tests** komut satırı seçeneği / **TestCaseFilter** komut satırı seçeneğiyle kullanılamaz.|
|**/Parallel**|Testlerin paralel olarak yürütül olacağını belirtir. Varsayılan olarak, makinede kullanılabilir olan tüm çekirdeklere kadar kullanılabilir. Bir ayarlar dosyasında kullanmak üzere çekirdek sayısını yapılandırabilirsiniz.|
|**/Enablecodecoverage**|Test çalıştırması içinde veri tanılama bağdaştırıcısı CodeCoverage'a olanak sağlar.<br />Varsayılan ayarlar, ayarlar dosyası kullanılarak belirtilmezse kullanılır.|
|**/InIsolation**|Testleri yalıtılmış bir işlemde çalıştırır.<br />Bu yalıtım, *vstest.console.exe* testlerde hata nedeniyle durdurulma ihtimalini daha azdır ancak testler daha yavaş çalışmasına neden olabilir.|
|**/UseVsixExtensions**|Bu seçenek, *vstest.console.exe* veya test çalıştırmasına yüklenmiş (varsa) VSIX uzantılarını atlar.<br />Bu seçenek kullanım dışıdır. Bir sonraki ana sürümden başlayarak Visual Studio seçeneği kaldırılabilir. Yeni bir paket olarak kullanılabilir hale NuGet.<br />Örnek: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*path*]**|Bu *vstest.console.exe* test çalıştırması içinde belirtilen bir yoldan (varsa) özel test bağdaştırıcıları kullanmaya güç sağlar.<br />Örnek: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*platform türü*]**|Geçerli çalışma zamanından belirlenen platform yerine, verilen platformu kullanılacak şekilde güçler. Bu seçenek yalnızca x86 ve x64 platformlarını Windows. ARM seçeneği bozuktur ve çoğu sistemde x64 ile sonuçlandırılır.<br />ARM64 gibi geçerli değerler listesinde yer almamış çalışma zamanlarında çalıştırmak için bu seçeneği BELIRTMEYİN.<br />Geçerli değerler: x86, x64 ve ARM.<br /> 
|**/Framework: [*framework version*]**|Test yürütmesi için kullanılacak hedef .NET sürümü.<br />Örnek değerler `Framework35` : , , , , `Framework40` `Framework45` `FrameworkUap10` `.NETCoreApp,Version=v1.1` .<br />TargetFrameworkAttribute, bu seçeneği derlemeden otomatik olarak algılamak için kullanılır ve özniteliği mevcut değilken varsayılan `Framework40` olarak ayarlanır. [TargetFrameworkAttribute'ı](/dotnet/api/system.runtime.versioning.targetframeworkattribute) .NET Core derlemelerinden kaldırırsanız bu seçeneği açıkça belirtmeniz gerekir.<br />Hedef çerçeve **Framework35** olarak belirtilirse, testler CLR 4.0 "uyumluluk modunda" çalışır.<br />Örnek: `/Framework:framework40`|
|**/TestCaseFilter:[*ifadesi*]**|Verilen ifadeyle eşan testler çalıştırın.<br /><ifadesi , <=<[ \> \><Expression ] \> \| \> biçimindedir.<br />Örnek: `/TestCaseFilter:"Priority=1"`<br />Örnek: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />**/TestCaseFilter** komut satırı seçeneği , /Tests komut satırı **seçeneğiyle** kullanılamaz. <br />İfade oluşturma ve kullanma hakkında bilgi için bkz. [TestCase filtresi.](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)|
|**/?**|Kullanım bilgilerini görüntüler.|
|**/Logger:[*uri/friendlyname*]**|Test sonuçları için bir günlükleyici belirtin. Birden çok günlükçiyi etkinleştirmek için parametresini birden çok kez belirtin.<br />Örnek: Sonuçları bir Visual Studio Test Sonuçları Dosyasında (TRX) günlüğe almak için kullanın<br />**/Logger:trx**<br />**[; LogFileName= \<Defaults to unique file name> ]**|
|**/ListTests:[*dosya adı*]**|Verilen test kapsayıcısı tarafından bulunan testleri listeler.|
|**/ListDiscoverers**|Yüklü test bulmalarını listeler.|
|**/ListExecutors**|Yüklü test yürütücülerini listeler.|
|**/ListLoggers**|Yüklü test günlüklerini listeler.|
|**/ListSettingsProviders**|Yüklü test ayarları sağlayıcılarını listeler.|
|**/Blame**|Testleri sorumlu modunda çalıştırır. Bu seçenek, test ana bilgisayarının kilitlenmesi neden olan sorunlu testleri yalıtmada yararlıdır. Bir kilitlenme algılandığında, içinde kilitlenmeden önce çalıştır edilen `TestResults/<Guid>/<Guid>_Sequence.xml` testlerin sırasını yakalayan bir dizi dosyası oluşturur. Daha fazla bilgi için bkz. [Blame data collector](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*dosya adı*]**|Tanılama izleme günlüklerini belirtilen dosyaya yazar.|
|**/ResultsDirectory:[*path*]**|Test sonuçları dizini yoksa belirtilen yolda oluşturulur.<br />Örnek: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|Geçerli işlemi başlatmakla sorumlu Üst Sürecin İşlem Kimliği.|
|**/Port:[*bağlantı noktası*]**|Yuva bağlantısı için bağlantı noktası ve olay iletilerini alma.|
|**/Collect:[*dataCollector friendlyName*]**|Test çalıştırması için veri toplayıcıyı sağlar. [Daha fazla bilgi.](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md)|

> [!TIP]
> Seçenekler ve değerler büyük/büyük/büyük harfe duyarlı değildir.

## <a name="examples"></a>Örnekler

Komut çalıştırma söz *dizimivstest.console.exe:*

`vstest.console.exe [TestFileNames] [Options]`

Aşağıdaki komut, *vstest.console.exe* kitaplığı için *aşağıdaki* myTestProject.dll:

```cmd
vstest.console.exe myTestProject.dll
```

Aşağıdaki komut, birden *vstest.console.exe* test dosyası içeren dosyaları çalıştırır. Test dosyası adlarını boşluklarla ayırma:

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Aşağıdaki komut, *vstest.console.exe* seçenekleriyle birlikte çalışır. Testleri yalıtılmış *bir işlemde* myTestFile.dlldosyasında çalıştırır ve *Local.RunSettings dosyasında belirtilen ayarları* kullanır. Ayrıca, yalnızca "Priority=1" olarak işaretlenmiş testleri çalıştırır ve sonuçları *bir .trx dosyasına kaydeder.*

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

Aşağıdaki komut, *vstest.console.exe* kitaplığı için `/blame` seçeneğiyle aşağıdaki ** myTestProject.dll:

```cmd
vstest.console.exe myTestFile.dll /blame
```

Bir test ana bilgisayarı kilitlenmesi *olduysa,sequence.xml* dosyası oluşturulur. Dosyası, kilitlenme sırasında çalıştırılıyor olan belirli bir test dahil olmak üzere yürütme dizisinde testlerin tam adlarını içerir.

Test ana bilgisayarı kilitlenmesi yoksa, *sequence.xml* dosyası oluşturulmaz.

Oluşturulan bir dosya *sequence.xml* örneği: 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
