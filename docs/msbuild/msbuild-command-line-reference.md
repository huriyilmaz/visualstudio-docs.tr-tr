---
title: MSBuild Command-Line Başvuru | Microsoft Docs
description: Proje veya çözüm MSBuild.exe oluşturmak için komut satırı komut satırı kullanmayı ve kullanabileceğiniz birkaç anahtarı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0f1b874554b7fd8b6359d91209474bfd81a15ebe
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132994989"
---
# <a name="msbuild-command-line-reference"></a>MSBuild komut satırı başvurusu

Bir proje *MSBuild.exe* çözüm dosyası derlemek içinMSBuild.exe'i kullanırsanız, sürecin çeşitli yönlerini belirtmek için birkaç anahtar dahilebilirsiniz.

Her anahtar iki şekilde kullanılabilir: -switch ve /switch. Belgeler yalnızca -switch formunu gösterir. Anahtarlar büyük/büyük/büyük harfe duyarlı değildir. MSBuild komut isteminden farklı bir kabuktan Windows çalıştırmanız, listelerin kabuk tarafından yorumlanması yerine MSBuild'a geçirildiklerinden emin olmak için bir anahtara bağımsız değişken listeleri (noktalı virgül veya virgülle ayrılmış) gerektirebilirsiniz.

## <a name="syntax"></a>Söz dizimi

```cmd
MSBuild.exe [Switches] [ProjectFile]
```

## <a name="arguments"></a>Bağımsız değişkenler

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`ProjectFile`|Belirttiğiniz proje dosyasında hedefleri derleme. Bir proje dosyası belirtmezseniz, MSBuild *proj* ile sona eren ve bu dosyayı kullanan bir dosya adı uzantısı için geçerli çalışma dizininde arama yapabilirsiniz. Bu bağımsız değişken için Visual Studio bir çözüm dosyası da belirtebilirsiniz.|

## <a name="switches"></a>Anahtarlar

