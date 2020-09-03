---
title: MıDL görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a43975244eaf064c9ed7608fa41c16854ca140f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633479"
---
# <a name="midl-task"></a>MIDL görevi

Microsoft Arabirim Tanımlama Dili (MıDL) derleyici aracını *midl.exe*sarmalanmış olarak kaydırır. Daha fazla bilgi için bkz. [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference).

## <a name="parameters"></a>Parametreler

 Aşağıda, **MIDL** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.

- **AdditionalIncludeDirectories**

     İsteğe bağlı **dize []** parametresi.

     İçeri aktarılan IDL dosyaları, eklenen üst bilgi dosyaları ve uygulama yapılandırma dosyaları (ACF) için aranan dizin listesine bir dizin ekler.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/ı** seçeneğine bakın.

- **AdditionalOptions**

     İsteğe bağlı **dize** parametresi.

     Komut satırı seçeneklerinin listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Diğer bir MıDL görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.

     Daha fazla bilgi için bkz. [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference).

- **ApplicationConfigurationMode**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , IDL dosyasında bazı ACF anahtar sözcüklerini kullanmanıza izin verir.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/app_config** seçeneğine bakın.

- **ClientStubFile**

     İsteğe bağlı **dize** parametresi.

     RPC arabirimi için istemci saplama dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)' nda **/cstub** seçeneğine bakın. Ayrıca bkz. bu tablodaki **ServerStubFile** parametresi.

- **CPreprocessOptions**

     İsteğe bağlı **dize** parametresi.

     C/C++ ön işlemcisi 'ne geçirilecek seçenekleri belirtir. Önişlemci seçeneklerinin boşlukla ayrılmış bir listesini belirtin.

     Daha fazla bilgi için [MIDL komut satırı başvurusu](/windows/desktop/Midl/midl-command-line-reference)içindeki **/cpp_opt** seçeneğine bakın.

- **DefaultCharType**

     İsteğe bağlı **dize** parametresi.

     C derleyicisinin üretilen kodu derlemek için kullanacağı varsayılan karakter türünü belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**İmza**|**/Char imzalandı**|
    |**İşaretlenmemiş**|**/Char işaretsiz**|
    |**ASCII**|**/Char ascii7**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/char** seçeneğine bakın.

- **DllDataFileName**

     İsteğe bağlı **dize** parametresi.

     Bir proxy DLL 'si için oluşturulan *dlldata* dosyasının dosya adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/dlldata** seçeneğine bakın.

- **Enableerrordenetimleri**

     İsteğe bağlı **dize** parametresi.

     Oluşturulan saplamalarının çalışma zamanında gerçekleştireceği hata denetimini belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Hiçbiri**|**/hata yok**|
    |**EnableCustom**|**/Error**|
    |**Tümü**|**/Error tümü**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Error** seçeneğine bakın.

- **ErrorCheckAllocations**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` bellek yetersiz hatalarını kontrol edin.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Error Allocation** seçeneğine bakın.

- **Errorchecksınır**

     İsteğe bağlı **Boolean** parametresi.

     `true`, Uyumlu ve değişen dizilerin boyutunu iletim uzunluğu belirtimine göre denetler.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Error bounds_check** seçeneğine bakın.

- **ErrorCheckEnumRange**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , sabit listesi değerlerinin izin verilen aralıkta olup olmadığını denetler.

     Daha fazla bilgi için, *midl.exe*için komut satırı yardımı 'nda (**/?**) **/Error sabit listesi** seçeneğine bakın.

- **Errorcheckrefişaretçiler**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , istemci saplamasına hiçbir null başvuru işaretçisi iletildiğini kontrol edin.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Error ref** seçeneğine bakın.

- **ErrorCheckStubData**

     İsteğe bağlı **Boolean** parametresi.

     `true`, Sunucu tarafında özel durumları hazırlamayı ve istemciye geri yayan bir saplama oluşturur.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Error stub_data** seçeneğine bakın.

- **GenerateClientFiles**

     İsteğe bağlı **dize** parametresi.

     Derleyicinin bir RPC arabirimi için istemci tarafı C kaynak dosyaları oluşturup oluşturmayacağını belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Hiçbiri**|**/Client yok**|
    |**Saplama**|**/Client saplama**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Client** seçeneğine bakın.

- **GenerateServerFiles**

     İsteğe bağlı **dize** parametresi.

     Derleyicinin bir RPC arabirimi için sunucu tarafı C kaynak dosyaları oluşturup oluşturmayacağını belirtir.

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

     Bir veya daha fazla *tanımlar*belirtir; diğer bir deyişle, bir ad ve isteğe bağlı bir değer, bir yönergesi tarafından olduğu gibi C Önişlemci 'ye geçirilir `#define` . Her tanımlamanın formu, *adı [= değer]*.

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
