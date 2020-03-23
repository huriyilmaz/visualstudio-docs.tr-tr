---
title: MIDL Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633479"
---
# <a name="midl-task"></a>MIDL görevi

Microsoft Arabirim Tanımı Dili (MIDL) derleyici aracı, *midl.exe*sarar. Daha fazla bilgi için [MIDL komut satırı başvurusuna](/windows/desktop/Midl/midl-command-line-reference)bakın.

## <a name="parameters"></a>Parametreler

 Aşağıdaki **MIDL** görevparametreleri açıklanır. Görev parametrelerinin çoğu ve birkaç parametre kümesi komut satırı seçeneğine karşılık gelir.

- **EkIncludeDirectories**

     İsteğe bağlı **String[]** parametresi.

     İçe aktarılan IDL dosyaları, dahil üstbilgi dosyaları ve uygulama yapılandırma dosyaları (ACF) için aranan dizinler listesine bir dizin ekler.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/I** seçeneğine bakın.

- **Ek Seçenekler**

     İsteğe bağlı **String** parametresi.

     Komut satırı seçenekleri listesi. Örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir MIDL görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.

     Daha fazla bilgi için [MIDL komut satırı başvurusuna](/windows/desktop/Midl/midl-command-line-reference)bakın.

- **UygulamaYapılandırma Modu**

     İsteğe bağlı **Boolean** parametresi.

     IdL `true`dosyasında bazı ACF anahtar kelimeleri kullanmanıza olanak sağlıyorsa.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/app_config** seçeneğine bakın.

- **İstemciStubFile**

     İsteğe bağlı **String** parametresi.

     RPC arabirimi için istemci saplama dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/cstub** seçeneğine bakın. Ayrıca bu tablodaki **ServerStubFile** parametresini de görün.

- **CPreprocessSeçenekleri**

     İsteğe bağlı **String** parametresi.

     C/C++ ön işlemcisine geçmek için seçenekleri belirtir. Önişlemci seçeneklerinin alanını sınırlandıran bir liste belirtin.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/cpp_opt** seçeneğine bakın.

- **Varsayılan CharType**

     İsteğe bağlı **String** parametresi.

     C derleyicisinin oluşturulan kodu derlemek için kullanacağı varsayılan karakter türünü belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Imzalı**|**/char imzalı**|
    |**Imzasız**|**/char imzasız**|
    |**Ascıı**|**/char ascii7**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/char** seçeneğine bakın.

- **DllDataFileName**

     İsteğe bağlı **String** parametresi.

     Proxy DLL için oluşturulan *dlldata* dosyasının dosya adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/dlldata** seçeneğine bakın.

- **Etkinleştirme Hata Denetimleri**

     İsteğe bağlı **String** parametresi.

     Oluşturulan saplamaların çalışma zamanında gerçekleştireceği hata denetimi türünü belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Yok**|**/hata yok**|
    |**Özel etkinleştirme**|**/hata**|
    |**Tümü**|**/hata tümü**|

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/hata** seçeneğine bakın.

- **ErrorCheckAllocations**

     İsteğe bağlı **Boolean** parametresi.

     Eğer `true`, bellek dışı hatalar için kontrol edin.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/hata ayırma** seçeneğine bakın.

- **ErrorCheckBounds**

     İsteğe bağlı **Boolean** parametresi.

     Uygunan `true`değişen ve değişen dizilerin boyutunu iletim uzunluğu belirtimine göre denetlerse.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/error bounds_check** seçeneğine bakın.

- **ErrorCheckEnumRange**

     İsteğe bağlı **Boolean** parametresi.

     Enum `true`değerlerinin izin verilen aralıkta olduğunu denetlerse.

     Daha fazla bilgi *için, midl.exe*için komut satırı yardım **(/?**) **/?** seçeneğine bakın.

- **ErrorCheckRefPointers**

     İsteğe bağlı **Boolean** parametresi.

     Eğer, `true`istemci saplamalarına null başvuru işaretçisi geçirilip geçirilemediğini denetleyin.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/hata ref** seçeneğine bakın.

- **ErrorCheckStubData**

     İsteğe bağlı **Boolean** parametresi.

     , `true`sunucu tarafında mareşal olmayan özel durumları yakalar ve istemciye geri yayan bir saplama oluşturur.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/error stub_data** seçeneğine bakın.