|Anahtar|Kısa biçim|Description|
|------------|----------------|-----------------|
|-detailedSummary|-ds|Derleme günlüğünün sonunda, yerleşik yapılandırmalar ve bunların düğümlere nasıl zamanlandığı hakkında ayrıntılı bilgiler gösterir.|
|-graphBuild[: `True` veya `False` ]|-graph[: `True` veya `False` ]|Proje MSBuild oluşturma ve oluşturma neden olur. Graf oluşturmak için bağımlılık oluşturmak için proje başvurularını tanımlamanız gerekir. Bu grafı oluşturmak için, geleneksel iş zamanlamalarından farklı olarak, onlara başvurulan projelerden önce proje başvuruları MSBuild gerekir. 16 MSBuild veya sonraki bir zaman gerektirir.|
|-help|/? veya -h|Kullanım bilgilerini görüntüleme. Aşağıdaki komut bir örnektir:<br /><br /> `msbuild.exe -?`|
|-ignoreProjectExtensions: `extensions`|-ignore: `extensions`|Hangi proje dosyasının derlemek üzere olduğunu belirlerken belirtilen uzantıları yoksayın. Aşağıdaki örnekte de olduğu gibi, birden çok uzantıyı ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `-ignoreprojectextensions:.vcproj,.sln`|
|-interactive[: `True` veya `False` ]|-|Derlemede yapılan eylemlerin kullanıcıyla etkileşim kurmasına izin ver olduğunu gösterir.  Bu bağımsız değişkeni etkileşimin beklenmiyor olduğu otomatik bir senaryoda kullanmayın. -interactive belirtmek, -interactive:true belirtmekle aynıdır.  Yanıt dosyasından gelen bir değeri geçersiz kılmak için parametresini kullanın.
|-isolateProjects[: `True` veya `False` ]|-isolate[: `True` veya `False` ]|Her MSBuild yalıtarak derlemeye neden olur. Proje grafiğinin değerlendirme zamanında statik olarak keşfedilebilir olması MSBuild, ancak büyük bir proje kümesi oluştururken zamanlamayı geliştirebilir ve bellek ek yükünü azaltabilir, bu daha kısıtlayıcı bir MSBuild modudur.|
|-maxCpuCount[: `number` ]|-m[: `number` ]|Bina sırasında en fazla eş zamanlı işlem sayısını belirtir. Bu anahtarı dahil etmezsanız varsayılan değer 1'tir. Bu anahtarı bir değer belirtmeden dahil ediyorsanız MSBuild işlemci sayısına kadar kullanırsınız. Daha fazla bilgi için, [bkz. Building multiple projects in parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Aşağıdaki örnek, MSBuild üç MSBuild kullanarak derlemesi için talimat verir ve bu da üç proje için aynı anda derlemeye olanak sağlar:<br /><br /> `msbuild myproject.proj -maxcpucount:3`|
|-noAutoResponse|-noautorsp|Otomatik olarak herhangi bir *MSBuild.rsp* dosyası dahil etme.|
|-nodeReuse:`value`|-nr:`value`|Düğümler için yeniden kullanımı etkinleştirin MSBuild devre dışı bırakma. Aşağıdaki değerleri belirtebilirsiniz:<br /><br /> -   **True .** Sonraki derlemelerin bunları kullanamı için derleme tamamdan sonra düğümler kalır (varsayılan).<br />-   **False .** Derleme tamamlandıktan sonra düğümler kalmaz.<br /><br /> Düğüm, yürütülen projeye karşılık gelen bir düğüm. **-maxcpucount anahtarını dahil ediyorsanız,** birden çok düğüm eşzamanlı olarak yürütülür.|
|-nologo||Başlangıç başlığı veya telif hakkı iletisi görüntülenmez.|
|<a name="preprocess"></a> -preprocess[: `filepath` ]|-pp[: `filepath` ]|Derleme sırasında içe aktarılmış olan ve sınırları işaretlenmiş olan tüm dosyaların geneli çizerek tek, toplu bir proje dosyası oluşturun. Hangi dosyaların içe aktarıldıklarını, dosyaların nereden içe aktarıldıklarını ve derlemeye katkıda bulunan dosyaları daha kolay belirlemek için bu anahtarı kullanabilirsiniz. Bu anahtarı kullanırken proje yerleşik olarak yer alamaz.<br /><br /> belirtirsiniz, `filepath` toplanan proje dosyası dosyaya çıktı verir. Aksi takdirde çıkış konsol penceresinde görüntülenir.<br /><br /> öğesini kullanarak başka bir proje dosyasına proje dosyası ekleme hakkında bilgi için bkz. Import `Import` [element (MSBuild)](../msbuild/import-element-msbuild.md) and [How to: Use](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)same target in multiple project files .|
|-outputResultsCache[:cacheFile]|-orc[:cacheFile]|Derlemenin derleme MSBuild önbelleklerinin içeriğini yazacak olduğu çıktı önbelleği dosyası. Bu ayar yalıtılmış derlemeleri de etkinleştirir (-yalıt).|
|-profileEvaluation:`<file>`|-|Profiller MSBuild değerlendirmeyi içerir ve sonucu belirtilen dosyaya yazar. Belirtilen dosyanın uzantısı '.md' ise sonuç Markdown biçiminde oluşturulur. Aksi takdirde, sekmeyle ayrılmış bir dosya üretir.|
|-property:`name`=`value`|-p:`name`=`value`|Belirtilen proje düzeyi özellikleri ayarlayın veya geçersiz kılın; burada `name` özellik adıdır ve `value` özellik değeridir. Aşağıdaki örnekte de olduğu gibi, her özelliği ayrı ayrı belirtin veya birden çok özelliği ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `-property:WarningLevel=2;OutDir=bin\Debug`|
|-restore|-r|Gerçek `Restore` hedeflerin yapıl öncesinde hedefi çalıştırır.|
|-restoreProperty:`name=value`|-rp:`name=value`|Bu proje düzeyi özellikleri yalnızca geri yükleme sırasında ayarlayın veya geçersiz kılın ve -property bağımsız değişkeniyle belirtilen özellikleri kullanmaz. `name` özellik adıdır ve `value` özellik değeridir. Birden çok özelliği ayırmak veya her özelliği ayrı belirtmek için noktalı virgül veya virgül kullanın.|
|-target:`targets`|-t:`targets`|Projede belirtilen hedefleri derleme. Her hedefi ayrı ayrı belirtin veya aşağıdaki örnekte de olduğu gibi, birden çok hedefi ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `-target:PrepareResources;Compile`<br /><br /> Bu anahtarı kullanarak herhangi bir hedef belirtirsiniz, bunlar proje dosyasındaki öznitelikte herhangi bir `DefaultTargets` hedef yerine çalıştırabilirsiniz. Daha fazla bilgi için [bkz. Hedef derleme sırası](../msbuild/target-build-order.md) [ve Nasıl 2.](../msbuild/how-to-specify-which-target-to-build-first.md)<br /><br /> Hedef, bir görev grubu olur. Daha fazla bilgi için [bkz. Hedefler.](../msbuild/msbuild-targets.md)|
|-targets[: `file` ]|-ts[: `file` ]|Kullanılabilir hedeflerin listesini, derleme işlemini yürütmeden belirtilen dosyaya (veya herhangi bir dosya belirtilmezse çıkış cihazına) yazın.|
|-toolsVersion:`version`|-tv:`version`|Aşağıdaki örnekte olduğu gibi projeyi derlemek için araç kümesi sürümünü belirtir: `-toolsversion:3.5`<br /><br /> Bu anahtarı kullanarak bir proje derlemek ve Project öğesinde belirtilen sürümden [(MSBuild) belirtebilirsiniz.](../msbuild/project-element-msbuild.md) Daha fazla bilgi için [bkz. ToolsVersion ayarlarını geçersiz kılma.](../msbuild/overriding-toolsversion-settings.md)<br /><br /> 4 MSBuild 4.5 için şu değerleri `version` belirtebilirsiniz: 2.0, 3.5 ve 4.0. 4.0 belirtirsiniz, `VisualStudioVersion` derleme özelliği hangi alt araç seti kullanmak için belirtir. Daha fazla bilgi için Araç Seti'nin [(ToolsVersion) Alt araç kümeleri bölümüne bakın.](../msbuild/msbuild-toolset-toolsversion.md)<br /><br /> Araç Seti, uygulama oluşturmak için kullanılan görevlerden, hedeflerden ve araçlardan oluşur. Araçlar,csc.exeve *vbc.exe.* ** Araç kümeleri hakkında daha fazla bilgi için bkz. [Araç Kümesi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [Standart ve özel araç kümesi yapılandırmaları](../msbuild/standard-and-custom-toolset-configurations.md)ve [Çoklu Hedef oluşturma.](../msbuild/msbuild-multitargeting-overview.md) **Not:**  Araç kümesi sürümü hedef çerçeveyle aynı değildir. Bu sürüm, projenin .NET Framework temel sürümüdür. Daha fazla bilgi için [bkz. Hedef çerçeve ve hedef platform.](../msbuild/msbuild-target-framework-and-target-platform.md)|
|-validate:[ `schema` ]|-val[ `schema` ]|Proje dosyasını doğrulama ve doğrulama başarılı olursa projeyi derleme.<br /><br /> belirtmezseniz, proje `schema` varsayılan şemaya göre doğrulanır.<br /><br /> `schema`belirtirsiniz, proje belirttiğiniz şemaya göre doğrulanır.<br /><br /> Aşağıdaki ayar bir örnektir: `-validate:MyExtendedBuildSchema.xsd`|
|-ayrıntılılık:`level`|-v:`level`|Derleme günlüğünde görüntülenmek için gereken bilgi miktarını belirtir. Her günlükç, bu günlükç için ayar level (ayrıntılılık) düzeyine göre olayları görüntüler.<br /><br /> Aşağıdaki ayrıntılılık düzeylerini belirtesiniz: `q[uiet]` , `m[inimal]` , `n[ormal]` (varsayılan), `d[etailed]` ve `diag[nostic]` .<br /><br /> Aşağıdaki ayar bir örnektir: `-verbosity:quiet`
|-version|-ver|Yalnızca sürüm bilgilerini görüntüleme. Proje henüz yerleşik değil.|
|@`file`||Metin dosyasından komut satırı anahtarları ekleme. Birden çok dosya varsa bunları ayrı ayrı belirtirsiniz. Daha fazla bilgi için bkz. [Yanıt dosyaları.](../msbuild/msbuild-response-files.md)|
|-warnAsError[: `code` [ `;code2` ]|-err[ `:code` [ `;code2` ]|Hata olarak davranan uyarı kodlarının listesi.  Birden çok uyarı kodu ayırmak için noktalı virgül veya virgül kullanın. Tüm uyarıları hata olarak kullanmak için anahtarını hiçbir değerle birlikte kullanın. Bir uyarı hata olarak kabul edilirse, hedef bir uyarı gibi yürütülmaya devam eder ancak genel derleme başarısız olur.<br/><br/>Örnek: `-err:MSB4130`|
|-warnAsMessage[: `code` [ `;code2` ]|-noWarn[: `code` [ `;code2` ]|Düşük öneme sahip iletiler olarak davranan uyarı kodlarının listesi.  Birden çok uyarı kodu ayırmak için noktalı virgül veya virgül kullanın.<br/><br/>Örnek: `-noWarn:MSB3026`|

### <a name="switches-for-loggers"></a>Günlükler için anahtarlar

|Anahtar|Kısa biçim|Description|
|------------|----------------|-----------------|
|-binaryLogger[:[LogFile=]`output.binlog`<br/>[; ProjectImports=[None,Embed,ZipFile]]]|-bl|Tüm derleme olaylarını sıkıştırılmış bir ikili dosyaya seri hale getirme. Dosya varsayılan olarak geçerli dizindedir ve *msbuild.binlog olarak adlandırılmıştır.* İkili günlük, daha sonra metin günlüklerini yeniden oluşturmak ve diğer analiz araçları tarafından kullanılan derleme işleminin ayrıntılı bir açıklamasıdır. İkili günlük genellikle en ayrıntılı metin tanılama düzeyi günlüğünden 10-20 kat daha küçüktür ancak daha fazla bilgi içerir.<br /><br />İkili günlükleyici varsayılan olarak, derleme sırasında karşılaşılan tüm içe aktarılan projeler ve hedef dosyalar da dahil olmak üzere proje dosyalarının kaynak metnini toplar. İsteğe bağlı `ProjectImports` anahtar bu davranışı kontrol eder:<br /><br /> -   **ProjectImports=None**. Proje içeri aktarmalarını toplamayın.<br /> -   **ProjectImports=Embed**. Proje içeri aktarmalarını günlük dosyasına ekleme (varsayılan).<br /> -   **ProjectImports=ZipFile**. Proje dosyalarını *\<output> .projectimports.zip* \<output> dosyasına kaydedin; burada ikili günlük dosyası adıyla aynı addır.<br /><br />ProjectImports için varsayılan ayar Ekle'dir.<br />**Not:** Günlükç *.cs*, *.cpp* gibi MSBuild olmayan kaynak dosyalarını toplamaz.<br />*Bir .binlog* dosyası proje/çözüm yerine bağımsız değişken *olarakmsbuild.exe* bir dosyaya aktararak "geri çalınır". Diğer günlük kayıtları, özgün derleme oluyor gibi günlük dosyasında yer alan bilgileri alır. İkili günlük ve kullanımları hakkında daha fazla bilgi için şu makaleyi okuyabilirsiniz: https://github.com/dotnet/msbuild/blob/main/documentation/wiki/Binary-Log.md <br /><br />**Örnekler:**<br /> -   `-bl`<br /> -    `-bl:output.binlog`<br /> -   `-bl:output.binlog;ProjectImports=None`<br /> -   `-bl:output.binlog;ProjectImports=ZipFile`<br /> -   `-bl:..\..\custom.binlog`<br /> -   `-binaryLogger`|
|-consoleLoggerParameters:<br /><br /> `parameters`|-clp:`parameters`|Belirttiğiniz parametreleri konsol penceresinde derleme bilgilerini görüntüleyen konsol günlükleyiciye iletir. Aşağıdaki parametreleri belirterek şunları yapabilirsiniz:<br /><br /> -   **PerformanceSummary**. Görevler, hedefler ve projelerde harcanan zamanı gösterir.<br />-   **Özet.** Hata ve uyarı özetini en sonunda gösterir.<br />-   **NoSummary**. Hata ve uyarı özetini en sonunda gösterme.<br />-   **ErrorsOnly**. Yalnızca hataları göster.<br />-   **Uyarılarİleri.** Yalnızca uyarıları göster.<br />-   **NoItemAndPropertyList**. Ayrıntılılık düzeyi olarak ayarlanırsa, her proje derlemesi başında görünecek öğelerin ve özelliklerin listesini `diagnostic` gösterme.<br />-   **ShowCommandLine**. İletileri `TaskCommandLineEvent` göster.<br />-   **ShowTimestamp**. Zaman damgasını herhangi bir iletinin ön eki olarak gösterir.<br />-   **ShowEventId**. Her bir başlatan olay, bitmiş olay ve ileti için olay kimliğini gösterir.<br />-   **ForceNoAlign**. Metni konsol arabelleğinin boyutuna hizalayın.<br />-   **DisableConsoleColor**. Tüm günlük mesajları için varsayılan Konsol renklerini kullanın.<br />-   **Disablemplogging**. Çok işlemcili modda çalışırken çıktının çok işlemcili günlük stilini devre dışı bırakın.<br />-   **Enablemplogging**. Çok işlemcili modda çalışırken bile çok işlemcili günlük stilini etkinleştirin. Bu günlük oluşturma stili varsayılan olarak açık olur.<br />-   **Ayrıntı düzeyi**. Bu günlükçü için **-ayrıntı** ayarını geçersiz kılın.<br /><br /> Aşağıdaki örnekte gösterildiği gibi, birden çok parametreyi ayırmak için noktalı virgül kullanın:<br /><br /> `-consoleloggerparameters:PerformanceSummary;NoSummary -verbosity:minimal`<br/><br/> Varsayılan konsol günlükçüsü normal ayrıntı düzeyine sahiptir ve bir içerir `Summary` .|
|-Distributedfilegünlükçü|-DFL|her bir MSBuild düğümünün derleme çıkışını kendi dosyasına kaydedin. Bu dosyaların başlangıç konumu geçerli dizindir. varsayılan olarak, dosyalar *MSBuild \<NodeId> . log* olarak adlandırılır. Filegünlükçü için dosyaların ve diğer parametrelerin konumunu belirtmek için **-FileLoggerParameters** anahtarını kullanabilirsiniz.<br /><br /> **-FileLoggerParameters** anahtarını kullanarak bir günlük dosyasına ad verirseniz, dağıtılmış günlükçü bu adı bir şablon olarak kullanır ve düğüm kimliğini her düğüm için bir günlük dosyası oluştururken bu ada ekler.|
|-Distributedgünlükçüsü:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|DL`central logger`*`forwarding logger`|her düğüme farklı bir günlükçü örneği ekleyerek MSBuild olayları günlüğe kaydedin. Birden çok günlüğe kaydetme belirtmek için, her Günlükçü ayrı ayrı belirtin.<br /><br /> Günlükçü belirtmek için günlükçü sözdizimini kullanın. Günlükçü sözdizimi için aşağıdaki **-günlükçü** anahtarına bakın.<br /><br /> Aşağıdaki örneklerde bu anahtarın nasıl kullanılacağı gösterilmektedir:<br /><br /> `-dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|
|-Filegünlükçü<br /><br /> *sayısından*|-fl [ `number` ]|Yapı çıkışını geçerli dizindeki tek bir dosyaya kaydedin. Belirtmezseniz `number` , çıkış dosyası *MSBuild. log* olarak adlandırılır. Öğesini belirtirseniz, `number` Çıkış dosyası *MSBuild \<n> . log* olarak adlandırılır; burada \<n> `number` . `Number` 1 ile 9 arasında bir sayı olabilir.<br /><br /> Dosya konumunu ve Filegünlükçü için diğer parametreleri belirtmek üzere **-FileLoggerParameters** anahtarını kullanabilirsiniz.|
|-fileLoggerParameters [sayı]:<br /><br /> `parameters`|-FLP [ `number` ]: `parameters`|Dosya günlükçüsü ve dağıtılmış dosya günlükçüsü için ek parametreleri belirtir. Bu anahtarın varlığı, karşılık gelen **filegünlükçü [** `number` **]** anahtarının mevcut olduğunu gösterir. `Number` 1 ile 9 arasında bir sayı olabilir.<br /><br /> **-Consoleloggerparameters** için listelenen tüm parametreleri kullanabilirsiniz. Aşağıdaki parametrelerden bir veya daha fazlasını da kullanabilirsiniz:<br /><br /> -   **Günlük dosyası**. Derleme günlüğünün yazıldığı günlük dosyasının yolu. Dağıtılmış dosya günlükçüsü bu yolu, günlük dosyalarının adlarına önek olarak ekler.<br />-   **Ekle**. Derleme günlüğünün günlük dosyasına eklenip eklenmeyeceğini belirler veya dosyanın üzerine yazar. Anahtarı ayarladığınızda, derleme günlüğü günlük dosyasına eklenir. Anahtar mevcut olmadığında, var olan bir günlük dosyasının içeriğinin üzerine yazılır.<br />     Örnek: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log;append`<br />     Açık `true` veya ayar eklerseniz, bu `false` ayar ne olursa olsun günlüğe eklenir. Append anahtarını eklemezseniz günlüğün üzerine yazılır.<br />     Bu durumda, dosyanın üzerine yazılır: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log`<br />     Bu durumda, dosyanın eklendiği yer: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log;append=true`<br />     Bu durumda, dosyanın eklendiği yer: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log;append=false`<br />-   **Kodlama**. Dosya için kodlamayı belirtir (örneğin, UTF-8, Unicode veya ASCII).<br /><br /> Aşağıdaki örnek, uyarılar ve hatalar için ayrı günlük dosyaları üretir:<br /><br /> `-flp1:logfile=errors.txt;errorsonly -flp2:logfile=warnings.txt;warningsonly`<br /><br /> Aşağıdaki örneklerde diğer olanaklar gösterilmektedir:<br /><br /> `-fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `-flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `-flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `-flp2:errorsonly;logfile=msbuild.err`|
|Medi<br /><br /> `logger`|girişindeki`logger`|MSBuild olaylarını günlüğe kaydetmek için kullanılacak günlükçüsü belirtir. Birden çok günlüğe kaydetme belirtmek için, her Günlükçü ayrı ayrı belirtin.<br /><br /> İçin aşağıdaki sözdizimini kullanın `logger` : `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerClass` : `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Derleme tam olarak bir günlükçü içeriyorsa günlükçü sınıfını belirtmeniz gerekmez.<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerAssembly` : `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Günlükçü parametreleri isteğe bağlıdır ve bu, tam olarak bunları girdiğiniz şekilde günlükçü 'ye geçirilir.<br /><br /> Aşağıdaki örneklerde **-günlükçü** anahtarı kullanılır.<br /><br /> `-logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|
|-Noconsolegünlükçü|-noconlog|Varsayılan konsol günlükçüsü 'yi devre dışı bırakın ve olayları konsola kaydetme.|

## <a name="example-1"></a>Örnek 1

 Aşağıdaki örnek `rebuild` *MyProject. proj* projesinin hedefini oluşturur.

```cmd
MSBuild.exe MyProject.proj -t:rebuild
```

## <a name="example-2"></a>Örnek 2

 Daha karmaşık derlemeler gerçekleştirmek için *MSBuild.exe* kullanabilirsiniz. Örneğin, bir çözümde belirli projelerin belirli hedeflerini oluşturmak için kullanabilirsiniz. Aşağıdaki örnek, projeyi yeniden oluşturur `NotInSolutionFolder` ve `InSolutionFolder` *newfolder* çözüm klasöründeki projeyi temizler.

```cmd
msbuild SlnFolders.sln -t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Yaygın MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
