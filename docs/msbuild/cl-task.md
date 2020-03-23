---
title: CL Görevi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb0e1feee1f7e1d271dd436a1879731354cbd8bb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865343"
---
# <a name="cl-task"></a>CL görevi

Microsoft C++ derleyici *aracıcl.exe'yi*sarar. Derleyici yürütülebilir (*.exe*) dosyaları, dinamik bağlantı kitaplığı (*.dll*) dosyaları veya kod modülü (*.netmodule*) dosyaları üretir. Daha fazla bilgi için [Derleyici seçeneklerine](/cpp/build/reference/compiler-options) bakın ve [komut satırından MSBuild kullanın](/cpp/build/msbuild-visual-cpp) ve [komut satırından Microsoft C++ araç kümesini kullanın.](/cpp/build/building-on-the-command-line)

## <a name="parameters"></a>Parametreler

 Aşağıdaki liste **CL** görevinin parametrelerini açıklar. Görev parametrelerinin çoğu ve birkaç parametre kümesi komut satırı seçeneğine karşılık gelir.

- **EkIncludeDirectories**

   İsteğe bağlı String[] parametresi.

   Aranan dizinler listesine bir dizin ekler.

   Daha fazla bilgi için bkz: [/I (Ek dizinler dahil)](/cpp/build/reference/i-additional-include-directories).

- **Ek Seçenekler**

   İsteğe bağlı String parametresi.

   Komut satırı seçenekleri listesi. Örneğin, "/\<option1\<> /\<option2> / option#>". Başka bir görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.

   Daha fazla bilgi için [Derleyici seçeneklerine](/cpp/build/reference/compiler-options)bakın.

- **EkUsingDirectories**

   İsteğe bağlı String[] parametresi.

   Derleyicinin **#using** yönergesine aktarılan dosya başvurularını çözümlemek için arayacağı bir dizini belirtir.

   Daha fazla bilgi için bkz: [/AI (Meta veri dizinlerini belirtin)](/cpp/build/reference/ai-specify-metadata-directories).

- **AlwaysAppend**

   İsteğe bağlı String parametresi.

   Komut satırına her zaman yayılan bir dize. Varsayılan değeri "**/c**"dür.

