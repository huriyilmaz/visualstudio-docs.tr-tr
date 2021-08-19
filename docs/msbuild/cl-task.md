---
title: CL Görev | Microsoft Docs
description: MSBuild CL görevinin amacını ve parametrelerini açıklar. Bu, Microsoft C++ derleyici aracını sarmalar ve cl.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
- vc.task.cl
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), CL task
- CL task (MSBuild (C++))
ms.assetid: 651ba971-b755-4f03-a549-4816beb3cc0d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b3f2d4fb5ce1a3ef2f5b4710067efdfe335231f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040053"
---
# <a name="cl-task"></a>CL görevi

Microsoft C++ derleyici aracını sarmalar ve *cl.exe.* Derleyici yürütülebilir (*.exe*) dosyaları, dinamik bağlantı kitaplığı (*.dll*) dosyaları veya kod modülü (*.netmodule*) dosyaları üretir. Daha fazla bilgi [için, bkz. Derleyici](/cpp/build/reference/compiler-options) [seçenekleri ve komut MSBuild'den](/cpp/build/msbuild-visual-cpp) Komut Satırı'MSBuild [Microsoft C++ araç kümesi kullanma.](/cpp/build/building-on-the-command-line)

## <a name="parameters"></a>Parametreler

 Aşağıdaki liste **CL** görevinin parametrelerini açıklar. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelen bir seçenektir.

- **AdditionalIncludeDirectories**

   İsteğe bağlı String[] parametresi.

   Ekleme dosyaları için aranan dizinler listesine bir dizin ekler.

   Daha fazla bilgi için bkz. [/I (Ek dizinleri dahil)](/cpp/build/reference/i-additional-include-directories).

- **AdditionalOptions**

   İsteğe bağlı Dize parametresi.

   Komut satırı seçeneklerinin listesi. Örneğin, "/ \<option1>  / \<option2>  / \<option#> ". Başka bir görev parametresiyle temsil etmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.

   Daha fazla bilgi için [bkz. Derleyici seçenekleri.](/cpp/build/reference/compiler-options)

- **AdditionalUsingDirectories**

   İsteğe bağlı String[] parametresi.

   Derleyicinin #using yönergesine geçirilen dosya başvurularını çözümlemek için **aray #using** belirtir.

   Daha fazla bilgi için [bkz. /AI (Meta veri dizinlerini belirt)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   İsteğe bağlı Dize parametresi.

   Komut satırına her zaman yayılan bir dize. Varsayılan değeri : "**/c**".

- **AssemblerListingLocation**

   Derleme kodunu içeren bir listeleme dosyası oluşturur.

   Daha fazla bilgi için bkz. [/FA, /Fa (Listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)içinde **/Fa** seçeneği.

- **AssemblerOutput**

   İsteğe bağlı Dize parametresi.

   Derleme kodunu içeren bir listeleme dosyası oluşturur.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NoListing** - *\<none>*

  - **AssemblyCode**  -  **/SSS**

  - **AssemblyAndMachineCode**  -  **/FAc**

  - **AssemblyAndSourceCode**  -  **/FAs**

  - **Tüm**  -  **/FAcs**

    Daha fazla bilgi için [,FA, /Fa (Listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)içinde **/FA**, **/FAc**, **/FAs** ve **/FAcs** seçeneklerine bakın.

- **BasicRuntimeChecks**

   İsteğe bağlı Dize parametresi.

   Çalışma zamanı hata denetimleri özelliğini [pragma](/cpp/preprocessor/runtime-checks) ile birlikte etkinleştiren runtime_checks devre dışı bıraktır.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** -                          *\<none>*

  - **StackFrameRuntimeCheck**  -  **/RTC'ler**

  - **UninitializedLocalUsageCheck**  -  **/RTCu**

  - **EnableFastChecks**  -                           **/RTC1**

    Daha fazla bilgi için bkz. [/RTC (Çalışma zamanı hata denetimleri)](/cpp/build/reference/rtc-run-time-error-checks).

- **BrowseInformation**

   İsteğe bağlı Boole parametresi.

   ise, `true` bir göz atma bilgileri dosyası oluşturur.

   Daha fazla bilgi için bkz. [/FR, /Fr (Create .sbr file)](/cpp/build/reference/fr-fr-create-dot-sbr-file)içinde **/FR** seçeneği.

- **BrowseInformationFile**

   İsteğe bağlı Dize parametresi.

   Göz atma bilgileri dosyası için bir dosya adı belirtir.

   Daha fazla bilgi için bu **tablodaki BrowseInformation** parametresine ve [ayrıca bkz. /FR, /Fr (Create .sbr file)](/cpp/build/reference/fr-fr-create-dot-sbr-file).

- **BufferSecurityCheck**

   İsteğe bağlı Boole parametresi.

   , dönüş adresinin üzerine yazacak bazı arabellek taşmalarını algılarsa, arabellek boyutu kısıtlamalarını zorlamadan koddan yararlanmaya `true` yönelik yaygın bir tekniktir.

   Daha fazla bilgi için bkz. [/GS (Arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check).

- **BuildingInIDE**

   İsteğe bağlı Boole parametresi.

   ise, `true` IDE **MSBuild** çağrıl olduğunu gösterir. Aksi **MSBuild** komut satırına çağrılır.

- **Callingconvention**

   İsteğe bağlı Dize parametresi.

   İşlev bağımsız değişkenlerinin yığına hangi sırayla itilmiş olduğunu, çağıranın işlevinin veya çağrılan işlevin çağrının sonundaki yığından bağımsız değişkenleri kaldırıp kaldırıp kaldırmayacaklarını ve derleyicinin tek tek işlevleri tanımlamak için kullandığı ad-dekorelama kuralını belirleyen çağırma kuralı belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Cdecl**  -  **/Gd**

  - **FastCall**  -                           **/Gr**

  - **StdCall**  -                           **/Gz**

    Daha fazla bilgi için bkz. [/Gd, /Gr, /Gv, /Gz (Çağırma kuralı)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **DerlemeA'lar**

   İsteğe bağlı Dize parametresi.

   Giriş dosyasının C veya C++ kaynak dosyası olarak derlenmiş olup olmadığını belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *\<none>*

  - **CompileAsC**  -  **/TC**

  - **CompileAsCpp**  -  **/TP**

    Daha fazla bilgi için bkz. [/Tc, /Tp, /TC, /TP (Kaynak dosya türünü belirtin)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **CompileAsManaged**

   İsteğe bağlı Dize parametresi.

   Uygulamaların ve bileşenlerin ortak dil çalışma zamanının (CLR) özelliklerini kullanmalarını sağlar.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **False** - *\<none>*

  - **true**  -  **/clr**

  - **Saf**  -  **/clr:pure**

  - **Kasa**  -  **/clr:safe**

  - **EskiSyntax**  -  **/clr:oldSyntax**

    Daha fazla bilgi için bkz. [/clr (Ortak dil çalışma zamanı derlemesi)](/cpp/build/reference/clr-common-language-runtime-compilation).

- **CreateHotpatchableImage**

   İsteğe bağlı Boole parametresi.

   ise, `true` derleyiciye bir görüntüyü düzeltme eki uygulama için *hazırlamasını söyler.* Bu parametre, her işlevin ilk yönergesi iki bayttır ve bu da düzeltme eki uygulama için gereklidir.

   Daha fazla bilgi için [bkz. /hotpatch (Hotpatchable görüntüsü oluşturma)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **DebugInformationFormat**

   İsteğe bağlı Dize parametresi.

   Programınız için oluşturulan hata ayıklama bilgileri türünü ve bu bilgilerin nesne (*.obj*) dosyalarında mı yoksa bir program veritabanında (PDB) mi tutulacaklarını seçer.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **EskiStyle**  -  **/Z7**

  - **ProgramDatabase**  -  **/Zi**

  - **EditAndContinue**  -  **/ZI**

    Daha fazla bilgi için bkz. [/Z7, /Zi, /ZI (Hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).

- **DisableLanguageExtensions**

   İsteğe bağlı Boole parametresi.

   true **ise,** derleyiciye ANSI C veya ANSI C++ ile uyumlu olan dil yapıları için bir hata yaymalarını söyler.

   Daha fazla bilgi için bkz. [/Za, /Ze (Dil uzantılarını devre dışı bırak)](/cpp/build/reference/za-ze-disable-language-extensions)içinde **/Za** seçeneği.

- **DisableSpecificWarnings**

   İsteğe bağlı String[] parametresi.

   Noktalı virgülle ayrılmış bir listede belirtilen uyarı numaralarını devre dışı verir.

   Daha fazla bilgi için `/wd` [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)içinde seçeneğine bakın.

- **EnableEnhancedInstructionSet**

   İsteğe bağlı Dize parametresi.

   Streaming SIMD Extensions (SSE) ve Streaming SIMD Extensions 2 (SSE2) yönergelerini kullanan kod oluşturma mimarisini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **StreamingSIMDExtensions**  -  **/arch:SSE**

  - **StreamingSIMDExtensions2**  -  **/arch:SSE2**

    Daha fazla bilgi için bkz. [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizations**

   İsteğe bağlı Boole parametresi.

   ise, statik iş parçacığı yerel depolaması, yani kullanılarak ayrılan veriler kullanılarak ayrılan veriler `true` için fiber güvenliği `__declspec(thread)` destekler.

   Daha fazla bilgi için bkz. [/GT (Fiber güvenli iş parçacığı yerel depolama desteği)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EnablePREfast**

   İsteğe bağlı Boole parametresi.

   ise, `true` kod analizini etkinleştirin.

   Daha fazla bilgi için bkz. [/analyze (Kod analizi)](/cpp/build/reference/analyze-code-analysis).

- **ErrorReporting**

   İsteğe bağlı Dize parametresi.

   İç derleyici hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamayı sağlar. Varsayılan olarak, IDE derlemeleri'nin ayarı **İstem** ve komut satırı derlemeleri ayarı **Kuyruk'tır.**

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Hiçbiri**  -  **/errorReport:none**

  - **İstem**  -  **/errorReport:prompt**

  - **Kuyruk**  -  **/errorReport:queue**

  - **Gönder**  -  **/errorReport:send**

    Daha fazla bilgi için bkz. [/errorReport (İç derleyici hatalarını raporla)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **ExceptionHandling**

   İsteğe bağlı Dize parametresi.

   Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **False** - *\<none>*

  - **Zaman uyumsuz**  -  **/EHa**

  - **Eşitleme**  -  **/EHsc**

  - **SyncCThrow**  -  **/EHs**

    Daha fazla bilgi için bkz. [/EH (Özel durum işleme modeli)](/cpp/build/reference/eh-exception-handling-model).

- **ExpandAttributedSource**

   İsteğe bağlı Boole parametresi.

   ise, `true` kaynak dosyaya ekli genişletilmiş öznitelikleri olan bir listeleme dosyası oluşturur.

   Daha fazla bilgi için bkz. [/Fx (Ekleme kodunu birleştir)](/cpp/build/reference/fx-merge-injected-code).

- **FavorSizeOrSpeed**

   İsteğe bağlı Dize parametresi.

   Kod boyutunun mu yoksa kod hızının mı tercihi olduğunu belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Ne** - *\<none>*

  - **Boyut**  -  **/OS**

  - **Hız**  -  **/Ot**

    Daha fazla bilgi için [bkz. /Os, /Ot (Küçük koda tercih edin, hızlı koda tercih edin)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **FloatingPointExceptions**

   İsteğe bağlı Boole parametresi.

   ise, `true` güvenilir kayan nokta özel durum modelini sağlar. Özel durumlar tetiklendiğinde hemen tetiklenir.

   Daha fazla bilgi için **,fp (Kayan nokta** davranışını belirt) içinde / [fp:except seçeneğine bakın.](/cpp/build/reference/fp-specify-floating-point-behavior)

- **FloatingPointModel**

   İsteğe bağlı Dize parametresi.

   Kayan nokta modelini ayarlar.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Hassas**  -  **/fp:precise**

  - **Katı**  -  **/fp:strict**

  - **Hızlı**  -  **/fp:fast**

    Daha fazla bilgi için bkz. [/fp (Kayan nokta davranışını belirtin)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceInForLoopScope**

   İsteğe bağlı Boole parametresi.

   ise, Microsoft uzantılarını ( /Ze ) kullanan döngüler için 'de standart `true` C++[davranışını uygulamaya alır.](/cpp/build/reference/za-ze-disable-language-extensions) [](/cpp/cpp/for-statement-cpp)

   Daha fazla bilgi için bkz. [/Zc:forScope (Döngü kapsamı için içinde uyumluluğu zorla)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **ForcedIncludeFiles**

   İsteğe `String[]` bağlı parametre.

   Önişlemcinin belirtilen bir veya daha fazla üst bilgi dosyalarını işlemeye neden olur.

   Daha fazla bilgi için bkz. [/FI (Zorla dahil olan dosya adı)](/cpp/build/reference/fi-name-forced-include-file).

- **ForcedUsingFiles**

   İsteğe **bağlı String[]** parametresi.

   Önişlemcinin belirtilen bir veya daha fazla veri **#using** neden olur.

   Daha fazla bilgi için bkz. [/FU (Zorlamalı #using adı)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FunctionLevelLinking**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` derleyicinin tek tek işlevleri paketlenmiş işlevler (COMDATs) şeklinde paketleyebiliyorsa.

   Daha fazla bilgi için [bkz. /Tüm (İşlev düzeyi bağlamayı etkinleştirme)](/cpp/build/reference/gy-enable-function-level-linking).

- **GenerateXMLDocumentationFiles**

   İsteğe `Boolean` bağlı parametre.

   ise, derleyicinin kaynak kod dosyalarındaki belge açıklamalarını işlemesi ve belge açıklamalarına sahip her kaynak kod dosyası için `true` *bir .xdc* dosyası oluşturmasına neden olur.

   Daha fazla bilgi için [bkz. /doc (belge açıklamalarını işleme) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Ayrıca bu **tablodaki XMLDocumentationFileName** parametresine de bakın.

- **IgnoreStandardIncludePath**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` derleyicinin PATH ve INCLUDE ortam değişkenlerde belirtilen dizinlerde include dosyaları aramasını önler.

   Daha fazla bilgi için bkz. [/X (Standart dahil etme yollarını yoksay)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   İsteğe **bağlı Dize** parametresi.

   Derleme için satır içi işlev genişletme düzeyini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *\<none>*

  - **Devre dışı**  -  **/Ob0**

  - **YalnızcaExplicitInline**  -  **/Ob1**

  - **AnySuitable**  -  **/Ob2**

    Daha fazla bilgi için bkz. [/Ob (Satır içi işlev genişletmesi)](/cpp/build/reference/ob-inline-function-expansion).

- **IntrinsicFunctions**

   İsteğe `Boolean` bağlı parametre.

   ise, bazı işlev çağrılarını, uygulamanın daha hızlı çalışmasına yardımcı olan iç veya başka `true` özel işlev biçimleriyle değiştirir.

   Daha fazla bilgi için [bkz. /Oi (Iç işlevler oluşturma)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   İsteğe `Boolean` bağlı parametre.

   ise, değiştirilen C++ sınıf tanımlarını (üst bilgi (.h) dosyalarında depolanan) içeren C++ kaynak dosyalarının yeniden derleme gerekip gerek olmadığını belirleyen en az yeniden `true` derlemeyi sağlar.

   Daha fazla bilgi için bkz. [/Gm (En az yeniden oluşturmayı etkinleştir)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` derlemek için birden çok işlemci kullanın. Bu parametre, bilgisayarınızda her etkili işlemci için bir işlem oluşturur.

   Daha fazla bilgi için bkz. [/MP (Birden çok işlemle derleme)](/cpp/build/reference/mp-build-with-multiple-processes). Ayrıca, bu **tablodaki ProcessorNumber** parametresine bakın.

- **ObjectFileName**

   İsteğe **bağlı Dize** parametresi.

   Varsayılan yerine kullanılacak nesne (.obj) dosya adını veya dizinini belirtir.

   Daha fazla bilgi için bkz. [/Fo (Nesne dosyası adı)](/cpp/build/reference/fo-object-file-name).

- **ObjectFiles**

   İsteğe **bağlı String[]** parametresi.

   Nesne dosyalarının listesi.

- **OmitDefaultLibName**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` nesne (*.obj*) dosyasından varsayılan C çalışma zamanı kitaplık adını atlar. Derleyici varsayılan olarak kitaplığın adını *.obj* dosyasına koyarak bağlantıleyiciyi doğru kitapla yönlendirer.

   Daha fazla bilgi için bkz. [/Zl (Varsayılan kitaplık adını atla)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` çağrı yığınında çerçeve işaretçilerinin oluşturulmasını bastırıyor.

   Daha fazla bilgi için [bkz. /Oy (Çerçeve işaretçisini atla)](/cpp/build/reference/oy-frame-pointer-omission).

- **OpenMPSupport**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` derleyicinin OpenMP yan tümcelerini ve yönergelerini işlemesine neden olur.

   Daha fazla bilgi için bkz. [/openmp (OpenMP 2.0 desteğini etkinleştirme)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **İyileştirme**

   İsteğe **bağlı Dize** parametresi.

   Hız ve boyut için çeşitli kod iyileştirmelerini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Devre dışı**  -  **/Od**

  - **MinSpace**  -  **/O1**

  - **MaxSpeed**  -  **/O2**

  - **Tam**  -  **/Ox**

    Daha fazla bilgi için bkz. [/O Seçenekleri (Kodu iyileştirme)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   İsteğe **bağlı Dize** parametresi.

   Derleme sırasında önceden bir üst bilgi (*.pch*) dosyası oluşturun veya kullanın.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotUsing** - *\<none>*

  - **Oluştur**  -  **/Yc**

  - **Kullanma**  -  **/Yu**

    Daha fazla bilgi için [bkz. /Yc (Önceden derlemeli](/cpp/build/reference/yc-create-precompiled-header-file) üst bilgi dosyası oluştur) [ve /Yu (Önceden derlemeli üst bilgi dosyasını kullan)](/cpp/build/reference/yu-use-precompiled-header-file). Ayrıca, bu **tablodaki PrecompiledHeaderFile** ve **PrecompiledHeaderOutputFile** parametrelerine bakın.

- **PrecompiledHeaderFile**

   İsteğe **bağlı Dize** parametresi.

   Oluşturmak veya kullanmak için önceden derlemeli bir üst bilgi dosyası adı belirtir.

   Daha fazla bilgi için [bkz. /Yc (Önceden derlemeli](/cpp/build/reference/yc-create-precompiled-header-file) üst bilgi dosyası oluştur) [ve /Yu (Önceden derlemeli üst bilgi dosyasını kullan)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   İsteğe **bağlı Dize** parametresi.

   Varsayılan yol adını kullanmak yerine önceden derlemeli üst bilgi için bir yol adı belirtir.

   Daha fazla bilgi için bkz. [/Fp (.pch dosyasını adı)](/cpp/build/reference/fp-name-dot-pch-file).

- **PreprocessKeepComments**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` ön işleme sırasında yorumları korur.

   Daha fazla bilgi için [bkz. /C (Ön işleme sırasında yorumları koru)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **ÖnişlemciDefinitions**

   İsteğe `String[]` bağlı parametre.

   Kaynak dosyanız için bir önişleme simgesi tanımlar.

   Daha fazla bilgi için bkz. [/D (Önişlemci tanımları)](/cpp/build/reference/d-preprocessor-definitions).

- **PreprocessOutput**

   İsteğe `ITaskItem[]` bağlı parametre.

   Görevler tarafından tüketilen ve yayılan bir önişlemci çıkış öğeleri dizisi tanımlar.

- **PreprocessOutputPath**

   İsteğe `String` bağlı parametre.

   **PreprocessToFile** parametresinin önceden işlenmemiş çıkışı yazdığı çıktı dosyasının adını belirtir.

   Daha fazla bilgi için bkz. [/Fi (Çıktı dosyası adını önişle)](/cpp/build/reference/fi-preprocess-output-file-name).

- **PreprocessSuppressLineNumbers**

   İsteğe `Boolean` bağlı parametre.

   ise, C ve C++ kaynak dosyalarını önişler ve önceden `true` işlenmemiş dosyaları standart çıkış cihazına kopyalar.

   Daha fazla bilgi için bkz. [/EP (Stdout'a önişle ve #line olmadan)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **PreprocessToFile**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` C ve C++ kaynak dosyalarını önişler ve önişlen çıkışı bir dosyaya yazar.

   Daha fazla bilgi için bkz. [/P (Bir dosyaya ön işleme)](/cpp/build/reference/p-preprocess-to-a-file).

- **ProcessorNumber**

   İsteğe `Integer` bağlı parametre.

   Çok işlemcili derlemede en fazla işlemci sayısını belirtir. Bu parametreyi **MultiProcessorCompilation parametresiyle birlikte** kullanın.

- **ProgramDataBaseFileName**

   İsteğe `String` bağlı parametre.

   Program veritabanı (PDB) dosyası için bir dosya adı belirtir.

   Daha fazla bilgi için bkz. [/Fd (Program veritabanı dosya adı)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   İsteğe `String` bağlı parametre.

   Çok iş parçacıklı bir modülün DLL olup olmadığını gösterir ve çalışma zamanı kitaplığının perakende veya hata ayıklama sürümlerini seçer.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **MultiThreaded**  -  **/MT**

  - **MultiThreadedDebug**  -  **/MTd**

  - **MultiThreadedDLL**  -  **/MD**

  - **MultiThreadedDebugDLL**  -  **/MDd**

    Daha fazla bilgi için bkz. [/MD, /MT, /LD (Çalışma zamanı kitaplığını kullan)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` çalışma zamanında C++ nesne türlerini denetlemeye kod ekler (çalışma zamanı türü bilgileri).

   Daha fazla bilgi için bkz. [/GR (Çalışma zamanı türü bilgilerini etkinleştir)](/cpp/build/reference/gr-enable-run-time-type-information).

- **ShowIncludes**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` derleyicinin ekleme dosyalarının listesini çıkışına neden olur.

   Daha fazla bilgi için bkz. [/showIncludes (Liste ekleme dosyaları)](/cpp/build/reference/showincludes-list-include-files).

- **SmallerTypeCheck**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` bir değerin daha küçük bir veri türüne atandığı ve veri kaybına neden olduğu bir çalışma zamanı hatası raporlar.

   Daha fazla bilgi için bkz. [/RTC'de /RTCc seçeneği (Çalışma zamanı hata denetimleri)](/cpp/build/reference/rtc-run-time-error-checks). 

- **Kaynaklar**

   Gerekli `ITaskItem[]` parametre.

   Boşluklarla ayrılmış kaynak dosyaların listesini belirtir.

- **StringPooling**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` derleyicinin program görüntüsünde aynı dizelerin bir kopyasını oluşturmalarını sağlar.

   Daha fazla bilgi için bkz. [/GF (Yinelenen dizeleri ortadan kaldırma)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   İsteğe `String` bağlı parametre.

   Bir yapıda tüm üyeler için bayt hizalamasını belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan**  -  **/Zp1**

  - **1Bayt**  -  **/Zp1**

  - **2Bayt**  -  **/Zp2**

  - **4Bayt**  -  **/Zp4**

  - **8Bayt**  -  **/Zp8**

  - **16Bayt**  -  **/Zp16**

    Daha fazla bilgi için bkz. [/Zp (Yapı üyesi hizalaması)](/cpp/build/reference/zp-struct-member-alignment).

- **SuppressStartupBanner**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.

   Daha fazla bilgi için bkz. [/nologo (Başlangıç başlığı gizleme) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   İsteğe `String` bağlı parametre.

   Bu görevin izleme günlüklerinin depolandığı ara dizini belirtir.

   Daha fazla bilgi için bu **tablodaki TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.

- **TreatSpecificWarningsAsErrors**

   İsteğe **bağlı String[]** parametresi.

   Belirtilen derleyici uyarıları listesini hata olarak davranır.

   Daha fazla bilgi  için `n` [bkz. /w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWarningAsError**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` tüm derleyici uyarılarını hata olarak işle.

   Daha fazla bilgi  için [bkz. /w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` türü yerel bir tür olarak `wchar_t` işle.

   Daha fazla bilgi için bkz. [/Zc:wchar_t (wchar_t türü)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **UndefineAllPreprocessorDefinitions**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` derleyicinin tanımladığı Microsoft'a özgü sembolleri tanımlar.

   Daha fazla bilgi için bkz. [/U, /u (Tanımsız semboller)](/cpp/build/reference/u-u-undefine-symbols)içinde **/u** seçeneği.

- **UndefinePreprocessorDefinitions**

   İsteğe `String[]` bağlı parametre.

   Tanımsız hale gelen bir veya daha fazla önişlemci sembolü listesini belirtir.

   Daha fazla bilgi için bkz. [/U, /u (Tanımsız semboller)](/cpp/build/reference/u-u-undefine-symbols)içinde **/U** seçeneği.

- **UseFullPaths**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` tanılamada derleyiciye geçirilen kaynak kod dosyalarının tam yolunu görüntüler.

   Daha fazla bilgi için bkz. [/FC (Tanılamada kaynak kod dosyasının tam yolu)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` çıkış dosyasının UTF-8 biçiminde oluşturulmuş olmasına neden olur.

   Daha fazla bilgi için bkz. [/FA, /Fa (Listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)içinde **/FAu** seçeneği.

- **WarningLevel**

   İsteğe `String` bağlı parametre.

   Derleyici tarafından oluşturulan en yüksek uyarı düzeyini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **TurnOffAllWarnings**  -  **/W0**

  - **Düzey1**  -  **/W1**

  - **Düzey2**  -  **/W2**

  - **Düzey3**  -  **/W3**

  - **Düzey4**  -  **/W4**

  - **EnableAllWarnings**  -  **/Wall**

    Daha fazla bilgi  için [bkz. /w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).

- **WholeProgramOptimization**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` tüm program iyileştirmeyi sağlar.

   Daha fazla bilgi için bkz. [/GL (Tam program iyileştirmesi)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   İsteğe `String` bağlı parametre.

   Oluşturulan XML belge dosyalarının adını belirtir. Bu parametre bir dosya veya dizin adı olabilir.

   Daha fazla bilgi için `name` [/doc (İşlem belgeleri yorumları) (C/C++) içinde bağımsız değişkenine bakın.](/cpp/build/reference/doc-process-documentation-comments-c-cpp) Ayrıca bu **tablodaki GenerateXMLDocumentationFiles** parametresine de bakın.

- **MinimalRebuildFromTracking**

   İsteğe `Boolean` bağlı parametre.

   ise, `true` izlenen bir artımlı derleme gerçekleştirilir; `false` ise, bir yeniden derleme gerçekleştirilir.

- **TLogReadFiles**

   İsteğe `ITaskItem[]` bağlı parametre.

   Okuma dosyası izleme günlüklerini temsil eden *bir öğe dizisi belirtir.*

   Okuma dosyası izleme günlüğü (*.tlog),* bir görev tarafından okunan giriş dosyalarının adlarını içerir ve artımlı derlemeleri desteklemek için proje derleme sistemi tarafından kullanılır. Daha fazla bilgi için bu **tablodaki TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.

- **TLogWriteFiles**

   İsteğe bağlı `ITaskItem[]` parametre.

   *Yazma dosyası izleme günlüklerini* temsil eden bir öğe dizisi belirtir.

   Yazma dosyası izleme günlüğü (*. TLog*), bir görev tarafından yazılan çıkış dosyalarının adlarını içerir ve proje yapı sistemi tarafından artımlı derlemeleri desteklemek için kullanılır. Daha fazla bilgi için bu tablodaki **TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.

- **TrackFileAccess**

   İsteğe bağlı `Boolean` parametre.

   İse `true` , dosya erişim desenlerini izler.

   Daha fazla bilgi için bu tablodaki **TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
