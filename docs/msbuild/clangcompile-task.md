---
title: ClangCompile Görev | Microsoft Docs
description: C++ derleyici aracını sarmalayan MSBuild ClangCompile görevinin amacını ve parametrelerini clang.exe.
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
ms.openlocfilehash: f4bc40eccaea9420bc61ccb95edf72322636e012fda03f5cd1592ebd88979f9a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428607"
---
# <a name="clangcompile-task"></a>ClangCompile görevi

Microsoft C++ derleyici aracını sarmalar ve clang.exe.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **ClangCompile görevinin parametreleri açıkılmaktadır.**

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe **bağlı string[]** parametresi.<br/><br/>Ekleme yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazla ise noktalı virgülle ayır.<br/><br/>`-I[path]` komutunu kullanın.|
|**AdditionalOptions**|İsteğe **bağlı dize** parametresi.|
|**BufferSecurityCheck**|İsteğe **bağlı dize** parametresi.<br/><br/>Güvenlik Denetimi, bir programın güvenliğine yapılan yaygın bir saldırı girişimi olan yığın arabelleği fazla çalıştırmalarını algılamaya yardımcı olur. <br/><br/>`fstack-protector` komutunu kullanın.|
|**BuildingInIde**|İsteğe **bağlı bool** parametresi.|
|**CLanguageStandard**|İsteğe **bağlı dize** parametresi.<br/><br/>C dil standardını belirler.<br/><br/>`std=[value]`c89 , **c99**, **c11**, **gnu99** veya **gnu11 değeriyle kullanın.** |
|**ClangVersion**|İsteğe **bağlı dize** parametresi.|
|**DerlemeA'lar**|İsteğe **bağlı dize** parametresi.<br/><br/>.c ve .cpp dosyaları için derleme dili seçeneğini belirleyin. Varsayılan , .c veya .cpp uzantısını temel alarak algılar.<br/><br/>, `-x c` `-x c++` kullanın.|
|**CppLanguageStandard**|İsteğe **bağlı dize** parametresi.<br/><br/>C++ dil standardını belirler.<br/><br/>`std=[value]` **c++98**, **c++11 , c++1y**, **gnu++98**, **gnu++11** veya **gnu++1y değeriyle kullanın.** |
|**DataLevelLinking**|İsteğe **bağlı bool** parametresi.<br/><br/>Her veri öğesini ayrı bir bölümde yayarak kullanılmayan verileri kaldırmak için bağlantılayıcı iyileştirmelerini sağlar.|
|**DebugInformationFormat**|İsteğe **bağlı dize** parametresi.<br/><br/>Derleyici tarafından oluşturulan hata ayıklama bilgileri türünü belirtir.<br/><br/>**Hiçbiri**, hata ayıklama bilgisi üretmez, bu nedenle derleme daha hızlı olabilir `g0` (kullanın).<br/>**FullDebug**, ŞUT2 hata ayıklama bilgilerini oluşturma `g2 -gdwarf-2` (kullanın).<br/>**LineNumber**, yalnızca Satır Numarası bilgilerini üretir `gline-tables-only` (kullanın).|
|**EnableNeonCodegen**|İsteğe **bağlı bool** parametresi.<br/><br/>NEON kayan nokta donanımı için kod oluşturmayı sağlar. Bu yalnızca arm mimarisi için geçerlidir.|
|**ExceptionHandling**|İsteğe **bağlı dize** parametresi.<br/><br/>Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.<br/><br/>**Devre dışı,** özel durum işlemeyi devre dışı bırak `fno-exceptions` (kullanın).<br/>**Etkinleştirildi,** özel durum işlemeyi etkinleştir `fexceptions` (kullanın).<br/>**UnwindTables,** gerekli statik verileri üretir, ancak oluşturulan kodu etkilemez `funwind-tables` (kullanın).|
|**FloatABI**|İsteğe **bağlı dize** parametresi.<br/><br/>Kayan nokta ABI'yi seçmek için seçim seçeneği.<br/><br/>**soft**, derleyicinin kayan nokta işlemleri için kitaplık çağrıları içeren çıkış oluşturmasını sağlar `mfloat-abi=soft` (kullanın).<br/>**softfp**, donanım kayan nokta yönergelerini kullanarak kod oluşturmanıza izin verir, ancak yine de soft-float çağırma kuralları kullanır `mfloat-abi=softfp` (kullanın).<br/>**hard**, kayan nokta yönergelerinin nesline izin verir ve FPU'ya özgü çağırma kuralları kullanır `mfloat-abi=hard` (kullanın).|
|**ForcedIncludeFiles**|İsteğe **bağlı string[]** parametresi.<br/><br/>Bir veya daha fazla zorlamalı dahil dosyası.<br/><br/>`-include [name]` komutunu kullanın.|
|**FunctionLevelLinking**|İsteğe **bağlı bool** parametresi.<br/><br/>Derleyicinin tek tek işlevleri paketlenmiş işlevler (COMDAT) şeklinde paketleyebiliyor. Düzenleme ve çalışmaya devam etmek için gereklidir.<br/><br/>`ffunction-sections` komutunu kullanın.|
|**GccToolChain**|İsteğe **bağlı dize** parametresi.<br/><br/>Gcc Araç Zinciri'nin klasör yolu.|
|**GNUMode**|İsteğe **bağlı bool** parametresi.<br/><br/>|
|**MSCompatibility**|İsteğe **bağlı bool** parametresi.<br/><br/>Tam Microsoft C++ uyumluluğunu etkinleştirin.|
|**MSCompatibilityVersion**|İsteğe **bağlı dize** parametresi.<br/><br/>Rapor için Microsoft derleyici sürüm numarasını temsil eden noktalı _MSC_VER (0 = tanımlamaz (varsayılan)).|
|**MSExtensions**|İsteğe **bağlı bool** parametresi.<br/><br/>Microsoft derleyicisi tarafından desteklenen standart olmayan bazı yapıları kabul eder.|
|**MSCompilerVersion**|İsteğe **bağlı dize** parametresi.<br/><br/>Microsoft derleyicisi sürüm numarası _MSC_VER (0 = bunu tanımlama (varsayılan)).|
|**MSVCErrorReport**|İsteğe **bağlı bool** parametresi.<br/><br/>Dosya ve Visual Studio ayrıştırmak için kullanabileceğiniz hataları rapor edin.|
|**ObjectFileName**|İsteğe **bağlı dize** parametresi.<br/><br/>Varsayılan nesne dosyası adını geçersiz kılmak için bir ad belirtir; dosya veya dizin adı olabilir.<br/><br/>`/Fo[name]` komutunu kullanın.|
|**OmitFramePointers**|İsteğe **bağlı bool** parametresi.<br/><br/>Çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.|
|**İyileştirme**|İsteğe **bağlı dize** parametresi.<br/><br/>Uygulama için iyileştirme düzeyini belirtir.<br/><br/>**Özel**, özel iyileştirme.<br/>**Devre** dışı, iyileştirmeyi devre dışı bırak (kullanım `O0` ).<br/>**MinSize**, boyut için iyileştirin (kullanım `Os` ).<br/>**Maxspeed**, hız için iyileştirin (kullanım `O2` ).<br/>**Tam**, pahalı iyileştirmeler (kullanım `O3` ).|
|**PositionIndependentCode**|İsteğe bağlı **bool** parametresi.<br/><br/>Paylaşılan bir kitaplıkta kullanılmak üzere konumdan bağımsız kod (PIC) üretin.|
|**PrecompiledHeader**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme sırasında önceden derlenmiş üst bilgi oluşturmayı veya kullanmayı mümkün.|
|**PrecompiledHeaderFile**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için kullanılacak üst bilgi dosyası adını belirtir. Bu dosya, derleme sırasında **zorunlu Içerme dosyalarına** da eklenecektir.|
|**PrecompiledHeaderOutputFileDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>Oluşturulan ön derlenmiş üstbilgi için dizini belirtir. Bu dizin, derleme sırasında **ek Içerme dizinlerine** da eklenecektir.|
|**PrecompiledHeaderCompileAs**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için derleme dil seçeneğini belirleyin.<br/><br/>Kullanın `-x c-header` , `-x c++-header` .|
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Kaynak dosyanız için bir ön işleme sembolleri tanımlar.<br/><br/>`-D` komutunu kullanın.|
|**RuntimeLibrary**|İsteğe bağlı **dize** parametresi.<br/><br/>Bağlama için çalışma zamanı kitaplığını belirtin.<br/><br/>,,, `MSVC /MT` `/MTd` Anahtarlarını kullanın `/MD` `/MDd` .<br/><br/>**Çoklu Iş parçacıklı**, uygulamanızın çalışma zamanı kitaplığının çoklu iş parçacıklı, statik sürümünü kullanmasına neden olur.<br/>**Multithreadeddebug**, _DEBUG ve _MT tanımlar. Bu seçenek, aynı zamanda, derleyicinin LIBCMTD.lib kitaplık adını .obj dosyasına koyarak bağlayıcının dış simgeleri çözme sırasında LIBCMTD.lib kullanmasını sağlar.<br/>**Multithreadeddll**, uygulamanızın iş PARÇACıKLı ve DLL 'ye özgü çalışma zamanı kitaplığının sürümünü kullanmasına neden olur. _MT ve _DLL tanımlar ve derleyicinin MSVCRT. lib kitaplık adını. obj dosyasına yerleştirmesini sağlar.<br/>**Multithreadeddebugdll**, _DEBUG, _MT ve _DLL tanımlar ve uygulamanızın çalışma zamanı kitaplığı 'nın çoklu iş parçacığı ve DLL 'ye özgü sürümünü kullanmasına neden olur. Ayrıca, derleyicinin MSVCRTD.lib kitaplık adını .obj dosyasına yerleştirmesini sağlar.|
|**RuntimeTypeInfo**|İsteğe bağlı **bool** parametresi.<br/><br/>Çalışma zamanında C++ nesne türlerini denetlemek için kod ekler (çalışma zamanı türü bilgileri).<br/><br/>Kullanın `frtti` , `fno-rtti` .|
|**ShowIncludes**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyici çıkışı içeren ekleme dosyalarının bir listesini oluşturur.<br/><br/>`-H` komutunu kullanın.|
|**Kaynaklar**|Gerekli **ıtaskitem []** parametresi.|
|**Strictaliizleme**|İsteğe bağlı **bool** parametresi.<br/><br/>En katı diğer ad kurallarını varsayın. Tek bir türdeki nesne, farklı türde bir nesneyle aynı adreste yer alacak şekilde hiçbir zaman kabul değildir.|
|**Sysroot**|İsteğe bağlı **dize** parametresi.<br/><br/>Üst bilgiler ve kitaplıklar için kök dizinin klasör yolu.|
|**TargetArch**|İsteğe bağlı **dize** parametresi.<br/><br/>Hedef mimari.|
|**Parmak modu**|İsteğe bağlı **dize** parametresi.<br/><br/>Thumb mikro mimarisi için yürütülen kodu oluşturun. Bu yalnızca ARM mimarisi için geçerlidir.<br/><br/>**Thumb**, parmak izi kodu oluştur (kullanın `mthumb` ).<br/>**ARM**, ARM kodu oluşturma (kullanım `marm` ).<br/>**Devre dışı**, seçenek seçilen platform için geçerli değil.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>İzleyici günlüğü dizini.|
|**TreatWarningAsError**|İsteğe bağlı **bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak değerlendirir.<br/><br/>Yeni bir proje için tüm derlemelerde kullanılması en iyi yöntem olabilir `/WX` ; Tüm uyarıların çözümlenmesi, en az olası bir hata bulma kod kusurlarını güvence altına alacak.|
|**UndefinePreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Bir veya daha fazla önişlemci tarafından tanımlanabileceğini belirtir.<br/><br/>`-U [macro]` komutunu kullanın.|
|**UndefineAllPreprocessorDefinitions**|İsteğe bağlı **bool** parametresi.<br/><br/>Önceden tanımlanmış tüm Önişlemci değerlerini tanımlayın.<br/><br/>`-undef` komutunu kullanın.|
|**UseMultiToolTask**|İsteğe bağlı **bool** parametresi.<br/><br/>Çok işlemcili derleme.|
|**Usekısaltenums**|İsteğe bağlı **bool** parametresi.<br/><br/>Sabit listesi türü, yalnızca olası değerlerin giriş kümesi için gereken sayıda bayt kullanır.|
|**Seçeneini**|İsteğe bağlı **bool** parametresi.<br/><br/>Çalıştırılacak komutları göster ve ayrıntılı çıkış kullan.|
|**Uyarı düzeyi**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyicinin kod hataları hakkında ne kadar sıkı olmasını istediğinizi seçin. Diğer bayraklar doğrudan **ek seçeneklere** eklenmelidir (o `/w` , `/Weverything` ).<br/><br/>Birlikte **kapatma**, tüm derleyici uyarılarını devre dışı bırakır (kullanın `w` ).<br/>**Enablealluyarıları**, varsayılan olarak devre dışı bırakılan (kullanım) dahil olmak üzere tüm uyarıları izin veriyor `Wall` .|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
