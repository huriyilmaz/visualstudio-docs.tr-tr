---
title: MSBuild Komut Satırı Başvurusu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb95da599e6362ad32c0ef94dcf9c184269ddedf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633414"
---
# <a name="msbuild-command-line-reference"></a>MSBuild komut satırı başvurusu

Bir proje veya çözüm dosyası oluşturmak için *MSBuild.exe'yi* kullandığınızda, işlemin çeşitli yönlerini belirtmek için birkaç anahtar ekleyebilirsiniz.

Her anahtar iki şekilde mevcuttur: -switch ve /switch. Belgeler yalnızca -switch formunu gösterir. Anahtarlar büyük/küçük harf duyarlı değildir. MSBuild'i Windows komut istemi dışındaki bir kabuktan çalıştırıyorsanız, bir anahtara geçiş bağımsız değişken listeleri (yarı iki nokta veya virgülle ayrılmış) listelerin kabuk tarafından yorumlandırılmak yerine MSBuild'e geçirilmesini sağlamak için tek veya çift tırnak işaretleri gerekebilir.

## <a name="syntax"></a>Sözdizimi

```cmd
MSBuild.exe [Switches] [ProjectFile]
```

## <a name="arguments"></a>Bağımsız Değişkenler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`ProjectFile`|Belirttiğiniz proje dosyasındaki hedefleri oluşturur. Bir proje dosyası belirtmezseniz, MSBuild *proj* ile biten ve bu dosyayı kullanan bir dosya adı uzantısı için geçerli çalışma dizinini arar. Ayrıca bu bağımsız değişken için bir Visual Studio çözüm dosyası belirtebilirsiniz.|

## <a name="switches"></a>Anahtarlar

