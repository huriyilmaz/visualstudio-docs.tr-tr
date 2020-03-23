---
title: Bağlantı Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865355"
---
# <a name="link-task"></a>Bağlantı görevi

Microsoft C++ bağlayıcı aracını sarar, *link.exe*. Bağlayıcı aracı, yürütülebilir (*.exe*) dosyası veya dinamik bağlantı kitaplığı (DLL) oluşturmak için Ortak Nesne Dosya Biçimi (COFF) nesne dosyalarını ve kitaplıklarını bağlar. Daha fazla bilgi için [Linker seçeneklerine](/cpp/build/reference/linker-options) bakın ve [komut satırından MSBuild kullanın](/cpp/build/msbuild-visual-cpp) ve [komut satırından Microsoft C++ araç kümesini kullanın.](/cpp/build/building-on-the-command-line)

## <a name="parameters"></a>Parametreler

 Aşağıdaki **Bağlantı** görevinin parametreleri açıklanır. Görev parametrelerinin çoğu ve birkaç parametre kümesi komut satırı seçeneğine karşılık gelir.

- **Ek Bağımlılıklar**

  İsteğe bağlı **String[]** parametresi.

  Komuta eklenecek giriş dosyalarının listesini belirtir.

  Daha fazla bilgi için [LINK giriş dosyalarına](/cpp/build/reference/link-input-files)bakın.

- **EkKütüphaneDirectories**

  İsteğe bağlı **String[]** parametresi.

  Çevre kitaplığı yolunu geçersiz kılar. Bir dizin adı belirtin.

  Daha fazla bilgi için bkz: [/LIBPATH (Ek Libpath).](/cpp/build/reference/libpath-additional-libpath)

- **Ek ManifestDependencies**

  İsteğe bağlı **String[]** parametresi.

  Bildirim dosyasının bölümüne `dependency` yerleştirilecek öznitelikleri belirtir.

  Daha fazla bilgi için bkz: [/MANIFESTDEPENDENCY (Bildirim bağımlılıklarını belirtin)](/cpp/build/reference/manifestdependency-specify-manifest-dependencies). Ayrıca [bkz.](/windows/desktop/SbsCs/publisher-configuration-files)

- **Ek Seçenekler**

  İsteğe bağlı **String** parametresi.

  Komut satırında belirtildiği gibi bağlayıcı seçenekleri listesi. Örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir **Bağlantı** görev parametresi tarafından temsil edilmeyen bağlayıcı seçeneklerini belirtmek için bu parametreyi kullanın.

  Daha fazla bilgi için [Linker seçeneklerine](/cpp/build/reference/linker-options)bakın.

- **AddmodulenamestoAssembly**

  İsteğe bağlı **String[]** parametresi.

  Bir derlemeye modül başvurusu ekler.

  Daha fazla bilgi için bkz: [/ASSEMBLYMODULE (Montaja Bir MSIL modülü ekleyin)](/cpp/build/reference/assemblymodule-add-a-msil-module-to-the-assembly).

- **İzolasyona İzin Ver**

  İsteğe bağlı **Boolean** parametresi.

  Eğer `true`, işletim sisteminin apaçık aramalar ve yükler yapmasına neden olur. Eğer, `false`DLs'lerin hiçbir bildirim yokmuş gibi yüklendiğini gösterirse.

  Daha fazla bilgi için bkz: [/ALLOWISOLATION (Manifest lookup)](/cpp/build/reference/allowisolation-manifest-lookup).

- **MontajHatabu**

  İsteğe bağlı **Boolean** parametresi.

  Hata `true` **Ayıklama Özniteliği** niyasını hata ayıklama bilgi izlemeyle birlikte yayar ve JIT optimizasyonlarını devre dışı kılabilir. Hata `false` **Ayıklama özniteliği** ni yayar, ancak hata ayıklama bilgi izleme devre dışı bırakmak ve JIT optimizasyonları sağlar.

  Daha fazla bilgi için bkz: [/ASSEMBLYDEBUG (Hata Ayıklama Özelliği Ekle)](/cpp/build/reference/assemblydebug-add-debuggableattribute).

- **AssemblyLinkKaynak**

  İsteğe bağlı **String[]** parametresi.

  Çıktı dosyasındaki bir .NET Framework kaynağına bağlantı oluşturur; kaynak dosyası çıktı dosyasına yerleştirilmez. Kaynağın adını belirtin.

  Daha fazla bilgi için bkz: [/ASSEMBLYLINKRESOURCE (.NET Framework kaynağına bağlantı)](/cpp/build/reference/assemblylinkresource-link-to-dotnet-framework-resource).

- **ÖznitelikFileTracking**

  Örtük **Boolean** parametresi.

  Bağlantı artımlı davranışı yakalamak için daha derin dosya izleme sağlar. Her zaman `true` döndürür.

- **Baseaddress**

  İsteğe bağlı **String** parametresi.

  Oluşturulmakta olan programın veya DLL'nin temel adresini ayarlar. `{address[,size] | @filename,key}` belirtin.

  Daha fazla bilgi için bkz: [/BASE (Temel adres).](/cpp/build/reference/base-base-address)

