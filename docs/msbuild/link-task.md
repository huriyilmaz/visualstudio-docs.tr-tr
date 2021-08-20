---
title: Görev | Microsoft Docs
description: COFF MSBuild kitaplıklarına bağlantı olan Microsoft C++ link.exe aracını sarmak için Bağlantı görevini nasıl kullandığını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108700"
---
# <a name="link-task"></a>Bağlantı görevi

Microsoft C++ bağlama aracını sarmalar ve *link.exe.* Bağlantı aracı, yürütülebilir (.exe *)* dosyası veya dinamik bağlantı kitaplığı (DLL) oluşturmak için Ortak Nesne Dosyası Biçimi (COFF) nesne dosyalarını ve kitaplıklarını bağlar. Daha fazla bilgi için, [bkz. Linker](/cpp/build/reference/linker-options) [seçenekleri ve Komut MSBuild'i](/cpp/build/msbuild-visual-cpp) kullanma ve [komut satırına ait Microsoft C++ araç kümesi kullanma.](/cpp/build/building-on-the-command-line)

## <a name="parameters"></a>Parametreler

 Aşağıda Bağlantı görevinin parametreleri **açık** almaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelen bir seçenektir.

- **Ek Bağımlılıklar**

  İsteğe **bağlı String[]** parametresi.

  Komutuna eklenecek giriş dosyalarının listesini belirtir.

  Daha fazla bilgi için bkz. [LINK giriş dosyaları.](/cpp/build/reference/link-input-files)

- **AdditionalLibraryDirectories**

  İsteğe **bağlı String[]** parametresi.

  Ortam kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.

  Daha fazla bilgi için bkz. [/LIBPATH (Ek Libpath)](/cpp/build/reference/libpath-additional-libpath).

- **AdditionalManifestDependencies**

  İsteğe **bağlı String[]** parametresi.

  Bildirim dosyasının bölümüne yerleştirilecek `dependency` öznitelikleri belirtir.

  Daha fazla bilgi için bkz. [/MANIFESTDEPENDENCY (Bildirim bağımlılıklarını belirtin)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Ayrıca [bkz. Publisher dosyaları.](/windows/desktop/SbsCs/publisher-configuration-files)

- **AdditionalOptions**

  İsteğe **bağlı Dize** parametresi.

  Komut satırda belirtilen bağlantıcı seçeneklerinin listesi. Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir Bağlantı görevi parametresiyle temsil etmeyen bağlantıcı seçeneklerini belirtmek için **bu** parametreyi kullanın.

  Daha fazla bilgi için [bkz. Linker seçenekleri.](/cpp/build/reference/linker-options)

- **AddModuleNamesToAssembly**

  İsteğe **bağlı String[]** parametresi.

  Bir derlemeye modül başvurusu ekler.

  Daha fazla bilgi için bkz. [/ASSEMBLYMODULE (Derlemeye MSIL modülü ekleme)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **allowIsolation**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` işletim sisteminin bildirim aramaları ve yüklemeleri yapmalarını sağlar. `false`ise, URL'lerin bildirim yok gibi yükleniyor olduğunu gösterir.

  Daha fazla bilgi için bkz. [/ALLOWISOLATION (Bildirim arama)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug**

  İsteğe **bağlı Boole parametresi.**

  , `true` hata ayıklama bilgileri izleme ile birlikte **DebuggableAttribute** özniteliğini yalıtır ve JIT iyileştirmelerini devre dışı gösterir. ise, `false` **DebuggableAttribute özniteliğini** yalıtır, ancak hata ayıklama bilgileri izlemesini devre dışı bırakarak JIT iyileştirmelerini sağlar.

  Daha fazla bilgi için bkz. [/ASSEMBLYDEBUG (DebuggableAttribute Ekle)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkResource**

  İsteğe **bağlı String[]** parametresi.

  Çıkış dosyasında .NET Framework bir bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmaz. Kaynağın adını belirtin.

  Daha fazla bilgi için bkz. [/ASSEMBLYLINKRESOURCE (.NET Framework bağlantısı)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Örtülü **Boole parametresi.**

  Bağlantı artımlı davranışını yakalamak için daha derin dosya izleme sağlar. Her zaman `true` döndürür.

- **Baseaddress**

  İsteğe **bağlı Dize** parametresi.

  Yerleşik program veya DLL için bir temel adres ayarlar. `{address[,size] | @filename,key}` belirtin.

  Daha fazla bilgi için bkz. [/BASE (Temel adres)](/cpp/build/reference/base-base-address).

- **BuildingInIDE**

  İsteğe **bağlı Boole parametresi.**

  true ise, IDE'MSBuild çağrılır. Aksi takdirde, MSBuild komut satırı çağrılır.

  Bu parametrenin eşdeğer bir bağlantı seçeneği yoktur.

- **CLRImageType**

  İsteğe **bağlı Dize** parametresi.

  Ortak dil çalışma zamanı (CLR) görüntüsünün türünü ayarlar.

  Her biri bir bağlantıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *\<none>*

  - **ForceIJWImage**  -  **/CLCRIAGETYPE:IJW**

  - **ForcePureILImage**  -  **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage**  -  **/CLRIMAGETYPE:SAFE**

  Daha fazla bilgi için bkz. [/CLRIMAGETYPE (CLR görüntüsünün türünü belirtin)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSupportLastError**

  İsteğe **bağlı Dize** parametresi.

  P/Invoke mekanizması aracılığıyla çağrılan işlevlerin son hata kodunu korur.

  Her biri bir bağlantıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin**  -  **/CLRSupportLastError**

  - **Devre dışı**  -  **/CLRSupportLastError:NO**

  - **SystemDlls**  -  **/CLRSupportLastError:SYSTEMDLL**

  Daha fazla bilgi için bkz. [/CLRSUPPORTLASTERROR (PInvoke](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls)çağrıları için son hata kodunu koru) .

- **CLRThreadAttribute**

  İsteğe **bağlı Dize** parametresi.

  CLR programınıza giriş noktası için iş parçacığı özniteliğini açıkça belirtir.

  Her biri bir bağlantıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **DefaultThreadingAttribute**  -  **/CLRTHREADATTRIBUTE:NONE**

  - **MTAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE:MTA**

  - **STAThreadingAttribute**  -  **/CLRTHREADATTRIBUTE:STA**

  Daha fazla bilgi için bkz. [/CLRTHREADATTRIBUTE (CLR iş parçacığı özniteliğini ayarla)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  İsteğe **bağlı Boole parametresi.**

  Bağlantılayıcının yönetilen koddan yerel URL'lere bağlantı oluşturan P/Invoke çağrılarına **SuppressUnmanagedCodeSecurityAttribute** uygulayıp uygulamaymayacaklarını belirtir.

  Daha fazla bilgi için bkz. [/CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute Ekle)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  İsteğe **bağlı Dize** parametresi.

  Bir görüntüyü düzeltme eki uygulama için hazırlar.

  Bir bağlantı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin**  -  **/FUNCTIONPADMIN**

  - **X86Image**  -  **/FUNCTIONPADMIN:5**

  - **X64Image**  -  **/FUNCTIONPADMIN:6**

  - **ItaniumImage**  -  **/FUNCTIONPADMIN:16**

  Daha fazla bilgi için bkz. [/FUNCTIONPADMIN (Hotpatchable görüntüsü oluşturma)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bir yürütülebilir dosyanın Veri Yürütme Önleme özelliğiyle uyumlu Windows olduğunu gösterir.

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

  Çekirdek modu sürücüsü oluşturmak için Windows NT parametresini belirtin.

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

  Daha fazla bilgi için `ICF[= iterations]` bkz. [/OPT (İyileştirmeler) bağımsız değişkeni.](/cpp/build/reference/opt-optimizations)

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

  ise, `true` yalnızca tercih edilen temel adrese yüklenemedi bir program veya DLL oluşturur.

  Daha fazla bilgi için bkz. [/FIXED (Sabit temel adres)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  İsteğe **bağlı Dize** parametresi.

  Bir sembole başvurulsa ama *tanımlanmamışsa veya* çarp tanımlı olsa bile,.exedosya veya DLL için geçerli bir dosya veya DLL oluşturması için linker'a söyler.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin**  -  **/FORCE**

  - **MultiplyDefinedSymbolOnly**  -  **/FORCE:MULTIPLE**

  - **UndefinedSymbolOnly**  -  **/FORCE:UNSOLVED**

  Daha fazla bilgi için bkz. [/FORCE (Dosya çıkışını zorla)](/cpp/build/reference/force-force-file-output).

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

  ise, `true` bu yapılandırma tarafından oluşturulan içeri aktarma kitaplığının bağımlı projelere içeri aktarılmaz gerektiğini belirtir.

  Bu parametre bir bağlantı seçeneğine karşılık gelen bir parametre değildir.

- **IgnoreSpecificDefaultLibraries**

  İsteğe **bağlı String[]** parametresi.

  Yoksaymak için bir veya daha fazla varsayılan kitaplık adı belirtir. Noktalı virgül kullanarak birden çok kitaplığı ayırma.

  Daha fazla bilgi için bkz. [/NODEFAULTLIB (Kitaplıkları yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  İsteğe **bağlı Boole parametresi.**

  ise, yalnızca görüntünün güvenli özel durum işleyicilerinin bir tabloyu da `true` üreteci bir görüntü üretir.

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

  Bu parametre bir bağlantı seçeneğine karşılık gelen bir parametre değildir.

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

  Örtülü **String[]** parametresi.

  Bağlantılı nesne dosyalarını belirtir.

- **İyileştirReferences**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` hiçbir zaman başvurulmamış işlevleri ve/veya verileri ortadan kaldırıyor.

  Daha fazla bilgi için `REF` [/OPT (İyileştirmeler) içinde bağımsız değişkenine bakın.](/cpp/build/reference/opt-optimizations)

- **Outputfile**

  İsteğe **bağlı Dize** parametresi.

  Bağlantının oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar.

  Daha fazla bilgi için bkz. [/OUT (Çıktı dosyası adı)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  İsteğe **bağlı Boole parametresi.**

  ve `true` Yazma Çıkışı etkinse, kayıt defteri yazmalarını **HKEY_CLASSES_ROOT'ye** yeniden yönlendirilmesi için **HKEY_CURRENT_USER.**

- **PreprocessOutput**

  İsteğe `ITaskItem[]` bağlı parametre.

  Görevler tarafından tüketilen ve yayılan bir önişlemci çıkış öğeleri dizisi tanımlar.

- **PreventDllBinding**

  İsteğe **bağlı Boole parametresi.**

  `true`ise, bağlı *Bind.exe* bağlı olmadığını gösterir.

  Daha fazla bilgi için bkz. [/ALLOWBIND (DLL bağlamayı engelle)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` Performans Araçları profilleyicisi ile kullanılan bir **çıkış** dosyası üretir.

  Daha fazla bilgi için bkz. [/PROFILE (Performans Araçları profilleyicisi)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

  İsteğe **bağlı Dize** parametresi.

  Çalışan programla ilgili bilgileri tutmak için kullanılacak *.pgd* dosyasının adını belirtir

  Daha fazla bilgi için bkz. [/PGD (Profil kılavuzlu iyileştirmeler için veritabanını belirtin)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  İsteğe **bağlı Dize** parametresi.

  Bağlantıcının oluşturduğu program veritabanı (PDB) için bir ad belirtir.

  Daha fazla bilgi için bkz. [/PDB (Program veritabanını kullanma)](/cpp/build/reference/pdb-use-program-database).

- **RandomizedBaseAddress**

  İsteğe **bağlı Boole parametresi.**

  ise, dosyanın adres alanı düzeni rastgeleleştirme `true` (ASLR)  özelliğini kullanarak yükleme zamanında rastgele olarak yeniden Windows.

  Daha fazla bilgi için bkz. [/DYNAMICBASE (Adres alanı düzenini rastgele kullanma)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **RegisterOutput**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bu derlemenin birincil çıkışını kaydeder.

- **SectionAlignment**

  İsteğe **bağlı Tamsayı** parametresi.

  Programın doğrusal adres alanı içindeki her bölümün hizalamasını belirtir. Parametre değeri, birim bayt sayısıdır ve iki güçtür.

  Daha fazla bilgi için bkz. [/ALIGN (Bölüm hizalaması)](/cpp/build/reference/align-section-alignment).

- **SetChecksum**

  İsteğe **bağlı Boole parametresi.**

  ise, `true` bir dosyanın üst bilgisinde sağlama *.exe* ayarlar.

  Daha fazla bilgi için bkz. [/RELEASE (Sağlamayı ayarlama)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  İsteğe **bağlı Dize** parametresi.

  Bağlama işlemi için ilerleme durumu raporlarının ayrıntılılıklarını belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Notset** - *\<none>*

  - **LinkVerbose**  -  **/VERBOSE**

  - **LinkVerboseLib**  -  **/VERBOSE:Lib**

  - **LinkVerboseICF**  -  **/VERBOSE:ICF**

  - **LinkVerboseREF**  -  **/VERBOSE:REF**

  - **LinkVerboseSAFESEH**  -  **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR**  -  **/VERBOSE:CLR**

  Daha fazla bilgi için bkz. [/VERBOSE (İlerleme iletilerini yazdırma)](/cpp/build/reference/verbose-print-progress-messages).

- **Kaynaklar**

  Gerekli `ITaskItem[]` parametre.

  Görevler tarafından tüketilebilir MSBuild kaynak dosya öğeleri içeren bir dizi tanımlar.

- **SpecifySectionAttributes**

  İsteğe **bağlı Dize** parametresi.

  Bir bölümün özniteliklerini belirtir. Bu, bölümün .obj dosyası *derlenmişken* ayarlanmış öznitelikleri geçersiz kılar.

  Daha fazla bilgi için bkz. [/SECTION (Bölüm özniteliklerini belirtin)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize**

  İsteğe **bağlı Dize** parametresi.

  Ek bellek ayrılırken her ayırmada fiziksel bellek miktarını belirtir.

  Daha fazla bilgi için `commit` bkz. [/STACK (Yığın ayırmaları) bağımsız değişkeni.](/cpp/build/reference/stack-stack-allocations)

- **StackReserveSize**

  İsteğe **bağlı Dize** parametresi.

  Sanal bellekte toplam yığın ayırma boyutunu belirtir.

  Daha fazla bilgi için `reserve` bkz. [/STACK (Yığın ayırmaları) bağımsız değişkeni.](/cpp/build/reference/stack-stack-allocations)

- **StripPrivateSymbols**

  İsteğe **bağlı Dize** parametresi.

  Müşterilerinize dağıtmak istemeyebilirsiniz sembolleri atlar ikinci bir program veritabanı (PDB) dosyası oluşturur. İkinci PDB dosyasının adını belirtin.

  Daha fazla bilgi için bkz. [/PDBSTRIPPED (Özel sembolleri şeritle)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Alt**

  İsteğe **bağlı Dize** parametresi.

  Yürütülebilir dosyanın ortamını belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Notset** - *\<none>*

  - **Konsol**  -  **/SUBSYSTEM:CONSOLE**

  - **Windows**  -  **/SUBSYSTEM:WINDOWS**

  - **Yerel**  -  **/SUBSYSTEM:NATIVE**

  - **EFI Uygulaması**  -  **/SUBSYSTEM:EFI_APPLICATION**

  - **EFI Önyükleme Hizmeti Sürücüsü**  -  **/SUBSYSTEM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM**  -  **/SUBSYSTEM:EFI_ROM**

  - **EFI Çalışma Zamanı**  -  **/SUBSYSTEM:EFI_RUNTIME_DRIVER**

  - **WindowsCE**  -  **/SUBSYSTEM:WINDOWSCE**

  - **POSIX**  -  **/SUBSYSTEM:POSIX**

  Daha fazla bilgi için bkz. [/SUBSYSTEM (Alt sistemi belirtin)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  İsteğe **bağlı Boole parametresi.**

  ise, bağlayıcıya son görüntüye bağlanabilir bir İçeri Aktarma `true` Adresi Tablosu (IAT) dahil edilemez.

  Daha fazla bilgi için `NOBIND` [/DELAY (Gecikme yükü içeri aktarma ayarları) bağımsız değişkenine bakın.](/cpp/build/reference/delay-delay-load-import-settings)

- **SupportUnloadOfDelayLoadedDLL**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , gecikme Yükleme Yardımcısı IŞLEVINE dll 'nin açıkça kaldırılmasını desteklediğini söyler.

  Daha fazla bilgi için `UNLOAD` [/Delay (yük içeri aktarma ayarlarını geciktir)](/cpp/build/reference/delay-delay-load-import-settings)bağımsız değişkenine bakın.

- **SuppressStartupBanner**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.

  Daha fazla bilgi için bkz. [/nologo (başlangıç başlığını gösterme) (bağlayıcı)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  İsteğe bağlı **Boolean** parametresi.

  `true`, İşletim sistemine önce bağlayıcı çıkışını bir takas dosyasına kopyalamasını söyler ve sonra görüntüyü oradan çalıştırır.

  Daha fazla bilgi için bkz `CD` . [/SWAPRUN (bağlayıcı çıktısını takas dosyasına yükle)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)bağımsız değişkeni. Ayrıca bkz. **SwapRunFromNet** parametresi.

- **SwapRunFromNET**

  İsteğe bağlı **Boolean** parametresi.

  `true`, İşletim sistemine önce bağlayıcı çıkışını bir takas dosyasına kopyalamasını söyler ve sonra görüntüyü oradan çalıştırır.

  Daha fazla bilgi için bkz `NET` . [/SWAPRUN (bağlayıcı çıktısını takas dosyasına yükle)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)bağımsız değişkeni. Ayrıca bkz. bu tablodaki **SwapRunFromCD** parametresi.

- **TargetMachine**

  İsteğe bağlı **dize** parametresi.

  Program veya DLL için hedef platformu belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** - *\<none>*

  - **Machineard**  -  **/Machine: ARM**

  - **Machineebc**  -  **/Machine: EBC**

  - **MachineIA64**  -  **/MACHINE: IA64**

  - **Machinemıps**  -  **/MACHINE: MIPS**

  - **MachineMIPS16**  -  **/MACHINE: kayıtlardan biri mıps16**

  - **Machinemıpsfpu**  -  **/MACHINE: MIPSFPU**

  - **MachineMIPSFPU16**  -  **/MACHINE: MIPSFPU16**

  - **MachineSH4**  -  **/MACHINE: sh4**

  - **Machinethumb**  -  **/MACHINE: Thumb**

  - **MachineX64**  -  **/Machine: x64**

  - **MachineX86**  -  **/Machine: x86**

  Daha fazla bilgi için bkz. [/Machine (hedef platformu belirt)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  İsteğe bağlı **Boolean** parametresi.

  `true`, Program görüntüsünün isteğe bağlı üst bilgisindeki IMAGE_OPTIONAL_HEADER Dllözellikler alanında bir bayrak ayarlar. Bu bayrak ayarlandığında, Terminal sunucusu uygulamada belirli değişiklikler yapmayacak.

  Daha fazla bilgi için bkz. [/T saware (Terminal Server 'ı algılayan uygulama oluşturma)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  İsteğe bağlı **dize** parametresi.

  İzleyici günlüğünün dizinini belirtir.

- **TreatLinkerWarningAsErrors**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bağlayıcı bir uyarı oluşturursa çıkış dosyası üretilmez.

  Daha fazla bilgi için bkz. [/WX (bağlayıcı uyarılarını hata olarak işle)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  İsteğe bağlı **Boolean** parametresi.

  varsa `true` , geçerli çıkış dosyası için .NET Framework derlemesi olmadan bir görüntü oluşturur.

  Daha fazla bilgi için bkz. [/NOASSEMBLY (MSIL Modülü oluşturma)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypeLibraryFile**

  İsteğe bağlı **dize** parametresi.

  *. Tlb* dosyasının dosya adı ve dosya adı uzantısını belirtir. Bir dosya adı veya yol ve dosya adı belirtin.

  Daha fazla bilgi için bkz. [/Tlhakkında (ad. tlb dosyası)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  İsteğe bağlı **tamsayı** parametresi.

  Bağlayıcı tarafından oluşturulan tür kitaplığı için Kullanıcı tarafından belirtilen bir değer belirtir. 1 ile 65535 arasında bir değer belirtin.

  Daha fazla bilgi için bkz. [/Tldeklarasyon (TypeLib için kaynak Kimliğini Belirt)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **Uıacexecutionlevel**

  İsteğe bağlı **dize** parametresi.

  Kullanıcı hesabı denetimiyle birlikte çalıştırıldığında, uygulama için istenen yürütme düzeyini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **AsInvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  Daha fazla bilgi için bkz `level` . [/Bildiriestuac bağımsız değişkeni (bildirimdeki UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **Uıacuıaccess**

  İsteğe bağlı **Boolean** parametresi.

  `true`Uygulama, Kullanıcı arabirimi koruma düzeylerini ve sürücüler girişini masaüstündeki daha yüksek izin üzerine atlar; Aksi takdirde, `false` .

  Daha fazla bilgi için bkz `uiAccess` . [/Bildiriestuac bağımsız değişkeni (bildirimdeki UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **Uselibrarydependencygirdileri**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , proje bağımlılıklarının kitaplık çıkışları ile bağlantılı olduğunda kitaplık dosyasının kendisi yerine kütüphaneian aracının girişleri kullanılır.

- **Sürüm**

  İsteğe bağlı **dize** parametresi.

  *.exe* veya *.dll* dosyasının üstbilgisine bir sürüm numarası koyun. " `major[.minor]` " Belirtin. `major`Ve `minor` bağımsız değişkenleri 0 ile 65535 arasında ondalık sayılardır.

  Daha fazla bilgi için bkz. [/Version (sürüm bilgileri)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
