---
title: ClangCompile görevi | Microsoft Docs
description: clang.exe C++ derleyici aracını sarmalayan MSBuild ClangCompile görevinin amacını ve parametrelerini açıklar.
ms.custom: SEO-VS-2020
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
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 63b278f322e66e6622064288d322709c51df336d
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796829"
---
# <a name="clangcompile-task"></a>ClangCompile görevi

Microsoft C++ derleyici aracı 'nı sarmalayan clang.exe.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **Clangcompile** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br/><br/>Ekleme yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazlaysa noktalı virgülle ayırın.<br/><br/>`-I[path]` komutunu kullanın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.|
|**BufferSecurityCheck**|İsteğe bağlı **dize** parametresi.<br/><br/>Güvenlik denetimi, bir programın güvenliği üzerinde yaygın olarak gerçekleştirilen bir saldırıya karşı yığın arabelleğinin çalıştırılmaların algılanmasına yardımcı olur. <br/><br/>`fstack-protector` komutunu kullanın.|
|**Buildingınıde**|İsteğe bağlı **bool** parametresi.|
|**CLanguageStandard**|İsteğe bağlı **dize** parametresi.<br/><br/>C dil standardını belirler.<br/><br/>`std=[value]` **C89** , **C99** , **C11** , **gnu99** veya **gnu11** değeri ile kullanın.|
|**ClangVersion**|İsteğe bağlı **dize** parametresi.|
|**CompileAs**|İsteğe bağlı **dize** parametresi.<br/><br/>. C ve. cpp dosyaları için derleme dil seçeneğini belirleyin. Varsayılan,. c veya. cpp uzantısı temelinde algılanacak.<br/><br/>Kullanın `-x c` , `-x c++` .|
|**CppLanguageStandard**|İsteğe bağlı **dize** parametresi.<br/><br/>C++ dil standardını belirler.<br/><br/>`std=[value]` **C++ 98** , **c++ 11** , **c + + 1Y** , **GNU + + 98** , **GNU + + 11** veya **GNU + + 1Y** değeri ile kullanın.|
|**Veri düzeyi bağlama**|İsteğe bağlı **bool** parametresi.<br/><br/>Her veri öğesini ayrı bir bölümde yayarak kullanılmayan verileri kaldırmak için bağlayıcı iyileştirmelerini sağlar.|
|**DebugInformationFormat**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir.<br/><br/>**Hiçbiri** hata ayıklama bilgisi üretmez, bu nedenle derleme daha hızlı (kullanım `g0` ) olabilir.<br/>**Fulldebug** , DWARF2 hata ayıklama bilgileri oluştur (kullanın `g2 -gdwarf-2` ).<br/>**LineNumber** , yalnızca satır numarası bilgisi oluşturun (kullanın `gline-tables-only` ).|
|**EnableNeonCodegen**|İsteğe bağlı **bool** parametresi.<br/><br/>NEON kayan nokta donanımı için kod oluşturmayı mümkün bir şekilde sunar. Bu yalnızca ARM mimarisi için geçerlidir.|
|**ExceptionHandling**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.<br/><br/>**Devre dışı** , özel durum işlemeyi devre dışı bırak (kullanım `fno-exceptions` ).<br/>**Etkin** , özel durum işlemeyi etkinleştir (kullanım `fexceptions` ).<br/>**Iwını tabloları** , gereken statik verileri oluşturur, ancak oluşturulan kodu etkilemez (kullanın `funwind-tables` ).|
|**FloatABI**|İsteğe bağlı **dize** parametresi.<br/><br/>Kayan nokta ABı seçmek için seçim seçeneği.<br/><br/>**Soft** , derleyicinin kayan nokta işlemleri için kitaplık çağrıları içeren çıkış oluşturmasına neden olur (kullanım `mfloat-abi=soft` ).<br/>**softfp** , donanım kayan nokta yönergeleri kullanılarak kod oluşturulmasına izin verir, ancak yine de yumuşak float çağırma kurallarını kullanır (kullanım `mfloat-abi=softfp` ).<br/>**Hard** , kayan nokta yönergelerinin oluşturulmasına izin verir ve FPU 'ya özgü çağrı kurallarını (kullanım) kullanır `mfloat-abi=hard` .|
|**ForcedIncludeFiles**|İsteğe bağlı **dize []** parametresi.<br/><br/>Bir veya daha fazla zorunlu ekleme dosyası.<br/><br/>`-include [name]` komutunu kullanın.|
|**Functionlevellink**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyicinin paketlenmiş işlevler (Compts) biçiminde tek tek işlevleri paketetmesine olanak tanır. Düzenle ve çalışmaya devam etmek için gereklidir.<br/><br/>`ffunction-sections` komutunu kullanın.|
|**Gcctoolzinciri**|İsteğe bağlı **dize** parametresi.<br/><br/>GCC araç zincirinin klasör yolu.|
|**GNUMode**|İsteğe bağlı **bool** parametresi.<br/><br/>|
|**MSCompatibility**|İsteğe bağlı **bool** parametresi.<br/><br/>Tam Microsoft C++ uyumluluğunu etkinleştirin.|
|**MSCompatibilityVersion**|İsteğe bağlı **dize** parametresi.<br/><br/>_MSC_VER raporlamak için Microsoft derleyicisi sürüm numarasını temsil eden noktayla ayrılmış değer (0 = tanımlama (varsayılan)).|
|**MSExtensions**|İsteğe bağlı **bool** parametresi.<br/><br/>Microsoft derleyicisi tarafından desteklenen bazı standart olmayan yapıları kabul edin.|
|**MSCompilerVersion**|İsteğe bağlı **dize** parametresi.<br/><br/>_MSC_VER raporlamak için Microsoft derleyicisi sürüm numarası (0 = tanımlama (varsayılan)).|
|**MSVCErrorReport**|İsteğe bağlı **bool** parametresi.<br/><br/>Visual Studio 'Nun dosya ve satır bilgileri için ayrıştırmak üzere kullanabileceği hataları raporlayın.|
|**ObjectFileName**|İsteğe bağlı **dize** parametresi.<br/><br/>Varsayılan nesne dosyası adını geçersiz kılacak bir ad belirtir; dosya veya dizin adı olabilir.<br/><br/>`/Fo[name]` komutunu kullanın.|
|**Omitframeişaretçiler**|İsteğe bağlı **bool** parametresi.<br/><br/>Çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.|
|**İyileştirme**|İsteğe bağlı **dize** parametresi.<br/><br/>Uygulamanın en iyi duruma getirme düzeyini belirtir.<br/><br/>**Özel** , özel iyileştirme.<br/>**Devre** dışı, iyileştirmeyi devre dışı bırak (kullanım `O0` ).<br/>**MinSize** , boyut için iyileştirin (kullanım `Os` ).<br/>**Maxspeed** , hız için iyileştirin (kullanım `O2` ).<br/>**Tam** , pahalı iyileştirmeler (kullanım `O3` ).|
|**PositionIndependentCode**|İsteğe bağlı **bool** parametresi.<br/><br/>Paylaşılan bir kitaplıkta kullanılmak üzere konumdan bağımsız kod (PIC) üretin.|
|**PrecompiledHeader**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme sırasında önceden derlenmiş üst bilgi oluşturmayı veya kullanmayı mümkün.|
|**PrecompiledHeaderFile**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için kullanılacak üst bilgi dosyası adını belirtir. Bu dosya, derleme sırasında **zorunlu Içerme dosyalarına** da eklenecektir.|
|**PrecompiledHeaderOutputFileDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>Oluşturulan ön derlenmiş üstbilgi için dizini belirtir. Bu dizin, derleme sırasında **ek Içerme dizinlerine** da eklenecektir.|
|**PrecompiledHeaderCompileAs**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için derleme dil seçeneğini belirleyin.<br/><br/>Kullanın `-x c-header` , `-x c++-header` .|
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Kaynak dosyanız için bir ön işleme sembolleri tanımlar.<br/><br/>`-D` komutunu kullanın.|
|**RuntimeLibrary**|İsteğe bağlı **dize** parametresi.<br/><br/>Bağlama için çalışma zamanı kitaplığını belirtin.<br/><br/>,,, `MSVC /MT` `/MTd` Anahtarlarını kullanın `/MD` `/MDd` .<br/><br/>**Çoklu Iş parçacıklı** , uygulamanızın çalışma zamanı kitaplığının çoklu iş parçacıklı, statik sürümünü kullanmasına neden olur.<br/>**Multithreadeddebug** , _DEBUG ve _MT tanımlar. Bu seçenek, aynı zamanda, derleyicinin LIBCMTD.lib kitaplık adını .obj dosyasına koyarak bağlayıcının dış simgeleri çözme sırasında LIBCMTD.lib kullanmasını sağlar.<br/>**Multithreadeddll** , uygulamanızın iş PARÇACıKLı ve DLL 'ye özgü çalışma zamanı kitaplığının sürümünü kullanmasına neden olur. _MT ve _DLL tanımlar ve derleyicinin MSVCRT. lib kitaplık adını. obj dosyasına yerleştirmesini sağlar.<br/>**Multithreadeddebugdll** , _DEBUG, _MT ve _DLL tanımlar ve uygulamanızın çalışma zamanı kitaplığı 'nın çoklu iş parçacığı ve DLL 'ye özgü sürümünü kullanmasına neden olur. Ayrıca, derleyicinin MSVCRTD.lib kitaplık adını .obj dosyasına yerleştirmesini sağlar.|
|**RuntimeTypeInfo**|İsteğe bağlı **bool** parametresi.<br/><br/>Çalışma zamanında C++ nesne türlerini denetlemek için kod ekler (çalışma zamanı türü bilgileri).<br/><br/>Kullanın `frtti` , `fno-rtti` .|
|**ShowIncludes**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyici çıkışı içeren ekleme dosyalarının bir listesini oluşturur.<br/><br/>`-H` komutunu kullanın.|
|**Ğına**|Gerekli **ıtaskitem []** parametresi.|
|**Strictaliizleme**|İsteğe bağlı **bool** parametresi.<br/><br/>En katı diğer ad kurallarını varsayın. Tek bir türdeki nesne, farklı türde bir nesneyle aynı adreste yer alacak şekilde hiçbir zaman kabul değildir.|
|**Sysroot**|İsteğe bağlı **dize** parametresi.<br/><br/>Üst bilgiler ve kitaplıklar için kök dizinin klasör yolu.|
|**TargetArch**|İsteğe bağlı **dize** parametresi.<br/><br/>Hedef mimari.|
|**Parmak modu**|İsteğe bağlı **dize** parametresi.<br/><br/>Thumb mikro mimarisi için yürütülen kodu oluşturun. Bu yalnızca ARM mimarisi için geçerlidir.<br/><br/>**Thumb** , parmak izi kodu oluştur (kullanın `mthumb` ).<br/>**ARM** , ARM kodu oluşturma (kullanım `marm` ).<br/>**Devre dışı** , seçenek seçilen platform için geçerli değil.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>İzleyici günlüğü dizini.|
|**TreatWarningAsError**|İsteğe bağlı **bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak değerlendirir.<br/><br/>Yeni bir proje için tüm derlemelerde kullanılması en iyi yöntem olabilir `/WX` ; Tüm uyarıların çözümlenmesi, en az olası bir hata bulma kod kusurlarını güvence altına alacak.|
|**UndefinePreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Bir veya daha fazla önişlemci tarafından tanımlanabileceğini belirtir.<br/><br/>`-U [macro]` komutunu kullanın.|
|**UndefineAllPreprocessorDefinitions**|İsteğe bağlı **bool** parametresi.<br/><br/>Önceden tanımlanmış tüm Önişlemci değerlerini tanımlayın.<br/><br/>`-undef` komutunu kullanın.|
|**UseMultiToolTask**|İsteğe bağlı **bool** parametresi.<br/><br/>Çok işlemcili derleme.|
|**Usekısaltenums**|İsteğe bağlı **bool** parametresi.<br/><br/>Sabit listesi türü, yalnızca olası değerlerin giriş kümesi için gereken sayıda bayt kullanır.|
|**Seçeneini**|İsteğe bağlı **bool** parametresi.<br/><br/>Çalıştırılacak komutları göster ve ayrıntılı çıkış kullan.|
|**Uyarı düzeyi**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyicinin kod hataları hakkında ne kadar sıkı olmasını istediğinizi seçin. Diğer bayraklar doğrudan **ek seçeneklere** eklenmelidir (o `/w` , `/Weverything` ).<br/><br/>Birlikte **kapatma** , tüm derleyici uyarılarını devre dışı bırakır (kullanın `w` ).<br/>**Enablealluyarıları** , varsayılan olarak devre dışı bırakılan (kullanım) dahil olmak üzere tüm uyarıları izin veriyor `Wall` .|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