- **BinaInIDE**

  İsteğe bağlı **Boolean** parametresi.

  Doğruysa, MSBuild'in IDE'den çağrıldığını gösterir. Aksi takdirde, MSBuild komut satırından çağrılır gösterir.

  Bu parametrenin eşdeğer bağlayıcı seçeneği yoktur.

- **CLRImageType**

  İsteğe bağlı **String** parametresi.

  Ortak bir dil çalışma zamanı (CLR) görüntüsünün türünü ayarlar.

  Her biri bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *yok>\<*

  - **ForceiJWImage** - **/CLRIMAGETYPE:IJW**

  - **ForcePureILImage** - **/CLRIMAGETYPE:PURE**

  - **ForceSafeILImage** - **/CLRIMAGETYPE:GÜVENLİ**

  Daha fazla bilgi için bkz: [/CLRIMAGETYPE (CLR görüntü türünü belirtin)](/cpp/build/reference/clrimagetype-specify-type-of-clr-image).

- **CLRSupportLastError**

  İsteğe bağlı **String** parametresi.

  P/Invoke mekanizması aracılığıyla çağrılan işlevlerin son hata kodunu korur.

  Her biri bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin** - **/CLRSupportLastError**

  - **Devre Dışı** - **/CLRSupportLastError:NO**

  - **SystemDlls** - **/CLRSupportLastError:SYSTEMDLL**

  Daha fazla bilgi için bkz: [/CLRSUPPORTLASTERROR (PInvoke aramaları için son hata kodunu koru)](/cpp/build/reference/clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls).

- **CLRThreadÖznitelik**

  İsteğe bağlı **String** parametresi.

  CLR programınızın giriş noktası için iş parçacığı özniteliğini açıkça belirtir.

  Her biri bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **DefaultThreadingAttribute** - **/CLRTHREADATTRIBUTE:NONE**

  - **MTAThreadingÖz** - **/CLRTHREADATTRIBUTE:MTA**

  - **STAThreadingÖz** - **/CLRTHREADATTRIBUTE:STA**

  Daha fazla bilgi için bkz: [/CLRTHREADATTRIBUTE (CLR iş parçacığı özniteliğini ayarla)](/cpp/build/reference/clrthreadattribute-set-clr-thread-attribute).

- **CLRUnmanagedCodeCheck**

  İsteğe bağlı **Boolean** parametresi.

  Bağlayıcının, yönetilen koddan yerel DL'lere bağlı oluşturulan P/Invoke çağrılarına **SuppressUnmanagedCodeSecurityAttribute** uygulayıp uygulamayacağı belirtilir.

  Daha fazla bilgi için bkz: [/CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute ekle)](/cpp/build/reference/clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute).

- **CreateHotPatchableImage**

  İsteğe bağlı **String** parametresi.

  Sıcak yama için bir görüntü hazırlar.

  Bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin** - **/FUNCTIONPADMIN**

  - **X86Image** - **/FUNCTIONPADMIN:5**

  - **X64Image** - **/FUNCTIONPADMIN:6**

  - **ItaniumImage** - **/FUNCTIONPADMIN:16**

  Daha fazla bilgi için bkz: [/FUNCTIONPADMIN (Hotpatchable image oluştur)](/cpp/build/reference/functionpadmin-create-hotpatchable-image).

- **DataExecutionPrevention**

  İsteğe bağlı **Boolean** parametresi.

  , `true`yürütülebilir bir Windows Veri Yürütme Önleme özelliği ile uyumlu olması için test edildiğini gösterir.

  Daha fazla bilgi için bkz: [/NXCOMPAT (Veri Yürütme Önleme ile uyumludur)](/cpp/build/reference/nxcompat-compatible-with-data-execution-prevention).

- **DelayLoadDLs**

  İsteğe bağlı **String[]** parametresi.

  Bu parametre, DL'lerin *gecikmeli yüklenmesine* neden olur. Yükü geciktirmek için DLL'nin adını belirtin.

  Daha fazla bilgi için bkz: [/DELAYLOAD (Gecikme yükü alma)](/cpp/build/reference/delayload-delay-load-import).

- **DelaySign**

  İsteğe bağlı **Boolean** parametresi.

  Bir `true`derlemeyi kısmen imzalarsa. Varsayılan değer `false` şeklindedir.

  Daha fazla bilgi için bkz: [/DELAYSIGN (Kısmen bir derlemeyi imzalayın)](/cpp/build/reference/delaysign-partially-sign-an-assembly).

- **Sürücü**

  İsteğe bağlı **String** parametresi.

  Windows NT çekirdek modu sürücüsü oluşturmak için bu parametreyi belirtin.

  Her biri bağlayıcı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet hiçbiri** - >*\<*

  - **Sürücü** - **/Sürücü**

  - **UpOnly** - **/DRIVER:UPONLY**

  - **WDM** - **/SÜRÜCÜ:WDM**

  Daha fazla bilgi için bkz: [/DRIVER (Windows NT çekirdek modu sürücüsü)](/cpp/build/reference/driver-windows-nt-kernel-mode-driver).

