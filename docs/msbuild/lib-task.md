---
title: LIB Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: a5794d059a17f39531a7788895b604ae0e9590ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633596"
---
# <a name="lib-task"></a>LIB görevi

Microsoft 32-Bit Library Manager aracını sarar, *lib.exe*. Kitaplık Yöneticisi, Ortak Nesne Dosya Biçimi (COFF) nesne dosyaları kitaplığını oluşturur ve yönetir. Kitaplık Yöneticisi ayrıca dışa aktarılan tanımlara başvurmak için dışa aktarma dosyaları oluşturabilir ve kitaplıklar içe aktarabilir. Daha fazla bilgi için [LIB başvurusu](/cpp/build/reference/lib-reference) ve [Running LIB'e](/cpp/build/reference/running-lib)bakın.

## <a name="parameters"></a>Parametreler

 Aşağıdaki **tabloda LIB** görevinin parametreleri açıklanmaktadır. Görev parametrelerinin çoğu komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**Ek Bağımlılıklar**|İsteğe bağlı **String[]** parametresi.<br /><br /> Komut satırına eklenecek ek öğeler belirtir.|
|**EkKütüphaneDirectories**|İsteğe bağlı **String[]** parametresi.<br /><br /> Çevre kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.<br /><br /> Daha fazla bilgi için bkz: [/LIBPATH (Ek Libpath).](/cpp/build/reference/libpath-additional-libpath)|
|**Ek Seçenekler**|İsteğe bağlı **String** parametresi.<br /><br /> Komut satırında belirtildiği gibi *lib.exe* seçeneklerinin listesi. Örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir **LIB** görev parametresi tarafından temsil edilmeyen *lib.exe* seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [Bkz. Running LIB.](/cpp/build/reference/running-lib)|
|**Görüntülü Kütüphane**|İsteğe bağlı **String** parametresi.<br /><br /> Çıktı kitaplığı hakkındaki bilgileri görüntüler. Bilgileri bir dosyaya yönlendirmek için bir dosya adı belirtin. Bilgileri konsola yönlendirmek için "CON" veya hiçbir şey belirtin.<br /><br /> Bu parametre *lib.exe* **/LIST** seçeneğine karşılık gelir.|
|**Hata Raporlama**|İsteğe bağlı **String** parametresi.<br /><br /> *lib.exe* çalışma zamanında başarısız olursa, microsoft'a iç hata bilgilerinin nasıl gönderilecek olduğunu belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **NoErrorReport** - **/ERRORREPORT:NONE**<br />-   **Hemen İste** - **/ERRORREPORT:PROMPT**<br />-   **QueueForNextLogin** - **/ERRORREPORT:QUEUE**<br />-   **SendErrorReport** - **/ERRORREPORT:SEND**<br /><br /> Daha fazla bilgi [için, Running LIB'deki](/cpp/build/reference/running-lib) **/ERRORREPORT** komut satırı seçeneğine bakın.|
|**İhracatAdLandırılmış Fonksiyonlar**|İsteğe bağlı **String[]** parametresi.<br /><br /> Dışa aktarmak için bir veya daha fazla işlevi belirtir.<br /><br /> Bu parametre **/EXPORT'** a karşılık gelir: *lib.exe*seçeneği.|
|**ForceSymbolReferences**|İsteğe bağlı **String** parametresi.<br /><br /> *Lib.exe'yi* belirtilen sembole bir referans eklemeye zorlar.<br /><br /> Bu parametre **/INCLUDE:** *lib.exe*seçeneğine karşılık gelir.|
|**Varsayılan Kitaplıkları Yok Sayma**|İsteğe bağlı `Boolean` parametre.<br /><br /> Harici `true`başvuruları çözdüğünde *lib.exe'nin* aradığı kitaplıklar listesinden tüm varsayılan kitaplıkları kaldırırsa.<br /><br /> Bu parametre *lib.exe* **/NODEFAULTLIB** seçeneğinin parametresiz formuna karşılık gelir.|
|**Varsayılan Varsayılan Kitaplıkları YokSay**|İsteğe bağlı **String[]** parametresi.<br /><br /> Belirtilen kitaplıkları, harici başvuruları çözdüğünde *aradığı kitaplıklar* listesinden kaldırır.<br /><br /> Bu parametre, bir `library` bağımsız değişken alan *lib.exe/NODEFAULTLIB* seçeneğine karşılık gelir. **/NODEFAULTLIB**|
|**LinkLibraryBağımlılıklar**|İsteğe bağlı `Boolean` parametre.<br /><br /> Proje `true`bağımlılıklarından kitaplık çıktılarının otomatik olarak bağlandığını belirtirse.|
|**LinkTimeCodeGeneration**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`bağlantı zamanı kodu oluşturma belirtir.<br /><br /> Bu parametre *lib.exe* **/LCTG** seçeneğine karşılık gelir.|
|**Minimum Gerekli Sürüm**|İsteğe bağlı **String** parametresi.<br /><br /> Alt sistemin en az gerekli sürümünü belirtir. 0 ile 65535 aralığındaki ondalık sayıların virgülle sınırlandırılmış bir listesini belirtin.|
|**ModülTanımDosyası**|İsteğe bağlı **String** parametresi.<br /><br /> Modül tanımlı dosyanın adını belirtir (*.def*).<br /><br /> Bu parametre, bir `filename` bağımsız değişken alan *lib.exe'nin* **/DEF** seçeneğine karşılık gelir.|
|**Adı**|İsteğe bağlı **String** parametresi.<br /><br /> Bir alma kitaplığı oluşturulduğunda, içe aktarma kitaplığı için inşa edilen DLL'nin adını belirtir.<br /><br /> Bu parametre, bir `filename` bağımsız değişken alan *lib.exe'nin* **/NAME** seçeneğine karşılık gelir.|
|**Outputfile**|İsteğe bağlı **String** parametresi.<br /><br /> *lib.exe'nin* oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar.<br /><br /> Bu parametre, bir `filename` bağımsız değişken alan *lib.exe/OUT* seçeneğine karşılık gelir. **/OUT**|
|**Nesneleri Kaldırma**|İsteğe bağlı **String[]** parametresi.<br /><br /> Belirtilen nesneyi çıkış kitaplığından atlar. *Lib.exe,* tüm nesneleri (nesne dosyalarında veya kitaplıklarda) birleştirerek ve bu seçenek tarafından belirtilen nesneleri silerek bir çıktı kitaplığı oluşturur.<br /><br /> Bu parametre, bir `membername` bağımsız değişken alan *lib.exe/REMOVE* seçeneğine karşılık gelir. **/REMOVE**|
|**Kaynak**|Gerekli `ITaskItem[]` parametre.<br /><br /> Boşluklara göre ayrılmış kaynak dosyaların listesini belirtir.|
|**Alt**|İsteğe bağlı **String** parametresi.<br /><br /> Çalıştırılabilir için ortamı belirtir. Alt sistem seçimi giriş noktası simgesini veya giriş noktası işlevini etkiler.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **Konsol** - **/ALT SİsteM:KONSOL**<br />-   **Windows** - **/ALT SİsteM:WINDOWS**<br />-   **Yerel** - **/ALT SİsteM:YEREL**<br />-   **EFI Uygulama** - **/ALT SİsteM:EFI_APPLICATION**<br />-   **EFI Önyükleme Hizmeti Sürücüsü** - **/ALT SİsteM:EFI_BOOT_SERVICE_DRIVER**<br />-   **EFI ROM** - **/ALT SİsteM:EFI_ROM**<br />-   **EFI Çalışma Süresi** - **/ALT SİsteM:EFI_RUNTIME_DRIVER**<br />-   **WindowsCE** - **/ALT SİsteM:WINDOWSCE**<br />-   **POSIX** - **/ALT SISTEM:POSIX**<br /><br /> Daha fazla bilgi için bkz: [/SUBSYSTEM (Alt sistemi belirtin)](/cpp/build/reference/subsystem-specify-subsystem).|
|**BastırmaBaşlangıç Banner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi [için, Running LIB'deki](/cpp/build/reference/running-lib) **/NOLOGO** seçeneğine bakın.|
|**Hedef Makine**|İsteğe bağlı **String** parametresi.<br /><br /> Program veya DLL için hedef platformu belirtir.<br /><br /> Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.<br /><br /> -   **MachineARM** - **/MACHINE:ARM**<br />-   **MachineEBC** - **/MACHINE:EBC**<br />-   **MachineIA64** - **/MACHINE:IA64**<br />-   **MachineMIPS** - **/MACHINE:MIPS**<br />-   **MachineMIPS16** - **/MACHINE:MIPS16**<br />-   **MachineMIPSFPU** -**/MACHINE:MIPSFPU**<br />-   **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**<br />-   **MachineSH4** - **/MACHINE:SH4**<br />-   **MachineTHUMB** - **/MACHINE:THUMB**<br />-   **MachineX64** - **/MACHINE:X64**<br />-   **MachineX86** - **/MACHINE:X86**<br /><br /> Daha fazla bilgi için bkz: [/MACHINE (Hedef platformu belirtin)](/cpp/build/reference/machine-specify-target-platform).|
|**TrackerLogDirectory**|İsteğe bağlı **String** parametresi.<br /><br /> İzleyici günlüğünün dizinini belirtir.|
|**TreatLibWarningasErrors**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true` *Lib.exe* bir uyarı oluşturursa, **LIB** görevinin çıktı dosyası oluşturmamalarına neden oluyorsa. , `false`bir çıktı dosyası oluşturulursa.<br /><br /> Daha fazla bilgi [için, Running LIB'deki](/cpp/build/reference/running-lib) **/WX** seçeneğine bakın.|
|**UseUnicodeResponseFiles**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer `true`, kütüphaneci yumurtladığında UNICODE yanıt dosyaları oluşturmak için proje sistemi talimat verir. Projedeki dosyaların UNICODE yolları ne zaman olduğunu belirtin. `true`|
|**Ayrıntılı**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Oturumdaki ilerlemeyle ilgili ayrıntıları görüntülerse; `true` bu eklenen *.obj* dosyalarının adlarını içerir. Bilgiler standart çıktıya gönderilir ve bir dosyaya yönlendirilebilir.<br /><br /> Daha fazla bilgi [için, Running LIB'deki](/cpp/build/reference/running-lib) **/VERBOSE** seçeneğine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)