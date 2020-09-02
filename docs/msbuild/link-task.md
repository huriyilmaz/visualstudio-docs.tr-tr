---
title: Bağlantı görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01105e3fd4c86d57077df7804e66592e32ebae07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78865355"
---
# <a name="link-task"></a>Bağlantı görevi

, Microsoft C++ bağlayıcı aracı *link.exe*sarmalanmış. Bağlayıcı aracı ortak nesne dosyası biçimi (COFF) nesne dosyalarını ve kitaplıklarını, yürütülebilir (*. exe*) dosya veya dinamik bağlantı KITAPLıĞı (dll) oluşturmak için bağlar. Daha fazla bilgi için bkz. [bağlayıcı seçenekleri](/cpp/build/reference/linker-options) ve [komut satırından MSBuild 'i kullanma](/cpp/build/msbuild-visual-cpp) ve [komut satırından Microsoft C++ araç takımını kullanma](/cpp/build/building-on-the-command-line).

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

  Daha fazla bilgi için bkz. [/Manifestdependency (Bildirim Bağımlılıklarını Belirt)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Ayrıca bkz. [Yayımcı yapılandırma dosyaları](/windows/desktop/SbsCs/publisher-configuration-files).

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

  Çıkış dosyasında bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıkış dosyasına yerleştirilmez. Kaynağın adını belirtin.

  Daha fazla bilgi için bkz. [/Assemblylinkresource (.NET Framework kaynağına bağlantı)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **AttributeFileTracking**

  Örtük **Boolean** parametresi.

  Daha derin dosya izlemenin bağlantı artımlı davranışını yakalamasını sağlar. Her zaman `true` döndürür.

- **BaseAddress**

  İsteğe bağlı **dize** parametresi.

  Oluşturulan program veya DLL için bir temel adres ayarlar. `{address[,size] | @filename,key}` belirtin.

  Daha fazla bilgi için bkz. [/Base (temel adres)](/cpp/build/reference/base-base-address).

- **Buildingınıde**

  İsteğe bağlı **Boolean** parametresi.

  True ise, MSBuild 'in IDE 'den çağrıldığı anlamına gelir. Aksi takdirde, MSBuild 'in komut satırından çağrıldığını gösterir.

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

- **Dataexecutionengellemesini**

  İsteğe bağlı **Boolean** parametresi.

  `true`, Bir yürütülebilir dosyanın Windows Veri Yürütme Engellemesi özelliği ile uyumlu olacak şekilde sınanmış olduğunu gösterir.

  Daha fazla bilgi için bkz. [/NXCOMPAT (veri yürütme engellemesi Ile uyumlu)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLLs**

  İsteğe bağlı **dize []** parametresi.

  Bu parametre, dll 'lerin *gecikmeli yüklenmesine* neden olur. Yük gecikmesi için DLL 'nin adını belirtin.

  Daha fazla bilgi için bkz. [/delayload (Gecikmeli yük içeri aktarma)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  İsteğe bağlı **Boolean** parametresi.

  Eğer `true` , bir derlemeyi kısmen imzalar. Varsayılan değer `false` şeklindedir.

  Daha fazla bilgi için bkz. [/delaysign (derlemeyi kısmen imzala)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Sürücü**

  İsteğe bağlı **dize** parametresi.

  Windows NT Çekirdek modu sürücüsü oluşturmak için bu parametreyi belirtin.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** - *\<none>*

  - **Sürücü**  -  **/DRIVER**

  - **Yalnızca yukarı**  -  **/DRIVER: yalnızca yukarı**

  - **WDM**  -  **/DRIVER: WDM**

  Daha fazla bilgi için bkz. [/Driver (WINDOWS NT Çekirdek modu sürücüsü)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  İsteğe bağlı **dize []** parametresi.

  Bir derlemeye kaynak dosyası katıştırır. Gerekli kaynak dosya adını belirtin. İsteğe bağlı olarak, kaynağı yüklemek için kullanılan mantıksal adı ve kaynak dosyasının özel olduğunu derleme bildiriminde belirten **özel** seçeneğini belirtin.

  Daha fazla bilgi için bkz. [/ASSEMBLYRESOURCE (yönetilen kaynağı katıştır)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **Enablecomdatkatlamalı**

  İsteğe bağlı **Boolean** parametresi.

  Varsa `true` , aynı COMDAT katlamayı mümkün bir şekilde sunar.

  Daha fazla bilgi için bkz `ICF[= iterations]` . [/opt (iyileştirmeler)](/cpp/build/reference/opt-optimizations)bağımsız değişkeni.

- **EnableUAC**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , Kullanıcı hesabı denetimi (UAC) bilgisinin program bildirimine gömülü olduğunu belirtir.

  Daha fazla bilgi için bkz. [/bildirimini estuac (BILDIRIMDEKI UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  İsteğe bağlı **dize** parametresi.

  Bir *. exe* dosyası veya dll için başlangıç adresi olarak bir giriş noktası işlevi belirtir. Parametre değeri olarak bir işlev adı belirtin.

  Daha fazla bilgi için bkz. [/Entry (giriş noktası simgesi)](/cpp/build/reference/entry-entry-point-symbol).

- **FixedBaseAddress**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , yalnızca tercih edilen temel adresinde yüklenebilen bir program veya dll oluşturur.

  Daha fazla bilgi için bkz. [/Fixed (sabit temel adres)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  İsteğe bağlı **dize** parametresi.

  Bağlayıcıya bir sembol başvuruluyorsa ancak tanımlanmasa bile geçerli bir *. exe* dosyası veya dll oluşturmasını söyler veya çarpma tanımlanmış olarak tanımlanır.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin**  -  **/Force**

  - Yalnızca Çoğullydefinedsymbol **MultiplyDefinedSymbolOnly**  -  **/Force: bırden çok**

  - Yalnızca Undefinedsymbol **UndefinedSymbolOnly**  -  **/Force: çözümlenmemiş**

  Daha fazla bilgi için bkz. [/Force (Dosya çıktısını zorla)](/cpp/build/reference/force-force-file-output).

- **Forcesyımbolreferences**

  İsteğe bağlı **dize []** parametresi.

  Bu parametre, bağlayıcının sembol tablosuna belirtilen bir sembol eklemesini söyler.

  Daha fazla bilgi için bkz. [/Include (simge başvurularını zorla)](/cpp/build/reference/include-force-symbol-references).

- **FunctionOrder**

  İsteğe bağlı **dize** parametresi.

  Bu parametre, belirtilen paketlenmiş işlevleri (Comtts) görüntüye önceden belirlenmiş bir sırada yerleştirerek programınızı iyileştirir.

  Daha fazla bilgi için bkz. [/Order (işlevleri sırayla yerleştirme)](/cpp/build/reference/order-put-functions-in-order).

- **GenerateDebugInformation**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , *. exe* dosyası veya dll için hata ayıklama bilgileri oluşturur.

  Daha fazla bilgi için bkz. [/Debug (hata ayıklama bilgisi oluştur)](/cpp/build/reference/debug-generate-debug-info).

- **GenerateManifest**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , yan yana bildirim dosyası oluşturur.

  Daha fazla bilgi için bkz. [/manifest (yan yana derleme bildirimi oluşturma)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bir *eşleme dosyası*oluşturur. Eşleme dosyasının dosya adı uzantısı *. Map*' dir.

  Daha fazla bilgi için bkz. [/Map (mapfile üret)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  İsteğe bağlı **dize** parametresi.

  Yığın üzerinde aynı anda ayrılacak fiziksel bellek miktarını belirtir.

  Daha fazla bilgi için bkz `commit` ./Heap içindeki bağımsız değişken [(yığın boyutunu ayarlama)](/cpp/build/reference/heap-set-heap-size). Ayrıca bkz. **Heaprezervesize** parametresi.

- **Heaprezervesize**

  İsteğe bağlı **dize** parametresi.

  Sanal bellekteki toplam yığın ayırmayı belirtir.

  Daha fazla bilgi için bkz `reserve` ./Heap içindeki bağımsız değişken [(yığın boyutunu ayarlama)](/cpp/build/reference/heap-set-heap-size). Ayrıca bkz. bu tablodaki **HeapCommitSize** parametresi.

- **IgnoreAllDefaultLibraries**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , bağlayıcının bir veya daha fazla varsayılan kitaplığı dış başvuruları çözümlediğinde aradığı kitaplık listesinden kaldırmasını söyler.

  Daha fazla bilgi için bkz. [/nodefaultlib (kitaplıkları Yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  İsteğe bağlı **Boolean** parametresi.

  İse `true` , kaynak kodundaki tüm IDL özniteliklerinin bir *. IDL* dosyasına işlenmediğini belirtir.

  Daha fazla bilgi için bkz. [/IGNOREIDL (öznitelikleri MIDL 'ye işleme)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  İsteğe bağlı **Boolean** parametresi.

  `true`Bu yapılandırma tarafından oluşturulan içeri aktarma kitaplığının bağımlı projelere aktarılmaması gerektiğini belirtir.

  Bu parametre bir bağlayıcı seçeneğine karşılık gelmiyor.

- **IgnoreSpecificDefaultLibraries**

  İsteğe bağlı **dize []** parametresi.

  Yoksayılacak bir veya daha fazla varsayılan kitaplık adını belirtir. Noktalı virgülle ayırarak birden çok kitaplığı ayırın.

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

  `true`Çıktıyı kaydet etkinse, kayıt defteri yazmaları **HKEY_CLASSES_ROOT** **HKEY_CURRENT_USER**yeniden yönlendirilmeye zorlar.

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

  `true`, Windows 'un *Adres alanı düzeni rastgele seçme* (ASLR) özelliğini kullanarak yükleme zamanında rastgele bir şekilde yeniden temel alan yürütülebilir bir görüntü oluşturur.

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

  İse `true` , bir *. exe* dosyasının üst bilgisindeki sağlama toplamını ayarlar.

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

  Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.

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

  Varsa `true` , geçerli çıkış dosyası için .NET Framework derlemesi olmadan bir görüntü oluşturur.

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

  *. Exe* veya *. dll* dosyasının üstbilgisine bir sürüm numarası koyun. " `major[.minor]` " Belirtin. `major`Ve `minor` bağımsız değişkenleri 0 ile 65535 arasında ondalık sayılardır.

  Daha fazla bilgi için bkz. [/Version (sürüm bilgileri)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