- **EmbedManagedResourceFile**

  İsteğe bağlı **String[]** parametresi.

  Bir derlemeye kaynak dosyası gömer. Gerekli kaynak dosya adını belirtin. İsteğe bağlı olarak, kaynağı yüklemek için kullanılan mantıksal adı ve derleme bildiriminde kaynak dosyasının özel olduğunu gösteren **PRIVATE** seçeneğini belirtin.

  Daha fazla bilgi için bkz: [/ASSEMBLYRESOURCE (Yönetilen bir kaynak gömün)](/cpp/build/reference/assemblyresource-embed-a-managed-resource).

- **EnableCOMANDFolding**

  İsteğe bağlı **Boolean** parametresi.

  Eğer, `true`aynı COMDAT katlama sağlar.

  Daha fazla bilgi `ICF[= iterations]` için [/OPT (Optimizasyonlar)](/cpp/build/reference/opt-optimizations)bağımsız değişkenine bakın.

- **EtkinleştirmeUAC**

  İsteğe bağlı **Boolean** parametresi.

  Kullanıcı `true`Hesabı Denetimi (UAC) bilgilerinin program bildirimine katıştırılmış olduğunu belirtirse.

  Daha fazla bilgi için bkz: [/MANIFESTUAC (UAC bilgilerini manifeste gömer)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest).

- **EntryPointSymbol**

  İsteğe bağlı **String** parametresi.

  Bir *.exe* dosyasının veya DLL'nin başlangıç adresi olarak bir giriş noktası işlevini belirtir. Parametre değeri olarak bir işlev adı belirtin.

  Daha fazla bilgi için bkz: [/ENTRY (Giriş noktası simgesi)](/cpp/build/reference/entry-entry-point-symbol).

- **SabitBaseAddress**

  İsteğe bağlı **Boolean** parametresi.

  , `true`yalnızca tercih ettiği temel adrese yüklenebilen bir program veya DLL oluşturursa.

  Daha fazla bilgi için bkz: [/FIXED (Sabit taban adresi)](/cpp/build/reference/fixed-fixed-base-address).

- **ForceFileOutput**

  İsteğe bağlı **String** parametresi.

  Bağlayıcıya, bir sembol başvurulsa, ancak tanımlanmamış olsa veya tanımlanan çarpılırsa bile geçerli bir *.exe* dosyası veya DLL oluşturmasını söyler.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Etkin** - **/FORCE**

  - **MultiplyDefinedSymbolOnly** - **/FORCE:ÇOKLU**

  - **TanımsızSymbolOnly** - **/FORCE:ÇÖZÜLMEMEd**

  Daha fazla bilgi için bkz: [/FORCE (Force dosya çıktısı)](/cpp/build/reference/force-force-file-output).

- **ForceSymbolReferences**

  İsteğe bağlı **String[]** parametresi.

  Bu parametre, bağlayıcıya sembol tablosuna belirtilen bir simge eklemesini söyler.

  Daha fazla bilgi için bkz: [/INCLUDE (Kuvvet sembolü referansları)](/cpp/build/reference/include-force-symbol-references).

- **İşlev Sırası**

  İsteğe bağlı **String** parametresi.

  Bu parametre, belirtilen paketlenmiş işlevleri (COMDATs) önceden belirlenmiş bir sırada görüntüye yerleştirerek programınızı optimize eder.

  Daha fazla bilgi için bkz: [/ORDER (Işlevleri sırayla koyun)](/cpp/build/reference/order-put-functions-in-order).

- **Hata Ayıklama Bilgi Oluşturma**

  İsteğe bağlı **Boolean** parametresi.

  Eğer `true`, *.exe* dosyası veya DLL için hata ayıklama bilgileri oluşturur.

  Daha fazla bilgi için bkz: [/DEBUG (Hata ayıklama bilgisi oluşturma)](/cpp/build/reference/debug-generate-debug-info).

- **Manifesto Oluşturma**

  İsteğe bağlı **Boolean** parametresi.

  Yan `true`yana bir bildirim dosyası oluşturuyorsa.

  Daha fazla bilgi için bkz: [/MANIFEST (Yan yana derleme bildirimi oluşturma)](/cpp/build/reference/manifest-create-side-by-side-assembly-manifest).

- **OluşturmaMapFile**

  İsteğe bağlı **Boolean** parametresi.

  Bir `true` *harita dosyası oluşturursa.* Harita dosyasının dosya adı uzantısı *.map'tir.*

  Daha fazla bilgi için bkz: [/MAP (Mapfile oluştur)](/cpp/build/reference/map-generate-mapfile).

