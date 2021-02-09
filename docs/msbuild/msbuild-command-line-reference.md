---
title: MSBuild Command-Line başvurusu | Microsoft Docs
description: MSBuild.exe komut satırını kullanarak proje veya çözüm dosyası oluşturma ve dahil etmek istediğiniz çeşitli anahtarlar hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: dcb11fd9bfec3fc2818751dd74ba3c0ac4dd12d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919153"
---
# <a name="msbuild-command-line-reference"></a>MSBuild komut satırı başvurusu

Bir proje veya çözüm dosyası oluşturmak için *MSBuild.exe* kullandığınızda, işlemin çeşitli yönlerini belirtmek için birkaç anahtar ekleyebilirsiniz.

Her anahtar iki biçimde kullanılabilir:-Switch ve/Switch. Belgeler yalnızca-switch formunu gösterir. Anahtarlar büyük/küçük harfe duyarlı değildir. Windows komut istemi dışında bir kabuktan MSBuild çalıştırırsanız, bir anahtara bağımsız değişkenlerin listesi (noktalı virgül veya virgülle ayrılmış olarak), listelerin, kabuğun yorumlanması yerine MSBuild 'e geçirildiğinden emin olmak için tek veya çift tırnak işareti gerekebilir.

## <a name="syntax"></a>Söz dizimi

```cmd
MSBuild.exe [Switches] [ProjectFile]
```

## <a name="arguments"></a>Bağımsız değişkenler

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`ProjectFile`|Belirttiğiniz proje dosyasında hedefleri oluşturur. Proje dosyası belirtmezseniz, MSBuild, *proj* içinde sonlanan ve bu dosyayı kullanan bir dosya adı uzantısı için geçerli çalışma dizinini arar. Ayrıca, bu bağımsız değişken için bir Visual Studio çözüm dosyası da belirtebilirsiniz.|

## <a name="switches"></a>Anahtarlar

