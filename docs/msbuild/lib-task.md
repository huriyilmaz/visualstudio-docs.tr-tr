---
title: LıB görevi | Microsoft Docs
description: MSBuild 'in, bir COFF nesne dosyaları kitaplığı oluşturup yöneten, lib.exe Microsoft 32-bit Kitaplığı Yöneticisi aracını kaydırmak için LIB görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3bf1029d42ce40d33e6eea1fcbe5e6434ff85a36
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904444"
---
# <a name="lib-task"></a>LIB görevi

Microsoft 32-bit Kitaplığı Yöneticisi aracı 'nı sarmalayan *lib.exe* . Kitaplık Yöneticisi ortak nesne dosyası biçimi (COFF) nesne dosyaları kitaplığını oluşturur ve yönetir. Kitaplık Yöneticisi ayrıca dışarı aktarma dosyaları oluşturabilir ve dışarı aktarılan tanımlara başvuru için kitaplıkları içeri aktarabilir. Daha fazla bilgi için bkz. [LIB Reference](/cpp/build/reference/lib-reference) ve [LIB çalışıyor](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **LIB** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi bir komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalDependencies**|İsteğe bağlı **dize []** parametresi.<br /><br /> Komut satırına eklenecek ek öğeleri belirtir.|
|**Additionallibrarydizinler**|İsteğe bağlı **dize []** parametresi.<br /><br /> Ortam kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.<br /><br /> Daha fazla bilgi için bkz. [/LIBPATH (ek libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen *lib.exe* seçeneklerinin bir listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Başka bir **LIB** Task parametresi tarafından temsil edilmeyen *lib.exe* seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bkz. [LIB çalıştırma](/cpp/build/reference/running-lib).|
|**DisplayLibrary**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıktı kitaplığıyla ilgili bilgileri görüntüler. Bilgileri bir dosyaya yönlendirmek için bir dosya adı belirtin. Bilgileri konsola yeniden yönlendirebilmek için "CON" veya Nothing değerini belirtin.<br /><br /> Bu parametre, *lib.exe* **/list** seçeneğine karşılık gelir.|
|**ErrorReporting**|İsteğe bağlı **dize** parametresi.<br /><br /> Çalışma zamanında *lib.exe* başarısız olursa, Microsoft 'a nasıl iç hata bilgileri gönderileceğini belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Noerrorreport**  -  **/errorreport: yok**<br />-   **Hemen sor**  -  **/errorreport: Prompt**<br />-   **Queuefornextlogin**  -  **/errorreport: kuyruk**<br />-   **Senderrorreport**  -  **/errorreport: gönder**<br /><br /> Daha fazla bilgi için bkz. [LIB](/cpp/build/reference/running-lib) **Report** komut satırı seçeneği.|
|**ExportNamedFunctions**|İsteğe bağlı **dize []** parametresi.<br /><br /> Dışarı aktarılacak bir veya daha fazla işlevi belirtir.<br /><br /> Bu parametre, *lib.exe* **/Export:** seçeneğine karşılık gelir.|
|**Forcesyımbolreferences**|İsteğe bağlı **dize** parametresi.<br /><br /> *lib.exe* , belirtilen simgeye bir başvuru içermesini zorlar.<br /><br /> Bu parametre, *lib.exe* **/include:** seçeneğine karşılık gelir.|
|**IgnoreAllDefaultLibraries**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , dış başvuruları çözümlediğinde *lib.exe* aradığı kitaplıklar listesinden tüm varsayılan kitaplıkları kaldırır.<br /><br /> Bu parametre, *lib.exe* **/nodefaultlib** seçeneğinin parametre-Less biçimine karşılık gelir.|
|**IgnoreSpecificDefaultLibraries**|İsteğe bağlı **dize []** parametresi.<br /><br /> Dış başvuruları çözümlerken, *lib.exe* aradığı kitaplıklar listesinden belirtilen kitaplıkları kaldırır.<br /><br /> Bu parametre bir bağımsız değişken alan *lib.exe* **/nodefaultlib** seçeneğine karşılık gelir `library` .|
|**LinkLibraryDependencies**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , proje bağımlılıklarından kitaplık çıktılarının otomatik olarak bağlandığını belirtir.|
|**LinkTimeCodeGeneration**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , bağlantı zamanı kod oluşturmayı belirtir.<br /><br /> Bu parametre, *lib.exe* **/LCTG** seçeneğine karşılık gelir.|
|**MinimumRequiredVersion**|İsteğe bağlı **dize** parametresi.<br /><br /> Alt sistemin gerekli en düşük sürümünü belirtir. 0 ile 65535 arasında ondalık sayıların virgülle ayrılmış bir listesini belirtin.|
|**ModuleDefinitionFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Modül tanım dosyasının ( *. def* ) adını belirtir.<br /><br /> Bu parametre, bir bağımsız değişken alan *lib.exe* **/def** seçeneğine karşılık gelir `filename` .|
|**Ad**|İsteğe bağlı **dize** parametresi.<br /><br /> İçeri aktarma kitaplığı oluşturulduğunda, içeri aktarma kitaplığının oluşturulduğu DLL 'in adını belirtir.<br /><br /> Bu parametre, bağımsız değişken alan *lib.exe* **/Name** seçeneğine karşılık gelir `filename` .|
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> *lib.exe* oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar.<br /><br /> Bu parametre, bir bağımsız değişken alan *lib.exe* **/Out** seçeneğine karşılık gelir `filename` .|
|**RemoveObjects**|İsteğe bağlı **dize []** parametresi.<br /><br /> Çıkış kitaplığından belirtilen nesneyi atlar. *Lib.exe* , tüm nesneleri birleştirerek (nesne dosyalarında veya kitaplıklarda) ve ardından bu seçenekle belirtilen tüm nesneleri silerek bir çıktı kitaplığı oluşturur.<br /><br /> Bu parametre, bir bağımsız değişken alan *lib.exe* **/Remove** seçeneğine karşılık gelir `membername` .|
|**Ğına**|Gerekli `ITaskItem[]` parametre.<br /><br /> Boşluklarla ayrılmış kaynak dosyalarının bir listesini belirtir.|
|**Sistemin**|İsteğe bağlı **dize** parametresi.<br /><br /> Yürütülebilir dosyanın ortamını belirtir. Alt sistem seçimi, giriş noktası sembolünü veya giriş noktası işlevini etkiler.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Konsol**  -  **/Subsystem: Console**<br />-   **Windows**  -  **/Subsystem: WINDOWS**<br />-   **Yerel**  -  **/Subsystem: NATIVE**<br />-   **EFI uygulaması**  -  **/Subsystem: EFI_APPLICATION**<br />-   **EFI Önyükleme hizmeti sürücüsü**  -  **/Subsystem: EFI_BOOT_SERVICE_DRIVER**<br />-   **EFı ROM**  -  **/Subsystem: EFI_ROM**<br />-   **EFI çalışma zamanı**  -  **/Subsystem: EFI_RUNTIME_DRIVER**<br />-   **WindowsCE**  -  **/Subsystem: WINDOWSCE**<br />-   **POSIX**  -  **/Subsystem: POSIX**<br /><br /> Daha fazla bilgi için bkz. [/Subsystem (alt sistemi belirt)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [LIB çalışma](/cpp/build/reference/running-lib)konumundaki **/nologo** seçeneğine bakın.|
|**TargetMachine**|İsteğe bağlı **dize** parametresi.<br /><br /> Program veya DLL için hedef platformu belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Machineard**  -  **/Machine: ARM**<br />-   **Machineebc**  -  **/Machine: EBC**<br />-   **MachineIA64**  -  **/MACHINE: IA64**<br />-   **Machinemıps**  -  **/MACHINE: MIPS**<br />-   **MachineMIPS16**  -  **/MACHINE: kayıtlardan biri mıps16**<br />-   **Machinemıpsfpu**  - **/MACHINE: MIPSFPU**<br />-   **MachineMIPSFPU16**  -  **/MACHINE: MIPSFPU16**<br />-   **MachineSH4**  -  **/MACHINE: sh4**<br />-   **Machinethumb**  -  **/MACHINE: Thumb**<br />-   **MachineX64**  -  **/Machine: x64**<br />-   **MachineX86**  -  **/Machine: x86**<br /><br /> Daha fazla bilgi için bkz. [/Machine (hedef platformu belirt)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğünün dizinini belirtir.|
|**TreatLibWarningAsErrors**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , *lib.exe* bir uyarı oluşturursa **LIB** görevinin çıkış dosyası oluşturmamasına neden olur. İse `false` , bir çıkış dosyası oluşturulur.<br /><br /> Daha fazla bilgi için [LIB çalışma](/cpp/build/reference/running-lib)konumundaki **/WX** seçeneğine bakın.|
|**UseUnicodeResponseFiles**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , kütüphaneian oluşturulduğunda proje SISTEMINE UNICODE yanıt dosyaları oluşturmasını söyler. `true`Projedeki dosyaların ne zaman UNICODE yolları olduğunu belirtin.|
|**Seçeneini**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, Oturum ilerlemesiyle ilgili ayrıntıları görüntüler; bu, eklenmekte olan *. obj* dosyalarının adlarını içerir. Bilgiler standart çıktıya gönderilir ve bir dosyaya yönlendirilebilir.<br /><br /> Daha fazla bilgi için [LIB çalışma](/cpp/build/reference/running-lib)içindeki **/verbose** seçeneğine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)