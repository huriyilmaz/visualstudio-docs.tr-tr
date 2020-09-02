---
title: MSBuild komut satırı başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d40bfefb1f89496b538612dfa1819cc6d65c76c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181060"
---
# <a name="msbuild-command-line-reference"></a>MSBuild Komut Satırı Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir proje veya çözüm dosyası oluşturmak için MSBuild.exe kullandığınızda, işlemin çeşitli yönlerini belirtmek için birkaç anahtar ekleyebilirsiniz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`ProjectFile`|Belirttiğiniz proje dosyasında hedefleri oluşturur. Proje dosyası belirtmezseniz, MSBuild, "proj" ile biten bir dosya adı uzantısı için geçerli çalışma dizinini arar ve bu dosyayı kullanır. Ayrıca, bu bağımsız değişken için bir Visual Studio çözüm dosyası da belirtebilirsiniz.|  
  
## <a name="switches"></a>Anahtarlar  
  
|Anahtar|Kısa biçim|Açıklama|  
|------------|----------------|-----------------|  
|/help|/? veya/h|Kullanım bilgilerini görüntüleyin. Aşağıdaki komut bir örnektir:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/DS|Oluşturulan yapılandırmaların ve düğümlerin nasıl zamanlandıkları hakkında derleme günlüğünün sonundaki ayrıntılı bilgileri göster.|  
|/ıgnoreprojecbir: `extensions`|/Ignore `extensions`|Oluşturulacak proje dosyasını belirlerken belirtilen uzantıları yoksayın. Aşağıdaki örnekte gösterildiği gibi, birden çok uzantıyı ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount [: `number` ]|/m [: `number` ]|Derlerken kullanılacak en fazla eşzamanlı işlem sayısını belirtir. Bu anahtarı eklemezseniz, varsayılan değer 1 ' dir. Bu anahtarı bir değer belirtmeden eklerseniz, MSBuild bilgisayardaki işlemci sayısına kadar kullanır. Daha fazla bilgi için bkz. [paralel olarak birden çok proje oluşturma](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> Aşağıdaki örnek, aynı anda üç projenin oluşturulmasına izin veren üç MSBuild işlemini kullanarak derleme için MSBuild 'e bildirir:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/nooto yanıtı|/noautorsp|MSBuild. rsp dosyalarını otomatik olarak eklemeyin.|  
|/nodeReuse:`value`|n`value`|MSBuild düğümlerinin yeniden kullanımını etkinleştirin veya devre dışı bırakın. Aşağıdaki değerleri belirtebilirsiniz:<br /><br /> -   **True**. Sonraki derlemelerin onları kullanabilmesi için derleme tamamlandıktan sonra düğümler kalır (varsayılan).<br />-   **Yanlış**. Derleme tamamlandıktan sonra düğümler kalmaz.<br /><br /> Düğüm, yürütülmekte olan bir projeye karşılık gelir. **/Maxcpucount** anahtarını eklerseniz, birden çok düğüm eşzamanlı olarak çalıştırılabilir.|  
|/nologo||Başlangıç başlığını veya telif hakkı iletisini gösterme.|  
|/preprocess [: `filepath` ]|/PP [: `filepath` ]|Bir derleme sırasında içeri aktarılacak tüm dosyaları satır içine alarak, tek bir toplanmış proje dosyası oluşturun ve sınırları işaretlenir. Bu anahtarı, hangi dosyaların içeri aktarıldığını, dosyaların içeri aktarılmakta olduğunu ve hangi dosyaların yapıya katkıda bulunduğunu daha kolay bir şekilde belirleyebilmeniz için kullanabilirsiniz. Bu anahtarı kullandığınızda proje derlenmez.<br /><br /> Bir belirtirseniz `filepath` , toplanmış proje dosyası dosyaya çıktıdır. Aksi takdirde, çıktı konsol penceresinde görünür.<br /><br /> Bir `Import` Proje dosyasını başka bir proje dosyasına eklemek için öğesinin nasıl kullanılacağı hakkında bilgi için, bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md) ve [nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|özelliði`name`=`value`|/p`name`=`value`|Belirtilen proje düzeyi özelliklerini ayarlayın veya geçersiz kılın; burada `name` özellik adıdır ve `value` özellik değeridir. Her bir özelliği ayrı ayrı belirtin ya da aşağıdaki örnekte gösterildiği gibi birden çok özelliği ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/Target`targets`|/t`targets`|Projede belirtilen hedefleri oluşturun. Her hedefi ayrı ayrı belirtin veya birden çok hedefi ayırmak için noktalı virgül veya virgül kullanın, aşağıdaki örnekte gösterildiği gibi:<br /><br /> `/target:Resources;Compile`<br /><br /> Bu anahtarı kullanarak herhangi bir hedef belirtirseniz, proje dosyasındaki özniteliğinde herhangi bir hedef yerine çalıştırırlar `DefaultTargets` . Daha fazla bilgi için bkz. [hedef derleme sırası](../msbuild/target-build-order.md) ve [nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Hedef bir görev grubudur. Daha fazla bilgi için bkz. [hedefler](../msbuild/msbuild-targets.md).|  
|ToolsVersion`version`|kaydedebilirsiniz`version`|Aşağıdaki örnekte gösterildiği gibi, projeyi oluşturmak için kullanılacak araç takımının sürümünü belirtir: `/toolsversion:3.5`<br /><br /> Bu anahtarı kullanarak bir proje oluşturabilir ve [Proje öğesinde (MSBuild)](../msbuild/project-element-msbuild.md)belirtilen sürümden farklı bir sürüm belirtebilirsiniz. Daha fazla bilgi için bkz. [araçları sürüm ayarlarını geçersiz kılma](../msbuild/overriding-toolsversion-settings.md).<br /><br /> MSBuild 4,5 için şu değerleri belirtebilirsiniz `version` : 2,0, 3,5 ve 4,0. 4,0 belirtirseniz, `VisualStudioVersion` Build özelliği hangi alt araç takımını kullanacağınızı belirtir. Daha fazla bilgi için araç kümesi 'nin [(Araçlar sürümü)](../msbuild/msbuild-toolset-toolsversion.md)alt araç kümeleri bölümüne bakın.<br /><br /> Bir araç takımı, bir uygulama oluşturmak için kullanılan görevlerden, hedeflerin ve araçlardan oluşur. Araçlar csc.exe ve vbc.exe gibi derleyiciler içerir. Araç kümeleri hakkında daha fazla bilgi için bkz. [araç takımı (Araçlar sürümü)](../msbuild/msbuild-toolset-toolsversion.md), [Standart ve özel araç takımı yapılandırması](../msbuild/standard-and-custom-toolset-configurations.md)ve [Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md). **Note:**  Araç takımı sürümü, bir projenin çalışmak üzere oluşturulduğu .NET Framework sürümü olan hedef Framework ile aynı değildir. Daha fazla bilgi için bkz. [hedef Framework ve hedef platform](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/Validate: [ `schema` ]|/Val [ `schema` ]|Proje dosyasını doğrulayın ve doğrulama başarılı olursa projeyi derleyin.<br /><br /> Belirtmezseniz `schema` , proje varsayılan şemaya göre onaylanır.<br /><br /> Belirtirseniz `schema` , proje belirttiğiniz şemaya göre onaylanır.<br /><br /> Aşağıdaki ayar bir örnektir: `/validate:MyExtendedBuildSchema.xsd`|  
|/Verbosity seçeneğiyle`level`|çıktıda`level`|Yapı günlüğünde görüntülenecek bilgi miktarını belirtir. Her Günlükçü, bu günlükçü için ayarladığınız ayrıntı düzeyine göre olayları görüntüler.<br /><br /> Aşağıdaki ayrıntı düzeylerini belirtebilirsiniz: `q[uiet]` , `m[inimal]` ,, `n[ormal]` `d[etailed]` ve `diag[nostic]` .<br /><br /> Aşağıdaki ayar bir örnektir: `/verbosity:quiet`|  
|/Version|/ver|Yalnızca sürüm bilgilerini görüntüleyin. Proje derlenmedi.|  
|@`file`||Bir metin dosyasından komut satırı anahtarları ekleyin. Birden çok dosya varsa, bunları ayrı olarak belirtirsiniz. Daha fazla bilgi için bkz. [yanıt dosyaları](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Günlükçüler için anahtarlar  
  
|Anahtar|Kısa biçim|Açıklama|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/CLP:`parameters`|Konsol penceresinde yapı bilgilerini görüntüleyen konsol günlükçüsü ' ne belirttiğiniz parametreleri geçirin. Aşağıdaki parametreleri belirtebilirsiniz:<br /><br /> -   **Performanslı**. Görevler, hedefler ve projelerde harcanan zamanı gösterir.<br />-   **Özet**. Hata ve uyarı özetini sonda görüntüleyin.<br />-   **Nosummary**. Hata ve uyarı özetini sonda gösterme.<br />-   **ErrorsOnly**. Yalnızca hataları göster.<br />-   **Warningsonly**. Yalnızca uyarıları göster.<br />-   **Noitelicpropertylist**. Ayrıntı düzeyi olarak ayarlanırsa her proje derlemesinin başlangıcında görünecek öğe ve özelliklerin listesini gösterme `diagnostic` .<br />-   **Showcommandline**. `TaskCommandLineEvent`İletileri göster.<br />-   **Showtimestamp**. Herhangi bir iletinin öneki olarak zaman damgasını gösterir.<br />-   **Showweventıd**. Her başlatılan olay, tamamlanan olay ve ileti için olay KIMLIĞINI görüntüleyin.<br />-   **ForceNoAlign**. Metni konsol arabelleğinin boyutuna hizalayın.<br />-   **Disableconsolecolor**. Tüm günlük mesajları için varsayılan Konsol renklerini kullanın.<br />-   **Disablemplogging**. Çok işlemcili modda çalışırken çıktının çok işlemcili günlük stilini devre dışı bırakın.<br />-   **Enablemplogging**. Çok işlemcili modda çalışırken bile çok işlemcili günlük stilini etkinleştirin. Bu günlük oluşturma stili varsayılan olarak açık olur.<br />-   **Ayrıntı düzeyi**. Bu günlükçü için **/ayrıntı** ayarını geçersiz kılın.<br /><br /> Aşağıdaki örnekte gösterildiği gibi, birden çok parametreyi ayırmak için noktalı virgül veya virgül kullanın:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/Distributedfilegünlükçü|/DFL|Her MSBuild düğümünün derleme çıkışını kendi dosyasına kaydedin. Bu dosyaların başlangıç konumu geçerli dizindir. Varsayılan olarak, dosyalar "MSBuild*NodeId*. log" olarak adlandırılmıştır. Dosya ve Filegünlükçü için diğer parametrelerin konumunu belirtmek için **/FileLoggerParameters** anahtarını kullanabilirsiniz.<br /><br /> **/FileLoggerParameters** anahtarını kullanarak bir günlük dosyasına ad verirseniz, dağıtılmış günlükçü bu adı bir şablon olarak kullanır ve düğüm kimliğini her düğüm için bir günlük dosyası oluştururken bu ada ekler.|  
|/distributedgünlükçüsü:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|DL`central logger`*`forwarding logger`|Her düğüme farklı bir günlükçü örneği ekleyerek MSBuild 'ten gelen olayları günlüğe kaydedin. Birden çok günlüğe kaydetme belirtmek için, her Günlükçü ayrı ayrı belirtin.<br /><br /> Günlükçü belirtmek için günlükçü sözdizimini kullanın. Günlükçü sözdizimi için aşağıdaki **/günlükçü** anahtarına bakın.<br /><br /> Aşağıdaki örneklerde bu anahtarın nasıl kullanılacağı gösterilmektedir:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/Filegünlükçü<br /><br /> *sayısından*|/fl [ `number` ]|Yapı çıkışını geçerli dizindeki tek bir dosyaya kaydedin. Belirtmezseniz `number` , çıkış dosyası MSBuild. log olarak adlandırılır. Belirtirseniz `number` , çıkış dosyası MSBuild `n` . log olarak adlandırılır; burada n 'dir `number` . `Number` 1 ile 9 arasında bir sayı olabilir.<br /><br /> Dosya konumunu ve Filegünlükçü için diğer parametreleri belirtmek için **/FileLoggerParameters** anahtarını kullanabilirsiniz.|  
|/FileLoggerParameters: [sayı]<br /><br /> `parameters`|/FLP: [ `number` ] `parameters`|Dosya günlükçüsü ve dağıtılmış dosya günlükçüsü için ek parametreleri belirtir. Bu anahtarın varlığı, karşılık gelen/**filegünlükçü [** `number` **]** anahtarının mevcut olduğunu gösterir. `Number` 1 ile 9 arasında bir sayı olabilir.<br /><br /> **/Consoleloggerparameters**için listelenen tüm parametreleri kullanabilirsiniz. Aşağıdaki parametrelerden bir veya daha fazlasını da kullanabilirsiniz:<br /><br /> -   **Günlük dosyası**. Derleme günlüğünün yazıldığı günlük dosyasının yolu. Dağıtılmış dosya günlükçüsü bu yolu, günlük dosyalarının adlarına önek olarak ekler.<br />-   **Ekle**. Derleme günlüğünün günlük dosyasına eklenip eklenmeyeceğini belirler veya dosyanın üzerine yazar. Anahtarı ayarladığınızda, derleme günlüğü günlük dosyasına eklenir. Anahtar mevcut olmadığında, var olan bir günlük dosyasının içeriğinin üzerine yazılır.<br />     Ekleme anahtarını eklerseniz, true veya false olarak ayarlanmış olsun, günlük eklenir. Append anahtarını eklemezseniz günlüğün üzerine yazılır.<br />     Bu durumda, dosyanın üzerine yazılır: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     Bu durumda, dosyanın eklendiği yer: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     Bu durumda, dosyanın eklendiği yer: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Kodlama**. Dosya için kodlamayı belirtir (örneğin, UTF-8, Unicode veya ASCII).<br /><br /> Aşağıdaki örnek, uyarılar ve hatalar için ayrı günlük dosyaları üretir:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> Aşağıdaki örneklerde diğer olanaklar gösterilmektedir:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|Medi<br /><br /> `logger`|/l`logger`|MSBuild 'ten olayları günlüğe kaydetmek için kullanılacak günlükçü 'yi belirtir. Birden çok günlüğe kaydetme belirtmek için, her Günlükçü ayrı ayrı belirtin.<br /><br /> İçin aşağıdaki sözdizimini kullanın `logger` : `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerClass` : `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> Derleme tam olarak bir günlükçü içeriyorsa günlükçü sınıfını belirtmeniz gerekmez.<br /><br /> İçin aşağıdaki sözdizimini kullanın `LoggerAssembly` : `{``AssemblyName``[,``StrongName``] &#124;``AssemblyFile``}`<br /><br /> Günlükçü parametreleri isteğe bağlıdır ve bu, tam olarak bunları girdiğiniz şekilde günlükçü 'ye geçirilir.<br /><br /> Aşağıdaki örnekler **/günlükçü** anahtarını kullanır.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolegünlükçü|/noconlog|Varsayılan konsol günlükçüsü 'yi devre dışı bırakın ve olayları konsola kaydetme.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `rebuild` projenin hedefini oluşturur `MyProject.proj` .  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Örnek  
 Daha karmaşık derlemeler gerçekleştirmek için MSBuild.exe kullanabilirsiniz. Örneğin, bir çözümde belirli projelerin belirli hedeflerini oluşturmak için kullanabilirsiniz. Aşağıdaki örnek, projeyi yeniden oluşturur `NotInSolutionFolder` ve `InSolutionFolder` `NewFolder` çözüm klasöründeki projeyi temizler.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Ortak MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
