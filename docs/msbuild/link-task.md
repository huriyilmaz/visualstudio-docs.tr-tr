---
title: Bağlantı görevi | Microsoft Docs
description: MSBuild, COFF nesne dosyalarını ve kitaplıklarını bağlayan link.exe Microsoft C++ bağlayıcı aracı 'nı kaydırmak için bağlantı görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.LinkStatus
- VC.Project.VCLinkerTool.CLRUnmanagedCodeCheck
- VC.Project.VCLinkerTool.SpecifySectionAttributes
- VC.Project.VCLinkerTool.SupportNobindOfDelayLoadedDLL
- VC.Project.VCLinkerTool.MinimumRequiredVersion
- VC.Project.VCLinkerTool.PerUserRedirection
- VC.Project.VCLinkerTool.CreateHotPatchableImage
- VC.Project.VCLinkerTool.DataExecutionPrevention
- VC.Project.VCLinkerTool.TreatLinkerWarningsAsErrors
- vc.task.link
- VC.Project.VCLinkerTool.ImageHasSafeExceptionHandlers
- VC.Project.VCLinkerTool.CLRSupportLastError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), Link task
- Link task (MSBuild (C++))
ms.assetid: 0a61f168-3113-4fa7-83a3-d9142e2a33f8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6a7f986674aa215e2fae98dc469bd1807afcedbc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625665"
---
# <a name="link-task"></a>Bağlantı görevi

, Microsoft C++ bağlayıcı aracı *link.exe* sarmalanmış. Bağlayıcı aracı ortak nesne dosyası biçimi (COFF) nesne dosyalarını ve kitaplıklarını bir yürütülebilir (*.exe*) dosya veya dinamik bağlantı KITAPLıĞı (dll) oluşturmak için bağlar. daha fazla bilgi için bkz. [bağlayıcı seçenekleri](/cpp/build/reference/linker-options) ve [komut satırından MSBuild kullanma](/cpp/build/msbuild-visual-cpp) ve [komut satırından Microsoft C++ araç takımını kullanma](/cpp/build/building-on-the-command-line).

## <a name="parameters"></a>Parametreler

 **Bağlantı** görevinin parametreleri aşağıda açıklanmıştır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.

- **AdditionalDependencies**

  İsteğe bağlı **dize []** parametresi.

  Komuta eklenecek giriş dosyalarının bir listesini belirtir.

  Daha fazla bilgi için bkz. [giriş dosyalarını bağlama](/cpp/build/reference/link-input-files).

