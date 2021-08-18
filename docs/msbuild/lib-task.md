---
title: LIB Görev | Microsoft Docs
description: COFF MSBuild kitaplığını oluşturan ve yöneten Microsoft 32 bit Kitaplık Yöneticisi aracını sarmak için LIB görevini nasıl kullandığını lib.exe öğrenin.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 8b0f7f475b8226630133fa6c4617c7c3c4fe8060
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143176"
---
# <a name="lib-task"></a>LIB görevi

Microsoft 32 Bit Kitaplık Yöneticisi aracını sarmalar ve *lib.exe.* Kitaplık Yöneticisi, Ortak Nesne Dosya Biçimi (COFF) nesne dosyalarının bir kitaplığını oluşturur ve yönetir. Kitaplık Yöneticisi, dışarı aktarıldı tanımlara başvuru yapmak için dışarı aktarma dosyaları ve içeri aktarma kitaplıkları da oluşturabilir. Daha fazla bilgi için, [bkz. LIB başvurusu](/cpp/build/reference/lib-reference) ve [Running LIB](/cpp/build/reference/running-lib).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **LIB** görevinin parametreleri açık almaktadır. Çoğu görev parametresi bir komut satırı seçeneğine karşılık gelen bir komut satırı seçeneğidir.

|Parametre|Açıklama|
|---------------|-----------------|
|**Ek Bağımlılıklar**|İsteğe **bağlı String[]** parametresi.<br /><br /> Komut satırına eklenecek ek öğeleri belirtir.|
|**AdditionalLibraryDirectories**|İsteğe **bağlı String[]** parametresi.<br /><br /> Ortam kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.<br /><br /> Daha fazla bilgi için bkz. [/LIBPATH (Ek Libpath)](/cpp/build/reference/libpath-additional-libpath).|
|**AdditionalOptions**|İsteğe **bağlı Dize** parametresi.<br /><br /> Komut *lib.exe* seçenekleri listesi. Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir LIB *görevlib.exe* temsil etmeyen farklı seçenekler belirtmek için **bu parametreyi** kullanın.<br /><br /> Daha fazla bilgi için [bkz. LIB Çalıştırma.](/cpp/build/reference/running-lib)|
|**DisplayLibrary**|İsteğe **bağlı Dize** parametresi.<br /><br /> Çıkış kitaplığıyla ilgili bilgileri görüntüler. Bilgileri bir dosyaya yönlendirmek için bir dosya adı belirtin. Bilgileri konsola yönlendirmek için "CON" veya hiçbir şey belirtme.<br /><br /> Bu parametre, parametresinin **/LIST** *seçeneğinelib.exe.*|
|**ErrorReporting**|İsteğe **bağlı Dize** parametresi.<br /><br /> Çalışma zamanında başarısız olursa Microsoft'a iç hata *lib.exe* nasıl gönder) olduğunu belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **NoErrorReport**  -  **/ERRORREPORT:NONE**<br />-   **PromptImmediately**  -  **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin**  -  **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport**  -  **/ERRORREPORT:SEND**<br /><br /> Daha fazla bilgi için LIB **Çalıştırma'da /ERRORREPORT** komut [satırı seçeneğine bakın.](/cpp/build/reference/running-lib)|
|**ExportNamedFunctions**|İsteğe **bağlı String[]** parametresi.<br /><br /> Dışarı aktarıla bir veya daha fazla işlev belirtir.<br /><br /> Bu parametre , **/EXPORT:** seçeneğine karşılık *lib.exe.*|
|**ForceSymbolReferences**|İsteğe **bağlı Dize** parametresi.<br /><br /> Bu *lib.exe* belirtilen sembole bir başvuru eklemek üzere güçler.<br /><br /> Bu parametre , **/INCLUDE:** seçeneğine karşılık *lib.exe.*|
|**IgnoreAllDefaultLibraries**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` dış başvuruları çözümleyelib.exekitaplıklar listesinden tüm varsayılan kitaplıkları kaldırır. <br /><br /> Bu parametre, parametresinin **/NODEFAULTLIB** seçeneğinin parametresiz biçimine *karşılıklib.exe.*|
|**IgnoreSpecificDefaultLibraries**|İsteğe **bağlı String[]** parametresi.<br /><br /> Belirtilen kitaplıkları, dış başvuruları *çözümleyelib.exe* kitaplıklar listesinden kaldırır.<br /><br /> Bu parametre, bağımsız değişken alanlib.exe **/NODEFAULTLIB** *seçeneğine* `library` karşılık geldi.|
|**LinkLibraryDependencies**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` proje bağımlılıklarından kitaplık çıkışların otomatik olarak içinde bağlanacaklarını belirtir.|
|**LinkTimeCodeGeneration**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` bağlantı zamanı kod oluşturma belirtir.<br /><br /> Bu parametre, parametresinin **/LCTG** seçeneğine *lib.exe.*|
|**MinimumRequiredVersion**|İsteğe **bağlı Dize** parametresi.<br /><br /> Alt sistemin gereken en düşük sürümünü belirtir. 0 ile 65535 aralığındaki ondalık sayıların virgülle ayrılmış listesini belirtin.|
|**ModuleDefinitionFile**|İsteğe **bağlı Dize** parametresi.<br /><br /> Modül tanımı dosyasının adını belirtir (*.def*).<br /><br /> Bu parametre, bağımsız değişken alanlib.exe **/DEF** *seçeneğine* karşılık `filename` geldi.|
|**Ad**|İsteğe **bağlı Dize** parametresi.<br /><br /> Bir içeri aktarma kitaplığı yerleşik olduğunda, içeri aktarma kitaplığının içinde yer alan DLL'nin adını belirtir.<br /><br /> Bu parametre, bağımsız değişken alanlib.exe **/NAME** *seçeneğine* karşılık `filename` geldi.|
|**Outputfile**|İsteğe **bağlı Dize** parametresi.<br /><br /> Varsayılan adı ve oluşturduğu programın konumunu *lib.exe* geçersiz kılar.<br /><br /> Bu parametre, bağımsız değişken alanlib.exe **/OUT** *seçeneğine* karşılık `filename` geldi.|
|**RemoveObjects**|İsteğe **bağlı String[]** parametresi.<br /><br /> Belirtilen nesneyi çıkış kitaplığından atlar. *Lib.exe* nesneleri birleştirerek (ister nesne dosyalarında ister kitaplıklarda) ve ardından bu seçenek tarafından belirtilen nesneleri silerek bir çıkış kitaplığı oluşturur.<br /><br /> Bu parametre, bağımsız değişken alanlib.exe **/REMOVE** *seçeneğine* `membername` karşılık geldi.|
|**Kaynaklar**|Gerekli `ITaskItem[]` parametre.<br /><br /> Boşluklarla ayrılmış kaynak dosyaların listesini belirtir.|
|**Alt**|İsteğe **bağlı Dize** parametresi.<br /><br /> Yürütülebilir dosyanın ortamını belirtir. Alt sistem seçimi, giriş noktası sembolünü veya giriş noktası işlevini etkiler.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Konsol**  -  **/SUBSYSTEM:CONSOLE**<br />-   **Windows**  -  **/SUBSYSTEM:WINDOWS**<br />-   **Yerel**  -  **/SUBSYSTEM:NATIVE**<br />-   **EFI Uygulaması**  -  **/SUBSYSTEM:EFI_APPLICATION**<br />-   **EFI Önyükleme Hizmeti Sürücüsü**  -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM**  -  **/SUBSYSTEM:EFI_ROM**<br />-   **EFI Çalışma Zamanı**  -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE**  -  **/SUBSYSTEM:WINDOWSCE**<br />-   **POSIX**  -  **/SUBSYSTEM:POSIX**<br /><br /> Daha fazla bilgi için bkz. [/SUBSYSTEM (Alt sistemi belirtin)](/cpp/build/reference/subsystem-specify-subsystem).|
|**SuppressStartupBanner**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için LIB **Çalıştırma'da /NOLOGO** [seçeneğine bakın.](/cpp/build/reference/running-lib)|
|**TargetMachine**|İsteğe **bağlı Dize** parametresi.<br /><br /> Program veya DLL için hedef platformu belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **MachineARM**  -  **/MACHINE:ARM**<br />-   **MachineEBC**  -  **/MACHINE:EBC**<br />-   **MachineIA64**  -  **/MACHINE:IA64**<br />-   **MachineMIPS**  -  **/MACHINE:MIPS**<br />-   **MachineMIPS16**  -  **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU**  - **/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16**  -  **/MACHINE:MIPSFPU16**<br />-   **MachineSH4**  -  **/MACHINE:SH4**<br />-   **MachineTHUMB**  -  **/MACHINE:THUMB**<br />-   **MachineX64**  -  **/MACHINE:X64**<br />-   **MachineX86**  -  **/MACHINE:X86**<br /><br /> Daha fazla bilgi için bkz. [/MACHINE (Hedef platformu belirtin)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|İsteğe **bağlı Dize** parametresi.<br /><br /> İzleyici günlüğünün dizinini belirtir.|
|**TreatLibWarningAsErrors**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` bir **uyarı oluşturursa LIB** görevinin bir çıkış *dosyasılib.exe* neden olur. ise, `false` bir çıkış dosyası oluşturulur.<br /><br /> Daha fazla bilgi için LIB **Çalıştırma'da /WX** [seçeneğine bakın.](/cpp/build/reference/running-lib)|
|**UseUnicodeResponseFiles**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` libraryan üretiken proje sistemine UNICODE yanıt dosyaları oluşturma talimatı sağlar. Proje `true` dosyalarında UNICODE yolları olduğunda belirtin.|
|**Ayrıntılı**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` oturumun ilerleme durumuyla ilgili ayrıntıları görüntüler; buna eklenen *.obj dosyalarının* adları da dahildir. Bilgiler standart çıkışa gönderilir ve bir dosyaya yeniden yönlendirebilirsiniz.<br /><br /> Daha fazla bilgi için LIB **Çalıştırma'daki /VERBOSE** [seçeneğine bakın.](/cpp/build/reference/running-lib)|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)