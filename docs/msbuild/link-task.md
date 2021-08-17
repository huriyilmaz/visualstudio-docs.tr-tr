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
ms.openlocfilehash: e225ca9b342b7808a5cc30beb69a63bc543c62def756ecd1754b908f9e49f0b0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443353"
---
# <a name="link-task"></a>Bağlantı görevi

Microsoft C++ bağlama aracını sarmalar ve *link.exe.* Bağlantı aracı, yürütülebilir (.exe) dosyası veya dinamik bağlantı kitaplığı (DLL) oluşturmak için Ortak Nesne *Dosyası* Biçimi (COFF) nesne dosyalarını ve kitaplıklarını bağlar. Daha fazla bilgi için, [bkz. Linker](/cpp/build/reference/linker-options) [seçenekleri ve Komut MSBuild'i](/cpp/build/msbuild-visual-cpp) kullanma ve komut [satırına ait Microsoft C++ araç kümesi kullanma.](/cpp/build/building-on-the-command-line)

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

  Çıkış dosyasında .NET Framework kaynağına bir bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmaz. Kaynağın adını belirtin.

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

  Yoksaymak için bir veya daha fazla varsayılan kitaplık adı belirtir. Noktalı virgülle ayırarak birden çok kitaplığı ayırın.

  Daha fazla bilgi için bkz. [/nodefaultlib (kitaplıkları Yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **Imagehassafeexceptionhandlers**

  İsteğe bağlı **Boolean** parametresi.

  Varsa `true` , bağlayıcı yalnızca görüntünün güvenli özel durum işleyicilerinin bir tablosunu da üretebilir bir görüntü oluşturur.

  Daha fazla bilgi için bkz. [/SafeSEH (görüntü güvenli özel durum işleyicilerine sahiptir)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Varsayılan kitaplık adının yerini alan, Kullanıcı tarafından belirtilen bir içeri aktarma kitaplığı adı.

  Daha fazla bilgi için bkz. [/ımplib (ad içeri aktarma kitaplığı)](/cpp/build/reference/implib-name-import-library).

- **KeyContainer**

  İsteğe bağlı **dize** parametresi.

  İmzalı bir derleme için anahtarı içeren kapsayıcı.

  Daha fazla bilgi için bkz. [/keycontainer (bir derlemeyi imzalamak için bir anahtar kapsayıcısı belirtin)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Ayrıca bkz. bu tablodaki **keyfile** parametresi.

- **Dosyasına**

  İsteğe bağlı **dize** parametresi.

  İmzalı bir derleme için anahtarı içeren bir dosyayı belirtir.

  Daha fazla bilgi için bkz. [/keyfile (bir derlemeyi imzalamak için anahtar veya anahtar çiftini belirtin)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Ayrıca, bkz. **keycontainer** parametresi.

- **LargeAddressAware**

  İsteğe bağlı **Boolean** parametresi.

  `true`Uygulama, 2 gigabayt 'tan daha büyük adresleri işleyebilir.

  Daha fazla bilgi için bkz. [/LARGEADDRESSAWARE (büyük adresleri işleme)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , ana çıkış dosyası olarak BIR DLL oluşturur.

  Daha fazla bilgi için bkz. [/dll (dll derleme)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  İsteğe bağlı **dize** parametresi.

  İç derleyici hatası (ıCE) bilgilerini doğrudan Microsoft 'a sağlamanıza olanak tanır.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Noerrorreport**  -  **/errorreport: yok**

  - **Hemen sor**  -  **/errorreport: Prompt**

  - **Queuefornextlogin**  -  **/errorreport: kuyruk**

  - **Senderrorreport**  -  **/errorreport: gönder**

  Daha fazla bilgi için bkz. [/errorreport (iç bağlayıcı hatalarını raporla)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **Linkıncreıncre**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , artımlı bağlamayı mümkün.

  Daha fazla bilgi için bkz. [/ıncreıncre(artımlı bağlantı)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , proje bağımlılıklarından kitaplık çıktılarının otomatik olarak bağlandığını belirtir.

  Bu parametre bir bağlayıcı seçeneğine karşılık gelmiyor.

- **Bağlantı durumu**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bağlayıcının bağlantının yüzdesini gösteren bir ilerleme göstergesi görüntüleneceğini belirtir.

  Daha fazla bilgi için `STATUS` [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation)bağımsız değişkenine bakın.

- **LinkTimeCodeGeneration**

  İsteğe bağlı **dize** parametresi.

  Profil temelli iyileştirme seçeneklerini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılanını** - *\<none>*

  - **Uselinktimecodegeneration**  -  **/LTCG**

  - **PGINSTRUMENT**  -  **/LTCG: PGINSTRUMENT**

  - **Pgoptimization**  -  **/LTCG: PGOptimize**

  - **PGUpdate**

    \-**/LTCG: PGUpdate**

  Daha fazla bilgi için bkz. [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation).

- **MANIFESTFILE**

  İsteğe bağlı **dize** parametresi.

  Varsayılan bildirim dosyası adını belirtilen dosya adı olarak değiştirir.

  Daha fazla bilgi için bkz. [/ManifestFile (ad bildirim dosyası)](/cpp/build/reference/manifestfile-name-manifest-file).

- **Mapdışarı aktarmalar**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bağlayıcının bir eşleme dosyasına aktarılmış işlevleri içermesini söyler.

  Daha fazla bilgi için bkz `EXPORTS` . [/MapInfo bağımsız değişkeni (mapfile Içinde bilgi ekleme)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **MapFileName**

  İsteğe bağlı **dize** parametresi.

  Varsayılan eşleme dosyası adını belirtilen dosya adıyla değiştirir.

- **MergedIDLBaseFileName**

  İsteğe bağlı **dize** parametresi.

  *. IDL* dosyasının dosya adı ve dosya adı uzantısını belirtir.

  Daha fazla bilgi için bkz. [/IDLOUT (MıDL çıktı dosyalarını Adlandır)](/cpp/build/reference/idlout-name-midl-output-files).

- **MergeSections**

  İsteğe bağlı **dize** parametresi.

  Bir görüntüdeki bölümleri birleştirir. `from-section=to-section` belirtin.

  Daha fazla bilgi için bkz. [/merge (bölümleri birleştirme)](/cpp/build/reference/merge-combine-sections).

- **Mıdlcommandfile**

  İsteğe bağlı **dize** parametresi.

  MıDL komut satırı seçeneklerini içeren bir dosyanın adını belirtin.

  Daha fazla bilgi için bkz. [/MIDL (MIDL komut satırı seçeneklerini belirtin)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **MinimumRequiredVersion**

  İsteğe bağlı **dize** parametresi.

  Alt sistemin gerekli en düşük sürümünü belirtir. Bağımsız değişkenler 0 ile 65535 aralığındaki ondalık sayılardır.

- **ModuleDefinitionFile**

  İsteğe bağlı **dize** parametresi.

  [Modül tanım dosyasının](/cpp/build/reference/module-definition-dot-def-files)adını belirtir.

  Daha fazla bilgi için bkz. [/def (modül tanım dosyasını belirt)](/cpp/build/reference/def-specify-module-definition-file).

- **MSDOSStubFileName**

  İsteğe bağlı **dize** parametresi.

  Belirtilen MS-DOS saplama programını bir Win32 programına iliştirir.

  Daha fazla bilgi için bkz. [/stub (MS-DOS saplama dosyası adı)](/cpp/build/reference/stub-ms-dos-stub-file-name).

- **NoEntryPoint**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` yalnızca kaynak dll 'i belirtir.

  Daha fazla bilgi için bkz. [/NOENTRY (giriş noktası yok)](/cpp/build/reference/noentry-no-entry-point).

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

  Daha fazla bilgi için bkz. [/PGD (Profil destekli iyileştirmeler için veritabanını belirtin)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

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

  Görevler tarafından MSBuild kaynak dosya öğeleri içeren bir dizi tanımlar.

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

  ise, `true` bağlayıcıya son görüntüye bağlanabilir bir İçeri Aktarma Adresi Tablosu (IAT) dahil edilemez.

  Daha fazla bilgi için `NOBIND` [/DELAY (Gecikme yükü içeri aktarma ayarları) bağımsız değişkenine bakın.](/cpp/build/reference/delay-delay-load-import-settings)

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

  Daha fazla bilgi için bkz. [/TLBOUT (.tlb dosyasını adı)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  İsteğe **bağlı Tamsayı** parametresi.

  Bir bağlantıcı tarafından oluşturulan tür kitaplığı için kullanıcı tarafından belirtilen değeri verir. 1 ile 65535 arasında bir değer belirtin.

  Daha fazla bilgi için bkz. [/TLBID (TypeLib için kaynak kimliğini belirtin)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  İsteğe **bağlı Dize** parametresi.

  Kullanıcı Hesabı Denetimi altında çalıştırıldıklarından uygulama için istenen yürütme düzeyini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Asınvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  Daha fazla bilgi için `level` bkz. [/MANIFESTUAC bağımsız değişkeni (Bildirime UAC bilgileri ekleme)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UACUIAccess**

  İsteğe **bağlı Boole parametresi.**

  ise, uygulama kullanıcı arabirimi koruma düzeylerini atlar ve `true` masaüstünde daha yüksek izinli pencerelere giriş sürücüleri; aksi takdirde, `false` .

  Daha fazla bilgi için `uiAccess` bkz. [/MANIFESTUAC bağımsız değişkeni (Bildirime UAC bilgileri ekleme)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **UseLibraryDependencyInputs**

  İsteğe **bağlı Boole parametresi.**

  ise, kitaplık dosyasının kendisi yerine kitaplık aracına yapılan girişler, proje bağımlılıklarının kitaplık çıkışları içinde `true` bağlı olduğunda kullanılır.

- **Sürüm**

  İsteğe **bağlı Dize** parametresi.

  .exeveya.dll *üst bilgisinde bir.dll* girin.  " " `major[.minor]` belirtin. ve `major` bağımsız `minor` değişkenleri 0 ile 65535 arasında ondalık sayılardır.

  Daha fazla bilgi için bkz. [/VERSION (Sürüm bilgileri)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
