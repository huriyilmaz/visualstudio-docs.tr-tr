---
title: LıB görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.Name
- VC.Project.VCLibrarianTool.TreatLibWarningsAsErrors
- VC.Project.VCLibrarianTool.Verbose
- vc.task.lib
- VC.Project.VCLibrarianTool.ErrorReporting
- VC.Project.VCLibrarianTool.LinkLibraryDependencies
- VC.Project.VCLibrarianTool.LinkTimeCodeGeneration
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), LIB task
- LIB task (MSBuild (C++))
ms.assetid: e062c7f9-cc69-4a83-9361-1bb5355e5fe8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9daeb5264a4bebb67cfd486a5f05708d7e025f3
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578532"
---
# <a name="lib-task"></a>LIB görevi
Microsoft 32-bit kitaplık Yöneticisi aracını, *lib. exe*' yi kaydırır. Kitaplık Yöneticisi ortak nesne dosyası biçimi (COFF) nesne dosyaları kitaplığını oluşturur ve yönetir. Kitaplık Yöneticisi ayrıca dışarı aktarma dosyaları oluşturabilir ve dışarı aktarılan tanımlara başvuru için kitaplıkları içeri aktarabilir. Daha fazla bilgi için bkz. [LIB Reference](/cpp/build/reference/lib-reference) ve [LIB çalışıyor](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda **LIB** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi bir komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalDependencies**|İsteğe bağlı **dize []** parametresi.<br /><br /> Komut satırına eklenecek ek öğeleri belirtir.|
|**Additionallibrarydizinler**|İsteğe bağlı **dize []** parametresi.<br /><br /> Ortam kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.<br /><br /> Daha fazla bilgi için bkz. [/LIBPATH (ek libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen *lib. exe* seçeneklerinin listesi. Örneğin,/\<Seçenek1 >/\<Seçenek2 >/\<Seçenek # >. Başka bir **LIB** Task parametresi tarafından temsil edilmeyen *LIB. exe* seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bkz. [LIB çalıştırma](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıktı kitaplığıyla ilgili bilgileri görüntüler. Bilgileri bir dosyaya yönlendirmek için bir dosya adı belirtin. Bilgileri konsola yeniden yönlendirebilmek için "CON" veya Nothing değerini belirtin.<br /><br /> Bu parametre *lib. exe*' nin **/list** seçeneğine karşılık gelir.|
|**ErrorReporting**|İsteğe bağlı **dize** parametresi.<br /><br /> Çalışma zamanında *lib. exe* başarısız olursa, Microsoft 'a nasıl iç hata bilgileri gönderileceğini belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Noerrorreport** -  **/errorreport: None**<br />-   **hemen sor** -  **/errorreport: Prompt**<br />-   **Queuefornextlogin** -  **/errorreport: Queue**<br />-   **Senderrorreport** -  **/errorreport: Send**<br /><br /> Daha fazla bilgi için bkz. [LIB](/cpp/build/reference/running-lib) **Report** komut satırı seçeneği.|
|**ExportNamedFunctions**|İsteğe bağlı **dize []** parametresi.<br /><br /> Dışarı aktarılacak bir veya daha fazla işlevi belirtir.<br /><br /> Bu parametre, *lib. exe*' nin **/Export:** seçeneğine karşılık gelir.|
|**Forcesyımbolreferences**|İsteğe bağlı **dize** parametresi.<br /><br /> *Lib. exe* ' yi belirtilen simgeye bir başvuru içerecek şekilde zorlar.<br /><br /> Bu parametre, *lib. exe*' nin **/include:** seçeneğine karşılık gelir.|
|**IgnoreAllDefaultLibraries**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, dış başvuruları çözümlediğinde *lib. exe* ' nin aradığı kitaplık listesinden tüm varsayılan kitaplıkları kaldırır.<br /><br /> Bu parametre, *lib. exe*' nin **/nodefaultlib** seçeneğinin parametre-Less biçimine karşılık gelir.|
|**IgnoreSpecificDefaultLibraries**|İsteğe bağlı **dize []** parametresi.<br /><br /> Dış başvuruları çözümlediğinde *lib. exe* ' nin aradığı kitaplık listesinden belirtilen kitaplıkları kaldırır.<br /><br /> Bu parametre, `library` bir bağımsız değişken alan *lib. exe* ' nin **/nodefaultlib** seçeneğine karşılık gelir.|
|**LinkLibraryDependencies**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, proje bağımlılıklarındaki kitaplık çıktılarının otomatik olarak bağlandığını belirtir.|
|**LinkTimeCodeGeneration**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, bağlantı zamanı kod oluşturmayı belirtir.<br /><br /> Bu parametre *lib. exe*' nin **/LCTG** seçeneğine karşılık gelir.|
|**MinimumRequiredVersion**|İsteğe bağlı **dize** parametresi.<br /><br /> Alt sistemin gerekli en düşük sürümünü belirtir. 0 ile 65535 arasında ondalık sayıların virgülle ayrılmış bir listesini belirtin.|
|**ModuleDefinitionFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Modül tanım dosyasının ( *. def*) adını belirtir.<br /><br /> Bu parametre, `filename` bir bağımsız değişken alan *lib. exe* ' nin **/def** seçeneğine karşılık gelir.|
|**Adı**|İsteğe bağlı **dize** parametresi.<br /><br /> İçeri aktarma kitaplığı oluşturulduğunda, içeri aktarma kitaplığının oluşturulduğu DLL 'in adını belirtir.<br /><br /> Bu parametre, `filename` bir bağımsız değişken alan *lib. exe* ' nin **/Name** seçeneğine karşılık gelir.|
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> *Lib. exe* ' nin oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar.<br /><br /> Bu parametre, `filename` bir bağımsız değişken alan *lib. exe* ' nin **/Out** seçeneğine karşılık gelir.|
|**RemoveObjects**|İsteğe bağlı **dize []** parametresi.<br /><br /> Çıkış kitaplığından belirtilen nesneyi atlar. *Lib. exe* , tüm nesneleri birleştirerek (nesne dosyalarında veya kitaplıklarda) ve ardından bu seçenekle belirtilen tüm nesneleri silerek bir çıktı kitaplığı oluşturur.<br /><br /> Bu parametre, `membername` bir bağımsız değişken alan *LIB. exe* ' nin **/Remove** seçeneğine karşılık gelir.|
|**Ğına**|Gerekli `ITaskItem[]` parametresi.<br /><br /> Boşluklarla ayrılmış kaynak dosyalarının bir listesini belirtir.|
|**Sistemin**|İsteğe bağlı **dize** parametresi.<br /><br /> Yürütülebilir dosyanın ortamını belirtir. Alt sistem seçimi, giriş noktası sembolünü veya giriş noktası işlevini etkiler.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **konsol** -  **/Subsystem: Console**<br />-   **windows** -  **/Subsystem: Windows**<br />-   **native** -  **/Subsystem: Native**<br />-   **EFI uygulaması** -  **/subsystem: EFI_APPLICATION**<br />-   **EFI Önyükleme hizmeti sürücüsü** -  **/subsystem: EFI_BOOT_SERVICE_DRIVER**<br />-   **EFı ROM** -  **/subsystem: EFI_ROM**<br />-   **EFI çalışma zamanı** -  **/subsystem: EFI_RUNTIME_DRIVER**<br />-   **windowsce** -  **/Subsystem: WindowsCE**<br />-   **posıx** -  **/Subsystem: POSIX**<br /><br /> Daha fazla bilgi için bkz. [/Subsystem (alt sistemi belirt)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [LIB çalışma](/cpp/build/reference/running-lib)konumundaki **/nologo** seçeneğine bakın.|
|**TargetMachine**|İsteğe bağlı **dize** parametresi.<br /><br /> Program veya DLL için hedef platformu belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Machineard** -  **/MACHINE: ARM**<br />-   **machineebc** -  **/MACHINE: EBC**<br />-   **MachineIA64** -  **/MACHINE: IA64**<br />-   **Machinemıps** -  **/MACHINE: MIPS**<br />-   **MachineMIPS16** -  **/MACHINE: kayıtlardan biri mıps16**<br />-   **Machinemıpsfpu** - **/Machine: mıpsfpu**<br />-   **MachineMIPSFPU16** -  **/MACHINE: MIPSFPU16**<br />-   **MachineSH4** -  **/MACHINE: sh4**<br />-   **machinethumb** -  **/MACHıNE: Thumb**<br />-   **MachineX64** -  **/Machine: x64**<br />-   **MachineX86** -  **/Machine: x86**<br /><br /> Daha fazla bilgi için bkz. [/Machine (hedef platformu belirt)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğünün dizinini belirtir.|
|**TreatLibWarningAsErrors**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, lib *. exe* bir uyarı oluşturursa **LIB** görevinin çıkış dosyası oluşturmamasına neden olur. `false`, bir çıkış dosyası oluşturulur.<br /><br /> Daha fazla bilgi için [LIB çalışma](/cpp/build/reference/running-lib)konumundaki **/WX** seçeneğine bakın.|
|**UseUnicodeResponseFiles**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, kütüphaneian oluşturulduğunda proje sistemine UNICODE yanıt dosyaları üretmesini söyler. Projedeki dosyaların UNICODE yolları olduğunda `true` belirtin.|
|**Seçeneini**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, oturum ilerlemesiyle ilgili ayrıntıları görüntüler; Bu, eklenmekte olan *. obj* dosyalarının adlarını içerir. Bilgiler standart çıktıya gönderilir ve bir dosyaya yönlendirilebilir.<br /><br /> Daha fazla bilgi için [LIB çalışma](/cpp/build/reference/running-lib)içindeki **/verbose** seçeneğine bakın.|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)