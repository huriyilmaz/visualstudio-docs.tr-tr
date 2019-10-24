---
title: ClangCompile görevi | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.clangcompile
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ClangCompile task
- ClangCompile task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 1bd1d749461c423d51e0f5b736563a9f9aa757c5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747337"
---
# <a name="clangcompile-task"></a>ClangCompile görevi

, Clang C++ . exe adlı Microsoft derleyici aracını sarmalanmış.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **Clangcompile** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br/><br/>Ekleme yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazlaysa noktalı virgülle ayırın.<br/><br/>@No__t_0 kullanın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.|
|**BufferSecurityCheck**|İsteğe bağlı **dize** parametresi.<br/><br/>Güvenlik denetimi, bir programın güvenliği üzerinde yaygın olarak gerçekleştirilen bir saldırıya karşı yığın arabelleğinin çalıştırılmaların algılanmasına yardımcı olur. <br/><br/>@No__t_0 kullanın.|
|**Buildingınıde**|İsteğe bağlı **bool** parametresi.|
|**CLanguageStandard**|İsteğe bağlı **dize** parametresi.<br/><br/>C dil standardını belirler.<br/><br/>**C89**, **C99**, **C11**, **gnu99**veya **gnu11**değeri ile `std=[value]` kullanın.|
|**ClangVersion**|İsteğe bağlı **dize** parametresi.|
|**CompileAs**|İsteğe bağlı **dize** parametresi.<br/><br/>. C ve. cpp dosyaları için derleme dil seçeneğini belirleyin. Varsayılan,. c veya. cpp uzantısı temelinde algılanacak.<br/><br/>@No__t_0 `-x c++` kullanın.|
|**CppLanguageStandard**|İsteğe bağlı **dize** parametresi.<br/><br/>C++ Dil standardını belirler.<br/><br/>**C++ 98**, **c++ 11**, **c + + 1Y**, **GNU + + 98**, **GNU + + 11**veya **GNU + + 1Y**değeri ile `std=[value]` kullanın.|
|**Veri düzeyi bağlama**|İsteğe bağlı **bool** parametresi.<br/><br/>Her veri öğesini ayrı bir bölümde yayarak kullanılmayan verileri kaldırmak için bağlayıcı iyileştirmelerini sağlar.|
|**DebugInformationFormat**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir.<br/><br/>**Hiçbiri**hata ayıklama bilgisi üretmez, derleme daha hızlı olabilir (`g0` kullanın).<br/>**Fulldebug**, DWARF2 hata ayıklama bilgileri oluştur (`g2 -gdwarf-2` kullanın).<br/>**LineNumber**, yalnızca satır numarası bilgisi oluştur (`gline-tables-only` kullanın).|
|**EnableNeonCodegen**|İsteğe bağlı **bool** parametresi.<br/><br/>NEON kayan nokta donanımı için kod oluşturmayı mümkün bir şekilde sunar. Bu yalnızca ARM mimarisi için geçerlidir.|
|**ExceptionHandling**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.<br/><br/>**Devre dışı**, özel durum işlemeyi devre dışı bırak (`fno-exceptions` kullanın).<br/>**Etkin**, özel durum işlemeyi etkinleştir (`fexceptions` kullanın).<br/>**Unııd tabloları**, gereken statik verileri oluşturur, ancak oluşturulan kodu etkilemez (`funwind-tables` kullanın).|
|**FloatABI**|İsteğe bağlı **dize** parametresi.<br/><br/>Kayan nokta ABı seçmek için seçim seçeneği.<br/><br/>**Soft**, derleyicinin kayan nokta işlemleri için kitaplık çağrıları içeren çıkış oluşturmasına neden olur (`mfloat-abi=soft` kullanın).<br/>**softfp**, donanım kayan nokta yönergeleri kullanılarak kod oluşturulmasına izin verir, ancak yine de yumuşak float çağırma kurallarını kullanır (`mfloat-abi=softfp` kullanın).<br/>**Hard**, kayan nokta yönergelerinin oluşturulmasına izin verir ve FPU 'ya özgü çağrı kurallarını kullanır (`mfloat-abi=hard` kullanın).|
|**ForcedIncludeFiles**|İsteğe bağlı **dize []** parametresi.<br/><br/>Bir veya daha fazla zorunlu ekleme dosyası.<br/><br/>@No__t_0 kullanın.|
|**Functionlevellink**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyicinin paketlenmiş işlevler (Compts) biçiminde tek tek işlevleri paketetmesine olanak tanır. Düzenle ve çalışmaya devam etmek için gereklidir.<br/><br/>@No__t_0 kullanın.|
|**Gcctoolzinciri**|İsteğe bağlı **dize** parametresi.<br/><br/>GCC araç zincirinin klasör yolu.|
|**GNUMode**|İsteğe bağlı **bool** parametresi.<br/><br/>|
|**MSCompatibility**|İsteğe bağlı **bool** parametresi.<br/><br/>Tam Microsoft C++ uyumluluğunu etkinleştirin.|
|**MSCompatibilityVersion**|İsteğe bağlı **dize** parametresi.<br/><br/>_MSC_VER içinde raporlanacak Microsoft derleyicisi sürüm numarasını gösteren noktayla ayrılmış değer (0 = tanımlama (varsayılan)).|
|**MSExtensions**|İsteğe bağlı **bool** parametresi.<br/><br/>Microsoft derleyicisi tarafından desteklenen bazı standart olmayan yapıları kabul edin.|
|**MSCompilerVersion**|İsteğe bağlı **dize** parametresi.<br/><br/>_MSC_VER içinde raporlanacak Microsoft derleyicisi sürüm numarası (0 = tanımlama (varsayılan)).|
|**MSVCErrorReport**|İsteğe bağlı **bool** parametresi.<br/><br/>Visual Studio 'Nun dosya ve satır bilgileri için ayrıştırmak üzere kullanabileceği hataları raporlayın.|
|**ObjectFileName**|İsteğe bağlı **dize** parametresi.<br/><br/>Varsayılan nesne dosyası adını geçersiz kılacak bir ad belirtir; dosya veya dizin adı olabilir.<br/><br/>@No__t_0 kullanın.|
|**Omitframeişaretçiler**|İsteğe bağlı **bool** parametresi.<br/><br/>Çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.|
|**İyileştirme**|İsteğe bağlı **dize** parametresi.<br/><br/>Uygulamanın en iyi duruma getirme düzeyini belirtir.<br/><br/>**Özel**, özel iyileştirme.<br/>**Devre**dışı, iyileştirmeyi devre dışı bırak (`O0` kullanın).<br/>**MinSize**, boyut için iyileştirin (`Os` kullanın).<br/>**Maxspeed**, hız için iyileştirin (`O2` kullanın).<br/>**Tam**ve pahalı iyileştirmeler (`O3` kullanın).|
|**PositionIndependentCode**|İsteğe bağlı **bool** parametresi.<br/><br/>Paylaşılan bir kitaplıkta kullanılmak üzere konumdan bağımsız kod (PIC) üretin.|
|**PrecompiledHeader**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme sırasında önceden derlenmiş üst bilgi oluşturmayı veya kullanmayı mümkün.|
|**PrecompiledHeaderFile**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için kullanılacak üst bilgi dosyası adını belirtir. Bu dosya, derleme sırasında **zorunlu Içerme dosyalarına** da eklenecektir.|
|**PrecompiledHeaderOutputFileDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>Oluşturulan ön derlenmiş üstbilgi için dizini belirtir. Bu dizin, derleme sırasında **ek Içerme dizinlerine** da eklenecektir.|
|**PrecompiledHeaderCompileAs**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için derleme dil seçeneğini belirleyin.<br/><br/>@No__t_0 `-x c++-header` kullanın.|
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Kaynak dosyanız için bir ön işleme sembolleri tanımlar.<br/><br/>@No__t_0 kullanın.|
|**RuntimeLibrary**|İsteğe bağlı **dize** parametresi.<br/><br/>Bağlama için çalışma zamanı kitaplığını belirtin.<br/><br/>@No__t_0, `/MTd`, `/MD`, `/MDd` anahtarlarını kullanın.<br/><br/>**Çoklu Iş parçacıklı**, uygulamanızın çalışma zamanı kitaplığının çoklu iş parçacıklı, statik sürümünü kullanmasına neden olur.<br/>**Multithreadeddebug**, _DEBUG ve _MT tanımlar. Bu seçenek, aynı zamanda, derleyicinin LIBCMTD.lib kitaplık adını .obj dosyasına koyarak bağlayıcının dış simgeleri çözme sırasında LIBCMTD.lib kullanmasını sağlar.<br/>**Multithreadeddll**, uygulamanızın iş PARÇACıKLı ve DLL 'ye özgü çalışma zamanı kitaplığının sürümünü kullanmasına neden olur. _MT ve _DLL tanımlar ve derleyicinin MSVCRT. lib kitaplık adını. obj dosyasına yerleştirmesini sağlar.<br/>**Multithreadeddebugdll**, _DEBUG, _MT ve _DLL öğelerini tanımlar ve uygulamanızın çalışma zamanı kitaplığı 'nın çoklu iş parçacığı ve DLL 'ye özgü sürümünü kullanmasına neden olur. Ayrıca, derleyicinin MSVCRTD.lib kitaplık adını .obj dosyasına yerleştirmesini sağlar.|
|**RuntimeTypeInfo**|İsteğe bağlı **bool** parametresi.<br/><br/>Çalışma zamanında nesne türlerini C++ denetlemek için kod ekler (çalışma zamanı türü bilgileri).<br/><br/>@No__t_0 `fno-rtti` kullanın.|
|**ShowIncludes**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyici çıkışı içeren ekleme dosyalarının bir listesini oluşturur.<br/><br/>@No__t_0 kullanın.|
|**Ğına**|Gerekli **ıtaskitem []** parametresi.|
|**Strictaliizleme**|İsteğe bağlı **bool** parametresi.<br/><br/>En katı diğer ad kurallarını varsayın. Tek bir türdeki nesne, farklı türde bir nesneyle aynı adreste yer alacak şekilde hiçbir zaman kabul değildir.|
|**Sysroot**|İsteğe bağlı **dize** parametresi.<br/><br/>Üst bilgiler ve kitaplıklar için kök dizinin klasör yolu.|
|**TargetArch**|İsteğe bağlı **dize** parametresi.<br/><br/>Hedef mimari.|
|**Parmak modu**|İsteğe bağlı **dize** parametresi.<br/><br/>Thumb mikro mimarisi için yürütülen kodu oluşturun. Bu yalnızca ARM mimarisi için geçerlidir.<br/><br/>**Thumb**, parmak izi kodu oluştur (`mthumb` kullanın).<br/>**ARM**, ARM kodu oluştur (`marm` kullanın).<br/>**Devre dışı**, seçenek seçilen platform için geçerli değil.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>İzleyici günlüğü dizini.|
|**TreatWarningAsError**|İsteğe bağlı **bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak değerlendirir.<br/><br/>Yeni bir proje için tüm derlemelerde `/WX` kullanılması en iyi yöntem olabilir; Tüm uyarıların çözümlenmesi, en az olası bulma kod kusurlarını güvence altına alacak.|
|**UndefinePreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Bir veya daha fazla önişlemci tarafından tanımlanabileceğini belirtir.<br/><br/>@No__t_0 kullanın.|
|**UndefineAllPreprocessorDefinitions**|İsteğe bağlı **bool** parametresi.<br/><br/>Önceden tanımlanmış tüm Önişlemci değerlerini tanımlayın.<br/><br/>@No__t_0 kullanın.|
|**UseMultiToolTask**|İsteğe bağlı **bool** parametresi.<br/><br/>Çok işlemcili derleme.|
|**Usekısaltenums**|İsteğe bağlı **bool** parametresi.<br/><br/>Sabit listesi türü, yalnızca olası değerlerin giriş kümesi için gereken sayıda bayt kullanır.|
|**Seçeneini**|İsteğe bağlı **bool** parametresi.<br/><br/>Çalıştırılacak komutları göster ve ayrıntılı çıkış kullan.|
|**Uyarı düzeyi**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyicinin kod hataları hakkında ne kadar sıkı olmasını istediğinizi seçin. Diğer bayraklar doğrudan **ek seçeneklere** eklenmelidir (o `/w`, `/Weverything`).<br/><br/>Tüm **derleyici uyarılarını devre**dışı bırakır (`w` kullanın).<br/>**Enablealluyarıları**, varsayılan olarak devre dışı bırakılan tüm uyarıları (`Wall` kullanın) mümkün şekilde sunar.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)