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
ms.openlocfilehash: 31bad6dfd0c336e4535e446d1167cb9fd6874972
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592210"
---
# <a name="link-task"></a>Bağlantı görevi
Microsoft C++ bağlayıcı aracı *LINK. exe*' yi sarmalanmış. Bağlayıcı aracı ortak nesne dosyası biçimi (COFF) nesne dosyalarını ve kitaplıklarını, yürütülebilir ( *. exe*) dosya veya dinamik bağlantı KITAPLıĞı (dll) oluşturmak için bağlar. Daha fazla bilgi için bkz. [bağlayıcı seçenekleri](/cpp/build/reference/linker-options).

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

  Bildirim dosyasının `dependency` bölümüne yerleştirilecek öznitelikleri belirtir.

  Daha fazla bilgi için bkz. [/Manifestdependency (Bildirim Bağımlılıklarını Belirt)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Ayrıca bkz. [Yayımcı yapılandırma dosyaları](/windows/desktop/SbsCs/publisher-configuration-files).

- **AdditionalOptions**

  İsteğe bağlı **dize** parametresi.

  Komut satırında belirtilen bağlayıcı seçeneklerinin bir listesi. Örneğin,/\<Seçenek1 >/\<Seçenek2 >/\<Seçenek # >. Başka bir **bağlantı** görevi parametresi tarafından temsil edilmeyen bağlayıcı seçeneklerini belirtmek için bu parametreyi kullanın.

  Daha fazla bilgi için bkz. [bağlayıcı seçenekleri](/cpp/build/reference/linker-options).

- **AddModuleNamesToAssembly**

  İsteğe bağlı **dize []** parametresi.

  Bir derlemeye modül başvurusu ekler.

  Daha fazla bilgi için bkz. [/ASSEMBLYMODULE (DERLEMEYE MSIL Modülü ekleme)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **ALLOWISOLATION**

  İsteğe bağlı **Boolean** parametresi.

  `true`, işletim sisteminin bildirim aramalarını ve yüklemelerini yapmasına neden olur. `false`, bir bildirim olmadığı gibi dll 'Lerin yüklendiğini belirtir.

  Daha fazla bilgi için bkz. [/ALLOWISOLATION (bildirim arama)](/cpp/build/reference/allowisolation-manifest-lookup).

- **AssemblyDebug**

  İsteğe bağlı **Boolean** parametresi.

  `true`, hata ayıklama bilgisi izleme ile birlikte, hata ayıklayıcı olan bir **öznitelik özniteliğini yayar** ve JIT iyileştirmelerini devre dışı bırakır. `false`, hata **ayıklayıcı, hata** ayıklama bilgileri izlemeyi devre dışı bırakır ve JIT iyileştirmelerini sunar.

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

  Oluşturulan program veya DLL için bir temel adres ayarlar. `{address[,size] | @filename,key}`belirtin.

  Daha fazla bilgi için bkz. [/Base (temel adres)](/cpp/build/reference/base-base-address).

- **Buildingınıde**

  İsteğe bağlı **Boolean** parametresi.

  True ise, MSBuild 'in IDE 'den çağrıldığı anlamına gelir. Aksi takdirde, MSBuild 'in komut satırından çağrıldığını gösterir.

  Bu parametrenin denk bağlayıcı seçeneği yok.

- **CLRImageType**

  İsteğe bağlı **dize** parametresi.

  Ortak dil çalışma zamanı (CLR) görüntüsünün türünü ayarlar.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** -  *\<yok >*

  - **ForceIJWImage** -  **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage** -  **/CLRIMAGETYPE:PURE**

  - **Forcesafeilımage** -  **/Clrimagetype: Safe**

  Daha fazla bilgi için bkz. [/Clrimagetype (clr görüntü türünü belirt)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSUPPORTLASTERROR 'ü**

  İsteğe bağlı **dize** parametresi.

  P/Invoke mekanizması aracılığıyla çağrılan işlevlerin son hata kodunu korur.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin** -  **/CLRSupportLastError**

  - **Devre dışı** -  **/CLRSupportLastError: Hayır**

  - **Systemdlls** -  **/CLRSupportLastError: systemdll**

  Daha fazla bilgi için bkz. [/CLRSUPPORTLASTERROR (PInvoke çağrıları için son hata kodunu koru)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).

- **CLRTHREADATTRIBUTE**

  İsteğe bağlı **dize** parametresi.

  CLR programınızın giriş noktası için iş parçacığı oluşturma özniteliğini açıkça belirtir.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Defaultthreadingattribute** -  **/CLRTHREADATTRIBUTE: None**

  - **Mtathreadingattribute** -  **/CLRTHREADATTRIBUTE: MTA**

  - **Stathreadingattribute** -  **/CLRTHREADATTRIBUTE: STA**

  Daha fazla bilgi için bkz. [/CLRTHREADATTRIBUTE (CLR iş parçacığı özniteliğini ayarlama)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  İsteğe bağlı **Boolean** parametresi.

  Bağlayıcının **SuppressUnmanagedCodeSecurityAttribute** ' i yönetilen koddan yerel dll 'lere bağlayıcı tarafından oluşturulan P/Invoke çağrılarına uygulayıp uygulayamayacağını belirtir.

  Daha fazla bilgi için bkz. [/CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute ekleyin)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  İsteğe bağlı **dize** parametresi.

  Sık yama için bir görüntü hazırlar.

  Bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin** -  **/functionpadmin**

  - **X86Image** -  **/functionpadmin: 5**

  - **X64Image** -  **/functionpadmin: 6**

  - **Itaniumımage** -  **/functionpadmin: 16**

  Daha fazla bilgi için bkz. [/functionpadmin (düzeltme eki eklenebilir görüntü oluşturma)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  İsteğe bağlı **Boolean** parametresi.

  `true`, Windows Veri Yürütme Engellemesi özelliği ile uyumlu olmak için bir yürütülebilir dosyanın test edildiğini gösterir.

  Daha fazla bilgi için bkz. [/NXCOMPAT (veri yürütme engellemesi Ile uyumlu)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLLs**

  İsteğe bağlı **dize []** parametresi.

  Bu parametre, dll 'lerin *gecikmeli yüklenmesine* neden olur. Yük gecikmesi için DLL 'nin adını belirtin.

  Daha fazla bilgi için bkz. [/delayload (Gecikmeli yük içeri aktarma)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bir derlemeyi kısmen imzalar. Varsayılan değer `false` şeklindedir.

  Daha fazla bilgi için bkz. [/delaysign (derlemeyi kısmen imzala)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Sürücü**

  İsteğe bağlı **dize** parametresi.

  Windows NT Çekirdek modu sürücüsü oluşturmak için bu parametreyi belirtin.

  Her biri bir bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** -  *\<yok >*

  - **Sürücü** -  **/Driver**

  - **Yalnızca up - ** **/DRIVER: uponly**

  - **Wdm** -  **/DRIVER: WDM**

  Daha fazla bilgi için bkz. [/Driver (WINDOWS NT Çekirdek modu sürücüsü)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  İsteğe bağlı **dize []** parametresi.

  Bir derlemeye kaynak dosyası katıştırır. Gerekli kaynak dosya adını belirtin. İsteğe bağlı olarak, kaynağı yüklemek için kullanılan mantıksal adı ve kaynak dosyasının özel olduğunu derleme bildiriminde belirten **özel** seçeneğini belirtin.

  Daha fazla bilgi için bkz. [/ASSEMBLYRESOURCE (yönetilen kaynağı katıştır)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **EnableCOMDATFolding**

  İsteğe bağlı **Boolean** parametresi.

  `true`, aynı COMDAT katlamayı mümkün bir şekilde sunar.

  Daha fazla bilgi için bkz. [/opt (iyileştirmeler)](/cpp/build/reference/opt-optimizations)`ICF[= iterations]` bağımsız değişkeni.

- **EnableUAC**

  İsteğe bağlı **Boolean** parametresi.

  `true`, Kullanıcı hesabı denetimi (UAC) bilgisinin program bildirimine gömülü olduğunu belirtir.

  Daha fazla bilgi için bkz. [/bildirimini estuac (BILDIRIMDEKI UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  İsteğe bağlı **dize** parametresi.

  Bir *. exe* dosyası veya dll için başlangıç adresi olarak bir giriş noktası işlevi belirtir. Parametre değeri olarak bir işlev adı belirtin.

  Daha fazla bilgi için bkz. [/Entry (giriş noktası simgesi)](/cpp/build/reference/entry-entry-point-symbol).

- **FixedBaseAddress**

  İsteğe bağlı **Boolean** parametresi.

  `true`, yalnızca tercih edilen temel adresinde yüklenebilen bir program veya DLL oluşturur.

  Daha fazla bilgi için bkz. [/Fixed (sabit temel adres)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  İsteğe bağlı **dize** parametresi.

  Bağlayıcıya bir sembol başvuruluyorsa ancak tanımlanmasa bile geçerli bir *. exe* dosyası veya dll oluşturmasını söyler veya çarpma tanımlanmış olarak tanımlanır.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin** -  **/Force**

  - **Multiplydefinedsymbolyalnızca** -  **/Force: MULTIPLE**

  - **Yalnızca Undefinedsymbolonly** -  **/Force: çözümlenmemiş**

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

  `true`, *. exe* dosyası veya dll için hata ayıklama bilgileri oluşturur.

  Daha fazla bilgi için bkz. [/Debug (hata ayıklama bilgisi oluştur)](/cpp/build/reference/debug-generate-debug-info).

- **GenerateManifest**

  İsteğe bağlı **Boolean** parametresi.

  `true`, yan yana bildirim dosyası oluşturur.

  Daha fazla bilgi için bkz. [/manifest (yan yana derleme bildirimi oluşturma)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **GenerateMapFile**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bir *eşleme dosyası*oluşturur. Eşleme dosyasının dosya adı uzantısı *. Map*' dir.

  Daha fazla bilgi için bkz. [/Map (mapfile üret)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  İsteğe bağlı **dize** parametresi.

  Yığın üzerinde aynı anda ayrılacak fiziksel bellek miktarını belirtir.

  Daha fazla bilgi için bkz./Heap içindeki `commit` bağımsız değişkeni [(yığın boyutunu ayarla)](/cpp/build/reference/heap-set-heap-size). Ayrıca bkz. **Heaprezervesize** parametresi.

- **Heaprezervesize**

  İsteğe bağlı **dize** parametresi.

  Sanal bellekteki toplam yığın ayırmayı belirtir.

  Daha fazla bilgi için bkz./Heap içindeki `reserve` bağımsız değişkeni [(yığın boyutunu ayarla)](/cpp/build/reference/heap-set-heap-size). Ayrıca bkz. bu tablodaki **HeapCommitSize** parametresi.

- **IgnoreAllDefaultLibraries**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bağlayıcının bir veya daha fazla varsayılan kitaplığı dış başvuruları çözdüğünde aradığı kitaplık listesinden kaldırmasını söyler.

  Daha fazla bilgi için bkz. [/nodefaultlib (kitaplıkları Yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **IgnoreEmbeddedIDL**

  İsteğe bağlı **Boolean** parametresi.

  `true`, kaynak kodundaki tüm IDL özniteliklerinin bir *. IDL* dosyasına işlenmediğini belirtir.

  Daha fazla bilgi için bkz. [/IGNOREIDL (öznitelikleri MIDL 'ye işleme)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **IgnoreImportLibrary**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bu yapılandırma tarafından oluşturulan içeri aktarma kitaplığının bağımlı projelere aktarılmaması gerektiğini belirtir.

  Bu parametre bir bağlayıcı seçeneğine karşılık gelmiyor.

- **IgnoreSpecificDefaultLibraries**

  İsteğe bağlı **dize []** parametresi.

  Yoksayılacak bir veya daha fazla varsayılan kitaplık adını belirtir. Noktalı virgülle ayırarak birden çok kitaplığı ayırın.

  Daha fazla bilgi için bkz. [/nodefaultlib (kitaplıkları Yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **Imagehassafeexceptionhandlers**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bağlayıcı yalnızca görüntünün güvenli özel durum işleyicilerinin bir tablosunu oluşturmak için bir görüntü oluşturur.

  Daha fazla bilgi için bkz. [/SafeSEH (görüntü güvenli özel durum işleyicilerine sahiptir)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **ImportLibrary**

  Varsayılan kitaplık adının yerini alan, Kullanıcı tarafından belirtilen bir içeri aktarma kitaplığı adı.

  Daha fazla bilgi için bkz. [/ımplib (ad içeri aktarma kitaplığı)](/cpp/build/reference/implib-name-import-library).

- **KeyContainer**

  İsteğe bağlı **dize** parametresi.

  İmzalı bir derleme için anahtarı içeren kapsayıcı.

  Daha fazla bilgi için bkz. [/keycontainer (bir derlemeyi imzalamak için bir anahtar kapsayıcısı belirtin)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Ayrıca bkz. bu tablodaki **keyfile** parametresi.

- **KeyFile**

  İsteğe bağlı **dize** parametresi.

  İmzalı bir derleme için anahtarı içeren bir dosyayı belirtir.

  Daha fazla bilgi için bkz. [/keyfile (bir derlemeyi imzalamak için anahtar veya anahtar çiftini belirtin)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Ayrıca, bkz. **keycontainer** parametresi.

- **LargeAddressAware**

  İsteğe bağlı **Boolean** parametresi.

  `true`, uygulama 2 gigabayt 'tan daha büyük adresleri işleyebilir.

  Daha fazla bilgi için bkz. [/LARGEADDRESSAWARE (büyük adresleri işleme)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  İsteğe bağlı **Boolean** parametresi.

  `true`, ana çıkış dosyası olarak bir DLL oluşturur.

  Daha fazla bilgi için bkz. [/dll (dll derleme)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  İsteğe bağlı **dize** parametresi.

  İç derleyici hatası (ıCE) bilgilerini doğrudan Microsoft 'a sağlamanıza olanak tanır.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Noerrorreport** -  **/errorreport: None**

  - **Hemen sor** -  **/errorreport: Prompt**

  - **QueueForNextLogin** -  **/ERRORREPORT:QUEUE**

  - **Senderrorreport** -  **/errorreport: Send**

  Daha fazla bilgi için bkz. [/errorreport (iç bağlayıcı hatalarını raporla)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **Linkıncreıncre**

  İsteğe bağlı **Boolean** parametresi.

  `true`, artımlı bağlamayı etkinleştirilir.

  Daha fazla bilgi için bkz. [/ıncreıncre(artımlı bağlantı)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryDependencies**

  İsteğe bağlı **Boolean** parametresi.

  `true`, proje bağımlılıklarındaki kitaplık çıktılarının otomatik olarak bağlandığını belirtir.

  Bu parametre bir bağlayıcı seçeneğine karşılık gelmiyor.

- **Bağlantı durumu**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bağlayıcının bağlantının yüzde oranını gösteren bir ilerleme göstergesi görüntüleneceğini belirtir.

  Daha fazla bilgi için/LTCG 'nin `STATUS` bağımsız değişkenine bakın [(bağlantı zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation).

- **LinkTimeCodeGeneration**

  İsteğe bağlı **dize** parametresi.

  Profil temelli iyileştirme seçeneklerini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** -  *\<yok >*

  - **UseLinkTimeCodeGeneration** -  **/LTCG**

  - **PGInstrument** -  **/LTCG:PGInstrument**

  - **PGOptimization** -  **/LTCG:PGOptimize**

  - **PGUpdate**

    \- **/LTCG:PGUpdate**

  Daha fazla bilgi için bkz. [/LTCG (bağlama zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation).

- **MANIFESTFILE**

  İsteğe bağlı **dize** parametresi.

  Varsayılan bildirim dosyası adını belirtilen dosya adı olarak değiştirir.

  Daha fazla bilgi için bkz. [/ManifestFile (ad bildirim dosyası)](/cpp/build/reference/manifestfile-name-manifest-file).

- **Mapdışarı aktarmalar**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bağlayıcıya bir eşleme dosyasına aktarılmış işlevleri dahil etmek için söyler.

  Daha fazla bilgi için bkz. [/MapInfo `EXPORTS` bağımsız değişkeni (Mapfile içinde bilgi ekleme)](/cpp/build/reference/mapinfo-include-information-in-mapfile).

- **MapFileName**

  İsteğe bağlı **dize** parametresi.

  Varsayılan eşleme dosyası adını belirtilen dosya adıyla değiştirir.

- **MergedIDLBaseFileName**

  İsteğe bağlı **dize** parametresi.

  *. IDL* dosyasının dosya adı ve dosya adı uzantısını belirtir.

  Daha fazla bilgi için bkz. [/IDLOUT (MıDL çıktı dosyalarını Adlandır)](/cpp/build/reference/idlout-name-midl-output-files).

- **MergeSections**

  İsteğe bağlı **dize** parametresi.

  Bir görüntüdeki bölümleri birleştirir. `from-section=to-section`belirtin.

  Daha fazla bilgi için bkz. [/merge (bölümleri birleştirme)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile**

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

  `true`, yalnızca kaynak DLL 'sini belirtir.

  Daha fazla bilgi için bkz. [/NOENTRY (giriş noktası yok)](/cpp/build/reference/noentry-no-entry-point).

- **ObjectFiles**

  Örtük **dize []** parametresi.

  Bağlı nesne dosyalarını belirtir.

- **OptimizeReferences**

  İsteğe bağlı **Boolean** parametresi.

  `true`, hiçbir şekilde başvurulmayan işlevleri ve/veya verileri ortadan kaldırır.

  Daha fazla bilgi için, [/opt (iyileştirmeler)](/cpp/build/reference/opt-optimizations)içindeki `REF` bağımsız değişkenine bakın.

- **OutputFile**

  İsteğe bağlı **dize** parametresi.

  Bağlayıcının oluşturduğu programın varsayılan adını ve konumunu geçersiz kılar.

  Daha fazla bilgi için bkz. [/Out (çıktı dosyası adı)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  İsteğe bağlı **Boolean** parametresi.

  `true` ve kayıt çıktısı etkinse, kayıt defteri yazmaları **HKEY_CLASSES_ROOT** **HKEY_CURRENT_USER**yeniden yönlendirilmeye zorlar.

- **PreprocessOutput**

  İsteğe bağlı `ITaskItem[]` parametresi.

  Görevler tarafından tüketilen ve yayılan bir Önişlemci çıkış öğeleri dizisi tanımlar.

- **PreventDllBinding**

  İsteğe bağlı **Boolean** parametresi.

  `true`, *bind. exe* ' nin bağlı görüntünün bağlı olmaması gerektiğini gösterir.

  Daha fazla bilgi için bkz. [/Allowbind (dll bağlamasını engelle)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  İsteğe bağlı **Boolean** parametresi.

  `true`, **performans araçları** Profilcisi ile kullanılabilecek bir çıkış dosyası üretir.

  Daha fazla bilgi için bkz. [/profile (performans araçları profil Oluşturucu)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

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

  `true`, bu derleme için birincil çıktıyı kaydeder.

- **Sectionhizalaması**

  İsteğe bağlı **tamsayı** parametresi.

  Programın doğrusal adres alanındaki her bölümün hizalamasını belirtir. Parametre değeri bir birim bayt sayısıdır ve ikinin gücünden oluşur.

  Daha fazla bilgi için bkz. [/align (Bölüm hizalaması)](/cpp/build/reference/align-section-alignment).

- **SetChecksum**

  İsteğe bağlı **Boolean** parametresi.

  `true`, *. exe* dosyasının üst bilgisindeki sağlama toplamını ayarlar.

  Daha fazla bilgi için bkz. [/Release (sağlama toplamını ayarla)](/cpp/build/reference/release-set-the-checksum).

- **ShowProgress**

  İsteğe bağlı **dize** parametresi.

  Bağlama işlemi için ilerleme raporlarının ayrıntı düzeyini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** -  *\<yok >*

  - **LinkVerbose** -  **/VERBOSE**

  - **LinkVerboseLib** -  **/VERBOSE:Lib**

  - **LinkVerboseICF** -  **/VERBOSE:ICF**

  - **LinkVerboseREF** -  **/VERBOSE:REF**

  - **LinkVerboseSAFESEH** -  **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR** -  **/VERBOSE:CLR**

  Daha fazla bilgi için bkz. [/verbose (ilerleme Iletilerini Yazdır)](/cpp/build/reference/verbose-print-progress-messages).

- **Ğına**

  Gerekli `ITaskItem[]` parametresi.

  Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.

- **Belirtilen Yılözniteliklerini**

  İsteğe bağlı **dize** parametresi.

  Bir bölümün özniteliklerini belirtir. Bu, bölüm için *. obj* dosyası derlendiğinde ayarlanan öznitelikleri geçersiz kılar.

  Daha fazla bilgi için bkz. [/section (bölüm özniteliklerini belirt)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize**

  İsteğe bağlı **dize** parametresi.

  Ek bellek tahsis edildiğinde her bir ayırdaki fiziksel bellek miktarını belirtir.

  Daha fazla bilgi için bkz./Stack 'in `commit` bağımsız değişkeni [(yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations).

- **StackReserveSize**

  İsteğe bağlı **dize** parametresi.

  Sanal bellekteki toplam yığın ayırma boyutunu belirtir.

  Daha fazla bilgi için bkz./Stack 'in `reserve` bağımsız değişkeni [(yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations).

- **StripPrivateSymbols**

  İsteğe bağlı **dize** parametresi.

  Müşterilerinize dağıtmak istemediğiniz sembolleri atlatabilecek ikinci program veritabanı (PDB) dosyası oluşturur. İkinci PDB dosyasının adını belirtin.

  Daha fazla bilgi için [/pdbstrıpped (özel simgeleri Şerit)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Sistemin**

  İsteğe bağlı **dize** parametresi.

  Yürütülebilir dosyanın ortamını belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** -  *\<yok >*

  - **Konsol** -  **/Subsystem: Console**

  - **Windows** -  **/Subsystem: Windows**

  - **Yerel** -  **/Subsystem: Native**

  - **EFI uygulaması** -  **/subsystem: EFI_APPLICATION**

  - **EFI Önyükleme hizmeti sürücüsü** -  **/subsystem: EFI_BOOT_SERVICE_DRIVER**

  - **EFı ROM** -  **/subsystem: EFI_ROM**

  - **EFI çalışma zamanı** -  **/subsystem: EFI_RUNTIME_DRIVER**

  - **Windowsce** -  **/Subsystem: WindowsCE**

  - **Posix** -  **/Subsystem: POSIX**

  Daha fazla bilgi için bkz. [/Subsystem (alt sistemi belirt)](/cpp/build/reference/subsystem-specify-subsystem).

- **SupportNobindOfDelayLoadedDLL**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bağlayıcıya son görüntüde bağlanabilir bir Içeri aktarma adres tablosu (ıAT) dahil olmadığını söyler.

  Daha fazla bilgi için bkz./Delay 'in `NOBIND` bağımsız değişkeni [(Gecikmeli yük içeri aktarma ayarları)](/cpp/build/reference/delay-delay-load-import-settings).

- **SupportUnloadOfDelayLoadedDLL**

  İsteğe bağlı **Boolean** parametresi.

  `true`, gecikme Yükleme Yardımcısı işlevine DLL 'nin açıkça kaldırılmasını desteklememesini söyler.

  Daha fazla bilgi için bkz./Delay 'in `UNLOAD` bağımsız değişkeni [(Gecikmeli yük içeri aktarma ayarları)](/cpp/build/reference/delay-delay-load-import-settings).

- **SuppressStartupBanner**

  İsteğe bağlı **Boolean** parametresi.

  `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.

  Daha fazla bilgi için bkz. [/nologo (başlangıç başlığını gösterme) (bağlayıcı)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  İsteğe bağlı **Boolean** parametresi.

  `true`, işletim sisteminin önce bağlayıcı çıkışını bir takas dosyasına kopyalamasını söyler ve sonra görüntüyü oradan çalıştırır.

  Daha fazla bilgi için bkz. [/SWAPRUN (bağlayıcı çıktısını takas dosyasına yükle)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)`CD` bağımsız değişkeni. Ayrıca bkz. **SwapRunFromNet** parametresi.

- **SwapRunFromNET**

  İsteğe bağlı **Boolean** parametresi.

  `true`, işletim sisteminin önce bağlayıcı çıkışını bir takas dosyasına kopyalamasını söyler ve sonra görüntüyü oradan çalıştırır.

  Daha fazla bilgi için bkz. [/SWAPRUN (bağlayıcı çıktısını takas dosyasına yükle)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)`NET` bağımsız değişkeni. Ayrıca bkz. bu tablodaki **SwapRunFromCD** parametresi.

- **TargetMachine**

  İsteğe bağlı **dize** parametresi.

  Program veya DLL için hedef platformu belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet** -  *\<yok >*

  - **Machineard** -  **/MACHINE: ARM**

  - **Machineebc** -  **/MACHINE: EBC**

  - **MachineIA64** -  **/MACHINE: IA64**

  - **Machinemıps** -  **/MACHINE: MIPS**

  - **MachineMIPS16** -  **/MACHINE: kayıtlardan biri mıps16**

  - **MachineMIPSFPU** -  **/MACHINE:MIPSFPU**

  - **MachineMIPSFPU16** -  **/MACHINE:MIPSFPU16**

  - **MachineSH4** -  **/MACHINE:SH4**

  - **Machinethumb** -  **/MACHıNE: Thumb**

  - **MachineX64** -  **/Machine: x64**

  - **MachineX86** -  **/Machine: x86**

  Daha fazla bilgi için bkz. [/Machine (hedef platformu belirt)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  İsteğe bağlı **Boolean** parametresi.

  `true`, program görüntüsünün isteğe bağlı üstbilgisindeki IMAGE_OPTIONAL_HEADER Dllözellikler alanında bir bayrak ayarlar. Bu bayrak ayarlandığında, Terminal sunucusu uygulamada belirli değişiklikler yapmayacak.

  Daha fazla bilgi için bkz. [/T saware (Terminal Server 'ı algılayan uygulama oluşturma)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  İsteğe bağlı **dize** parametresi.

  İzleyici günlüğünün dizinini belirtir.

- **TreatLinkerWarningAsErrors**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bağlayıcı bir uyarı oluşturursa çıkış dosyası oluşturulmasına neden olur.

  Daha fazla bilgi için bkz. [/WX (bağlayıcı uyarılarını hata olarak işle)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnOffAssemblyGeneration**

  İsteğe bağlı **Boolean** parametresi.

  `true`, .NET Framework bütünleştirilmiş kodu olmadan geçerli çıkış dosyası için bir görüntü oluşturur.

  Daha fazla bilgi için bkz. [/NOASSEMBLY (MSIL Modülü oluşturma)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypeLibraryFile**

  İsteğe bağlı **dize** parametresi.

  *. Tlb* dosyasının dosya adı ve dosya adı uzantısını belirtir. Bir dosya adı veya yol ve dosya adı belirtin.

  Daha fazla bilgi için bkz. [/Tlhakkında (ad. tlb dosyası)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  İsteğe bağlı **tamsayı** parametresi.

  Bağlayıcı tarafından oluşturulan tür kitaplığı için Kullanıcı tarafından belirtilen bir değer belirtir. 1 ile 65535 arasında bir değer belirtin.

  Daha fazla bilgi için bkz. [/Tldeklarasyon (TypeLib için kaynak Kimliğini Belirt)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  İsteğe bağlı **dize** parametresi.

  Kullanıcı hesabı denetimiyle birlikte çalıştırıldığında, uygulama için istenen yürütme düzeyini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **AsInvoker** - `level='asInvoker'`

  - **HighestAvailable** - `level='highestAvailable'`

  - **RequireAdministrator** - `level='requireAdministrator'`

  Daha fazla bilgi için bkz. [/manifest estuac `level` bağımsız değişkeni (BILDIRIMDEKI UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **Uıacuıaccess**

  İsteğe bağlı **Boolean** parametresi.

  `true`, uygulama kullanıcı arabirimi koruma düzeylerini ve sürücü girişini, masaüstündeki daha yüksek izinli pencereler için atlar; Aksi takdirde, `false`.

  Daha fazla bilgi için bkz. [/manifest estuac `uiAccess` bağımsız değişkeni (BILDIRIMDEKI UAC bilgilerini katıştırır)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **Uselibrarydependencygirdileri**

  İsteğe bağlı **Boolean** parametresi.

  `true`, proje bağımlılıklarının kitaplık çıkışları bağlantılı olduğunda kitaplık dosyasının kendisi yerine kütüphaneian aracının girişleri kullanılır.

- **Sürüm**

  İsteğe bağlı **dize** parametresi.

  *. Exe* veya *. dll* dosyasının üstbilgisine bir sürüm numarası koyun. "`major[.minor]`" öğesini belirtin. `major` ve `minor` bağımsız değişkenleri 0 ile 65535 arasında ondalık sayılardır.

  Daha fazla bilgi için bkz. [/Version (sürüm bilgileri)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