|Anahtar|Kısa biçim|Açıklama|
|------------|----------------|-----------------|
|-ayrıntılıÖzet|-ds|Yapı günlüğünün sonunda, yapılan yapılandırmalar ve düğümlere nasıl zamanlandıkları hakkında ayrıntılı bilgileri gösterin.|
|-graphBuild[:`True` `False`veya ]|-grafik[:`True` `False`veya ]|MSBuild'in bir proje grafiği oluşturmasına ve oluşturmasına neden olur. Grafik oluşturmak, form bağımlılıkları için proje başvurularını tanımlamayı içerir. Bu grafiği oluşturma, geleneksel MSBuild zamanlamasından farklı olarak, bunlara başvuran projelerden önce proje başvuruları oluşturmaya çalışmayı içerir.|
|-yardım|/? veya -h|Kullanım bilgilerini görüntüleyin. Aşağıdaki komut bir örnektir:<br /><br /> `msbuild.exe -?`|
|-yoksProjectExtensions:`extensions`|-yok sayma:`extensions`|Hangi proje dosyasının oluşturulacaşmasını belirlerken belirtilen uzantıları yoksayın. Aşağıdaki örnekte görüldüğü gibi, birden çok uzantıyı ayırmak için bir yarı sütun veya virgül kullanın:<br /><br /> `-ignoreprojectextensions:.vcproj,.sln`|
|`True` -etkileşimli[: `False`veya ]|-|Yapıdaki eylemlerin kullanıcıyla etkileşime girmesine izin verildiğini gösterir.  Bu bağımsız değişkeni etkileşimin beklenmediğini otomatik bir senaryoda kullanmayın. -etkileşimli belirtme ,-etkileşimli:true'yu belirtmekle aynıdır.  Yanıt dosyasından gelen bir değeri geçersiz kılmak için parametreyi kullanın.
|-izoleProjeler[:`True` `False`veya ]|-izole[:`True` `False`veya ]|MSBuild'in her projeyi izole olarak oluşturmasına neden olur. Bu, proje grafiğinin değerlendirme sırasında statik olarak keşfedilebilir olmasını gerektirdiğinden, MSBuild'in daha kısıtlayıcı bir modudur, ancak büyük bir proje kümesi oluştururken zamanlamayı artırabilir ve bellek yükü azaltabilir.|
|-maxCpuCount[:`number`]|-m[:`number`]|Oluştururken kullanılacak en fazla eşzamanlı işlem sayısını belirtir. Bu anahtarı eklemezseniz, varsayılan değer 1'dir. Bu anahtarı bir değer belirtmeden eklerseniz, MSBuild bilgisayardaki işlemci sayısına kadar kullanır. Daha fazla bilgi için [bkz.](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)<br /><br /> Aşağıdaki örnek, MSBuild'e üç projenin aynı anda oluşturulmasına olanak tanıyan üç MSBuild işlemi kullanarak oluşturması talimatını verir:<br /><br /> `msbuild myproject.proj -maxcpucount:3`|
|-noAutoResponse|-noautorsp|*MsBuild.rsp* dosyalarını otomatik olarak eklemeyin.|
|-düğümReuse:`value`|-nr:`value`|MSBuild düğümlerinin yeniden kullanımını etkinleştirin veya devre dışı edin. Aşağıdaki değerleri belirtebilirsiniz:<br /><br /> -   **Doğru.** Sonraki yapılar (varsayılan) bunları kullanabilirsiniz böylece düğümleri yapı bittikten sonra kalır.<br />-   **Yanlış**. Düğümler yapı tamamlandıktan sonra kalmaz.<br /><br /> Düğüm, yürütülen bir projeye karşılık gelir. **-maxcpucount** anahtarını eklerseniz, birden çok düğüm aynı anda çalıştırılabilir.|
|-nologo||Başlangıç bayrağını veya telif hakkı iletisini görüntülemeyin.|
|<a name="preprocess"></a>-ön işlem[:`filepath`]|-pp[:`filepath`]|Bir yapı sırasında içe aktarılacak tüm dosyaları, sınırları işaretlenmiş olarak hizalayarak tek bir toplu proje dosyası oluşturun. Hangi dosyaların içe aktarıldığını, dosyaların nereden alındığını ve hangi dosyaların yapıya katkıda bulunacağını daha kolay belirlemek için bu anahtarı kullanabilirsiniz. Bu anahtarı kullandığınızda, proje oluşturulmaz.<br /><br /> Bir `filepath`, toplanan proje dosyası dosyaya çıktı belirtirseniz. Aksi takdirde, çıkış konsol penceresinde görünür.<br /><br /> Proje dosyasını başka `Import` bir proje dosyasına eklemek için öğenin nasıl kullanılacağı hakkında bilgi için alma [öğesi (MSBuild)](../msbuild/import-element-msbuild.md) ve [Nasıl Yapılır'a bakın: Aynı hedefi birden çok proje dosyasında kullanın.](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)|
|-outputResultsCache[:cacheFile]|-orc[:cacheFile]|MSBuild'in yapı nın sonundaki yapı sonucunun içeriğini yazacağı çıktı önbelleği dosyası. Bu ayar da yalıtılmış yapılar (-yalıtma) açar.|
|-profileEvaluation:`<file>`|-|Profilleri MSBuild değerlendirme ve belirtilen dosyaya sonucu yazar. Belirtilen dosyanın uzantısı '.md' ise, sonuç Markdown biçiminde oluşturulur. Aksi takdirde, sekme ayrılmış bir dosya üretilir.|
|-özellik:`name`=`value`|-p:`name`=`value`|Özellik adı ve özellik değeri olan `name` belirtilen proje düzeyi `value` özelliklerini ayarlayın veya geçersiz kılın. Her özelliği ayrı ayrı belirtin veya aşağıdaki örnekte görüldüğü gibi birden çok özelliği ayırmak için bir yarı nokta veya virgül kullanın:<br /><br /> `-property:WarningLevel=2;OutDir=bin\Debug`|
|-geri yükleme|-r|Gerçek `Restore` hedefleri oluşturmadan önce hedefi çalıştırın.|
|-restoreÖzellik:`name=value`|-rp:`name=value`|Bu proje düzeyi özelliklerini yalnızca geri yükleme sırasında ayarlayın veya geçersiz kılın ve -özellik bağımsız değişkeni ile belirtilen özellikleri kullanmayın. `name`özellik adıdır ve `value` özellik değeridir. Birden çok özelliği ayırmak veya her özelliği ayrı ayrı belirtmek için bir yarı sütun veya virgül kullanın.|
|-hedef:`targets`|-t:`targets`|Projede belirtilen hedefleri oluşturun. Her hedefi ayrı ayrı belirtin veya aşağıdaki örnekte görüldüğü gibi birden çok hedefi ayırmak için bir yarı nokta veya virgül kullanın:<br /><br /> `-target:PrepareResources;Compile`<br /><br /> Bu anahtarı kullanarak herhangi bir hedef belirtirseniz, proje dosyasındaki öznitelikteki `DefaultTargets` hedefler yerine çalıştırılırlar. Daha fazla bilgi için bkz: [Hedef oluşturma sırası](../msbuild/target-build-order.md) ve [Nasıl: Önce hangi hedefin oluşturulabildiğini belirtin.](../msbuild/how-to-specify-which-target-to-build-first.md)<br /><br /> Hedef, bir görev grubudur. Daha fazla bilgi için [Bkz. Hedefler.](../msbuild/msbuild-targets.md)|
|-toolsVersion:`version`|-tv:`version`|Aşağıdaki örnekte görüldüğü gibi, projeyi oluşturmak için kullanılacak Araç Kümesi sürümünü belirtir:`-toolsversion:3.5`<br /><br /> Bu anahtarı kullanarak, bir proje oluşturabilir ve [Proje öğesinde (MSBuild)](../msbuild/project-element-msbuild.md)belirtilen sürümden farklı bir sürüm belirtebilirsiniz. Daha fazla bilgi için, [Geçersiz Kılma AraçlarıSürüm ayarlarına](../msbuild/overriding-toolsversion-settings.md)bakın.<br /><br /> MSBuild 4.5 için `version`aşağıdaki değerleri belirtebilirsiniz: 2.0, 3.5 ve 4.0. 4.0 belirtirseniz, `VisualStudioVersion` yapı özelliği hangi alt araç kümesinin kullanılacağını belirtir. Daha fazla bilgi [için, Araç Kümesi 'nin (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)alt araç kümeleri bölümüne bakın.<br /><br /> Araç Kümesi, bir uygulama oluşturmak için kullanılan görevlerden, hedeflerden ve araçlardan oluşur. Araçlar *csc.exe* ve *vbc.exe*gibi derleyiciler içerir. Araç Kümeleri hakkında daha fazla bilgi [için, Bkz. Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [Standart ve özel araç seti yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)ve [Multitargeting](../msbuild/msbuild-multitargeting-overview.md). **Not:**  Araç kümesi sürümü, bir projenin çalıştırmak üzere inşa edildiği .NET Framework'ün sürümü olan hedef çerçeveyle aynı değildir. Daha fazla bilgi için [Hedef çerçevesi ve hedef platformuna](../msbuild/msbuild-target-framework-and-target-platform.md)bakın.|
|-doğrula:[ ]`schema`|-val[`schema`]|Proje dosyasını doğrulayın ve doğrulama başarılı olursa projeyi oluşturun.<br /><br /> Belirtmezseniz, `schema`proje varsayılan şema karşı doğrulanır.<br /><br /> Belirtirseniz, `schema`proje belirttiğiniz şema karşı doğrulanır.<br /><br /> Aşağıdaki ayar bir örnektir:`-validate:MyExtendedBuildSchema.xsd`|
|-ayrıntılılık:`level`|-v:`level`|Yapı günlüğünde görüntülenecek bilgi miktarını belirtir. Her kaydedici, o kaydedici için ayarladığınız ayrıntılılık düzeyine göre olayları görüntüler.<br /><br /> Aşağıdaki ayrıntılı düzeyleri belirtebilirsiniz: `q[uiet]`, `m[inimal]` `n[ormal]` , `d[etailed]`(varsayılan), `diag[nostic]`ve .<br /><br /> Aşağıdaki ayar bir örnektir:`-verbosity:quiet`
|-sürüm|-ver|Yalnızca sürüm bilgilerini görüntüleyin. Proje oluşturulmamadı.|
|@`file`||Metin dosyasından komut satırı anahtarları ekleyin. Birden çok dosyanız varsa, bunları ayrı ayrı belirtirsiniz. Daha fazla bilgi için [Yanıt dosyalarına](../msbuild/msbuild-response-files.md)bakın.|
|-warnAsError[:`code``;code2`[ ]|-err[`:code``;code2`[ ]|Hata olarak davranır uyarı kodları listesi.  Birden çok uyarı kodunu ayırmak için bir yarı kolon veya virgül kullanın. Tüm uyarıları hata olarak ele almak için, anahtarı hiçbir değer olmadan kullanın. Bir uyarı hata olarak kabul edildiğinde, hedef bir uyarı yatılıyormuş gibi yürütmeye devam eder, ancak genel yapı başarısız olur.<br/><br/>Örnek: `-err:MSB4130`|
|-warnAsMessage[:`code``;code2`[ ]|-noWarn[:`code``;code2`[ ]|Düşük öneme sahip iletiler olarak davranır için uyarı kodları listesi.  Birden çok uyarı kodunu ayırmak için bir yarı kolon veya virgül kullanın.<br/><br/>Örnek: `-noWarn:MSB3026`|

### <a name="switches-for-loggers"></a>Loggers için anahtarlar

|Anahtar|Kısa biçim|Açıklama|
|------------|----------------|-----------------|
|-binaryLogger[:[LogFile=]`output.binlog`<br/>[; ProjectImports=[Yok,Gömmek,ZipFile]]]|-bl|Tüm yapı olaylarını sıkıştırılmış ikili bir dosyaya serileştirir. Varsayılan olarak dosya geçerli dizinde ve *msbuild.binlog*adlı. İkili günlük, daha sonra metin günlüklerini yeniden oluşturmak için kullanılabilecek ve diğer çözümleme araçları tarafından kullanılabilecek yapı işleminin ayrıntılı bir açıklamasıdır. İkili günlük genellikle en ayrıntılı metin tanı düzeyi günlüğünden 10-20kat daha küçüktür, ancak daha fazla bilgi içerir.<br /><br />Varsayılan olarak ikili kaydedici, yapı sırasında karşılaşılan tüm içe aktarılan projeler ve hedef dosyalar da dahil olmak üzere proje dosyalarının kaynak metnini toplar. İsteğe `ProjectImports` bağlı anahtar bu davranışı denetler:<br /><br /> -   **ProjectImports=Yok**. Proje ithalatını toplama.<br /> -   **ProjectImports=Embed**. Günlük dosyasına proje içeri aktarımlarını göm (varsayılan).<br /> -   **ProjectImports=ZipFile**. Proje dosyalarını * \<çıktı>.projectimports.zip* çıktısı \<> ikili günlük dosya adı ile aynı adı taşıyan çıktıya kaydedin.<br /><br />ProjectImports için varsayılan ayar Embed'dir.<br />**Not**: logger *.cs*, *.cpp* vb gibi MSBuild olmayan kaynak dosyaları toplamaz<br />*Bir .binlog* dosyası, proje/çözüm yerine bir bağımsız değişken olarak *msbuild.exe'ye* geçirilerek "oynatılabilir". Diğer kaydediciler, günlük dosyasında bulunan bilgileri orijinal yapı gerçekleşiyormuş gibi alır. İkili günlük ve kullanımları hakkında daha fazla bilgi edinebilirsiniz:https://github.com/Microsoft/msbuild/wiki/Binary-Log <br /><br />**Örnekler**:<br /> -   `-bl`<br /> -    `-bl:output.binlog`<br /> -   `-bl:output.binlog;ProjectImports=None`<br /> -   `-bl:output.binlog;ProjectImports=ZipFile`<br /> -   `-bl:..\..\custom.binlog`<br /> -   `-binaryLogger`|
|-consoleLoggerParametreleri:<br /><br /> `parameters`|-clp:`parameters`|Belirttiğiniz parametreleri konsol penceresinde yapı bilgilerini görüntüleyen konsol kaydedicisine iletin. Aşağıdaki parametreleri belirtebilirsiniz:<br /><br /> -   **PerformansÖzeti**. Görevlerde, hedeflerde ve projelerde harcanan zamanı gösterin.<br />-   **Özet**. Sonunda hata ve uyarı özetini göster.<br />-   **NoSummary**. Sonunda hata ve uyarı özetini göstermeyin.<br />-   **HatalarSadece**. Yalnızca hataları göster.<br />-   **UyarılarSadece**. Yalnızca uyarıları gösterin.<br />-   **NoitemandPropertylist**. Ayrıntılı lık düzeyi ayarlanmışsa, her proje yapısının başında görünecek öğelerin ve özelliklerin `diagnostic`listesini göstermeyin.<br />-   **ShowCommandLine**. İletileri göster. `TaskCommandLineEvent`<br />-   **ShowTimestamp**. Zaman damgasını herhangi bir iletinin öneki olarak gösterin.<br />-   **ShowEventid**. Başlatılan her olay, tamamlanan olay ve ileti için etkinlik kimliğini gösterin.<br />-   **ForceNoAlign**. Metni konsol arabelleği boyutuna hizalamayın.<br />-   **Devre Dışı KonsolColor**. Tüm günlük iletileri için varsayılan konsol renklerini kullanın.<br />-   **Devre Dışı** Çok işlemcili olmayan modda çalışırken çıktının çok işlemcili günlük stilini devre dışı edin.<br />-   **EtkinleştirmeMPLogging**. Çok işlemcili olmayan modda çalışırken bile çok işlemcili günlük stilini etkinleştirin. Bu günlük stili varsayılan olarak açıktır.<br />-   **Ayrıntılı lık.** Bu kaydedici için **-ayrıntılı ayar** geçersiz kılın.<br /><br /> Aşağıdaki örnekte görüldüğü gibi, birden çok parametreyi ayırmak için bir yarı nokta kullanın:<br /><br /> `-consoleloggerparameters:PerformanceSummary;NoSummary -verbosity:minimal`<br/><br/> Varsayılan konsol kaydedici si normal bir renktedir ve bir `Summary`.|
|-distributedFileLogger|-dfl|Her MSBuild düğümünün yapı çıktısını kendi dosyasına kaydedin. Bu dosyaların ilk konumu geçerli dizinidir. Varsayılan olarak, dosyaları *MSBuild\<Düğüm iddaa>.log*olarak adlandırılır. FileLoggerParametreler için dosyaların konumunu ve fileLogger için diğer parametreleri belirtmek için **-fileLoggerParametreler** anahtarını kullanabilirsiniz.<br /><br /> **-fileLoggerParametreler** anahtarını kullanarak bir günlük dosyası adsanız, dağıtılmış kaydedici şablon olarak bu adı kullanır ve her düğüm için bir günlük dosyası oluştururken düğüm kimliğini bu ada ekler.|
|-distributedLogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|-dl:`central logger`*`forwarding logger`|MsBuild'teki olayları günlüğe kaydederek her düğüme farklı bir logger örneği iliştirin. Birden çok günlüğe kaydedin, her logger'ı ayrı ayrı belirtin.<br /><br /> Logger sözdizimini bir logger belirtmek için kullanırsınız. Logger sözdizimi için aşağıdaki **-logger** anahtarına bakın.<br /><br /> Aşağıdaki örnekler, bu anahtarın nasıl kullanılacağını gösterir:<br /><br /> `-dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|
|-fileLogger<br /><br /> *[sayı]*|-fl[`number`]|Yapı çıktısını geçerli dizindeki tek bir dosyaya günlüğe kaydedin. Belirtmezseniz, `number`çıktı dosyasının adı *msbuild.log.* Belirtirseniz, `number`çıktı dosyası *msbuild\<n>.log* \<, n `number`> . `Number`1'den 9'a kadar bir basamak olabilir.<br /><br /> Dosyanın konumunu ve fileLogger için diğer parametreleri belirtmek için **-fileLoggerParametreler** anahtarını kullanabilirsiniz.|
|-fileLoggerParametreler:[sayı]<br /><br /> `parameters`|-flp:[ `number`]`parameters`|Dosya kaydedicisi ve dağıtılmış dosya kaydedicisi için herhangi bir ek parametre belirtir. Bu anahtarın varlığı, ilgili -**filelogger[**`number`**]** anahtarının mevcut olduğu anlamına gelir. `Number`1'den 9'a kadar bir basamak olabilir.<br /><br /> **-consoleloggerparametreleri**için listelenen tüm parametreleri kullanabilirsiniz. Aşağıdaki parametrelerden birini veya birkaçını da kullanabilirsiniz:<br /><br /> -   **LogFile**. Yapı günlüğünün yazıldığı günlük dosyasına giden yol. Dağıtılmış dosya kaydedici, bu yolu günlük dosyalarının adlarına önekleri.<br />-   **Ek.** Yapı günlüğünün günlük dosyasına eklenip eklenmediğini veya üzerine yazıp yazmadığını belirler. Anahtarı ayarladığınızda, yapı günlüğü günlük dosyasına eklenir. Anahtar olmadığında, varolan bir günlük dosyasının içeriği üzerine yazılır.<br />     Ek anahtarıeklerseniz, doğru veya yanlış olarak ayarlanmış olsun, günlük eklenir. Ek anahtarını eklemezseniz, günlük üzerine yazılır.<br />     Bu durumda dosya üzerine yazılır:`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log`<br />     Bu durumda dosya eklenir:`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=true`<br />     Bu durumda dosya eklenir:`msbuild myfile.proj -l:FileLogger,Microsoft.Build;logfile=MyLog.log;append=false`<br />-   **Kodlama**. Dosyanın kodlamasını belirtir (örneğin, UTF-8, Unicode veya ASCII).<br /><br /> Aşağıdaki örnek, uyarılar ve hatalar için ayrı günlük dosyaları oluşturur:<br /><br /> `-flp1:logfile=errors.txt;errorsonly -flp2:logfile=warnings.txt;warningsonly`<br /><br /> Aşağıdaki örnekler diğer olasılıkları gösterir:<br /><br /> `-fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `-flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `-flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `-flp2:errorsonly;logfile=msbuild.err`|
|-logger:<br /><br /> `logger`|-l:`logger`|MSBuild'teki olayları günlüğe kaydetmek için kullanılacak logger'ı belirtir. Birden çok günlüğe kaydedin, her logger'ı ayrı ayrı belirtin.<br /><br /> Aşağıdaki sözdizimini `logger`kullanın:`[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Aşağıdaki sözdizimini `LoggerClass`kullanın:`[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Derleme tam olarak bir logger içeriyorsa logger sınıfını belirtmeniz gerekmez.<br /><br /> Aşağıdaki sözdizimini `LoggerAssembly`kullanın: `{``AssemblyName``[,``StrongName``] &#124;``AssemblyFile``}`<br /><br /> Logger parametreleri isteğe bağlıdır ve tam olarak girdiğinizde kaydediciye aktarılır.<br /><br /> Aşağıdaki **örneklerde -logger** anahtarı kullanılır.<br /><br /> `-logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|
|-noConsoleLogger|-noconlog|Varsayılan konsol kaydedicisini devre dışı bırakıp olayları konsola günlüğe kaydetmeyin.|

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `rebuild` *MyProject.proj* projesinin hedefini oluşturur.

```cmd
MSBuild.exe MyProject.proj -t:rebuild
```

## <a name="example"></a>Örnek

 Daha karmaşık yapılar gerçekleştirmek için *MSBuild.exe'yi* kullanabilirsiniz. Örneğin, bir çözümde belirli projelerin belirli hedeflerini oluşturmak için kullanabilirsiniz. Aşağıdaki örnek, projeyi `NotInSolutionFolder` yeniden yeniden `InSolutionFolder`yapılandırılır ve *NewFolder* çözüm klasöründe bulunan projeyi temizler.

```cmd
msbuild SlnFolders.sln -t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Ortak MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
