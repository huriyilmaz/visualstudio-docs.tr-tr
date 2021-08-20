---
title: MIDL Görev | Microsoft Docs
description: Microsoft Arabirim Tanımlama Dili (MIDL) derleyici aracını sarmalayıcı olan MSBuild MIDL görevi hakkında bilgi midl.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), MIDL task
- MIDL task (MSBuild (C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 89d9469c2e81572f66a70b5f61881b4baa9fde68
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108674"
---
# <a name="midl-task"></a>MIDL görevi

Microsoft Arabirim Tanımlama Dili (MIDL) derleyici aracını *sarmalarmidl.exe.* Daha fazla bilgi için bkz. [MIDL komut satırı başvurusu.](/windows/desktop/Midl/midl-command-line-reference)

## <a name="parameters"></a>Parametreler

 Aşağıda **MIDL** görevinin parametreleri açık almaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelen bir seçenektir.

- **AdditionalIncludeDirectories**

     İsteğe **bağlı String[]** parametresi.

     İçe aktarılan IDL dosyaları, dahil edilen üst bilgi dosyaları ve uygulama yapılandırma dosyaları (ACF) aranacak dizin listesine bir dizin ekler.

     Daha fazla bilgi için MIDL komut satırı başvurusunda **/I** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **AdditionalOptions**

     İsteğe **bağlı Dize** parametresi.

     Komut satırı seçeneklerinin listesi. Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir MIDL görev parametresiyle temsil etmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.

     Daha fazla bilgi için bkz. [MIDL komut satırı başvurusu.](/windows/desktop/Midl/midl-command-line-reference)

- **ApplicationConfigurationMode**

     İsteğe **bağlı Boole parametresi.**

     ise, `true` IDL dosyasında bazı ACF anahtar sözcükleri kullanmana olanak sağlar.

     Daha fazla bilgi için MIDL komut app_config içinde **/app_config** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **ClientStubFile**

     İsteğe **bağlı Dize** parametresi.

     Rpc arabirimi için istemci saplama dosyasının adını belirtir.

     Daha fazla bilgi için MIDL komut satırı başvurusunda **/cstub** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference) Ayrıca bu **tablodaki ServerStubFile** parametresine de bakın.

- **CPreprocessOptions**

     İsteğe **bağlı Dize** parametresi.

     C/C++ ön işlemciye geçiş seçeneklerini belirtir. Ön işlemci seçeneklerinin boşlukla ayrılmış listesini belirtin. seçeneğini `/E` içermesi gerekir.

     Daha fazla bilgi için MIDL komut cpp_opt başvurusunda **/cpp_opt** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **DefaultCharType**

     İsteğe **bağlı Dize** parametresi.

     C derleyicisi tarafından oluşturulan kodu derlemek için kullanabileceği varsayılan karakter türünü belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Imzalı**|**/char imzalı**|
    |**Imzasız**|**/char imzasız**|
    |**Ascıı**|**/char ascii7**|

     Daha fazla bilgi için MIDL komut satırı başvurusunda **/char** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **DllDataFileName**

     İsteğe **bağlı Dize** parametresi.

     Proxy DLL için oluşturulan *dlldata dosyasının* dosya adını belirtir.

     Daha fazla bilgi için MIDL komut satırı başvurusunda **/dlldata** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **EnableErrorChecks**

     İsteğe **bağlı Dize** parametresi.

     Oluşturulan saplamaların çalışma zamanında gerçekleştirecekleri hata denetimi türünü belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Hiçbiri**|**/error none**|
    |**EnableCustom**|**/error**|
    |**Tümü**|**/error all**|

     Daha fazla bilgi için MIDL komut satırı başvurusunda **/error** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **ErrorCheckAllocations**

     İsteğe **bağlı Boole parametresi.**

     ise, `true` yetersiz bellek hatalarını denetleyin.

     Daha fazla bilgi için MIDL **komut satırı başvurusunda /error** [ayırma seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **ErrorCheckBounds**

     İsteğe **bağlı Boole parametresi.**

     ise, uyumlu değişken ve değişen dizilerin boyutunu iletim `true` uzunluğu belirtimine göre denetler.

     Daha fazla bilgi için MIDL **komut satırı bounds_check /error** bounds_check [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **ErrorCheckEnumRange**

     İsteğe **bağlı Boole parametresi.**

     ise, `true` enum değerlerinin izin verilebilir bir aralıkta olduğunu denetler.

     Daha fazla bilgi için, komut satırı yardımı (**/?**) içinde **/error enum** seçeneğine bakın ve *midl.exe.*

- **ErrorCheckRefPointers**

     İsteğe **bağlı Boole parametresi.**

     ise, `true` hiçbir null başvuru işaretçisinin istemci saplamalara geçirilene olmadığını kontrol edin.

     Daha fazla bilgi için MIDL komut satırı başvurusunda **/error ref** [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **ErrorCheckStubData**

     İsteğe **bağlı Boole parametresi.**

     ise, sunucu tarafında şekillendirilen özel durumları yakalayacak ve bunları istemciye geri `true` yayılayacak bir saplama oluşturur.

     Daha fazla bilgi için MIDL komut stub_data içinde **/error** stub_data [seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **GenerateClientFiles**

     İsteğe **bağlı Dize** parametresi.

     Derleyicinin bir RPC arabirimi için istemci tarafı C kaynak dosyaları oluşturıp oluşturmay olmadığını belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Hiçbiri**|**/client none**|
    |**Saplama**|**/client stub**|

     Daha fazla bilgi için MIDL **komut satırı** başvurusunda [/client seçeneğine bakın.](/windows/desktop/Midl/midl-command-line-reference)

- **GenerateServerFiles**

     İsteğe **bağlı Dize** parametresi.

     Derleyicinin bir RPC arabirimi için sunucu tarafı C kaynak dosyaları oluşturıp oluşturmay olmadığını belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Hiçbiri**|**/Server hiçbiri**|
    |**Saplama**|**/Server saplama**|

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/Server** seçeneğine bakın.

- **GenerateStublessProxies**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , nesne arabirimleri için saplamasız proxy 'leriyle birlikte tam olarak yorumlanan saplamalar üretir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/oıcf** seçeneğine bakın.

- **GenerateTypeLibrary**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , bir tür kitaplığı (*. tlb*) dosyası oluşturulmaz.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/notlb** seçeneğine bakın.

- **HeaderFileName**

     İsteğe bağlı **dize** parametresi.

     Oluşturulan üst bilgi dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/h** veya **/Header** seçeneğine bakın.

- **Ignorestandardincludepath**

     İsteğe bağlı **Boolean** parametresi.

     `true`MIDL görevi yalnızca **Additionalıncludedizinler** anahtarını kullanarak belirtilen dizinleri arar ve geçerlI dizini ve INCLUDE ortam değişkeni tarafından belirtilen dizinleri yoksayar.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/no_def_idir** seçeneğine bakın.

- **Interfaceıdentifierfilename**

     İsteğe bağlı **dize** parametresi.

     Bir COM arabirimi için *arabirim tanımlayıcı dosyasının* adını belirtir. Bu, IDL dosya adına "_i. c" eklenerek elde edilen varsayılan adı geçersiz kılar.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/IID** seçeneğine bakın.

- **LocaleID**

     İsteğe bağlı **int** parametresi.

     Giriş dosyalarında, dosya adlarında ve Dizin yollarında Uluslararası karakterlerin kullanımını sağlayan *yerel ayar tanımlayıcısını* belirtir. Ondalık yerel ayar tanımlayıcısı belirtin.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/LCID** seçeneğine bakın. Ayrıca bkz. [yerel ayar tanımlayıcıları](/windows/desktop/intl/locale-identifiers).

- **MkTypLibCompatible**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , *mktyplib.exe* sürüm 2,03 ile uyumlu olacak şekilde giriş dosyasının biçimini gerektirir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/mktyplib203** seçeneğine bakın. Ayrıca bkz. MSDN Web sitesinde [ODL dosya sözdizimi](/previous-versions/windows/desktop/automat/odl-file-syntax) .

- **OutputDirectory**

     İsteğe bağlı **dize** parametresi.

     MıDL görevinin çıktı dosyalarını yazdığı varsayılan dizini belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Out** seçeneğine bakın.

- **PreprocessorDefinitions**

     İsteğe bağlı **dize []** parametresi.

     Bir veya daha fazla *tanımlar* belirtir; diğer bir deyişle, bir ad ve isteğe bağlı bir değer, bir yönergesi tarafından olduğu gibi C Önişlemci 'ye geçirilir `#define` . Her tanımlamanın formu, *adı [= değer]*.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/d** seçeneğine bakın. Ayrıca bkz. bu tablodaki **UndefinePreprocessorDefinitions** parametresi.

- **ProxyFileName**

     İsteğe bağlı **dize** parametresi.

     Bir COM arabirimi için arabirim proxy dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/proxy** seçeneğine bakın.

- **RedirectOutputAndErrors**

     İsteğe bağlı **dize** parametresi.

     Hata iletileri ve uyarılar gibi çıktıyı standart çıktısından belirtilen dosyaya yeniden yönlendirir.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/o** seçeneğine bakın.

- **ServerStubFile**

     İsteğe bağlı **dize** parametresi.

     RPC arabirimi için sunucu saplama dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/sstub** seçeneğine bakın. Ayrıca bkz. bu tablodaki **ClientStubFile** parametresi.

- **Kaynak**

     Gerekli `ITaskItem[]` parametre.

     Boşluklarla ayrılmış kaynak dosyalarının bir listesini belirtir.

- **Structmemberhizalaması**

     İsteğe bağlı **dize** parametresi.

     Hedef sistemdeki yapıların hizalamasını (*paketleme düzeyi*) belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**1**|**/ZP1**|
    |**2**|**/ZP2**|
    |**4**|**/ZP4**|
    |**8**|**/ZP8**|

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)' nda **/ZP** seçeneğine bakın. **/ZP** seçeneği, **/Pack** seçeneğine ve eski **/ALIGN** seçeneğine eşdeğerdir.

- **Suppresscompileruyarılar**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , MıDL görevinin uyarı iletilerini bastırır.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/no_warn** seçeneğine bakın.

- **SuppressStartupBanner**

     İsteğe bağlı `Boolean` parametre.

     İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/nologo** seçeneğine bakın.

- **TargetEnvironment**

     İsteğe bağlı **dize** parametresi.

     Uygulamanın çalıştığı ortamı belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**Win32**|**/env Win32**|
    |**Itanium**|**/env IA64**|
    |**X64**|**/env x64**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/env** seçeneğine bakın.

- **TrackerLogDirectory**

     İsteğe bağlı `String` parametre.

     Bu görev için İzleme günlüklerinin depolandığı ara dizini belirtir.

- **TypeLibFormat**

     İsteğe bağlı **dize** parametresi.

     Tür kitaplığı dosyasının biçimini belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**Eskibiçim**|**/oldtlb**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/newtlb** ve **/oldtlb** seçeneklerine bakın.

- **TypeLibraryName**

     İsteğe bağlı **dize** parametresi.

     Tür kitaplığı dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/tlb** seçeneğine bakın.

- **UndefinePreprocessorDefinitions**

     İsteğe bağlı **dize []** parametresi.

     Adı bir yönergesi ile C Önişlemci 'ya geçirerek bir adın önceki tanımını kaldırır `#undefine` . Önceden tanımlanmış bir veya daha fazla ad belirtin.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/u** seçeneğine bakın. Ayrıca bkz. bu tablodaki **PreprocessorDefinitions** parametresi.

- **ValidateAllParameters**

     İsteğe bağlı `Boolean` parametre.

     İse `true` , çalışma zamanında bütünlük denetimleri gerçekleştirmek için kullanılan ek hata denetleme bilgileri üretir. Varsa `false` , hata denetimi bilgileri oluşturulmaz.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/dayanıklı** ve **/no_robust** seçeneklerine bakın.

- **WarnAsError**

     İsteğe bağlı `Boolean` parametre.

     Varsa `true` , tüm uyarıları hata olarak değerlendirir.

     **WarningLevel** MIDL görev parametresi belirtilmemişse, varsayılan düzey 1 olan uyarılar hata olarak kabul edilir.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/WX** seçeneklerine bakın. Ayrıca bkz. bu tablodaki **WarningLevel** parametresi.

- **Uyarı düzeyi**

     İsteğe bağlı **dize** parametresi.

     Görüntülenecek uyarıların önem derecesini (*Uyarı düzeyi*) belirtir. 0 değeri için hiçbir uyarı yayınlanmadı. Aksi takdirde, uyarı düzeyi belirtilen değere eşit veya ondan daha küçükse bir uyarı yayınlanır.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)' nda **/w** seçeneğine bakın. Ayrıca bkz. bu tablodaki **warnaserror** parametresi.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