- **HeapCommitSize**

  İsteğe bağlı **String** parametresi.

  Yığındaki fiziksel bellek miktarını bir seferde ayırmak için belirtir.

  Daha fazla bilgi `commit` için [/HEAP (Küme yığını boyutu)](/cpp/build/reference/heap-set-heap-size)bağımsız değişkenine bakın. Ayrıca, **HeapReserveSize** parametrebakın.

- **HeapReserveSize**

  İsteğe bağlı **String** parametresi.

  Sanal bellekteki toplam yığın ayırmayı belirtir.

  Daha fazla bilgi `reserve` için [/HEAP (Küme yığını boyutu)](/cpp/build/reference/heap-set-heap-size)bağımsız değişkenine bakın. Ayrıca, bu tablodaki **HeapCommitSize** parametreye bakın.

- **Varsayılan Kitaplıkları Yok Sayma**

  İsteğe bağlı **Boolean** parametresi.

  `true`, bağlayıcıya dış başvuruları çözdüğünde aradığı kitaplıklar listesinden bir veya daha fazla varsayılan kitaplık kaldırmasını söylerse.

  Daha fazla bilgi için bkz: [/NODEFAULTLIB (Kitaplıkları yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **YoksayGömülüIDL**

  İsteğe bağlı **Boolean** parametresi.

  Kaynak `true`kodundaki herhangi bir IDL özniteliklerinin *.idl* dosyasında işlenmemesi gerektiğini belirtirse.

  Daha fazla bilgi için bkz: [/IGNOREIDL (Öznitelikleri MIDL'de işlemeyin)](/cpp/build/reference/ignoreidl-don-t-process-attributes-into-midl).

- **Alma Kitaplığını YokSama**

  İsteğe bağlı **Boolean** parametresi.

  Bu `true`yapılandırma tarafından oluşturulan alma kitaplığı bağımlı projelere içe aktarılmaması gerektiğini belirtirse.

  Bu parametre bağlayıcı seçeneğine karşılık gelmez.

- **Varsayılan Varsayılan Kitaplıkları YokSay**

  İsteğe bağlı **String[]** parametresi.

  Varsayılan kitaplıkların bir veya daha fazla adını yoksaymak için belirtir. Yarı-iki nokta üst üste kullanarak birden çok kitaplık ayırın.

  Daha fazla bilgi için bkz: [/NODEFAULTLIB (Kitaplıkları yoksay)](/cpp/build/reference/nodefaultlib-ignore-libraries).

- **ImageHasSafeExceptionHandlers**

  İsteğe bağlı **Boolean** parametresi.

  `true`Eğer , bağlayıcı bir görüntü üretirse, yalnızca görüntünün güvenli özel durum işleyicilerinin tablosunu da oluşturabiliyorsa.

  Daha fazla bilgi için bkz: [/SAFESEH (Görüntüde güvenli özel durum işleyicileri vardır)](/cpp/build/reference/safeseh-image-has-safe-exception-handlers).

- **İthalat Kütüphanesi**

  Varsayılan kitaplık adının yerine kullanıcı tarafından belirtilen bir içe aktarma kitaplığı adı.

  Daha fazla bilgi için bkz: [/IMPLIB (Ad alma kitaplığı)](/cpp/build/reference/implib-name-import-library).

- **Keycontainer**

  İsteğe bağlı **String** parametresi.

  İmzalı bir derleme için anahtar içeren kapsayıcı.

  Daha fazla bilgi için bkz: [/KEYCONTAINER (Derlemeyi imzalamak için anahtar kapsayıcı belirtin)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly). Ayrıca, bu tablodaki **KeyFile** parametresini görün.

- **Keyfile**

  İsteğe bağlı **String** parametresi.

  İmzalı derleme anahtarını içeren bir dosya belirtir.

  Daha fazla bilgi için bkz: [/KEYFILE (Derlemeyi imzalamak için anahtar veya anahtar çiftini belirtin)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly). Ayrıca, **KeyContainer** parametresini görün.

- **LargeAddressAware**

  İsteğe bağlı **Boolean** parametresi.

  Eğer `true`, uygulama 2 gigabayt daha büyük adresleri işleyebilir.

  Daha fazla bilgi için bkz: [/LARGEADDRESSAWARE (Büyük adresleri tut)](/cpp/build/reference/largeaddressaware-handle-large-addresses).

- **LinkDLL**

  İsteğe bağlı **Boolean** parametresi.

  Ana `true`çıktı dosyası olarak bir DLL oluşturursa.

  Daha fazla bilgi için bkz: [/DLL (DLL oluştur)](/cpp/build/reference/dll-build-a-dll).

- **LinkErrorReporting**

  İsteğe bağlı **String** parametresi.

  Dahili derleyici hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamanızı sağlar.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NoErrorReport** - **/ERRORREPORT:NONE**

  - **Hemen İste** - **/ERRORREPORT:PROMPT**

  - **QueueForNextLogin** - **/ERRORREPORT:QUEUE**

  - **SendErrorReport** - **/ERRORREPORT:SEND**

  Daha fazla bilgi için bkz: [/ERRORREPORT (İç bağlayıcı hatalarını bildirin)](/cpp/build/reference/errorreport-report-internal-linker-errors).

- **LinkIncremental**

  İsteğe bağlı **Boolean** parametresi.

  Eğer, `true`artımlı bağlantı sağlar.

  Daha fazla bilgi için bkz: [/INCREMENTAL (Bağlantı artımlı)](/cpp/build/reference/incremental-link-incrementally).

- **LinkLibraryBağımlılıklar**

  İsteğe bağlı **Boolean** parametresi.

  Proje `true`bağımlılıklarından kitaplık çıktılarının otomatik olarak bağlandığını belirtirse.

  Bu parametre bağlayıcı seçeneğine karşılık gelmez.

- **Bağlantı Durumu**

  İsteğe bağlı **Boolean** parametresi.

  Eğer, `true`bağlayıcı bağlantının yüzde sinin tamamladığını gösteren bir ilerleme göstergesi görüntülemek için olduğunu belirtir.

  Daha fazla bilgi `STATUS` için [/LTCG (Bağlantı zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation)bağımsız değişkenine bakın.

- **LinkTimeCodeGeneration**

  İsteğe bağlı **String** parametresi.

  Profil güdümlü optimizasyon seçenekleri belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *yok>\<*

  - **UseLinkTimeCodeGeneration** - **/LTCG**

  - **PGInstrument** - **/LTCG:PGInstrument**

  - **PGOptimizasyon** - **/LTCG:PGOptimize**

  - **PGUpdate**

    \-**/LTCG:PGUpdate**

  Daha fazla bilgi için bkz: [/LTCG (Bağlantı zamanı kodu oluşturma)](/cpp/build/reference/ltcg-link-time-code-generation).

- **ManifestFile**

  İsteğe bağlı **String** parametresi.

  Varsayılan bildirim dosya adını belirtilen dosya adıyla değiştirir.

  Daha fazla bilgi için bkz: [/MANIFESTFILE (Ad bildirimi dosyası)](/cpp/build/reference/manifestfile-name-manifest-file).

- **MapExports**

  İsteğe bağlı **Boolean** parametresi.

  Eğer, `true`bağlayıcıya dışa aktarılan işlevleri bir harita dosyasına eklemesini söyler.

  Daha fazla bilgi `EXPORTS` için [/MAPINFO (Mapfile'daki bilgileri dahil et)](/cpp/build/reference/mapinfo-include-information-in-mapfile)bağımsız değişkenine bakın.

- **MapFileName**

  İsteğe bağlı **String** parametresi.

  Varsayılan harita dosya adını belirtilen dosya adıyla değiştirir.

- **BirleştirmeIDLBaseFileName**

  İsteğe bağlı **String** parametresi.

  *.idl* dosyasının dosya adı ve dosya adı uzantısını belirtir.

  Daha fazla bilgi için bkz: [/IDLOUT (Name MIDL çıktı dosyaları)](/cpp/build/reference/idlout-name-midl-output-files).

- **Birleştirme Bölümleri**

  İsteğe bağlı **String** parametresi.

  Görüntüdeki bölümleri birleştirir. `from-section=to-section` belirtin.

  Daha fazla bilgi için bkz: [/MERGE (Bölümleri birleştir)](/cpp/build/reference/merge-combine-sections).

- **MidlCommandFile**

  İsteğe bağlı **String** parametresi.

  MIDL komut satırı seçeneklerini içeren bir dosyanın adını belirtin.

  Daha fazla bilgi için bkz: [/MIDL (MIDL komut satırı seçeneklerini belirtin)](/cpp/build/reference/midl-specify-midl-command-line-options).

- **Minimum Gerekli Sürüm**

  İsteğe bağlı **String** parametresi.

  Alt sistemin en az gerekli sürümünü belirtir. Bağımsız değişkenler 0 ile 65535 aralığındaki ondalık sayılardır.

- **ModülTanımDosyası**

  İsteğe bağlı **String** parametresi.

  [Modül tanım dosyasının](/cpp/build/reference/module-definition-dot-def-files)adını belirtir.

  Daha fazla bilgi için bkz: [/DEF (Modül tanımlı dosya belirtin)](/cpp/build/reference/def-specify-module-definition-file).

- **MSDOSStubFileName**

  İsteğe bağlı **String** parametresi.

  Belirtilen MS-DOS saplama programını Win32 programına bağlar.

  Daha fazla bilgi için bkz: [/STUB (MS-DOS saplama dosya adı)](/cpp/build/reference/stub-ms-dos-stub-file-name).

- **NoEntryPoint**

  İsteğe bağlı **Boolean** parametresi.

  Eğer, `true`yalnızca kaynak DLL belirtir.

  Daha fazla bilgi için bkz: [/NOENTRY (Giriş noktası yok).](/cpp/build/reference/noentry-no-entry-point)

- **ObjectFiles**

  Örtük **String[]** parametresi.

  Bağlı nesne dosyalarını belirtir.

- **Optimize Referanslar**

  İsteğe bağlı **Boolean** parametresi.

  Eğer, `true`hiç başvurulamayan işlevleri ve/veya verileri ortadan kaldırırsa.

  Daha fazla bilgi `REF` için [/OPT (Optimizations)](/cpp/build/reference/opt-optimizations)deki bağımsız değişkene bakın.

- **Outputfile**

  İsteğe bağlı **String** parametresi.

  Bağlayıcının oluşturduğu varsayılan adı ve programın konumunu geçersiz kılar.

  Daha fazla bilgi için bkz: [/OUT (Çıktı dosya adı)](/cpp/build/reference/out-output-file-name).

- **PerUserRedirection**

  İsteğe bağlı **Boolean** parametresi.

  Ve `true` Kayıt Çıktısı etkinleştirilirse, kuvvetler kayıt defteri **HKEY_CURRENT_USER**yönlendirilecek **HKEY_CLASSES_ROOT** yazar.

- **ProprocessOutput**

  İsteğe bağlı `ITaskItem[]` parametre.

  Görevler tarafından tüketilebilen ve yayılan bir dizi önişlemci çıktı öğesi tanımlar.

- **PreventDllBinding**

  İsteğe bağlı **Boolean** parametresi.

  , `true` *Bind.exe'ye* bağlı görüntünün bağlı olmaması gerektiğini gösterirse.

  Daha fazla bilgi için bkz: [/ALLOWBIND (DLL bağlamayı engelle)](/cpp/build/reference/allowbind-prevent-dll-binding).

- **Profil**

  İsteğe bağlı **Boolean** parametresi.

  Performans `true` **Araçları** profilleyicisi ile kullanılabilecek bir çıktı dosyası üretirse.

  Daha fazla bilgi için bkz: [/PROFILE (Performance Tools profiler)](/cpp/build/reference/profile-performance-tools-profiler).

- **ProfileGuidedDatabase**

  İsteğe bağlı **String** parametresi.

  Çalışan program hakkında bilgi tutmak için kullanılacak *.pgd* dosyasının adını belirtir

  Daha fazla bilgi için bkz: [/PGD (Profil güdümlü optimizasyonlar için veritabanı belirtin)](/cpp/build/reference/pgd-specify-database-for-profile-guided-optimizations).

- **ProgramDatabaseFile**

  İsteğe bağlı **String** parametresi.

  Bağlayıcının oluşturduğu program veritabanı (PDB) için bir ad belirtir.

  Daha fazla bilgi için bkz: [/PDB (Program veritabanını kullan)](/cpp/build/reference/pdb-use-program-database).

- **RandomizeBaseAddress**

  İsteğe bağlı **Boolean** parametresi.

  If `true`, generates an executable image that can be randomly rebased at load time by using the *address space layout randomization* (ASLR) feature of Windows.

  Daha fazla bilgi için bkz: [/DYNAMICBASE (Adres alanı düzeni rasgeleleştirmekullanın)](/cpp/build/reference/dynamicbase-use-address-space-layout-randomization).

- **Kayıt Çıktısı**

  İsteğe bağlı **Boolean** parametresi.

  Bu `true`yapının birincil çıktısını kaydederse.

- **Bölüm Hizalama**

  İsteğe bağlı **İnteger** parametresi.

  Her bölümün hizalanmasını programın doğrusal adres alanı içinde belirtir. Parametre değeri bayt birim numarasıdır ve iki güçtür.

  Daha fazla bilgi için bkz: [/ALIGN (Bölüm hizalaması)](/cpp/build/reference/align-section-alignment).

- **SetChecksum**

  İsteğe bağlı **Boolean** parametresi.

  Checksum'u `true`bir *.exe* dosyasının üstbilgisinde ayarlarsa.

  Daha fazla bilgi için bkz: [/RELEASE (Checksum'u ayarla)](/cpp/build/reference/release-set-the-checksum).

- **İlerlemeyi Göster**

  İsteğe bağlı **String** parametresi.

  Bağlama işlemi için ilerleme raporlarının ayrıntılılığını belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet hiçbiri** - >*\<*

  - **LinkVerbose** - **/VERBOSE**

  - **LinkVerboseLib** - **/VERBOSE:Lib**

  - **BağlantıVerboseICF** - **/VERBOSE:ICF**

  - **LinkVerboseREF** - **/VERBOSE:REF**

  - **LinkVerboseSAFESEH** - **/VERBOSE:SAFESEH**

  - **LinkVerboseCLR** - **/VERBOSE:CLR**

  Daha fazla bilgi için bkz: [/VERBOSE (Devam iletilerini yazdır)](/cpp/build/reference/verbose-print-progress-messages).

- **Kaynak**

  Gerekli `ITaskItem[]` parametre.

  Görevler tarafından tüketilebilen ve yayılabilen bir dizi MSBuild kaynak dosya öğesi tanımlar.

- **BelirtmeBölüm Özellikleri**

  İsteğe bağlı **String** parametresi.

  Bir bölümün özniteliklerini belirtir. Bu, bölümün *.obj* dosyası derlendiğinde ayarlanan öznitelikleri geçersiz kılar.

  Daha fazla bilgi için bkz: [/SECTION (Bölüm özniteliklerini belirtin)](/cpp/build/reference/section-specify-section-attributes).

- **StackCommitSize Boyutu**

  İsteğe bağlı **String** parametresi.

  Ek bellek tahsis edildiğinde, her ayırmadaki fiziksel bellek miktarını belirtir.

  Daha fazla bilgi `commit` için [/STACK (Yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations)bağımsız değişkenine bakın.

- **StackReserveSize**

  İsteğe bağlı **String** parametresi.

  Sanal bellekteki toplam yığın ayırma boyutunu belirtir.

  Daha fazla bilgi `reserve` için [/STACK (Yığın ayırmaları)](/cpp/build/reference/stack-stack-allocations)bağımsız değişkenine bakın.

- **StripPrivateSemboller**

  İsteğe bağlı **String** parametresi.

  Müşterilerinize dağıtmak istemediğiniz simgeleri atlayan ikinci bir program veritabanı (PDB) dosyası oluşturur. İkinci PDB dosyasının adını belirtin.

  Daha fazla bilgi için bkz: [/PDBSTRIPPED (Özel sembolleri şeritle)](/cpp/build/reference/pdbstripped-strip-private-symbols).

- **Alt**

  İsteğe bağlı **String** parametresi.

  Çalıştırılabilir için ortamı belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet hiçbiri** - >*\<*

  - **Konsol** - **/ALT SİsteM:KONSOL**

  - **Windows** - **/ALT SİsteM:WINDOWS**

  - **Yerel** - **/ALT SİsteM:YEREL**

  - **EFI Uygulama** - **/ALT SİsteM:EFI_APPLICATION**

  - **EFI Önyükleme Hizmeti Sürücüsü** - **/ALT SİsteM:EFI_BOOT_SERVICE_DRIVER**

  - **EFI ROM** - **/ALT SİsteM:EFI_ROM**

  - **EFI Çalışma Süresi** - **/ALT SİsteM:EFI_RUNTIME_DRIVER**

  - **WindowsCE** - **/ALT SİsteM:WINDOWSCE**

  - **POSIX** - **/ALT SISTEM:POSIX**

  Daha fazla bilgi için bkz: [/SUBSYSTEM (Alt sistemi belirtin)](/cpp/build/reference/subsystem-specify-subsystem).

- **DestekNobindOfDelayLoadedDLL**

  İsteğe bağlı **Boolean** parametresi.

  , `true`bağlayıcıya son görüntüye bağlanabilir bir İçe Aktarma Adresi Tablosu (IAT) eklememelerini söylerse.

  Daha fazla bilgi `NOBIND` için [/DELAY (Gecikme yükü alma ayarları)](/cpp/build/reference/delay-delay-load-import-settings)bağımsız değişkenine bakın.

- **DestekUnloadOfDelayLoadedDLL**

  İsteğe bağlı **Boolean** parametresi.

  DLL'nin `true`açık bir şekilde boşaltılmasını desteklemek için gecikme yükü yardımcı işlevini söylerse.

  Daha fazla bilgi `UNLOAD` için [/DELAY (Gecikme yükü alma ayarları)](/cpp/build/reference/delay-delay-load-import-settings)bağımsız değişkenine bakın.

- **BastırmaBaşlangıç Banner**

  İsteğe bağlı **Boolean** parametresi.

  Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.

  Daha fazla bilgi için bkz: [/NOLOGO (Başlangıç bayrağını bastırın) (bağlayıcı)](/cpp/build/reference/nologo-suppress-startup-banner-linker).

- **SwapRunFromCD**

  İsteğe bağlı **Boolean** parametresi.

  İşletim `true`sistemine önce bağlayıcı çıktısını bir takas dosyasına kopyalamasını ve sonra görüntüyü oradan çalıştırmasını söylerse.

  Daha fazla bilgi `CD` için [/SWAPRUN (Dosyayı takas etmek için bağlayıcı çıktısını yükleyin)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)bağımsız değişkenine bakın. Ayrıca **SwapRunFromNET** parametresini de görün.

- **SwapRunFromNET**

  İsteğe bağlı **Boolean** parametresi.

  İşletim `true`sistemine önce bağlayıcı çıktısını bir takas dosyasına kopyalamasını ve sonra görüntüyü oradan çalıştırmasını söylerse.

  Daha fazla bilgi `NET` için [/SWAPRUN (Dosyayı takas etmek için bağlayıcı çıktısını yükleyin)](/cpp/build/reference/swaprun-load-linker-output-to-swap-file)bağımsız değişkenine bakın. Ayrıca, bu tablodaki **SwapRunFromCD** parametresini görün.

- **Hedef Makine**

  İsteğe bağlı **String** parametresi.

  Program veya DLL için hedef platformu belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotSet hiçbiri** - >*\<*

  - **MachineARM** - **/MACHINE:ARM**

  - **MachineEBC** - **/MACHINE:EBC**

  - **MachineIA64** - **/MACHINE:IA64**

  - **MachineMIPS** - **/MACHINE:MIPS**

  - **MachineMIPS16** - **/MACHINE:MIPS16**

  - **MachineMIPSFPU** - **/MACHINE:MIPSFPU**

  - **MachineMIPSFPU16** - **/MACHINE:MIPSFPU16**

  - **MachineSH4** - **/MACHINE:SH4**

  - **MachineTHUMB** - **/MACHINE:THUMB**

  - **MachineX64** - **/MACHINE:X64**

  - **MachineX86** - **/MACHINE:X86**

  Daha fazla bilgi için bkz: [/MACHINE (Hedef platformu belirtin)](/cpp/build/reference/machine-specify-target-platform).

- **TerminalServerAware**

  İsteğe bağlı **Boolean** parametresi.

  Program `true`görüntüsünün isteğe bağlı üstbilgisinde IMAGE_OPTIONAL_HEADER DllCharacteristics alanına bir bayrak ayarlarsa. Bu bayrak ayarlandığında, Terminal Server uygulamada belirli değişiklikler yapmaz.

  Daha fazla bilgi için bkz: [/TSAWARE (Terminal Server aware uygulaması oluşturun)](/cpp/build/reference/tsaware-create-terminal-server-aware-application).

- **TrackerLogDirectory**

  İsteğe bağlı **String** parametresi.

  İzleyici günlüğünün dizinini belirtir.

- **TreatLinkerWarningAsErrors**

  İsteğe bağlı **Boolean** parametresi.

  Eğer `true`, bağlayıcı bir uyarı oluşturursa hiçbir çıktı dosyası oluşturulacak neden olur.

  Daha fazla bilgi için bkz: [/WX (Bağlayıcı uyarılarını hata olarak ele aürün)](/cpp/build/reference/wx-treat-linker-warnings-as-errors).

- **TurnoffAssemblyGeneration**

  İsteğe bağlı **Boolean** parametresi.

  Eğer `true`, bir .NET Framework derlemesi olmadan geçerli çıktı dosyası için bir görüntü oluşturur.

  Daha fazla bilgi için bkz: [/NOASSEMBLY (MSIL modülü oluşturma)](/cpp/build/reference/noassembly-create-a-msil-module).

- **TypeLibraryFile**

  İsteğe bağlı **String** parametresi.

  *.tlb* dosyasının dosya adı ve dosya adı uzantısını belirtir. Bir dosya adı veya bir yol ve dosya adı belirtin.

  Daha fazla bilgi için bkz: [/TLBOUT (İsim .tlb dosyası)](/cpp/build/reference/tlbout-name-dot-tlb-file).

- **TypeLibraryResourceID**

  İsteğe bağlı **İnteger** parametresi.

  Bağlayıcı tarafından oluşturulan tür kitaplığı için kullanıcı tarafından belirtilen bir değer belirler. 1 ile 65535 arasında bir değer belirtin.

  Daha fazla bilgi için bkz: [/TLBID (TypeLib için kaynak kimliği belirtin)](/cpp/build/reference/tlbid-specify-resource-id-for-typelib).

- **UACExecutionLevel**

  İsteğe bağlı **String** parametresi.

  Kullanıcı Hesabı Denetimi ile çalıştırıldığında uygulama için istenen yürütme düzeyini belirtir.

  Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Asınvoker** - `level='asInvoker'`

  - **En Yüksek Kullanılabilir** - `level='highestAvailable'`

  - **Zorunlu Yönetici** - `level='requireAdministrator'`

  Daha fazla bilgi `level` için [/MANIFESTUAC (UAC bilgilerini manifeste gömün)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)bağımsız değişkenine bakın.

- **UACUIAccess**

  İsteğe bağlı **Boolean** parametresi.

  `true`Uygulama kullanıcı arabirimi koruma düzeylerini atlar ve masaüstünde daha yüksek izinli pencerelere giriş sürücüler; aksi `false`takdirde, .

  Daha fazla bilgi `uiAccess` için [/MANIFESTUAC (UAC bilgilerini manifeste gömün)](/cpp/build/reference/manifestuac-embeds-uac-information-in-manifest)bağımsız değişkenine bakın.

- **KullanımLibraryDependencyInputs**

  İsteğe bağlı **Boolean** parametresi.

  `true`Proje bağımlılıklarının kitaplık çıktıları bağlandığında kütüphane dosyasının kendisi yerine kütüphane aracına girişler kullanılırsa.

- **Sürüm**

  İsteğe bağlı **String** parametresi.

  *.exe* veya *.dll* dosyasının üstbilgisinde bir sürüm numarası koyun. "`major[.minor]`" belirtin. Ve `major` `minor` bağımsız değişkenler 0 ile 65535 arasında ondalık sayılardır.

  Daha fazla bilgi için bkz: [/VERSION (Sürüm bilgileri)](/cpp/build/reference/version-version-information).

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