- **AssemblerListingLocation**

   Derleme kodu içeren bir giriş dosyası oluşturur.

   Daha fazla bilgi için [/Fa, /Fa (Listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file) **seçeneğine** bakın.

- **AssemblerÇıktı**

   İsteğe bağlı String parametresi.

   Derleme kodu içeren bir giriş dosyası oluşturur.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Hiçbir>Listeleme** - *\<*

  - **Montaj Kodu** - **/FA**

  - **AssemblyAndMachineCode** - **/FAc**

  - **AssemblyAndSourceCode** - **/FAs**

  - **Tüm** - **/FAcs**

    Daha fazla bilgi için **/FA**, **/FAc**, **/FAs**, ve **/ FAcs** seçenekleri / [FA, / Fa (Listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)bakın.

- **BasicRuntimeChecks**

   İsteğe bağlı String parametresi.

   [runtime_checks](/cpp/preprocessor/runtime-checks) pragma ile birlikte çalışma zamanı hata denetimleri özelliğini etkinleştirir ve devre dışı kılabilir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** -                          *yok>\<*

  - **StackFrameRuntimeCheck** - **/RTC'ler**

  - **UninitializedLocalUsageCheck** - **/RTCu**

  - **Hızlı Kontrolleri** -                          **Etkinleştirme /RTC1**

    Daha fazla bilgi için bkz: [/RTC (Çalışma zamanı hata denetimleri).](/cpp/build/reference/rtc-run-time-error-checks)

- **GözatBilgi**

   İsteğe bağlı Boolean parametresi.

   Bir `true`gözatma bilgi dosyası oluşturursa.

   Daha fazla bilgi için **/FR,** [/Fr (.sbr dosyası oluştur)](/cpp/build/reference/fr-fr-create-dot-sbr-file)seçeneğine bakın.

- **GözatInformationFile**

   İsteğe bağlı String parametresi.

   Gözatma bilgileri dosyası için bir dosya adı belirtir.

   Daha fazla bilgi için bu tablodaki **Gözat Bilgi** parametresini ve [/FR, /Fr (.sbr dosyası oluşturma)](/cpp/build/reference/fr-fr-create-dot-sbr-file)'ye bakın.

- **BufferSecurityCheck**

   İsteğe bağlı Boolean parametresi.

   Geri `true`dönüş adresinin üzerine çıkan bazı arabellek taşmaları algılarsa, arabellek boyutu kısıtlamalarını zorlamayan koddan yararlanmak için yaygın bir teknik.

   Daha fazla bilgi için bkz: [/GS (Arabellek güvenlik denetimi)](/cpp/build/reference/gs-buffer-security-check).

- **BinaInIDE**

   İsteğe bağlı Boolean parametresi.

   `true`MSBuild'in **MSBuild** IDE tarafından çağrıldığını gösterirse. Aksi takdirde, **MSBuild** komut satırında çağrılır.

- **Callingconvention**

   İsteğe bağlı String parametresi.

   İşlev bağımsız değişkenlerinin yığına itme sırasını, arayan işlevin veya çağrılan işlevin çağrının sonundaki yığından bağımsız değişkenleri kaldırıp kaldırmadığını ve ad-dekorasyon kuralını belirleyen çağrı kuralını belirtir. derleyici tek tek işlevleri tanımlamak için kullanır.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Cdecl** - **/Gd**

  - **FastCall** -                          **/Gr**

  - **StdCall** -                          **/Gz**

    Daha fazla bilgi için bkz: [/Gd, /Gr, /Gv, /Gz (Çağrı sözleşmesi)](/cpp/build/reference/gd-gr-gv-gz-calling-convention).

- **DerleeAs**

   İsteğe bağlı String parametresi.

   Giriş dosyasının C veya C++ kaynak dosyası olarak derlenip derlenip derlenip derlenip derlenip derlenip derlenip derlenip derlenip derlilemeyeceğini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *yok>\<*

  - **DerlemeAsC** - **/TC**

  - **DerlemeAsCpp** - **/TP**

    Daha fazla bilgi için bkz: [/Tc, /Tp, /TC, /TP (Kaynak dosya türünü belirtin)](/cpp/build/reference/tc-tp-tc-tp-specify-source-file-type).

- **DerleeAsManaged**

   İsteğe bağlı String parametresi.

   Uygulamaların ve bileşenlerin ortak dil çalışma süresi (CLR) özelliklerini kullanmasını sağlar.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **yanlış** - *hiçbiri>\<*

  - **gerçek** - **/clr**

  - **Saf** - **/clr:saf**

  - **Güvenli** - **/clr:güvenli**

  - **OldSyntax** - **/clr:oldSyntax**

    Daha fazla bilgi için bkz: [/clr (Ortak dil çalışma zamanı derlemesi).](/cpp/build/reference/clr-common-language-runtime-compilation)

- **CreateHotpatchableImage**

   İsteğe bağlı Boolean parametresi.

   Eğer, `true`derleyici *sıcak yama*için bir görüntü hazırlamak için söyler. Bu parametre, her işlevin ilk talimatının sıcak yama için gerekli olan iki bayt olmasını sağlar.

   Daha fazla bilgi için bkz: [/hotpatch (Hotpatchable image oluştur)](/cpp/build/reference/hotpatch-create-hotpatchable-image).

- **Hata AyıklamaInformationFormat**

   İsteğe bağlı String parametresi.

   Programınız için oluşturulan hata ayıklama bilgilerinin türünü ve bu bilgilerin nesne *(.obj*) dosyalarında mı yoksa program veritabanında (PDB) tutulup tutulmadığını seçer.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **OldStyle** - **/Z7**

  - **ProgramVeritabanı** - **/Zi**

  - **EditAndContinue** - **/ZI**

    Daha fazla bilgi için bkz: [/Z7, /Zi, /ZI (Hata ayıklama bilgi biçimi).](/cpp/build/reference/z7-zi-zi-debug-information-format)

- **Dil Uzantılarını Devre Dışı**

   İsteğe bağlı Boolean parametresi.

   **Doğruysa,** derleyiciye ANSI C veya ANSI C++ ile uyumlu olmayan dil yapıları için bir hata yontmasını söyler.

   Daha fazla bilgi **/Za** için [/Za, /Ze (Dil uzantılarını devre dışı)](/cpp/build/reference/za-ze-disable-language-extensions)seçeneğine bakın.

- **Devre Dışı Özel Uyarılar**

   İsteğe bağlı String[] parametresi.

   Yarı sütunlu sınırlı bir listede belirtilen uyarı numaralarını devre dışı alır.

   Daha fazla bilgi `/wd` için [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)seçeneğine bakın.

- **EtkinleştirmeInstructionSet**

   İsteğe bağlı String parametresi.

   Akış SIMD Uzantıları (SSE) ve Streaming SIMD Uzantıları 2 (SSE2) yönergelerini kullanan kod oluşturma mimarisini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **StreamingSIMDExtensions** - **/arch:SSE**

  - **StreamingSIMDExtensions2** - **/arch:SSE2**

    Daha fazla bilgi için bkz: [/arch (x86)](/cpp/build/reference/arch-x86).

- **EnableFiberSafeOptimizasyonasyonları**

   İsteğe bağlı Boolean parametresi.

   Statik `true`iş parçacığı yerel depolama kullanılarak ayrılan veriler için fiber güvenliğini destekliyorsa, yani kullanılarak `__declspec(thread)`ayrılan veriler.

   Daha fazla bilgi için bkz: [/GT (Fiber güvenli iş parçacığı yerel depolamayı destekleyin)](/cpp/build/reference/gt-support-fiber-safe-thread-local-storage).

- **EtkinleştirMEPREfast**

   İsteğe bağlı Boolean parametresi.

   Eğer `true`, kod analizi etkinleştirin.

   Daha fazla bilgi için bkz. [/analyze (Kod analizi)](/cpp/build/reference/analyze-code-analysis).

- **Hata Raporlama**

   İsteğe bağlı String parametresi.

   Dahili derleyici hatası (ICE) bilgilerini doğrudan Microsoft'a sağlamanızı sağlar. Varsayılan olarak, IDE yapılarında ayar **İstem** ve komut satırı yapılarında ayar **Sıra'dır.**

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Yok** - **/errorReport:none**

  - **Komut istemi** - **/errorReport:prompt**

  - **Sıra** - **/hataRapor:queue**

  - **Gönder** - **/errorReport:gönder**

    Daha fazla bilgi için bkz: [/errorReport (İç derleyici hatalarını bildirin)](/cpp/build/reference/errorreport-report-internal-compiler-errors).

- **Özel Durum Kullanımı**

   İsteğe bağlı String parametresi.

   Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **yanlış** - *hiçbiri>\<*

  - **Async** - **/EHa**

  - **Senkronize** - **/EHsc**

  - **SyncCThrow** - **/EHs**

    Daha fazla bilgi için bkz: [/EH (Özel Durum işleme modeli).](/cpp/build/reference/eh-exception-handling-model)

- **ExpandAttributedSource**

   İsteğe bağlı Boolean parametresi.

   Kaynak `true`dosyaya enjekte edilen öznitelikleri genişleten bir listeleme dosyası oluşturursa.

   Daha fazla bilgi için bkz: [/Fx (Enjekte edilen kodu birleştir)](/cpp/build/reference/fx-merge-injected-code).

- **Favorsizeorspeed**

   İsteğe bağlı String parametresi.

   Kod boyutunu veya kod hızını kayırmayı belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Neither** - *Hiçbiri\<>*

  - **Boyut** - **/Os**

  - **Hız** - **/Ot**

    Daha fazla bilgi için bkz: [/Os, /Ot (Küçük kodu tercih et, hızlı kodu tercih et)](/cpp/build/reference/os-ot-favor-small-code-favor-fast-code).

- **KayanNokta Özel Durumlar**

   İsteğe bağlı Boolean parametresi.

   Eğer, `true`güvenilir kayan nokta özel durum modelini etkinleştiriyor. Özel durumlar, tetiklendikten hemen sonra yükseltilir.

   Daha fazla bilgi için /**fp:/fp** seçeneği hariç [(Kayan nokta davranışı belirtin)](/cpp/build/reference/fp-specify-floating-point-behavior)bakın.

- **KayanNokta Modeli**

   İsteğe bağlı String parametresi.

   Kayan nokta modelini ayarlar.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Kesin** - **/fp:precise**

  - **Sıkı** - **/fp:sıkı**

  - **Hızlı** - **/fp:hızlı**

    Daha fazla bilgi için bkz: [/fp (Kayan nokta davranışını belirtin)](/cpp/build/reference/fp-specify-floating-point-behavior).

- **ForceConformanceForLoopScope**

   İsteğe bağlı Boolean parametresi.

   `true`Microsoft uzantıları[(/Ze)](/cpp/build/reference/za-ze-disable-language-extensions)kullanan döngüler [için](/cpp/cpp/for-statement-cpp) standart C++ davranışını uygularsa.

   Daha fazla bilgi için [bkz: /Zc:forScope (Döngü kapsamı için zorlama uygunluğu)](/cpp/build/reference/zc-forscope-force-conformance-in-for-loop-scope).

- **Zorunlu Dosyalar**

   İsteğe bağlı `String[]` parametre.

   Önişlemcinin bir veya daha fazla belirtilen üstbilgi dosyasını işlemesine neden olur.

   Daha fazla bilgi için bkz: [/FI (Ad zorunlu dosya dahil)](/cpp/build/reference/fi-name-forced-include-file).

- **Zorunlu Dosyaları Kullanma**

   İsteğe bağlı **String[]** parametresi.

   Önişlemcinin bir veya daha fazla belirtilen **#using** dosyasını işlemesine neden olur.

   Daha fazla bilgi için bkz: [/FU (Ad zorla #using dosyası)](/cpp/build/reference/fu-name-forced-hash-using-file).

- **FonksiyonLevelLinking**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`derleyicinin tek tek işlevleri paketlenmiş işlevler (COMDATs) biçiminde paketlemesini sağlar.

   Daha fazla bilgi için bkz: [/Gy (İşlev düzeyinde bağlamayı etkinleştir)](/cpp/build/reference/gy-enable-function-level-linking).

- **XMLDocumentationFiles oluşturma**

   İsteğe bağlı `Boolean` parametre.

   Derleyicinin `true`kaynak kod dosyalarındaki belge açıklamalarını işlemesine ve belge açıklamaları içeren her kaynak kod dosyası için *bir .xdc* dosyası oluşturmasına neden oluyorsa.

   Daha fazla bilgi için bkz: [/doc (İşlem belgeleri açıklamaları) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp). Ayrıca bu tablodaki **XMLDocumentationFileName** parametresini de görün.

- **StandartIncludePath'i YokSay**

   İsteğe bağlı `Boolean` parametre.

   Derleyicinin `true`PATH ve INCLUDE ortam değişkenlerinde belirtilen dizinlere dosya eklemeyi engellerse.

   Daha fazla bilgi için bkz: [/X (Saystandardı yoksayma yolları)](/cpp/build/reference/x-ignore-standard-include-paths).

- **InlineFunctionExpansion**

   İsteğe bağlı **String** parametresi.

   Yapı için satır ara işlev genişletme düzeyini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - *yok>\<*

  - **Engelli** - **/Ob0**

  - **OnlyExplicitInline** - **/Ob1**

  - **AnyUygun** - **/Ob2**

    Daha fazla bilgi için bkz: [/Ob (Satır ara işlev genişletme)](/cpp/build/reference/ob-inline-function-expansion).

- **İntrinsİkFonksiyonlar**

   İsteğe bağlı `Boolean` parametre.

   Bazı `true`işlev çağrılarının yerine uygulamanızın daha hızlı çalışmasına yardımcı olan işlevin içsel veya başka özel biçimleri yer alır.

   Daha fazla bilgi için bkz: [/Oi (İçsel işlevler üret)](/cpp/build/reference/oi-generate-intrinsic-functions).

- **MinimalRebuild**

   İsteğe bağlı `Boolean` parametre.

   Değiştirilen `true`C++ sınıf tanımlarını (üstbilgi (.h) dosyalarında depolanan) içeren C++ kaynak dosyalarının yeniden derlenip derlenmediğini belirleyen en az yeniden oluşturmayı mümkün kılarsa.

   Daha fazla bilgi için bkz: [/Gm (En az yeniden oluşturmayı etkinleştir)](/cpp/build/reference/gm-enable-minimal-rebuild).

- **MultiProcessorCompilation**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`derlemek için birden çok işlemci kullanın. Bu parametre, bilgisayarınızdaki her etkili işlemci için bir işlem oluşturur.

   Daha fazla bilgi için bkz: [/MP (Birden çok işlemle yapıla)](/cpp/build/reference/mp-build-with-multiple-processes). Ayrıca, bu tablodaki **İşlemci Sayısı** parametresini görün.

- **ObjectFileName**

   İsteğe bağlı **String** parametresi.

   Varsayılan yerine kullanılacak bir nesne (.obj) dosya adı veya dizin belirtir.

   Daha fazla bilgi için bkz: [/Fo (Nesne dosya adı).](/cpp/build/reference/fo-object-file-name)

- **ObjectFiles**

   İsteğe bağlı **String[]** parametresi.

   Nesne dosyalarının listesi.

- **OmitDefaultLibName**

   İsteğe bağlı `Boolean` parametre.

   , `true`nesneden varsayılan C çalışma zamanı kitaplığı adını atlarsa (*.obj*) dosyasından. Varsayılan olarak, derleyici, bağlayıcıyı doğru kitaplığa yönlendirmek için kitaplığın adını *.obj* dosyasına koyar.

   Daha fazla bilgi için bkz: [/Zl (Varsayılan kitaplık adını atlatır)](/cpp/build/reference/zl-omit-default-library-name).

- **OmitFramePointers**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`çağrı yığınında çerçeve işaretçileri oluşturulmasını bastırır.

   Daha fazla bilgi için bkz: [/Oy (Çerçeve işaretçisi ihmali).](/cpp/build/reference/oy-frame-pointer-omission)

- **OpenMPDesteği**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`derleyicinin OpenMP yan tümcelerini ve yönergeleri işlemesine neden oluyorsa.

   Daha fazla bilgi için bkz/ [openmp (OpenMP 2.0 desteği etkinleştir)](/cpp/build/reference/openmp-enable-openmp-2-0-support).

- **İyileştirme**

   İsteğe bağlı **String** parametresi.

   Hız ve boyut için çeşitli kod optimizasyonları belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Engelli** - **/Od**

  - **MinSpace** - **/O1**

  - **Maksimum Hız** - **/O2**

  - **Tam** - **/ Öküz**

    Daha fazla bilgi için bkz: [/O Seçenekleri (Kodu optimize edin)](/cpp/build/reference/o-options-optimize-code).

- **PrecompiledHeader**

   İsteğe bağlı **String** parametresi.

   Yapı sırasında önceden derlenmiş bir üstbilgi (*.pch*) dosyası oluşturun veya kullanın.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **NotUsing** - Hiçbir>kullanma*\<*

  - **Oluşturma** - **/Yc**

  - **Kullan** - **/Yu**

    Daha fazla bilgi için bkz: [/Yc (Önceden derlenmiş üstbilgi dosyası oluşturma)](/cpp/build/reference/yc-create-precompiled-header-file) ve [/Yu (Önceden derlenmiş üstbilgi dosyalarını kullanın)](/cpp/build/reference/yu-use-precompiled-header-file). Ayrıca, bu tabloda **PrecompiledHeaderFile** ve **PrecompiledHeaderOutputFile** parametrelerine bakın.

- **PrecompiledHeaderFile**

   İsteğe bağlı **String** parametresi.

   Oluşturmak veya kullanmak için önceden derlenmiş bir üstbilgi dosya adı belirtir.

   Daha fazla bilgi için bkz: [/Yc (Önceden derlenmiş üstbilgi dosyası oluşturma)](/cpp/build/reference/yc-create-precompiled-header-file) ve [/Yu (Önceden derlenmiş üstbilgi dosyalarını kullanın)](/cpp/build/reference/yu-use-precompiled-header-file).

- **PrecompiledHeaderOutputFile**

   İsteğe bağlı **String** parametresi.

   Varsayılan yol adını kullanmak yerine önceden derlenmiş bir üstbilgi için bir yol adı belirtir.

   Daha fazla bilgi için bkz: [/Fp (Ad .pch dosyası)](/cpp/build/reference/fp-name-dot-pch-file).

- **Ön İşlemKeepComments**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`ön işleme sırasında yorumları korur.

   Daha fazla bilgi için bkz: [/C (Ön işleme sırasında açıklamaları koru)](/cpp/build/reference/c-preserve-comments-during-preprocessing).

- **Önİşleme İşlemci Tanımlar**

   İsteğe bağlı `String[]` parametre.

   Kaynak dosyanız için bir ön işleme simgesi tanımlar.

   Daha fazla bilgi için bkz: [/D (Önişlemci tanımları).](/cpp/build/reference/d-preprocessor-definitions)

- **ProprocessOutput**

   İsteğe bağlı `ITaskItem[]` parametre.

   Görevler tarafından tüketilebilen ve yayılan bir dizi önişlemci çıktı öğesi tanımlar.

- **ÖnprosesOutputPath**

   İsteğe bağlı `String` parametre.

   **PreprocessToFile** parametresi önceden işlenmiş çıktıyı yazdığı çıktı dosyasının adını belirtir.

   Daha fazla bilgi için bkz: [/Fi (Proprocess output ime dosya adı)](/cpp/build/reference/fi-preprocess-output-file-name).

- **ÖnİşlemeSuppressLineNumbers**

   İsteğe bağlı `Boolean` parametre.

   C `true`ve C++ kaynak dosyalarını önceden işler ve önceden işlenmiş dosyaları standart çıktı aygıtına kopyalarsa.

   Daha fazla bilgi için bkz: [/EP (Ön İşlem #line yönergeleri olmadan stdout için)](/cpp/build/reference/ep-preprocess-to-stdout-without-hash-line-directives).

- **ÖnİşlemeToFile**

   İsteğe bağlı `Boolean` parametre.

   Eğer `true`, C ve C++ kaynak dosyalarını önceden işler ve önceden işlenmiş çıktıyı bir dosyaya yazarsa.

   Daha fazla bilgi için bkz: [/P (Dosyaya ön işlem)](/cpp/build/reference/p-preprocess-to-a-file).

- **İşlemci Numarası**

   İsteğe bağlı `Integer` parametre.

   Çok işlemcili derlemede kullanılacak maksimum işlemci sayısını belirtir. Bu parametreyi **MultiProcessorCompilation** parametresi ile birlikte kullanın.

- **ProgramDataBaseFileName**

   İsteğe bağlı `String` parametre.

   Program veritabanı (PDB) dosyası için bir dosya adı belirtir.

   Daha fazla bilgi için bkz: [/Fd (Program veritabanı dosya adı)](/cpp/build/reference/fd-program-database-file-name).

- **RuntimeLibrary**

   İsteğe bağlı `String` parametre.

   Çok iş parçacığı modülünün DLL olup olmadığını gösterir ve çalışma zamanı kitaplığı perakende veya hata ayıklama sürümlerini seçer.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **MultiThreaded** - **/ MT**

  - **MultiThreadedDebug** - **/MTd**

  - **MultiThreadedDLL** - **/MD**

  - **MultiThreadedDebugDLL** - **/MDd**

    Daha fazla bilgi için bkz: [/MD, /MT, /LD (Çalışma zamanı kitaplığını kullan)](/cpp/build/reference/md-mt-ld-use-run-time-library).

- **RuntimeTypeInfo**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`çalışma zamanında C++ nesne türlerini denetlemek için kod ekler (çalışma zamanı türü bilgileri).

   Daha fazla bilgi için bkz: [/GR (Çalışma zamanı türü bilgilerini etkinleştir)](/cpp/build/reference/gr-enable-run-time-type-information).

- **Gösterİç**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`derleyicinin dahil dosyaların listesini çıktısına neden olur.

   Daha fazla bilgi için bkz/ [showIncludes (Liste dosyaları içerir)](/cpp/build/reference/showincludes-list-include-files).

- **Daha Küçük TypeCheck**

   İsteğe bağlı `Boolean` parametre.

   Bir `true`değer daha küçük bir veri türüne atanmışsa ve veri kaybına neden olursa, çalışma zamanı hatası bildirir.

   Daha fazla bilgi için **/RTC** 'deki /RTCc seçeneğine bakın [(Çalışma zamanı hata denetimleri).](/cpp/build/reference/rtc-run-time-error-checks)

- **Kaynak**

   Gerekli `ITaskItem[]` parametre.

   Boşluklara göre ayrılmış kaynak dosyaların listesini belirtir.

- **StringPooling**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`derleyiciprogram görüntüsünde aynı dizeleri bir kopyasını oluşturmak için sağlar.

   Daha fazla bilgi için bkz: [/GF (Yinelenen dizeleri ortadan kaldırın)](/cpp/build/reference/gf-eliminate-duplicate-strings).

- **StructMemberAlignment**

   İsteğe bağlı `String` parametre.

   Bir yapıdaki tüm üyeler için bayt hizalamasını belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **Varsayılan** - **/Zp1**

  - **1Bayt** - **/Zp1**

  - **2Bayt** - **/Zp2**

  - **4Bayt** - **/Zp4**

  - **8Bayt** - **/Zp8**

  - **16Bayt** - **/Zp16**

    Daha fazla bilgi için bkz: [/Zp (Struct üye hizalaması)](/cpp/build/reference/zp-struct-member-alignment).

- **BastırmaBaşlangıç Banner**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.

   Daha fazla bilgi için bkz: [/nologo (Bastırma başlangıç başlığı) (C/C++)](/cpp/build/reference/nologo-suppress-startup-banner-c-cpp).

- **TrackerLogDirectory**

   İsteğe bağlı `String` parametre.

   Bu görev için izleme günlüklerinin depolandığı ara dizini belirtir.

   Daha fazla bilgi için bu tablodaki **TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.

- **TreatSpecificWarningsAsErrors**

   İsteğe bağlı **String[]** parametresi.

   Derleyici uyarılarının belirtilen listesini hata olarak ele akurum.

   Daha fazla bilgi **/we** `n` için [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)seçeneğine bakın.

- **TreatWarningasError**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`tüm derleyici uyarıları hata olarak ele.

   Daha fazla bilgi için bkz: **/WX** seçeneği [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level).

- **TreatWChar_tAsBuiltInType**

   İsteğe bağlı `Boolean` parametre.

   If, `true` `wchar_t` türü yerel bir tür olarak ele.

   Daha fazla bilgi için [bkz: /Zc:wchar_t (wchar_t yerel türüdür)](/cpp/build/reference/zc-wchar-t-wchar-t-is-native-type).

- **TanımsızAllPreprocessorDefinitions**

   İsteğe bağlı `Boolean` parametre.

   Derleyicinin `true`tanımladığı Microsoft'a özgü simgeler tanımlamıyorsa.

   Daha fazla bilgi için [/U, /u (Tanımlanmamış semboller)](/cpp/build/reference/u-u-undefine-symbols) **seçeneğine** bakın.

- **TanımsızPreprocessorDefinitions**

   İsteğe bağlı `String[]` parametre.

   Tanımdan çıkarmak için bir veya daha fazla önişlemci sembolünün listesini belirtir.

   Daha fazla bilgi için bkz: **/U,** [/u (Tanımlanmamış semboller)](/cpp/build/reference/u-u-undefine-symbols).

- **UseFullPaths**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`tanılamada derleyiciye geçirilen kaynak kod dosyalarının tam yolunu görüntüler.

   Daha fazla bilgi için bkz: [/FC (Tanılamada kaynak kodu dosyasının tam yolu)](/cpp/build/reference/fc-full-path-of-source-code-file-in-diagnostics).

- **UseUnicodeForAssemblerListing**

   İsteğe bağlı `Boolean` parametre.

   Eğer `true`, çıkış dosyasıutf-8 biçiminde oluşturulacak neden olur.

   Daha fazla bilgi için **/FA,** [/Fa (Listeleme dosyası)](/cpp/build/reference/fa-fa-listing-file)seçeneğine bakın.

- **Uyarı Düzeyi**

   İsteğe bağlı `String` parametre.

   Derleyici tarafından oluşturulacak en yüksek uyarı düzeyini belirtir.

   Her biri bir komut satırı seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **TurnoffAllWarnings** - **/ W0**

  - **Seviye1** - **/W1**

  - **Seviye2** - **/W2**

  - **Seviye3** - **/W3**

  - **Seviye4** - **/W4**

  - **EnableAllWarnings** - **/Duvar**

    Daha fazla bilgi için_n_ **/w,** [/W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Uyarı düzeyi)](/cpp/build/reference/compiler-option-warning-level)seçeneğine bakın.

- **TümProgramOptimization**

   İsteğe bağlı `Boolean` parametre.

   Eğer, `true`tüm program optimizasyonu sağlar.

   Daha fazla bilgi için bkz: [/GL (Tüm program optimizasyonu)](/cpp/build/reference/gl-whole-program-optimization).

- **XMLDocumentationFileName**

   İsteğe bağlı `String` parametre.

   Oluşturulan XML belge dosyalarının adını belirtir. Bu parametre bir dosya veya dizin adı olabilir.

   Daha fazla bilgi `name` için [/doc (İşlem belgeleri açıklamaları) (C/C++)](/cpp/build/reference/doc-process-documentation-comments-c-cpp)bağımsız değişkenine bakın. Ayrıca bu tablodaki **GenerateXMLDocumentationFiles** parametresini de görün.

- **MinimalRebuildFromTracking**

   İsteğe bağlı `Boolean` parametre.

   `true`İzlenen artımlı yapı gerçekleştirilirse; , `false`yeniden yapıgerçekleştirilirse.

- **TLogreadFiles**

   İsteğe bağlı `ITaskItem[]` parametre.

   *Okunan dosya izleme günlüklerini*temsil eden bir dizi öğe belirtir.

   Okuma dosyası izleme günlüğü (*.tlog*) bir görev tarafından okunan giriş dosyalarının adlarını içerir ve proje oluşturma sistemi tarafından artımlı yapılar desteklemek için kullanılır. Daha fazla bilgi için bu tablodaki **TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.

- **TLogWriteFiles**

   İsteğe bağlı `ITaskItem[]` parametre.

   *Yazma dosyası izleme günlüklerini*temsil eden bir dizi öğe belirtir.

   Yazma dosyası izleme günlüğü (*.tlog*) bir görev tarafından yazılmış çıktı dosyalarının adlarını içerir ve artımlı yapılar desteklemek için proje oluşturma sistemi tarafından kullanılır. Daha fazla bilgi için bu tablodaki **TrackerLogDirectory** ve **TrackFileAccess** parametrelerine bakın.

- **TrackFileAccess**

   İsteğe bağlı `Boolean` parametre.

   Dosya `true`erişim desenlerini izlerse.

   Daha fazla bilgi için bu tablodaki **TLogReadFiles** ve **TLogWriteFiles** parametrelerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