- **Additionallibrarydizinler**

  İsteğe bağlı **dize []** parametresi.

  Ortam kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.

  Daha fazla bilgi için bkz. [/LIBPATH (ek libpath)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  İsteğe bağlı **dize []** parametresi.

  `dependency`Bildirim dosyasının bölümüne yerleştirilecek öznitelikleri belirtir.

  Daha fazla bilgi için bkz. [/Manifestdependency (Bildirim Bağımlılıklarını Belirt)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). ayrıca bkz. [Publisher yapılandırma dosyaları](/windows/desktop/SbsCs/publisher-configuration-files).

- **AdditionalOptions**

  İsteğe bağlı **dize** parametresi.

  Komut satırında belirtilen bağlayıcı seçeneklerinin bir listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Başka bir **bağlantı** görevi parametresi tarafından temsil edilmeyen bağlayıcı seçeneklerini belirtmek için bu parametreyi kullanın.

  Daha fazla bilgi için bkz. [bağlayıcı seçenekleri](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  İsteğe bağlı **dize []** parametresi.

  Bir derlemeye modül başvurusu ekler.

  Daha fazla bilgi için bkz. [/ASSEMBLYMODULE (DERLEMEYE MSIL Modülü ekleme)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **ALLOWISOLATION**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , işletim sisteminin bildirim aramalarını ve yüklemelerini yapmasına neden olur. İse `false` , dll 'lerin bir bildirim olmadığı gibi yüklendiğini belirtir.

  Daha fazla bilgi için bkz. [/ALLOWISOLATION (bildirim arama)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug**

  İsteğe bağlı **Boolean** parametresi.

  `true`Hata ayıklayıcı, hata ayıklama bilgileri izleme ile birlikte hata ayıklamış **ggableattribute** ÖZNITELIĞINI yayar ve JIT iyileştirmeleri devre dışı bırakır Eğer `false` , hata ayıklayıcı **ggableattribute** özniteliğini yayar, ancak hata ayıklama bilgileri izlemeyi devre DıŞı bırakır ve JIT iyileştirmelerini mümkün

  Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (hata ayıklama Ggableattribute Ekle)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **ASSEMBLYLINKRESOURCE**

  İsteğe bağlı **dize []** parametresi.

  çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez. Kaynağın adını belirtin.

  daha fazla bilgi için bkz. [/assemblylinkresource (.NET Framework kaynağına bağlantı)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Örtük **Boolean** parametresi.

  Daha derin dosya izlemenin bağlantı artımlı davranışını yakalamasını sağlar. Her zaman `true` döndürür.

- **BaseAddress**

  İsteğe bağlı **dize** parametresi.

  Oluşturulan program veya DLL için bir temel adres ayarlar. `{address[,size] | @filename,key}` belirtin.

  Daha fazla bilgi için bkz. [/Base (temel adres)](/cpp/build/reference/base-base-address).

- **Buildingınıde**

  İsteğe bağlı **Boolean** parametresi.

  true ise, MSBuild ıde 'den çağrılacağını gösterir. aksi takdirde, MSBuild komut satırından çağrılacağını gösterir.

  Bu parametrenin denk bağlayıcı seçeneği yok.

- **CLRIMAGETYPE**

  İsteğe bağlı **dize** parametresi.

  Ortak dil çalışma zamanı (CLR) görüntüsünün türünü ayarlar.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılanını** - *\<none>*

  - **ForceIJWImage**  -  **/Clrimagetype: IJW**

  - **Forcepureilımage**  -  **/Clrimagetype: saf**

  - **Forcesafeılımage**  -  **/Clrimagetype: güvenli**

  Daha fazla bilgi için bkz. [/Clrimagetype (clr görüntü türünü belirt)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSUPPORTLASTERROR 'ü**

  İsteğe bağlı **dize** parametresi.

  P/Invoke mekanizması aracılığıyla çağrılan işlevlerin son hata kodunu korur.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin**  -  **/CLRSupportLastError**

  - **Devre dışı**  -  **/CLRSupportLastError: Hayır**

  - **Sistem dll 'leri**  -  **/CLRSupportLastError: SYSTEMDLL**

  Daha fazla bilgi için bkz. [/CLRSUPPORTLASTERROR (PInvoke çağrıları için son hata kodunu koru)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).

- **CLRTHREADATTRIBUTE**

  İsteğe bağlı **dize** parametresi.

  CLR programınızın giriş noktası için iş parçacığı oluşturma özniteliğini açıkça belirtir.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Defaultthreadingattribute**  -  **/CLRTHREADATTRIBUTE: yok**

  - **Mtathreadingattribute**  -  **/CLRTHREADATTRIBUTE: MTA**

  - **Stathreadingattribute**  -  **/CLRTHREADATTRIBUTE: STA**

  Daha fazla bilgi için bkz. [/CLRTHREADATTRIBUTE (CLR iş parçacığı özniteliğini ayarlama)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  İsteğe bağlı **Boolean** parametresi.

  Bağlayıcının **SuppressUnmanagedCodeSecurityAttribute** ' i yönetilen koddan yerel dll 'lere bağlayıcı tarafından oluşturulan P/Invoke çağrılarına uygulayıp uygulayamayacağını belirtir.

  Daha fazla bilgi için bkz. [/CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute ekleyin)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **Createhotpatchableımage**

  İsteğe bağlı **dize** parametresi.

  Sık yama için bir görüntü hazırlar.

  Bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin**  -  **/Functionpadmin**

  - **X86Image**  -  **/Functionpadmin: 5**

  - **X64Image**  -  **/Functionpadmin: 6**

  - **Itaniumımage**  -  **/Functionpadmin: 16**

  Daha fazla bilgi için bkz. [/functionpadmin (düzeltme eki eklenebilir görüntü oluşturma)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bir yürütülebilir dosyanın Veri Yürütme Önleme özelliğiyle Windows olduğunu gösterir.

  Daha fazla bilgi için bkz. [/NXCOMPAT (Veri Yürütme Önleme ile Uyumlu)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLL'ler**

  İsteğe **bağlı String[]** parametresi.

  Bu parametre, *URL'lerin gecikmeli* yüklenmesine neden olur. Yükü geciktirmek için DLL adını belirtin.

  Daha fazla bilgi için bkz. [/DELAYLOAD (Yükü içeri aktarmayı geciktir)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bir derlemeyi kısmen imzalar. Varsayılan değer `false` şeklindedir.

  Daha fazla bilgi için bkz. [/DELAYSIGN (Derlemeyi kısmen imzalama)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Sürücü**

  İsteğe **bağlı Dize** parametresi.

  Çekirdek modu sürücüsü oluşturmak için Windows NT belirtin.

  Her biri bir bağlantıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Notset** - *\<none>*

  - **Sürücü**  -  **/Driver**

  - **UpOnly**  -  **/DRIVER:UPONLY**

  - **WDM**  -  **/DRIVER:WDM**

  Daha fazla bilgi için bkz. [/DRIVER (Windows NT çekirdek modu sürücüsü)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  İsteğe **bağlı String[]** parametresi.

  Bir derlemeye kaynak dosyası katıştırır. Gerekli kaynak dosyası adını belirtin. İsteğe bağlı olarak, kaynağı yüklemek için kullanılan mantıksal adı ve kaynak dosyasının özel olduğunu derleme bildiriminde belirten **PRIVATE** seçeneğini belirtin.

  Daha fazla bilgi için bkz. [/ASSEMBLYRESOURCE (Yönetilen kaynak ekleme)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **EnableCOMDATFolding**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` aynı COMDAT katlamayı sağlar.

  Daha fazla bilgi için `ICF[= iterations]` bkz. [/OPT (İyileştirmeler)](/cpp/build/reference/opt-optimizations)bağımsız değişkeni.

- **EnableUAC**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` Kullanıcı Hesabı Denetimi (UAC) bilgisinin program bildirimine ekli olduğunu belirtir.

  Daha fazla bilgi için bkz. [/MANIFESTUAC (Bildirime UAC bilgileri ekleme)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  İsteğe **bağlı Dize** parametresi.

  Bir giriş noktası işlevini bir dosyanın veya *DLL'nin başlangıç.exe* olarak belirtir. Parametre değeri olarak bir işlev adı belirtin.

  Daha fazla bilgi için bkz. [/ENTRY (Giriş noktası simgesi)](/cpp/build/reference/entry-entry-point-symbol).

- **FixedBaseAddress**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` yalnızca tercih edilen temel adrese yüklen bir program veya DLL oluşturur.

  Daha fazla bilgi için bkz. [/FIXED (Sabit temel adres)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  İsteğe **bağlı Dize** parametresi.

  Bir sembole başvurulsa ancak *tanımlanmamış olsa.exe* veya çarpma tanımlanmış olsa bile, bağlantıcıya geçerli bir dosya veya DLL oluşturması söyler.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin**  -  **/FORCE**

  - **MultiplyDefinedSymbolOnly**  -  **/FORCE:MULTIPLE**

  - **UndefinedSymbolOnly**  -  **/FORCE:UNRESOLVED**

  Daha fazla bilgi için bkz. [/FORCE (Dosya çıktısını zorla)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences**

  İsteğe **bağlı String[]** parametresi.

  Bu parametre, bağlantıcıya sembol tablosuna belirtilen bir simgeyi eklemesi söyler.

  Daha fazla bilgi için bkz. [/INCLUDE (Simge başvurularını zorla)](/cpp/build/reference/include-force-symbol-references).

- **FunctionOrder**

  İsteğe **bağlı Dize** parametresi.

  Bu parametre, belirtilen paketlenmiş işlevleri (COMDAT) görüntüye önceden belirlenen bir sırada yerleştirerek programınızı iyiler.

  Daha fazla bilgi için bkz. [/ORDER (İşlevleri sırayla koy)](/cpp/build/reference/order-put-functions-in-order).

- **GenerateDebugInformation**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` dosya veya DLL  için.exeoluşturması gerekir.

  Daha fazla bilgi için bkz. [/DEBUG (Hata ayıklama bilgisi oluşturma)](/cpp/build/reference/debug-generate-debug-info).

- **GenerateManifest**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` yan yana bildirim dosyası oluşturur.

  Daha fazla bilgi için [bkz. /MANIFEST (Yan yana derleme bildirimi oluşturma)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bir eşleme *dosyası oluşturur.* Eşleme dosyasının dosya adı uzantısı *.map'tir.*

  Daha fazla bilgi için bkz. [/MAP (Eşlem dosyası oluştur)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  İsteğe **bağlı Dize** parametresi.

  Yığında aynı anda ayrılacak fiziksel bellek miktarını belirtir.

  Daha fazla bilgi için `commit` [/HEAP (Yığın boyutunu ayarla) içinde bağımsız değişkenine bakın.](/cpp/build/reference/heap-set-heap-size) Ayrıca bkz. **HeapReserveSize** parametresi.

- **HeapReserveSize**

  İsteğe **bağlı Dize** parametresi.

  Sanal bellekte toplam yığın ayırmayı belirtir.

  Daha fazla bilgi için `reserve` [/HEAP (Yığın boyutunu ayarla) içinde bağımsız değişkenine bakın.](/cpp/build/reference/heap-set-heap-size) Ayrıca, bu **tablodaki HeapCommitSize** parametresine bakın.

- **IgnoreAllDefaultLibraries**

  İsteğe **bağlı Boole parametresi.**

  ise, bağlantıcıya dış başvuruları çözümleye kadar arama yaptığı kitaplık listesinden bir veya daha `true` fazla varsayılan kitaplığı kaldırmayı söyler.

  Daha fazla bilgi için bkz. [/NODEFAULTLIB (Kitaplıkları yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` kaynak kodda herhangi bir IDL özniteliğinin *bir .idl* dosyasına işlenmeyecek olduğunu belirtir.

  Daha fazla bilgi için bkz. [/IGNOREIDL (Öznitelikleri MIDL'ye işleme)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bu yapılandırma tarafından oluşturulan içeri aktarma kitaplığının bağımlı projelere içeri aktarılamayacak şekilde belirtir.

  Bu parametre bir linker seçeneğine karşılık gelen bir parametre değildir.

- **IgnoreSpecificDefaultLibraries**

  İsteğe **bağlı String[]** parametresi.

  Yoksaymak için bir veya daha fazla varsayılan kitaplık adı belirtir. Noktalı virgül kullanarak birden çok kitaplığı ayırma.

  Daha fazla bilgi için bkz. [/NODEFAULTLIB (Kitaplıkları yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  İsteğe **bağlı Boole parametresi.**

  ise, yalnızca görüntünün güvenli özel durum işleyicilerinin bir tablosu da `true` üreteci bir görüntü üretir.

  Daha fazla bilgi için bkz. [/SAFESEH (Görüntüde güvenli özel durum işleyicileri vardır)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Varsayılan kitaplık adının yerini alan, kullanıcı tarafından belirtilen içeri aktarma kitaplığı adı.

  Daha fazla bilgi için bkz. [/IMPLIB (İçeri aktarma kitaplığını adla)](/cpp/build/reference/implib-name-import-library).

- **Keycontainer**

  İsteğe **bağlı Dize** parametresi.

  İmzalı derlemenin anahtarını içeren kapsayıcı.

  Daha fazla bilgi için bkz. [/KEYCONTAINER (Derlemeyi imzalamak için anahtar kapsayıcısı belirtin)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Ayrıca, bu **tablodaki KeyFile** parametresine bakın.

- **Keyfile**

  İsteğe **bağlı Dize** parametresi.

  İmzalı derlemenin anahtarını içeren bir dosyayı belirtir.

  Daha fazla bilgi için bkz. [/INILE (Derlemeyi imzalamak için anahtar veya anahtar çifti belirtin)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Ayrıca bkz. **KeyContainer** parametresi.

- **LargeAddressAware**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` uygulama 2 gigabayttan büyük adresleri işebilir.

  Daha fazla bilgi için bkz. [/LARGEADDRESSAWARE (Büyük adresleri işleme)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` ana çıkış dosyası olarak bir DLL oluşturur.

  Daha fazla bilgi için bkz. [/DLL (DLL Derleme)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  İsteğe **bağlı Dize** parametresi.

  İç derleyici hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamayı sağlar.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NoErrorReport**  -  **/ERRORREPORT:NONE**

  - **PromptImmediately**  -  **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin**  -  **/ERRORREPORT:QUEUE**

  - **SendErrorReport**  -  **/ERRORREPORT:SEND**

  Daha fazla bilgi için bkz. [/ERRORREPORT (İç bağlantı hatalarını raporla)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **LinkIncremental**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` artımlı bağlamayı sağlar.

  Daha fazla bilgi için bkz. [/INCREMENTAL (Artımlı olarak bağlantı)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` proje bağımlılıklarından kitaplık çıkışların otomatik olarak içinde bağlanacaklarını belirtir.

  Bu parametre bir linker seçeneğine karşılık gelen bir parametre değildir.

- **LinkStatus**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bağlantının tamamlandıktan yüzdesini gösteren bir ilerleme göstergesi görüntülemek için bağlantının olduğunu belirtir.

  Daha fazla bilgi için `STATUS` bkz. [/LTCG (Bağlantı zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation)bağımsız değişkeni.

- **LinkTimeCodeGeneration**

  İsteğe **bağlı Dize** parametresi.

  Profil destekli iyileştirme seçeneklerini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *\<none>*

  - **UseLinkTimeCodeGeneration**  -  **/LTCG**

  - **PGInstrument**  -  **/LTCG:PGInstrument**

  - **PGOptimization**  -  **/LTCG:PGOptimize**

  - **PGUpdate**

    \-**/LTCG:PGUpdate**

  Daha fazla bilgi için bkz. [/LTCG (Bağlantı zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation).

- **ManifestFile**

  İsteğe **bağlı Dize** parametresi.

  Varsayılan bildirim dosyası adını belirtilen dosya adıyla değiştirir.

  Daha fazla bilgi için bkz. [/MANIFESTFILE (Bildirim dosyasını ad)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapExports**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bağlantıcıya dışarı aktaran işlevleri bir eşleme dosyasına dahil eder.

  Daha fazla bilgi için `EXPORTS` [/MAPINFO (Bilgileri eşlem dosyasına dahil edin) bağımsız değişkenine bakın.](/cpp/build/reference/mapinfo-include-information-in-mapfile)

- **MapFileName**

  İsteğe **bağlı Dize** parametresi.

  Varsayılan eşleme dosyası adını belirtilen dosya adıyla değiştirir.

- **MergedIDLBaseFileName**

  İsteğe **bağlı Dize** parametresi.

  *.idl* dosyasının dosya adını ve dosya adı uzantısını belirtir.

  Daha fazla bilgi için bkz. [/IDLOUT (MIDL çıkış dosyalarını adla)](/cpp/build/reference/idlout-name-midl-output-files).

- **MergeSections**

  İsteğe **bağlı Dize** parametresi.

  Bir görüntüde bölümleri birleştirir. `from-section=to-section` belirtin.

  Daha fazla bilgi için bkz. [/MERGE (Bölümleri birleştir)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile**

  İsteğe **bağlı Dize** parametresi.

  MIDL komut satırı seçeneklerini içeren bir dosyanın adını belirtin.

  Daha fazla bilgi için bkz. [/MIDL (MIDL komut satırı seçeneklerini belirtin)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **MinimumRequiredVersion**

  İsteğe **bağlı Dize** parametresi.

  Alt sistemin gereken en düşük sürümünü belirtir. Bağımsız değişkenler 0 ile 65535 aralığındaki ondalık sayılardır.

- **ModuleDefinitionFile**

  İsteğe **bağlı Dize** parametresi.

  Modül tanım dosyasının [adını belirtir.](/cpp/build/reference/module-definition-dot-def-files)

  Daha fazla bilgi için bkz. [/DEF (Modül tanımı dosyasını belirtin)](/cpp/build/reference/def-specify-module-definition-file).

- **MSDOSStubFileName**

  İsteğe **bağlı Dize** parametresi.

  Belirtilen MS-DOS saplama programını win32 programına iliştirer.

  Daha fazla bilgi için bkz. [/STUB (MS-DOS saplama dosyası adı)](/cpp/build/reference/stub-ms-dos-stub-file-name).

- **NoEntryPoint**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` yalnızca kaynak DLL'lerini belirtir.

  Daha fazla bilgi için bkz. [/NOENTRY (Giriş noktası yok)](/cpp/build/reference/noentry-no-entry-point).

- **ObjectFiles**

  Örtük **dize []** parametresi.

  Bağlı nesne dosyalarını belirtir.

- **OptimizeReferences**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , hiçbir şekilde başvurulmayan işlevleri ve/veya verileri ortadan kaldırır.

  Daha fazla bilgi için bkz `REF` . [/opt (iyileştirmeler)](/cpp/build/reference/opt-optimizations)içindeki bağımsız değişken.

- **Çıktı**

  İsteğe bağlı **dize** parametresi.

  Bağlayıcının oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar.

  Daha fazla bilgi için bkz. [/Out (çıktı dosyası adı)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  İsteğe bağlı **Boolean** parametresi.

  `true`Çıktıyı kaydet etkinse, kayıt defteri yazmaları **HKEY_CLASSES_ROOT** **HKEY_CURRENT_USER** yeniden yönlendirilmeye zorlar.

- **PreprocessOutput**

  İsteğe bağlı `ITaskItem[]` parametre.

  Görevler tarafından tüketilen ve yayılan bir Önişlemci çıkış öğeleri dizisi tanımlar.

- **PreventDllBinding**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bağlı resmin bağlı olmaması gerektiğini *Bind.exe* gösterir.

  Daha fazla bilgi için bkz. [/Allowbind (dll bağlamasını engelle)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , **performans araçları** Profilcisi ile kullanılabilecek bir çıkış dosyası üretir.

  Daha fazla bilgi için bkz. [/profile (performans araçları profil Oluşturucu)](/cpp/build/reference/profile-performance-tools-profiler).

- **Profilekılavuz Ddatabase**

  İsteğe bağlı **dize** parametresi.

  Çalışan programla ilgili bilgileri tutmak için kullanılacak *. pgd* dosyasının adını belirtir

  Daha fazla bilgi için bkz. [/PGD (Profil temelli iyileştirmeler için veritabanını belirt)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  İsteğe bağlı **dize** parametresi.

  Bağlayıcının oluşturduğu program veritabanı (PDB) için bir ad belirtir.

  Daha fazla bilgi için bkz. [/pdb (program veritabanını kullan)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , Windows *Adres alanı düzeni rastgele seçme* (ASLR) özelliğini kullanarak yükleme zamanında rastgele bir şekilde yeniden temellendiren yürütülebilir bir görüntü oluşturur.

  Daha fazla bilgi için bkz. [/DynamicBase (adres boşluğu düzeni rastgele seçimini kullan)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RegisterOutput**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bu derleme için birincil çıktıyı kaydeder.

- **Sectionhizalaması**

  İsteğe bağlı **tamsayı** parametresi.

  Programın doğrusal adres alanındaki her bölümün hizalamasını belirtir. Parametre değeri bir birim bayt sayısıdır ve ikinin gücünden oluşur.

  Daha fazla bilgi için bkz. [/align (Bölüm hizalaması)](/cpp/build/reference/align-section-alignment).

- **SetChecksum**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , *.exe* bir dosyanın üst bilgisindeki sağlama toplamını ayarlar.

  Daha fazla bilgi için bkz. [/Release (sağlama toplamını ayarla)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  İsteğe bağlı **dize** parametresi.

  Bağlama işlemi için ilerleme raporlarının ayrıntı düzeyini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** - *\<none>*

  - **Linkverbose**  -  **/Verbose**

  - **LinkVerboseLib**  -  **/Verbose: lib**

  - **LinkVerboseICF**  -  **/verbose: ICF**

  - **LinkVerboseREF**  -  **/verbose: ref**

  - **LinkVerboseSAFESEH**  -  **/verbose: SafeSEH**

  - **LinkVerboseCLR**  -  **/verbose: clr**

  Daha fazla bilgi için bkz. [/verbose (ilerleme Iletilerini Yazdır)](/cpp/build/reference/verbose-print-progress-messages).

- **Kaynaklar**

  Gerekli `ITaskItem[]` parametre.

  görevler tarafından tüketilen ve yayılan MSBuild kaynak dosya öğelerinin dizisini tanımlar.

- **Belirtilen Yılözniteliklerini**

  İsteğe bağlı **dize** parametresi.

  Bir bölümün özniteliklerini belirtir. Bu, bölüm için *. obj* dosyası derlendiğinde ayarlanan öznitelikleri geçersiz kılar.

  Daha fazla bilgi için bkz. [/section (bölüm özniteliklerini belirt)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize**

  İsteğe bağlı **dize** parametresi.

  Ek bellek tahsis edildiğinde her bir ayırdaki fiziksel bellek miktarını belirtir.

  Daha fazla bilgi için bkz `commit` . [/Stack (yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations)bağımsız değişkeni.

- **Stackrezervesize**

  İsteğe bağlı **dize** parametresi.

  Sanal bellekteki toplam yığın ayırma boyutunu belirtir.

  Daha fazla bilgi için bkz `reserve` . [/Stack (yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations)bağımsız değişkeni.

- **StripPrivateSymbols**

  İsteğe bağlı **dize** parametresi.

  Müşterilerinize dağıtmak istemediğiniz sembolleri atlatabilecek ikinci program veritabanı (PDB) dosyası oluşturur. İkinci PDB dosyasının adını belirtin.

  Daha fazla bilgi için bkz. [/Pdbçıkarıldı (özel sembolleri Strip)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Sistemin**

  İsteğe bağlı **dize** parametresi.

  Yürütülebilir dosyanın ortamını belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** - *\<none>*

  - **Konsol**  -  **/Subsystem: Console**

  - **Windows**  -  **/Subsystem: WINDOWS**

  - **Yerel**  -  **/Subsystem: NATIVE**

  - **EFI uygulaması**  -  **/Subsystem: EFI_APPLICATION**

  - **EFI Önyükleme hizmeti sürücüsü**  -  **/Subsystem: EFI_BOOT_SERVICE_DRIVER**

  - **EFı ROM**  -  **/Subsystem: EFI_ROM**

  - **EFI çalışma zamanı**  -  **/Subsystem: EFI_RUNTIME_DRIVER**

  - **WindowsCE**  -  **/Subsystem: WINDOWSCE**

  - **POSIX**  -  **/Subsystem: POSIX**

  Daha fazla bilgi için bkz. [/Subsystem (alt sistemi belirt)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bağlayıcının son görüntüde bağlanabilir bir Içeri aktarma adres tablosu (ıAT) içermeyeceğini söyler.

  Daha fazla bilgi için `NOBIND` [/Delay (yük içeri aktarma ayarlarını geciktir)](/cpp/build/reference/delay-delay-load-import-settings)bağımsız değişkenine bakın.

- **SupportUnloadOfDelayLoadedDLL**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` gecikme yüklemesi yardımcı işlevine DLL'nin açık olarak kaldırmayı desteklemesi söyler.

  Daha fazla bilgi için `UNLOAD` [/DELAY (Gecikme yükü içeri aktarma ayarları) bağımsız değişkenine bakın.](/cpp/build/reference/delay-delay-load-import-settings)

- **SuppressStartupBanner**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.

  Daha fazla bilgi için bkz. [/NOLOGO (Başlangıç başlığı gizleme) (bağlantılayıcı)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  İsteğe **bağlı Boole parametresi.**

  ise, işletim sistemine önce bağlantıcı çıktısını bir takas dosyasına kopyalamasını ve ardından `true` görüntüyü orada çalıştırmasını söyler.

  Daha fazla bilgi için `CD` [/SWAPRUN (Bağlantıcı çıktısını takas dosyasına yükle) bağımsız değişkenine bakın.](/cpp/build/reference/swaprun-load-linker-output-to-swap-file) Ayrıca bkz. **SwapRunFromNET** parametresi.

- **SwapRunFromNET**

  İsteğe **bağlı Boole parametresi.**

  ise, işletim sistemine önce bağlantıcı çıktısını bir takas dosyasına kopyalamasını ve ardından `true` görüntüyü orada çalıştırmasını söyler.

  Daha fazla bilgi için `NET` [/SWAPRUN (Bağlantıcı çıktısını takas dosyasına yükle) bağımsız değişkenine bakın.](/cpp/build/reference/swaprun-load-linker-output-to-swap-file) Ayrıca, bu **tablodaki SwapRunFromCD** parametresine bakın.

- **TargetMachine**

  İsteğe **bağlı Dize** parametresi.

  Program veya DLL için hedef platformu belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Notset** - *\<none>*

  - **MachineARM**  -  **/MACHINE:ARM**

  - **MachineEBC**  -  **/MACHINE:EBC**

  - **MachineIA64**  -  **/MACHINE:IA64**

  - **MachineMIPS**  -  **/MACHINE:MIPS**

  - **MachineMIPS16**  -  **/MACHINE:MIPS16**

  - **MachineMIPSFPU**  -  **/MACHINE:MIPSFPU**

  - **MachineMIPSFPU16**  -  **/MACHINE:MIPSFPU16**

  - **MachineSH4**  -  **/MACHINE:SH4**

  - **MachineTHUMB**  -  **/MACHINE:THUMB**

  - **MachineX64**  -  **/MACHINE:X64**

  - **MachineX86**  -  **/MACHINE:X86**

  Daha fazla bilgi için bkz. [/MACHINE (Hedef platformu belirtin)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` program görüntüsünün isteğe IMAGE_OPTIONAL_HEADER dllCharacteristics alanında bir bayrak ayarlar. Bu bayrak ayarlanırsa, Terminal Sunucusu uygulamada belirli değişiklikler yapmaz.

  Daha fazla bilgi için bkz. [/TSAWARE (Terminal Sunucusu'na uygun uygulama oluşturma)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  İsteğe **bağlı Dize** parametresi.

  İzleyici günlüğünün dizinini belirtir.

- **TreatLinkerWarningAsErrors**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bağlantıcı bir uyarı oluşturursa hiçbir çıkış dosyası oluşturulmaz.

  Daha fazla bilgi için bkz. [/WX (Bağlantıcı uyarılarını hata olarak davran)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` geçerli çıkış dosyası için bir derleme derlemesi olmadan .NET Framework oluşturur.

  Daha fazla bilgi için bkz. [/NOASSEMBLY (MSIL modülü oluşturma)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypeLibraryFile**

  İsteğe **bağlı Dize** parametresi.

  *.tlb* dosyasının dosya adını ve dosya adı uzantısını belirtir. Bir dosya adı veya yol ve dosya adı belirtin.

  Daha fazla bilgi için bkz. [/TLBOUT (.tlb dosyası adı)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  İsteğe **bağlı Tamsayı** parametresi.

  Bir bağlantıcı tarafından oluşturulan tür kitaplığı için kullanıcı tarafından belirtilen bir değer verir. 1 ile 65535 arasında bir değer belirtin.

  Daha fazla bilgi için bkz. [/TLBID (TypeLib için kaynak kimliğini belirtin)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  İsteğe **bağlı Dize** parametresi.

  Kullanıcı Hesabı Denetimi altında çalıştırıldıklarından uygulama için istenen yürütme düzeyini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Asınvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  Daha fazla bilgi için `level` bkz. [/MANIFESTUAC (Bildirime UAC bilgileri ekleme)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)bağımsız değişkeni.

- **UACUIAccess**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` uygulama kullanıcı arabirimi koruma düzeylerini atlar ve masaüstünde daha yüksek izinli pencerelere giriş sürücüleri; aksi takdirde, `false` .

  Daha fazla bilgi için `uiAccess` bkz. [/MANIFESTUAC (Bildirime UAC bilgileri ekleme)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)bağımsız değişkeni.

- **UseLibraryDependencyInputs**

  İsteğe **bağlı Boole parametresi.**

  ise, kitaplık dosyasının kendisi yerine kitaplık aracına yapılan girişler, proje bağımlılıklarının kitaplık çıkışları içinde `true` bağlı olduğunda kullanılır.

- **Sürüm**

  İsteğe **bağlı Dize** parametresi.

  .exeveya *.dll.*  " " `major[.minor]` belirtin. ve `major` bağımsız `minor` değişkenleri 0 ile 65535 arasında ondalık sayılardır.

  Daha fazla bilgi için bkz. [/VERSION (Sürüm bilgileri)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