|Anahtar|Kısa biçim|Description|
|------------|----------------|-----------------|
|-detailedSummary|-DS|Oluşturulan yapılandırmaların ve düğümlerin nasıl zamanlandıkları hakkında derleme günlüğünün sonundaki ayrıntılı bilgileri göster.|
|-graphBuild [: `True` veya `False` ]|-Graf [: `True` or `False` ]|MSBuild 'in bir proje grafiği oluşturmasına ve oluşturmasına neden olur. Bir Graph oluşturmak, form bağımlılıklarına proje başvurularını tanımlamayı içerir. Bu grafiği oluşturmak, geleneksel MSBuild zamanlamasından farklı olarak, bunlara başvuran projelerden önce proje başvuruları oluşturmaya çalışıyor. MSBuild 16 veya üzerini gerektirir.|
|-yardım|/? or-h|Kullanım bilgilerini görüntüleyin. Aşağıdaki komut bir örnektir:<br /><br /> `msbuild.exe -?`|
|-ıgnoreprojecbir: `extensions`|Yoksay `extensions`|Oluşturulacak proje dosyasını belirlerken belirtilen uzantıları yoksayın. Aşağıdaki örnekte gösterildiği gibi, birden çok uzantıyı ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `-ignoreprojectextensions:.vcproj,.sln`|
|-Interactive [: `True` or `False` ]|-|Derlemedeki eylemlerin kullanıcıyla etkileşime girmesine izin verildiğini gösterir.  Bu bağımsız değişkeni, etkileşimin beklenmediği bir otomatik senaryoda kullanmayın. -INTERACTIVE belirtildiğinde,-INTERACTIVE: true olarak belirtiliyor.  Bir yanıt dosyasından gelen bir değeri geçersiz kılmak için parametresini kullanın.
|-ısoteprojects [: `True` veya `False` ]|-yalıt [: `True` veya `False` ]|MSBuild 'in her bir projeyi yalıtımına oluşturmasına neden olur. Bu, proje grafiğinin değerlendirme zamanında statik olarak keşfedilmesini gerektirdiğinden, ancak büyük bir proje oluştururken zamanlamayı iyileştirebilecek ve bellek yükünü azaltmanıza yönelik bir MSBuild 'in daha kısıtlayıcı bir modudur.|
|-maxCpuCount [: `number` ]|-d [: `number` ]|Derlerken kullanılacak en fazla eşzamanlı işlem sayısını belirtir. Bu anahtarı eklemezseniz, varsayılan değer 1 ' dir. Bu anahtarı bir değer belirtmeden eklerseniz, MSBuild bilgisayardaki işlemci sayısına kadar kullanır. Daha fazla bilgi için bkz. [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Aşağıdaki örnek, aynı anda üç projenin oluşturulmasına izin veren üç MSBuild işlemini kullanarak derleme için MSBuild 'e bildirir:<br /><br /> `msbuild myproject.proj -maxcpucount:3`|
|-Nooto yanıtı|-noautorsp|*MSBuild. rsp* dosyalarını otomatik olarak eklemeyin.|
|-nodeReuse:`value`|n`value`|MSBuild düğümlerinin yeniden kullanımını etkinleştirin veya devre dışı bırakın. Aşağıdaki değerleri belirtebilirsiniz:<br /><br /> -   **True**. Sonraki derlemelerin onları kullanabilmesi için derleme tamamlandıktan sonra düğümler kalır (varsayılan).<br />-   **Yanlış**. Derleme tamamlandıktan sonra düğümler kalmaz.<br /><br /> Düğüm, yürütülmekte olan bir projeye karşılık gelir. **-Maxcpucount** anahtarını eklerseniz, birden çok düğüm eşzamanlı olarak çalıştırılabilir.|
|-nologo||Başlangıç başlığını veya telif hakkı iletisini gösterme.|
|<a name="preprocess"></a> -preprocess [: `filepath` ]|-PP [: `filepath` ]|Bir derleme sırasında içeri aktarılacak tüm dosyaları satır içine alarak, tek bir toplanmış proje dosyası oluşturun ve sınırları işaretlenir. Bu anahtarı, hangi dosyaların içeri aktarıldığını, dosyaların içeri aktarılmakta olduğunu ve hangi dosyaların yapıya katkıda bulunduğunu daha kolay bir şekilde belirleyebilmeniz için kullanabilirsiniz. Bu anahtarı kullandığınızda proje derlenmez.<br /><br /> Bir belirtirseniz `filepath` , toplanmış proje dosyası dosyaya çıktıdır. Aksi takdirde, çıktı konsol penceresinde görünür.<br /><br /> Bir `Import` Proje dosyasını başka bir proje dosyasına eklemek için öğesinin nasıl kullanılacağı hakkında bilgi için, bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md) ve [nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|
|-outputResultsCache [: cacheFile]|-Orc [: cacheFile]|MSBuild 'in derleme sonunda yapı sonuç önbelleklerinin içeriğini yazacağı çıkış önbelleği dosyası. Bunun ayarlanması ayrıca yalıtılmış derlemeler (-yalıt) açar.|
|-profileEvaluation:`<file>`|-|Profiller MSBuild değerlendirmesi ve sonucu belirtilen dosyaya yazar. Belirtilen dosyanın uzantısı '. MD ' ise, sonuç markı biçiminde oluşturulur. Aksi takdirde, sekmeyle ayrılmış bir dosya oluşturulur.|
|özelliði`name`=`value`|Lama`name`=`value`|Belirtilen proje düzeyi özelliklerini ayarlayın veya geçersiz kılın; burada `name` özellik adıdır ve `value` özellik değeridir. Her bir özelliği ayrı ayrı belirtin ya da aşağıdaki örnekte gösterildiği gibi birden çok özelliği ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `-property:WarningLevel=2;OutDir=bin\Debug`|
|-geri yükleme|-r|`Restore`Asıl hedefleri oluşturmadan önce hedefi çalıştırır.|
|-restoreProperty:`name=value`|RP`name=value`|Bu proje düzeyi özelliklerini yalnızca geri yükleme sırasında ayarlayın veya geçersiz kılın ve-Property bağımsız değişkeniyle belirtilen özellikleri kullanmayın. `name` , özellik adıdır ve `value` özellik değeridir. Birden çok özelliği ayırmak için noktalı virgül veya virgül kullanın veya her bir özelliği ayrı ayrı belirtin.|
|hedef`targets`|şı`targets`|Projede belirtilen hedefleri oluşturun. Her hedefi ayrı ayrı belirtin veya birden çok hedefi ayırmak için noktalı virgül veya virgül kullanın, aşağıdaki örnekte gösterildiği gibi:<br /><br /> `-target:PrepareResources;Compile`<br /><br /> Bu anahtarı kullanarak herhangi bir hedef belirtirseniz, proje dosyasındaki özniteliğinde herhangi bir hedef yerine çalıştırırlar `DefaultTargets` . Daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md) ve [nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Hedef bir görev grubudur. Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md).|
|-targets [: `file` ]|-TS [: `file` ]|Yapı işlemini gerçekten yürütmeden, kullanılabilir hedeflerin listesini belirtilen dosyaya (veya herhangi bir dosya belirtilmemişse çıkış cihazına) yazın.|
|ToolsVersion`version`|kaydedebilirsiniz`version`|Aşağıdaki örnekte gösterildiği gibi, projeyi oluşturmak için kullanılacak araç takımının sürümünü belirtir: `-toolsversion:3.5`<br /><br /> Bu anahtarı kullanarak bir proje oluşturabilir ve [Proje öğesinde (MSBuild)](../msbuild/project-element-msbuild.md)belirtilen sürümden farklı bir sürüm belirtebilirsiniz. Daha fazla bilgi için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).<br /><br /> MSBuild 4,5 için şu değerleri belirtebilirsiniz `version` : 2,0, 3,5 ve 4,0. 4,0 belirtirseniz, `VisualStudioVersion` Build özelliği hangi alt araç takımını kullanacağınızı belirtir. Daha fazla bilgi için araç kümesi 'nin [(Araçlar sürümü)](../msbuild/msbuild-toolset-toolsversion.md)alt araç kümeleri bölümüne bakın.<br /><br /> Bir araç takımı, bir uygulama oluşturmak için kullanılan görevlerden, hedeflerin ve araçlardan oluşur. Araçlar *csc.exe* ve *vbc.exe* gibi derleyiciler içerir. Araç kümeleri hakkında daha fazla bilgi için bkz. [araç takımı (Araçlar sürümü)](../msbuild/msbuild-toolset-toolsversion.md), [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md)ve [Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md). **Note:**  Araç takımı sürümü, bir projenin çalışmak üzere oluşturulduğu .NET Framework sürümü olan hedef Framework ile aynı değildir. Daha fazla bilgi için bkz. [hedef Framework ve hedef platform](../msbuild/msbuild-target-framework-and-target-platform.md).|
|-Doğrula: [ `schema` ]|-Val [ `schema` ]|Proje dosyasını doğrulayın ve doğrulama başarılı olursa projeyi derleyin.<br /><br /> Belirtmezseniz `schema` , proje varsayılan şemaya göre onaylanır.<br /><br /> Belirtirseniz `schema` , proje belirttiğiniz şemaya göre onaylanır.<br /><br /> Aşağıdaki ayar bir örnektir: `-validate:MyExtendedBuildSchema.xsd`|
|ayrıntı`level`|Yönetim`level`|Yapı günlüğünde görüntülenecek bilgi miktarını belirtir. Her Günlükçü, bu günlükçü için ayarladığınız ayrıntı düzeyine göre olayları görüntüler.<br /><br /> Aşağıdaki ayrıntı düzeylerini belirtebilirsiniz: `q[uiet]` , `m[inimal]` , `n[ormal]` (varsayılan), `d[etailed]` ve `diag[nostic]` .<br /><br /> Aşağıdaki ayar bir örnektir: `-verbosity:quiet`
|-sürüm|-ver|Yalnızca sürüm bilgilerini görüntüleyin. Proje derlenmedi.|
|@`file`||Bir metin dosyasından komut satırı anahtarları ekleyin. Birden çok dosya varsa, bunları ayrı olarak belirtirsiniz. Daha fazla bilgi için bkz. [yanıt dosyaları](../msbuild/msbuild-response-files.md).|
|-warnAsError [: `code` [ `;code2` ]|-ERR [ `:code` [ `;code2` ]|Hata olarak ele edilecek uyarı kodlarının listesi.  Birden çok uyarı kodunu ayırmak için noktalı virgül veya virgül kullanın. Tüm uyarıları hata olarak değerlendirmek için, anahtarı hiçbir değer olmadan kullanın. Bir uyarı hata olarak kabul edildiğinde, hedef bir uyarı gibi yürütülmeye devam eder, ancak genel derleme başarısız olur.<br/><br/>Örnek: `-err:MSB4130`|
|-warnAsMessage [: `code` [ `;code2` ]|-noWarn [: `code` [ `;code2` ]|Düşük öneme sahip iletiler olarak kabul edilecek uyarı kodlarının listesi.  Birden çok uyarı kodunu ayırmak için noktalı virgül veya virgül kullanın.<br/><br/>Örnek: `-noWarn:MSB3026`|

### <a name="switches-for-loggers"></a>Günlükçüler için anahtarlar

|Anahtar|Kısa biçim|Description|
|------------|----------------|-----------------|
|-Binarygünlükçü [: [LogFile =]`output.binlog`<br/>[; ProjectImports = [None, embed, ZipFile]]]|-BL|Tüm derleme olaylarını sıkıştırılmış bir ikili dosyaya serileştirir. Varsayılan olarak, dosya geçerli dizindir ve *MSBuild. binlog* olarak adlandırılır. İkili günlük, daha sonra metin günlüklerini yeniden oluşturmak ve diğer çözümleme araçları tarafından kullanılmak üzere kullanılabilecek yapı işleminin ayrıntılı bir açıklamasıdır. İkili günlük genellikle en ayrıntılı metin Tanılama düzeyi günlüğünden 10-20X küçüktür, ancak daha fazla bilgi içerir.<br /><br />İkili günlükçü, derleme sırasında karşılaşılan tüm içeri aktarılan projeler ve hedef dosyalar dahil olmak üzere proje dosyalarının kaynak metnini varsayılan olarak toplar. İsteğe bağlı `ProjectImports` anahtar, bu davranışı denetler:<br /><br /> -   **Projectımports = None**. Proje içeri aktarmaları toplanmaz.<br /> -   **Projectimports = embed**. Proje içeri aktarmalarını günlük dosyasına ekleyin (varsayılan).<br /> -   **Projectımports = ZipFile**. Proje dosyalarını, *\<output>* \<output> ikili günlük dosyası adıyla aynı ada sahip.projectimports.zipkaydedin.<br /><br />Projectımports için varsayılan ayar ekleme ' dir.<br />**Not**: günlükçü, *. cs*, *. cpp* vb. gibi MSBuild olmayan kaynak dosyaları toplanmaz.<br />Bir *. binlog* dosyası, bir proje/çözüm yerine bir bağımsız değişken olarak *msbuild.exe* ileterek "çalınabilir". Diğer Günlükçüler, ilk derleme gerçekleşenler gibi günlük dosyasında yer alan bilgileri alır. İkili günlük ve kullanımları hakkında daha fazla bilgiyi şurada bulabilirsiniz: https://github.com/Microsoft/msbuild/wiki/Binary-Log <br /><br />**Örnekler**:<br /> -   `-bl`<br /> -    `-bl:output.binlog`<br /> -   `-bl:output.binlog;ProjectImports=None`<br /> -   `-bl:output.binlog;ProjectImports=ZipFile`<br /> -   `-bl:..\..\custom.binlog`<br /> -   `-binaryLogger`|
|-consoleLoggerParameters:<br /><br /> `parameters`|-CLP:`parameters`|Konsol penceresinde yapı bilgilerini görüntüleyen konsol günlükçüsü ' ne belirttiğiniz parametreleri geçirin. Aşağıdaki parametreleri belirtebilirsiniz:<br /><br /> -   **Performanslı**. Görevler, hedefler ve projelerde harcanan zamanı gösterir.<br />-   **Özet**. Hata ve uyarı özetini sonda görüntüleyin.<br />-   **Nosummary**. Hata ve uyarı özetini sonda gösterme.<br />-   **ErrorsOnly**. Yalnızca hataları göster.<br />-   **Warningsonly**. Yalnızca uyarıları göster.<br />-   **Noitelicpropertylist**. Ayrıntı düzeyi olarak ayarlanırsa her proje derlemesinin başlangıcında görünecek öğe ve özelliklerin listesini gösterme `diagnostic` .<br />-   **Showcommandline**. `TaskCommandLineEvent`İletileri göster.<br />-   **Showtimestamp**. Herhangi bir iletinin öneki olarak zaman damgasını gösterir.<br />-   **Showweventıd**. Her başlatılan olay, tamamlanan olay ve ileti için olay KIMLIĞINI görüntüleyin.<br />-   **ForceNoAlign**. Metni konsol arabelleğinin boyutuna hizalayın.<br />-   **Disableconsolecolor**. Tüm günlük mesajları için varsayılan Konsol renklerini kullanın.<br />-   **Disablemplogging**. Çok işlemcili modda çalışırken çıktının çok işlemcili günlük stilini devre dışı bırakın.<br />-   **Enablemplogging**. Çok işlemcili modda çalışırken bile çok işlemcili günlük stilini etkinleştirin. Bu günlük oluşturma stili varsayılan olarak açık olur.<br />-   **Ayrıntı düzeyi**. Bu günlükçü için **-ayrıntı** ayarını geçersiz kılın.<br /><br /> Aşağıdaki örnekte gösterildiği gibi, birden çok parametreyi ayırmak için noktalı virgül kullanın:<br /><br /> `-consoleloggerparameters:PerformanceSummary;NoSummary -verbosity:minimal`<br/><br/> Varsayılan konsol günlükçüsü normal ayrıntı düzeyine sahiptir ve bir içerir `Summary` .|
|-Distributedfilegünlükçü|-DFL|Her MSBuild düğümünün derleme çıkışını kendi dosyasına kaydedin. Bu dosyaların başlangıç konumu geçerli dizindir. Varsayılan olarak, dosyalar *MSBuild \<NodeId> . log* olarak adlandırılır. Filegünlükçü için dosyaların ve diğer parametrelerin konumunu belirtmek için **-FileLoggerParameters** anahtarını kullanabilirsiniz.<br /><br /> **-FileLoggerParameters** anahtarını kullanarak bir günlük dosyasına ad verirseniz, dağıtılmış günlükçü bu adı bir şablon olarak kullanır ve düğüm kimliğini her düğüm için bir günlük dosyası oluştururken bu ada ekler.|
|-Distributedgünlükçüsü:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|DL`central logger`*`forwarding logger`|Her düğüme farklı bir günlükçü örneği ekleyerek MSBuild 'ten gelen olayları günlüğe kaydedin. Birden çok günlüğe kaydetme belirtmek için, her Günlükçü ayrı ayrı belirtin.<br /><br /> Günlükçü belirtmek için günlükçü sözdizimini kullanın. Günlükçü sözdizimi için aşağıdaki **-günlükçü** anahtarına bakın.<br /><br /> Aşağıdaki örneklerde bu anahtarın nasıl kullanılacağı gösterilmektedir:<br /><br /> `-dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|
|-Filegünlükçü<br /><br /> *sayısından*|-fl [ `number` ]|Yapı çıkışını geçerli dizindeki tek bir dosyaya kaydedin. Belirtmezseniz `number` , çıkış dosyası *MSBuild. log* olarak adlandırılır. Öğesini belirtirseniz, `number` Çıkış dosyası *MSBuild \<n> . log* olarak adlandırılır; burada \<n> `number` . `Number` 1 ile 9 arasında bir sayı olabilir.<br /><br /> Dosya konumunu ve Filegünlükçü için diğer parametreleri belirtmek üzere **-FileLoggerParameters** anahtarını kullanabilirsiniz.|
|-fileLoggerParameters [sayı]:<br /><br /> `parameters`|-FLP [ `number` ]: `parameters`|Dosya günlükçüsü ve dağıtılmış dosya günlükçüsü için ek parametreleri belirtir. Bu anahtarın varlığı, karşılık gelen **filegünlükçü [** `number` **]** anahtarının mevcut olduğunu gösterir. `Number` 1 ile 9 arasında bir sayı olabilir.<br /><br /> **-Consoleloggerparameters** için listelenen tüm parametreleri kullanabilirsiniz. Aşağıdaki parametrelerden bir veya daha fazlasını da kullanabilirsiniz:<br /><br /> -   **Günlük dosyası**. Derleme günlüğünün yazıldığı günlük dosyasının yolu. Dağıtılmış dosya günlükçüsü bu yolu, günlük dosyalarının adlarına önek olarak ekler.<br />-   **Ekle**. Derleme günlüğünün günlük dosyasına eklenip eklenmeyeceğini belirler veya dosyanın üzerine yazar. Anahtarı ayarladığınızda, derleme günlüğü günlük dosyasına eklenir. Anahtar mevcut olmadığında, var olan bir günlük dosyasının içeriğinin üzerine yazılır.<br />     Örnek: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log;append`<br />     Açık `true` veya ayar eklerseniz, bu `false` ayar ne olursa olsun günlüğe eklenir. Append anahtarını eklemezseniz günlüğün üzerine yazılır.<br />     Bu durumda, dosyanın üzerine yazılır: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log`<br />     Bu durumda, dosyanın eklendiği yer: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log;append=true`<br />     Bu durumda, dosyanın eklendiği yer: `msbuild myfile.proj -flp:FileLogger,Microsoft.Build;logfile=MyLog.log;append=false`<br />-   **Kodlama**. Dosya için kodlamayı belirtir (örneğin, UTF-8, Unicode veya ASCII).<br /><br /> Aşağıdaki örnek, uyarılar ve hatalar için ayrı günlük dosyaları üretir:<br /><br /> `-flp1:logfile=errors.txt;errorsonly -flp2:logfile=warnings.txt;warningsonly`<br /><br /> Aşağıdaki örneklerde diğer olanaklar gösterilmektedir:<br /><br /> `-fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `-flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `-flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `-flp2:errorsonly;logfile=msbuild.err`|
|Medi<br /><br /> `logger`|girişindeki`logger`|MSBuild 'ten olayları günlüğe kaydetmek için kullanılacak günlükçü 'yi belirtir. Birden çok günlüğe kaydetme belirtmek için, her Günlükçü ayrı ayrı belirtin.<br /><br /> İçin aşağıdaki sözdizimini kullanın `logger` : `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerClass` : `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Derleme tam olarak bir günlükçü içeriyorsa günlükçü sınıfını belirtmeniz gerekmez.<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerAssembly` : `{``AssemblyName``[,``StrongName``] &#124;``AssemblyFile``}`<br /><br /> Günlükçü parametreleri isteğe bağlıdır ve bu, tam olarak bunları girdiğiniz şekilde günlükçü 'ye geçirilir.<br /><br /> Aşağıdaki örneklerde **-günlükçü** anahtarı kullanılır.<br /><br /> `-logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `-logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|
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