- **Müşteri Dosyaları Oluşturma**

     İsteğe bağlı **String** parametresi.

     Derleyicinin rpc arabirimi için istemci tarafındaki C kaynak dosyalarını oluşturup oluşturmadığını belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Yok**|**/istemci yok**|
    |**Saplama**|**/istemci saplama**|

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/istemci** seçeneğine bakın.

- **Sunucu Dosyalarını Oluşturma**

     İsteğe bağlı **String** parametresi.

     Derleyicinin rpc arabirimi için sunucu tarafındaki C kaynak dosyalarını oluşturup oluşturmadığını belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Yok**|**/sunucu yok**|
    |**Saplama**|**/sunucu saplama**|

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/sunucu** seçeneğine bakın.

- **StublessProxies üretir**

     İsteğe bağlı **Boolean** parametresi.

     Eğer, `true`nesne arabirimleri için saplamaz yakınlıkları ile birlikte tam olarak yorumlanmış saplamalar oluşturur.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Oicf** seçeneğine bakın.

- **TypeLibrary oluşturma**

     İsteğe bağlı **Boolean** parametresi.

     If `true`, bir tür kitaplığı (*.tlb*) dosyası oluşturulmuyor.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/notlb** seçeneğine bakın.

- **BaşlıkFileName**

     İsteğe bağlı **String** parametresi.

     Oluşturulan üstbilgi dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/h** veya **/header** seçeneğine bakın.

- **StandartIncludePath'i YokSay**

     İsteğe bağlı **Boolean** parametresi.

     MIDL görevi yalnızca **Ek IncludeDirectories** anahtarını kullanarak belirtilen dizinleri arar ve geçerli dizinve INCLUDE ortamı değişkeni tarafından belirtilen dizinleri yoksa. `true`

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/no_def_idir** seçeneğine bakın.

- **InterfaceIdentifierFileName**

     İsteğe bağlı **String** parametresi.

     COM arabirimi için *arabirim tanımlayıcı dosyasının* adını belirtir. Bu, IDL dosya adına "_i.c" ekleyerek elde edilen varsayılan adı geçersiz kılar.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/iid** seçeneğine bakın.

- **Localeıd**

     İsteğe bağlı **int** parametresi.

     Giriş dosyalarında, dosya adlarında ve dizin yollarında uluslararası karakterlerin kullanılmasını sağlayan *yerel* tanımlayıcıyı belirtir. Ondalık yerel bir yerel tanımlayıcı belirtin.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/lcid** seçeneğine bakın. Ayrıca [bkz.](/windows/desktop/intl/locale-identifiers)

- **MkTypLibUyumlu**

     İsteğe bağlı **Boolean** parametresi.

     Eğer, `true`giriş dosyasının biçiminin *mktyplib.exe* sürüm 2.03 ile uyumlu olmasını gerektiriyorsa.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/mktyplib203** seçeneğine bakın. Ayrıca, MSDN web sitesinde [ODL dosya sözdizimine](/previous-versions/windows/desktop/automat/odl-file-syntax) bakın.

- **Outputdirectory**

     İsteğe bağlı **String** parametresi.

     MIDL görevinin çıktı dosyalarını yazdığı varsayılan dizini belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/out** seçeneğine bakın.

- **Önİşleme İşlemci Tanımlar**

     İsteğe bağlı **String[]** parametresi.

     Bir veya daha fazla *tanım*belirtir; diğer bir ad ve isteğe bağlı bir değer c önişlemcisine bir `#define` yönerge tarafından aktarılır. Her tanımların biçimi, *adı[=değer]*.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/D** seçeneğine bakın. Ayrıca, bu tabloda **Tanımsızİşlemtanımları** Tanımlı Tanımlar parametrebakın.

- **ProxyFileName**

     İsteğe bağlı **String** parametresi.

     Com arabirimi için arabirim proxy dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/proxy** seçeneğine bakın.

- **Yeniden YönlendirmeOutputAndErrors**

     İsteğe bağlı **String** parametresi.

     Hata iletileri ve uyarılar gibi çıktıları standart çıktıdan belirtilen dosyaya yönlendirir.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/o** seçeneğine bakın.

