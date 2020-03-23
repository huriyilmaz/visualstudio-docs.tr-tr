---
title: ClangCompile Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: c1526fbd3c2c0822781f0e011999ddcb9c679170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275470"
---
# <a name="clangcompile-task"></a>ClangCompile görevi

Microsoft C++ derleyici aracı clang.exe'yi sarar.

## <a name="parameters"></a>Parametreler

Aşağıdaki **tabloda ClangCompile** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**EkIncludeDirectories**|İsteğe bağlı **dize[]** parametresi.<br/><br/>İçle yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazla ise yarı-kolon ile ayrı.<br/><br/>`-I[path]` adresini kullanın.|
|**Ek Seçenekler**|İsteğe bağlı **dize** parametresi.|
|**BufferSecurityCheck**|İsteğe bağlı **dize** parametresi.<br/><br/>Güvenlik Denetimi, bir programın güvenliğine yönelik yaygın bir saldırı girişimi olan yığın arabelleği aşırı çalıştırmalarını algılamaya yardımcı olur. <br/><br/>`fstack-protector` adresini kullanın.|
|**BinaInIde**|İsteğe bağlı **bool** parametresi.|
|**CLanguageStandard**|İsteğe bağlı **dize** parametresi.<br/><br/>C dil standardını belirler.<br/><br/>`std=[value]` **C89**değeri ile kullanın , **c99**, **c11**, **gnu99**, veya **gnu11**.|
|**ClangVersion**|İsteğe bağlı **dize** parametresi.|
|**DerleeAs**|İsteğe bağlı **dize** parametresi.<br/><br/>.c ve .cpp dosyaları için dil ekle seçeneğini seçin. Varsayılan değer .c veya .cpp extention'a göre algılar.<br/><br/>Kullanın `-x c` `-x c++`, .|
|**CppLanguageStandard**|İsteğe bağlı **dize** parametresi.<br/><br/>C++ dil standardını belirler.<br/><br/>`std=[value]` **c++98**, **c++11**, **c++1y**, **gnu++98**, **gnu++11**, veya **gnu++1y**değeri ile kullanın.|
|**DataLevelLinking**|İsteğe bağlı **bool** parametresi.<br/><br/>Bağlayıcı optimizasyonların, her veri öğesini ayrı bir bölüme yayarak kullanılmayan verileri kaldırmasını sağlar.|
|**Hata AyıklamaInformationFormat**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir.<br/><br/>**Yok,** hiçbir hata ayıklama bilgi üretir, bu nedenle `g0`derleme daha hızlı olabilir (kullanın).<br/>**FullDebug**, CÜCE2 hata ayıklama bilgileri oluşturmak (kullanın). `g2 -gdwarf-2`<br/>**LineNumber**, yalnızca Satır Numarası `gline-tables-only`bilgilerini oluşturun (kullanın).|
|**EnableNeonCodegen**|İsteğe bağlı **bool** parametresi.<br/><br/>NEON kayan nokta donanımı için kod oluşturmayı sağlar. Bu sadece kol mimarisi için geçerlidir.|
|**Özel Durum Kullanımı**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyici tarafından kullanılacak özel durum işleme modelini belirtir.<br/><br/>**Devre dışı bırakılmış,** özel `fno-exceptions`durum işlemeyi devre dışı bırakma (kullanın).<br/>**Etkin**, özel durum `fexceptions`işleme (kullanım) etkinleştirin.<br/>**UnwindTables,** gerekli statik veri üretir, ancak oluşturulan kodu `funwind-tables`etkilemez (kullanın).|
|**FloatABI**|İsteğe bağlı **dize** parametresi.<br/><br/>Kayan noktası ABI seçmek için seçim seçeneği.<br/><br/>**yumuşak**, derleyicinin kayan nokta işlemleri için kitaplık `mfloat-abi=soft`çağrıları içeren çıktı oluşturmasına neden olur (kullanın).<br/>**softfp**, donanım kayan nokta yönergeleri kullanarak kod üretimi sağlar, ama yine de `mfloat-abi=softfp`soft-float arama kuralları (kullanın) kullanır.<br/>**sabit,** kayan nokta yönergelerinin üretimine izin verir ve FPU'ya özgü çağrı kuralları (kullanım) `mfloat-abi=hard`kullanır.|
|**Zorunlu Dosyalar**|İsteğe bağlı **dize[]** parametresi.<br/><br/>Bir veya daha fazla zorla dosyaları içerir.<br/><br/>`-include [name]` adresini kullanın.|
|**FonksiyonLevelLinking**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyicinin tek tek işlevleri paketlenmiş işlevler (COMDATs) biçiminde paketlemesine olanak tanır. Edinilmesi ve çalışmaya devam edilmesi için gereklidir.<br/><br/>`ffunction-sections` adresini kullanın.|
|**GccToolChain**|İsteğe bağlı **dize** parametresi.<br/><br/>Gcc Takım Zinciri klasör yolu.|
|**GNUMode**|İsteğe bağlı **bool** parametresi.<br/><br/>|
|**MSUyumluluk**|İsteğe bağlı **bool** parametresi.<br/><br/>Tam Microsoft C++ uyumluluğunu etkinleştirin.|
|**MSCompatibilityVersion**|İsteğe bağlı **dize** parametresi.<br/><br/>_MSC_VER içinde rapor lanması için Microsoft derleyici sürüm numarasını temsil eden nokta ayrılmış değer (0 = tanımlamaz (varsayılan)).|
|**MSExtensions**|İsteğe bağlı **bool** parametresi.<br/><br/>Microsoft derleyicisi tarafından desteklenen bazı standart dışı yapıları kabul edin.|
|**MSCompilerVersion**|İsteğe bağlı **dize** parametresi.<br/><br/>Microsoft derleyici sürüm numarası _MSC_VER (0 = (varsayılan) olarak tanımlamıyorum rapor etmek.|
|**MSVCErrorReport**|İsteğe bağlı **bool** parametresi.<br/><br/>Visual Studio'nun dosya ve satır bilgilerini ayrışdırmak için kullanabileceği hataları bildirin.|
|**ObjectFileName**|İsteğe bağlı **dize** parametresi.<br/><br/>Varsayılan nesne dosya adını geçersiz kılmak için bir ad belirtir; dosya veya dizin adı olabilir.<br/><br/>`/Fo[name]` adresini kullanın.|
|**OmitFramePointers**|İsteğe bağlı **bool** parametresi.<br/><br/>Çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.|
|**İyileştirme**|İsteğe bağlı **dize** parametresi.<br/><br/>Uygulama için en iyi duruma getirilmesi düzeyini belirtir.<br/><br/>**Özel,** özel optimizasyon.<br/>**Devre dışı bırakılmış,** optimizasyonu `O0`devre dışı bırakma (kullanın).<br/>**MinSize**, boyut (kullanım) `Os`için optimize .<br/>**MaxSpeed**, hız için `O2`optimize (kullanın).<br/>**Tam**, pahalı optimizasyonlar `O3`(kullanın).|
|**PositionIndependentCode**|İsteğe bağlı **bool** parametresi.<br/><br/>Paylaşılan bir kitaplıkta kullanılmak üzere Konum Bağımsız Kodu (PIC) oluşturun.|
|**PrecompiledHeader**|İsteğe bağlı **dize** parametresi.<br/><br/>Yapı sırasında önceden derlenmiş bir üstbilginin oluşturulmasını veya kullanılmasını sağlar.|
|**PrecompiledHeaderFile**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için kullanılacak üstbilgi dosya adını belirtir. Bu dosya, yapı sırasında **Zorunlu Ekleme Dosyaları'na** da eklenir.|
|**PrecompiledHeaderOutputFileDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>Oluşturulan önceden derlenen üstbilginin dizinini belirtir. Bu dizin, yapı sırasında **Ek Dahil Dizinleri'ne** de eklenir.|
|**PrecompiledHeaderCompileAs**|İsteğe bağlı **dize** parametresi.<br/><br/>Önceden derlenmiş üstbilgi dosyası için dili derle seçeneğini seçin.<br/><br/>Kullanın `-x c-header` `-x c++-header`, .|
|**Önİşleme İşlemci Tanımlar**|İsteğe bağlı **dize[]** parametresi.<br/><br/>Kaynak dosyanız için önceden işleme sembolleri tanımlar.<br/><br/>`-D` adresini kullanın.|
|**RuntimeLibrary**|İsteğe bağlı **dize** parametresi.<br/><br/>Bağlama için çalışma zamanı kitaplığını belirtin.<br/><br/>Anahtarlar kullanın. `MSVC /MT` `/MTd` `/MD` `/MDd`<br/><br/>**MultiThreaded**, uygulamanızın çalışma zamanı kitaplığın çok iş parçacığı, statik sürümünü kullanmasına neden olur.<br/>**MultiThreadedDebug,**_DEBUG ve _MT tanımlar. Bu seçenek, aynı zamanda, derleyicinin LIBCMTD.lib kitaplık adını .obj dosyasına koyarak bağlayıcının dış simgeleri çözme sırasında LIBCMTD.lib kullanmasını sağlar.<br/>**MultiThreadedDLL,** uygulamanızın çalışma zamanı kitaplığın çok iş parçacığı ve DLL'ye özgü sürümünü kullanmasına neden olur. _MT ve _DLL tanımlar ve derleyicinin .obj dosyasına MSVCRT.lib kitaplık adını yerleştirmesine neden olur.<br/>**MultiThreadedDebugDLL,**_DEBUG, _MT ve _DLL tanımlar ve uygulamanızın çalışma zamanı kitaplığı hata ayıklama multithread ve DLL'ye özgü sürümünü kullanmasına neden olur. Ayrıca, derleyicinin MSVCRTD.lib kitaplık adını .obj dosyasına yerleştirmesini sağlar.|
|**RuntimeTypeInfo**|İsteğe bağlı **bool** parametresi.<br/><br/>Çalışma zamanında C++ nesne türlerini denetlemek için kod ekler (çalışma zamanı türü bilgileri).<br/><br/>Kullanın `frtti` `fno-rtti`, .|
|**Gösterİç**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyici çıktısı içeren dosyaların listesini oluşturur.<br/><br/>`-H` adresini kullanın.|
|**Kaynak**|Gerekli **ITaskItem[]** parametresi.|
|**Sıkı Aliasing**|İsteğe bağlı **bool** parametresi.<br/><br/>En katı takma adı alma kurallarını varsayalım. Bir türdeki bir nesnenin, farklı bir türdeki bir nesneyle aynı adreste ikamet ettiği asla varsayılamaz.|
|**Sysroot**|İsteğe bağlı **dize** parametresi.<br/><br/>Üstbilgi ve kitaplıklar için kök dizinine klasör yolu.|
|**Hedef Kemer**|İsteğe bağlı **dize** parametresi.<br/><br/>Hedef Mimari.|
|**ThumbMode**|İsteğe bağlı **dize** parametresi.<br/><br/>Başparmak mikromimarisi için çalıştıran kod oluşturun. Bu sadece kol mimarisi için geçerlidir.<br/><br/>**Başparmak**, Başparmak kodu `mthumb`(kullanın) oluşturmak.<br/>**ARM**, Kol kodu `marm`(kullanın) oluşturmak.<br/>**Devre dışı bırakılmış,** seçilen platform için geçerli olmayan seçenek.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br/><br/>İzleyici Günlük Dizini.|
|**TreatWarningasError**|İsteğe bağlı **bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak ele akurum.<br/><br/>Yeni bir proje için, tüm `/WX` derlemelerde kullanmak en iyisi olabilir; tüm uyarıların çözülmesi, bulunması mümkün olan en az kod hatasını sağlayacaktır.|
|**TanımsızPreprocessorDefinitions**|İsteğe bağlı **dize[]** parametresi.<br/><br/>Bir veya daha fazla önişlemci tanımlanmamış belirtir.<br/><br/>`-U [macro]` adresini kullanın.|
|**TanımsızAllPreprocessorDefinitions**|İsteğe bağlı **bool** parametresi.<br/><br/>Daha önce tanımlanmış tüm önişlemci değerlerini tanımdan tanımlayın.<br/><br/>`-undef` adresini kullanın.|
|**MultiToolTask'ı kullanma**|İsteğe bağlı **bool** parametresi.<br/><br/>Çok işlemcili Derleme.|
|**Kullanım ShortEnums**|İsteğe bağlı **bool** parametresi.<br/><br/>Enum türü, olası değerler kümesinin giriş imi tarafından gereken kadar bayt kullanır.|
|**Ayrıntılı**|İsteğe bağlı **bool** parametresi.<br/><br/>Ayrıntılı çıktıyı çalıştırmak ve kullanmak için komutları göster.|
|**Uyarı Düzeyi**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleyicinin kod hataları yla ilgili ne kadar katı olmasını istediğinizi seçin. Diğer bayraklar doğrudan **Ek** Seçenekler'e `/w` `/Weverything`eklenmelidir (se , ).<br/><br/>**TurnOffAllWarnings**, tüm derleyici uyarıları devre `w`dışı kullanabilirsiniz (kullanın).<br/>**EnableAllWarnings**, varsayılan olarak devre dışı bırakılanlar `Wall`(kullanım) dahil olmak üzere tüm uyarıları sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)