- **ServerStubFile**

     İsteğe bağlı **String** parametresi.

     RPC arabirimi için sunucu saplama dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/sstub** seçeneğine bakın. Ayrıca, bu tablodaki **ClientStubFile** parametresini de görün.

- **Kaynak**

     Gerekli `ITaskItem[]` parametre.

     Boşluklara göre ayrılmış kaynak dosyaların listesini belirtir.

- **StructMemberAlignment**

     İsteğe bağlı **String** parametresi.

     Hedef sistemdeki yapıların hizalanmasını *(paketleme düzeyini)* belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Notset**|*\<hiçbiri>*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/Zp** seçeneğine bakın. **/Zp** seçeneği **/pack** seçeneğine ve eski **/hizalama** seçeneğine eşdeğerdir.

- **SuppressCompilerUyarılar**

     İsteğe bağlı **Boolean** parametresi.

     Midl `true`görevinden gelen uyarı iletilerini bastırırsa.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/no_warn** seçeneğine bakın.

- **BastırmaBaşlangıç Banner**

     İsteğe bağlı `Boolean` parametre.

     Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/nologo** seçeneğine bakın.

- **HedefÇevre**

     İsteğe bağlı **String** parametresi.

     Uygulamanın çalıştığı ortamı belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Notset**|*\<hiçbiri>*|
    |**Win32**|**/env win32**|
    |**Itanium**|**/env ia64**|
    |**X64, X64**|**/env x64**|

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/env** seçeneğine bakın.

- **TrackerLogDirectory**

     İsteğe bağlı `String` parametre.

     Bu görev için izleme günlüklerinin depolandığı ara dizini belirtir.

- **TypeLibFormat**

     İsteğe bağlı **String** parametresi.

     Tür kitaplığı dosyasının biçimini belirtir.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**Yeni Biçim**|**/newtlb**|
    |**Eski Biçim**|**/oldtlb**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/newtlb** ve **/oldtlb** seçeneklerine bakın.

- **TypeLibraryNameAdı**

     İsteğe bağlı **String** parametresi.

     Tür kitaplığı dosyasının adını belirtir.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/tlb** seçeneğine bakın.

- **TanımsızPreprocessorDefinitions**

     İsteğe bağlı **String[]** parametresi.

     Bir adın önceki tüm tanımını c önişlemcisine bir `#undefine` yönerge yle geçiyormuş gibi aktararak kaldırır. Bir veya daha fazla önceden tanımlanmış ad belirtin.

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/U** seçeneğine bakın. Ayrıca, bu tablodaki **PreprocessorDefinitions** parametresini de görün.

- **Tüm Parametreleri Doğrula**

     İsteğe bağlı `Boolean` parametre.

     , `true`çalışma zamanında bütünlük denetimleri gerçekleştirmek için kullanılan ek hata denetimi bilgileri oluşturur. `false`Hata denetleme bilgileri oluşturulmazsa.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/sağlam** ve **/no_robust** seçeneklerine bakın.

- **WarnasError**

     İsteğe bağlı `Boolean` parametre.

     Eğer, `true`tüm uyarıları hata olarak ele alırsa.

     **WarningLevel** MIDL görev parametresi belirtilmemişse, varsayılan düzeydeki uyarılar, düzey 1, hata olarak kabul edilir.

     Daha fazla bilgi için [MIDL komut satırı başvurusundaki](/windows/desktop/Midl/midl-command-line-reference) **/WX** seçeneklerine bakın. Ayrıca, bu tablodaki **Uyarı Düzeyi** parametresini görün.

- **Uyarı Düzeyi**

     İsteğe bağlı **String** parametresi.

     Yakılacak uyarıların önem derecesini *(uyarı düzeyini)* belirtir. 0 değeri için hiçbir uyarı yayımlanır. Aksi takdirde, uyarı düzeyi sayısal olarak belirtilen değerden daha az veya eşitse bir uyarı yayılır.

     Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

    |Değer|Komut satırı araçları|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     Daha fazla bilgi için [MIDL komut satırı başvurusunda](/windows/desktop/Midl/midl-command-line-reference) **/W** seçeneğine bakın. Ayrıca, bu tablodaki **WarnAsError** parametresini görün.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
