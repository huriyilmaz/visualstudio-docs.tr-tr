---
title: Visual C++ proje genişletilebilirliği
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10869ad290b0b8df614d25d792d0b3ed1e88eb17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825563"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ proje sistemi genişletilebilirliği ve araç takımı tümleştirmesi

Visual C++ proje sistemi. vcxproj dosyaları için kullanılır. [Visual Studio ortak proje sistemine (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) dayalıdır ve yeni araç kümelerinin, yapı mimarlarının ve hedef platformların kolay tümleştirilmesi için ek, C++ özel genişletilebilirlik noktaları sağlar.

## <a name="c-msbuild-targets-structure"></a>C++ MSBuild hedefleri yapısı

Tüm. vcxproj dosyaları şu dosyaları içeri aktarır:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Bu dosyalar, kendilerini kendileri belirler. Bunun yerine, bu özellik değerlerine bağlı olarak diğer dosyaları içeri aktarırlar:

- `$(ApplicationType)`

   Örnekler: Windows Mağazası, Android, Linux

- `$(ApplicationTypeRevision)`

   Bu, ana. Minor [. Build [. Revision]] biçiminde geçerli bir sürüm dizesi olmalıdır.

   Örnekler: 1,0, 10.0.0.0

- `$(Platform)`

   Geçmiş nedenlerle "Platform" adlı derleme mimarisi.

   Örnekler: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Örnekler: v140, v141, v141_xp, LLVM

Bu özellik değerleri kök klasörü altındaki klasör adlarını belirtir `$(VCTargetsPath)` :

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Uygulama türü*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Platform*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Platform*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

`$(VCTargetsPath)` \\ *Platformlar* \\ klasörü `$(ApplicationType)` , boş olduğunda, Windows Masaüstü projeleri için kullanılır.

### <a name="add-a-new-platform-toolset"></a>Yeni platform araç takımı Ekle

Yeni bir araç takımı eklemek için (örneğin, var olan Win32 platformu için "myaraç takımı *MyToolset* ") Win32 platformlu `$(VCTargetsPath)` * \\ \\ \\ \\ platformları*altında bir myaraç kutusu klasörü oluşturun ve içinde *araç kümesi. props* ve araç kümesi *. targets* dosyaları oluşturun.

*Platformtoolsets* altındaki her klasör adı, burada gösterildiği gibi, belirtilen platform için kullanılabilir bir **platform araç takımı** olarak **Proje özellikleri** iletişim kutusunda görünür:

![Proje özellik sayfaları iletişim kutusunda platform araç takımı özelliği](media/vc-project-extensibility-platform-toolset-property.png "Proje özellik sayfaları iletişim kutusunda platform araç takımı özelliği")

Bu araç takımının desteklediği her bir mevcut platform klasöründe benzer *Myaraç kümesi* klasörleri ve *araç* takımı. *targets* dosyaları oluşturun.

### <a name="add-a-new-platform"></a>Yeni bir platform ekleyin

Yeni bir platform eklemek için, örneğin, "myplatform", *MyPlatform* platformlar `$(VCTargetsPath)` * \\ \\ *altında bir myplatform klasörü oluşturun ve içinde *Platform. default. props*, *Platform. props*ve *Platform. targets* dosyaları oluşturun. Ayrıca `$(VCTargetsPath)` ,<strong><em>Platform</em></strong>* \\ platformtoolsets \\ * klasörü için * \\ \\ bir platform*oluşturun ve içinde en az bir araç takımı oluşturun.

Her biri için *platformlar* klasörü altındaki tüm klasör adları `$(ApplicationType)` , `$(ApplicationTypeRevision)` bir proje için KULLANILABILIR **Platform** seçenekleri olarak IDE 'de görüntülenir.

![Yeni proje platformu iletişim kutusunda yeni platform seçeneği](media/vc-project-extensibility-new-project-platform.png "Yeni proje platformu iletişim kutusunda yeni platform seçeneği")

### <a name="add-a-new-application-type"></a>Yeni bir uygulama türü ekleyin

Yeni bir uygulama türü eklemek için, *MyApplicationType* uygulama türü `$(VCTargetsPath)` * \\ \\ * altında bir MyApplicationType klasörü oluşturun ve içinde bir *Varsayılanlar. props* dosyası oluşturun. Uygulama türü için en az bir düzeltme gereklidir, bu nedenle bir `$(VCTargetsPath)` * \\ uygulama türü \\ MyApplicationType \\ 1,0* klasörü oluşturun ve içinde bir *varsayılan. props* dosyası oluşturun. Ayrıca, bir `$(VCTargetsPath)` * \\ ApplicationType \\ MyApplicationType \\ 1,0 \\ platformları* klasörü oluşturmanız ve içinde en az bir platform oluşturmanız gerekir.

`$(ApplicationType)` ve `$(ApplicationTypeRevision)` özellikleri Kullanıcı arabiriminde görünmez. Proje şablonlarında tanımlanırlar ve Proje oluşturulduktan sonra değiştirilemez.

## <a name="the-vcxproj-import-tree"></a>. Vcxproj içeri aktarma ağacı

Microsoft C++ props ve targets dosyaları için basitleştirilmiş bir içeri aktarmalar ağacı şöyle görünür:

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importbefore* \\ *Varsayılan* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama* \\ `$(ApplicationType)` türü \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama* \\ `$(ApplicationType)` türü \\ `$(ApplicationTypeRevision)` \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama* \\ `$(ApplicationType)` türü \\ `$(ApplicationTypeRevision)` \\ *Platforms* \\ `$(Platform)` Platformlar \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importafter* \\ *Varsayılan* \\ \* . *props*

Windows Masaüstü projeleri tanımlamaz `$(ApplicationType)` , bu nedenle yalnızca içeri aktarırlar

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importbefore* \\ *Varsayılan* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platforms* \\ `$(Platform)` Platformlar \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Importafter* \\ *Varsayılan* \\ \* . *props*

`$(_PlatformFolder)`Platform klasörü konumlarını tutmak için özelliğini kullanacağız `$(Platform)` . Bu özellik

> `$(VCTargetsPath)`\\*Platform*\\`$(Platform)`

Windows Masaüstü uygulamaları için ve

> `$(VCTargetsPath)`\\*Uygulama* \\ `$(ApplicationType)` türü \\ `$(ApplicationTypeRevision)` \\ *Platformlar*\\`$(Platform)`

diğer her şey için.

Props dosyaları şu sırayla içeri aktarılır:

> `$(VCTargetsPath)`\\*Microsoft. cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importbefore* \\ \* . *props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platformtoolsets* \\ `$(PlatformToolset)` \\ *Araç takımı. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importafter* \\ \* . *props*

Hedef dosyalar şu sırada içeri aktarılır:

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importbefore* \\ \* . *hedefler* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platformtoolsets* \\ `$(PlatformToolset)` \\ *Araç takımı. Target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Importafter* \\ \* . *hedefler*

Araç takımı için bazı varsayılan özellikler tanımlamanız gerekiyorsa, uygun ımportbefore ve ımportafter klasörlerine dosya ekleyebilirsiniz.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Araç kümesi. props ve araç takımı. targets dosyalarını yazar

*Araç kümesi. props* ve *araç takımı. targets* dosyaları, bu araç takımı kullanıldığında bir derleme sırasında ne olacağı hakkında tam denetime sahiptir. Ayrıca, **Özellik sayfaları** iletişim kutusundaki içerik ve proje davranışının diğer bazı yönleri gıbı bazı IDE kullanıcı arabiriminden kullanılabilir hata ayıklayıcıları da denetleyebilir.

Bir araç kümesi tüm derleme işlemini geçersiz kılabilir, ancak genellikle araç takımının bazı yapı adımlarını değiştirmesini veya eklemesini ya da mevcut yapı araçlarının bir parçası olarak farklı yapı araçlarını kullanmasını istersiniz. Bu hedefi başarmak için, araç takımının içeri aktarabileceği birçok ortak özellik ve hedef dosya vardır. Araç takımının ne olmasını istediğinize bağlı olarak, bu dosyalar içeri aktarma veya örnek olarak kullanılması yararlı olabilir:

- `$(VCTargetsPath)`\\*Microsoft. CppCommon. targets*

  Bu dosya, yerel yapı sürecinin ana parçalarını tanımlar ve ayrıca şunları içeri aktarır:

  - `$(VCTargetsPath)`\\*Microsoft. CppBuild. targets*

  - `$(VCTargetsPath)`\\*Microsoft. BuildSteps. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common. props*

   Microsoft derleyicileri ve hedef pencereleri kullanan araç takımları varsayılanlarını ayarlar.

- `$(VCTargetsPath)`\\*Microsoft. cpp. WindowsSDK. props*

   Bu dosya Windows SDK konumunu belirler ve Windows 'u hedefleyen uygulamalar için bazı önemli özellikleri tanımlar.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Araç takımını özel hedefleri varsayılan C++ derleme işlemiyle tümleştirin

Varsayılan C++ derleme işlemi, *Microsoft. CppCommon. targets*içinde tanımlanmıştır. Hedefleri belirli bir yapı aracını çağırmayın; ana derleme adımlarını, sıralarını ve bağımlılıklarını belirler.

C++ derlemesi, aşağıdaki hedeflere göre temsil edilen üç ana adıma sahiptir:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Her derleme adımı bağımsız olarak yürütülebildiğinden, bir adımda çalışan hedefler, farklı bir adımın parçası olarak çalışan hedeflerde tanımlanan öğe gruplarına ve özelliklere güvenmemelidir. Bu bölüm belirli derleme performansı iyileştirmelerine izin verir. Varsayılan olarak kullanılmasa da bu ayrımı dikkate almanız önerilir.

Her adımın içinde çalıştırılan hedefler şu özellikler tarafından denetlenir:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Her adımın önceki ve sonraki özellikleri de vardır.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Her adımda bulunan hedeflerin örnekleri için bkz *. Microsoft. CppBuild. targets* dosyası:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Hedefleri gibi hedeflere bakarsanız, `_ClCompile` bunlara doğrudan kendileri tarafından hiçbir şey yapmayamaz, bunun yerine diğer hedeflere bağlı olarak şunlar vardır `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` ve diğer derleme aracına özgü hedefler, *Microsoft. CppBuild. targets*içinde boş hedefler olarak tanımlanmıştır:

```xml
<Target Name="ClCompile"/>
```

`ClCompile`Hedef boş olduğu için, bir araç kümesi tarafından geçersiz kılınmadığı müddetçe gerçek bir yapı eylemi gerçekleştirilmez. Araç takımı hedefleri hedefi geçersiz kılabilir `ClCompile` , diğer bir deyişle, `ClCompile` *Microsoft. cppbuild. targets*alındıktan sonra başka bir tanım içerebilir:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Visual Studio, platformlar arası destek uygulanmadan önce oluşturulmuş ada karşın, `ClCompile` hedefin CL.exe çağrısı gerekmez. Ayrıca uygun MSBuild görevlerini kullanarak Clang, GCC veya diğer derleyiciler çağırabilir.

`ClCompile`Hedef, `SelectClCompile` tek dosya derleme komutunun IDE 'de çalışması için gerekli olan, hedef dışında hiçbir bağımlılığı içermemelidir.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Araç kümesi hedeflerinde kullanılacak MSBuild görevleri

Gerçek bir yapı aracını çağırmak için hedefin bir MSBuild görevi çağırması gerekir. Çalıştırmak için bir komut satırı belirtmenize izin veren temel bir [Exec görevi](../msbuild/exec-task.md) vardır. Ancak, derleme araçlarının genellikle birçok seçeneği, girişi vardır. ve artımlı derlemeler izlemek için çıkış yapar, bu nedenle bunlar için özel görevlere sahip olmak daha mantıklı olur. Örneğin, `CL` görev MSBuild özelliklerini CL.exe anahtarlara çevirir, bunları bir yanıt dosyasına yazar ve CL.exe çağırır. Ayrıca, daha sonra Artımlı derlemeler için tüm giriş ve çıkış dosyalarını izler. Daha fazla bilgi için bkz. [Artımlı derlemeler ve güncel denetimler](#incremental-builds-and-up-to-date-checks).

Microsoft.Cpp.Common.Tasks.dll şu görevleri uygular:

- `BSCMake`

- `CL`

- `ClangCompile` (Clang-GCC anahtarları)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (yürütme gibi, giriş ve çıkış izleme ile)

- `SetEnv`

- `GetOutOfDateItems`

Var olan bir araçla aynı eylemi gerçekleştiren ve benzer komut satırı anahtarlarına (Clang-CL ve CL do olarak) sahip olan bir aracınız varsa, her ikisi için de aynı görevi kullanabilirsiniz.

Bir yapı aracı için yeni bir görev oluşturmanız gerekiyorsa, aşağıdaki seçeneklerden birini seçebilirsiniz:

1. Bu görevi nadiren kullanırsanız veya birkaç saniyelik derleme için önemi yoksa, MSBuild ' inline ' görevlerini kullanabilirsiniz:

   - Xaml görevi (özel bir yapı kuralı)

     Xaml görev bildiriminin bir örneği için bkz `$(VCTargetsPath)` \\ . *buildcustomizations* \\ *masm.xml*ve kullanımı için bkz `$(VCTargetsPath)` \\ . *buildcustomizations* \\ *Masd. targets*.

   - [Kod görevi](../msbuild/msbuild-inline-tasks.md)

1. Daha iyi görev performansı istiyorsanız veya yalnızca daha karmaşık işlevlere ihtiyaç duyuyorsanız, normal MSBuild [görev yazma](../msbuild/task-writing.md) işlemini kullanın.

   Aracın tüm giriş ve çıkışları,,, ve durumlarında olduğu gibi araç komut satırında listelenmiyorsa `CL` `MIDL` `RC` ve otomatik giriş ve çıkış dosyası izlemeyi ve. TLog dosyası oluşturmayı istiyorsanız, görevi sınıftan türetirsiniz `Microsoft.Build.CPPTasks.TrackedVCToolTask` . Mevcut olduğunda, temel [araç görev](/dotnet/api/microsoft.build.utilities.tooltask) sınıfı için belgeler olsa da, sınıfının ayrıntıları için örnek veya belge yoktur `TrackedVCToolTask` . Bu belirli bir ilgi çekici olacaksa, [developercommunity.VisualStudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html)üzerindeki bir isteğe sesinizi ekleyin.

## <a name="incremental-builds-and-up-to-date-checks"></a>Artımlı derlemeler ve güncel denetimler

Varsayılan MSBuild Artımlı derleme hedefleri `Inputs` ve özniteliklerini kullanır `Outputs` . Bunları belirtirseniz, MSBuild yalnızca girdilerden herhangi birinin tüm çıkışlardan daha yeni bir zaman damgasına sahip olması durumunda hedefi çağırır. Kaynak dosyalar genellikle diğer dosyaları içerdiğinden veya içeri aktarırken ve derleme araçları araç seçeneklerine bağlı olarak farklı çıktılar ürettiğinden, MSBuild hedeflerindeki tüm olası giriş ve çıkışları belirtmek zordur.

Bu sorunu yönetmek için C++ derlemesi artımlı derlemeleri desteklemek için farklı bir teknik kullanır. Çoğu hedef giriş ve çıkışları belirtmez ve sonuç olarak her zaman derleme sırasında çalıştırılır. Hedefler tarafından çağrılan görevler,. TLog uzantısına sahip olan *TLog* dosyaları için tüm girişler ve çıktılar hakkındaki bilgileri yazar. . TLog dosyaları, daha sonra nelerin değiştirildiğini ve yeniden oluşturulması gerektiğini ve güncel olduğunu denetlemek için derlemeler tarafından kullanılır. . TLog dosyaları aynı zamanda IDE 'de varsayılan derleme güncel denetimi için tek kaynaktır.

Tüm giriş ve çıkışları öğrenmek için, yerel araç görevleri tracker.exe ve MSBuild tarafından sağlanmış olan [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) sınıfını kullanır.

Microsoft.Build.CPPTasks.Common.dll `TrackedVCToolTask` ortak soyut temel sınıfı tanımlar. Yerel araç görevlerinin çoğu bu sınıftan türetilir.

Visual Studio 2017 güncelleştirme 15,8 ' den başlayarak, `GetOutOfDateItems` bilinen giriş ve çıkışlarla özel hedefler için. TLog dosyaları üretmek üzere Microsoft.Cpp.Common.Tasks.dll ' de uygulanan görevi kullanabilirsiniz.
Alternatif olarak, görevi kullanarak da oluşturabilirsiniz `WriteLinesToFile` . `_WriteMasmTlogs` `$(VCTargetsPath)` \\ Örnek olarak *buildcustomizations* \\ *Masd. targets* içindeki hedefe bakın.

## <a name="tlog-files"></a>. TLog dosyaları

Üç tür. TLog dosyası vardır: *okuma*, *yazma*ve *komut satırı*. Okuma ve yazma. TLog dosyaları Artımlı derlemeler ve IDE 'deki güncel denetim tarafından kullanılır. Komut satırı. TLog dosyaları yalnızca artımlı derlemelerde kullanılır.

MSBuild,. tlog dosyalarını okumak ve yazmak için bu yardımcı sınıfları sağlar:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[Düz TrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) sınıfı hem okuma hem de yazma. TLog dosyalarına erişmek ve çıktılardan daha yeni olan girişleri belirlemek için kullanılabilir veya bir çıktı eksikse. Bu, güncel denetiminde kullanılır.

Komut satırı. TLog dosyaları, derlemede kullanılan komut satırlarıyla ilgili bilgiler içerir. Bunlar yalnızca artımlı derlemeler için, güncel denetimler için kullanılır, bu nedenle iç biçim bunları üreten MSBuild göreviyle belirlenir.

### <a name="read-tlog-format"></a>Oku. TLog biçimi

. Tlog dosyalarını *Oku* ( \* . Read. \* . tlog), kaynak dosyalarla ve bağımlılıklarıyla ilgili bilgiler içerir.

Satırın başındaki bir şapka ( **^** ) bir veya daha fazla kaynağı gösterir. Aynı bağımlılıkları paylaşan kaynaklar dikey çubukla ( **\|** ) ayrılır.

Bağımlılık dosyaları, her biri kendi satırı üzerinde kaynaklardan sonra listelenir. Tüm dosya adları tam yollardır.

Örneğin, proje kaynaklarınızın *F: \\ Test \\ ConsoleApplication1 \\ ConsoleApplication1*içinde bulunduğunu varsayın. Kaynak dosyanızda, *Class1. cpp*, bu şunları içeriyorsa,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

sonra *CL. Read. 1. TLog* dosyası, kaynak dosyayı ve ardından iki bağımlılığı içerir:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Dosya adlarının büyük harfle yazılması gerekmez, ancak bazı araçlar için kolaylık vardır.

### <a name="write-tlog-format"></a>Write. TLog biçimi

*Write* . TLog ( \* . Write. \* . tlog) dosyaları kaynakları ve çıkışları birbirine bağlanır.

Satırın başındaki bir şapka ( **^** ) bir veya daha fazla kaynağı gösterir. Birden çok kaynak dikey çubukla ( **\|** ) ayrılır.

Kaynaklardan oluşturulan çıkış dosyalarının, her biri kendi satırı üzerinde kaynaklardan sonra listelenmesi gerekir. Tüm dosya adları tam yol olmalıdır.

Örneğin, ek bir kaynak dosyası *Class1. cpp*olan bir basit ConsoleApplication projesi için *LINK. Write. 1. TLog* dosyası şunları içerebilir:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Tasarım zamanı oluşturma

IDE 'de. vcxproj projeleri, projeden ek bilgi almak ve çıkış dosyalarını yeniden oluşturmak için bir MSBuild hedefleri kümesi kullanır. Bu hedeflerin bazıları yalnızca tasarım zamanı yapılarında kullanılır, ancak çoğu düzenli derlemelerde ve tasarım zamanı yapılarında kullanılır.

Tasarım zamanı yapıları hakkında genel bilgi için bkz. [Tasarım zamanı derlemeler](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)için CPS belgeleri. Bu belge yalnızca Visual C++ projelerine kısmen uygulanabilir.

`CompileDesignTime` `Compile` Tasarım zamanı derlemeler belgelerinde bahsedilen ve hedefleri hiçbir zaman. vcxproj projeleri için çalıştırılmaz. Visual C++. vcxproj projeleri, IntelliSense bilgilerini almak için farklı tasarım zamanı hedefleri kullanır.

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense bilgileri için tasarım zamanı hedefleri

. Vcxproj projelerinde kullanılan tasarım zamanı hedefleri, `$(VCTargetsPath)` \\ *Microsoft. cpp. DesignTime. targets*içinde tanımlanmıştır.

`GetClCommandLines`Hedef, IntelliSense için derleyici seçeneklerini toplar:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` – Tasarım zamanı oluşturma başlatması için yalnızca tasarım zamanı hedefleri gereklidir. Diğer şeyler arasında bu hedefler, performansı artırmak için bazı normal derleme işlevlerini devre dışı bırakır.

- `ComputeCompileInputsTargets` – derleyici seçeneklerini ve öğelerini değiştiren bir hedef kümesi. Bu hedefler hem tasarım zamanında hem de normal derlemelerde çalışır.

Hedef, `CLCommandLine` IntelliSense için kullanılacak komut satırını oluşturmak üzere görevi çağırır. Yine de, adına rağmen yalnızca CL seçeneklerini değil, Clang ve GCC seçeneklerini de işleyebilir. Derleyici anahtarlarının türü, özelliği tarafından denetlenir `ClangMode` .

Şu anda, görev tarafından oluşturulan komut satırı, `CLCommandLine` IntelliSense altyapısının ayrıştırılmasında daha kolay olduklarından, her zaman (Clang modunda bile) CL anahtarları kullanır.

Derlemeden önce çalışan bir hedef ekliyorsanız, normal veya tasarım zamanı, tasarım zamanı yapılarını bozmadığından veya performansı etkilemediğinden emin olun. Hedefini sınamanın en kolay yolu bir geliştirici komut istemi açmak ve şu komutu çalıştırmalıdır:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Bu komut, sonunda hedefler ve görevler için performans özetine sahip, ayrıntılı bir yapı günlüğü olan *MSBuild. log*dosyası oluşturur.

`Condition ="'$(DesignTimeBuild)' != 'true'"`Tasarım zamanı yapıları için değil, yalnızca normal derlemeler için anlamlı olan tüm işlemlerde kullandığınızdan emin olun.

### <a name="design-time-targets-that-generate-sources"></a>Kaynak üreten tasarım zamanı hedefleri

*Bu özellik, masaüstü yerel projeleri için varsayılan olarak devre dışıdır ve önbelleğe alınmış projelerde Şu anda desteklenmemektedir*.

`GeneratorTarget`Bir proje öğesi için meta veriler tanımlanmışsa, proje yüklendiğinde ve kaynak dosya değiştirildiğinde hedef otomatik olarak çalıştırılır.

::: moniker range="vs-2017"

Örneğin,. xaml dosyalarından. cpp veya. h dosyalarını otomatik olarak oluşturmak için, `$(VSInstallDir)` \\ *MSBuild* \\ *Microsoft* \\ *WindowsXAML* \\ *v 15.0* \\ \* \\ *Microsoft. Windows. UI. xaml. cpp. targets* dosyaları bu varlıkları tanımlar:

::: moniker-end

::: moniker range=">=vs-2019"

Örneğin,. xaml dosyalarından. cpp veya. h dosyalarını otomatik olarak oluşturmak için, `$(VSInstallDir)` \\ *MSBuild* \\ *Microsoft* \\ *WindowsXAML* \\ *v 16.0* \\ \* \\ *Microsoft. Windows. UI. xaml. cpp. targets* dosyaları bu varlıkları tanımlar:

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

`Task.HostObject`Kaynak dosyalarının kaydedilmemiş içeriğini almak için kullanmak üzere, pkgdef içindeki verilen projeler için hedefler ve görevin [Msbuildhostobjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) olarak kaydedilmesi gerekir:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual Studio IDE 'de Proje genişletilebilirliği Visual C++

Visual C++ proje sistemi [vs proje sistemine](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)dayalıdır ve kendi genişletilebilirlik noktalarını kullanır. Ancak, proje hiyerarşisi uygulamasının CPS 'e göre değil, Visual C++ 'a özgüdür ve hiyerarşi genişletilebilirliği proje öğeleriyle sınırlıdır.

### <a name="project-property-pages"></a>Proje özellik sayfaları

Genel tasarım bilgileri için bkz. [VC + + projeleri Için çerçeve Çoklu hedefleme](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

Basit koşullarda, bir C++ projesi için **Proje özellikleri** iletişim kutusunda gördüğünüz Özellik sayfaları *kural* dosyaları tarafından tanımlanır. Bir kural dosyası bir özellik sayfasında gösterilecek özellikler kümesini ve bunların proje dosyasında nasıl ve nerede kaydedileceğini belirtir. Kural dosyaları, XAML biçimi kullanan. xml dosyalarıdır. Bunları seri hale getirmek için kullanılan türler [Microsoft. Build. Framework. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes)içinde açıklanmıştır. Projelerdeki kural dosyalarının kullanımı hakkında daha fazla bilgi için bkz. [özellik sayfası XML kural dosyaları](/cpp/build/reference/property-page-xml-files).

Kural dosyaları `PropertyPageSchema` öğe grubuna eklenmelidir:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` meta veri, kural türü tarafından da denetlenen kural görünürlüğünü sınırlar ve şu değerlerden birine sahip olabilir:

`Project` | `File` | `PropertySheet`

CPS, bağlam türü için diğer değerleri destekler, ancak Visual C++ projelerinde kullanılmaz.

Kuralın birden fazla bağlamda görünebilmelidir, burada gösterildiği gibi, bağlam değerlerini ayırmak için noktalı virgül (**;**) kullanın:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Kural biçimi ve ana türler

Kural biçimi basittir, bu nedenle bu bölüm yalnızca kuralın Kullanıcı arabiriminde nasıl göründüğünü etkileyen öznitelikleri açıklar.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate`Özniteliği, kuralın **Özellik sayfaları** iletişim kutusunda nasıl görüntüleneceğini tanımlar. Öznitelik şu değerlerden birine sahip olabilir:

| Öznitelik | Açıklama |
|------------| - |
| `generic` | Tüm özellikler kategori başlıkları altındaki bir sayfada gösterilir<br/>Kural `Project` , ve bağlamlarına ait olabilir `PropertySheet` , ancak `File` .<br/><br/> Örnek: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Kategoriler alt sayfalar olarak gösterilir.<br/>Kural tüm bağlamlarda görünebilir: `Project` , `PropertySheet` ve `File` .<br/>Kural, `ItemType` `Rule.DataSource` öğe grubuna dahil edilmedikleri takdirde, proje özellikleri ' nde yalnızca projede tanımlı öğe varsa görünür `ProjectTools` .<br/><br/>Örnek: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | Sayfa, hata ayıklama sayfasının bir parçası olarak gösterilir.<br/>Kategoriler Şu anda yok sayıldı.<br/>Kural adı, hata ayıklama başlatıcısı MEF nesnesinin `ExportDebugger` özniteliğiyle eşleşmelidir.<br/><br/>Örnek: `$(VCTargetsPath)` \\ *1033* \\ *hata ayıklayıcı \_ yerel \_windows.xml* |
| *Özel* | Özel şablon. Şablonun adı `ExportPropertyPageUIFactoryProvider` `PropertyPageUIFactoryProvider` MEF nesnesinin özniteliğiyle eşleşmelidir. Bkz. **Microsoft. VisualStudio. ProjectSystem. tasarımcılar. Properties. ıpropertypageuifactoryprovider**.<br/><br/> Örnek: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Kural, özellik kılavuz tabanlı şablonlardan birini kullanıyorsa, özellikleri için bu genişletilebilirlik noktalarını kullanabilir:

- [Özellik değeri düzenleyicileri](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Dinamik Enum değerleri sağlayıcısı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Bir kuralı genişletme

Mevcut bir kuralı kullanmak istiyorsanız, ancak yalnızca birkaç özelliği ekleme veya kaldırma (yani gizleme) ihtiyacı varsa, bir [uzantı kuralı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)oluşturabilirsiniz.

#### <a name="override-a-rule"></a>Bir kuralı geçersiz kıl

Araç takımının çoğu proje varsayılan kuralını kullanmasını, ancak bunlardan yalnızca birini veya birkaçını değiştirmesini isteyebilirsiniz. Örneğin, yalnızca C/C++ kuralını farklı derleyici anahtarlarını gösterecek şekilde değiştirmek istediğinizi varsayalım. Var olan kuralla aynı ada ve görünen ada sahip yeni bir kural sağlayabilir ve `PropertyPageSchema` varsayılan cpp hedefleri içeri aktardıktan sonra öğeyi öğe grubuna dahil edebilirsiniz. Projede, belirtilen ada sahip tek bir kural kullanılır ve en son `PropertyPageSchema` öğe grubu WINS 'e eklenir.

#### <a name="project-items"></a>Proje öğeleri

*ProjectItemsSchema.xml* dosyası, `ContentType` `ItemType` Proje öğesi olarak kabul edilen öğeler için ve değerlerini tanımlar ve `FileExtension` Yeni bir dosyanın hangi öğe grubuna ekleneceğini belirleyen öğeleri tanımlar.

Varsayılan projectıtemsschema dosyası `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*içinde bulunur. Genişletmek için, *MyProjectItemsSchema.xml*gibi yeni bir adla bir şema dosyası oluşturmanız gerekir:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Ardından hedefler dosyasına şunu ekleyin:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Örnek: `$(VCTargetsPath)` \\ *buildcustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Hata ayıklayıcıları

Visual Studio 'daki hata ayıklama hizmeti, hata ayıklama altyapısı için genişletilebilirliği destekler. Daha fazla bilgi için şu örneklere bakın:

- [Mıengine, lldb hata ayıklamayı destekleyen açık kaynak proje](https://github.com/Microsoft/MIEngine)

- [Visual Studio hata ayıklama altyapısı örneği](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Hata ayıklama motoru ve hata ayıklama oturumunun diğer özelliklerini belirtmek için bir [hata ayıklama başlatıcısı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) MEF bileşeni uygulamanız ve bir kural eklemeniz gerekir `debugger` . Bir örnek için bkz `$(VCTargetsPath)` \\ \\ . 1033 hata ayıklayıcı \_ yerel \_windows.xml dosyası.

### <a name="deploy"></a>Dağıtma

. vcxproj projeleri, [dağıtım sağlayıcıları](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)Için Visual Studio proje sistemi genişletilebilirliği kullanır.

### <a name="build-up-to-date-check"></a>Güncel denetim oluşturma

Varsayılan olarak, derleme güncellik denetimi, `$(TlogLocation)` tüm derleme girişleri ve çıkışları için derleme sırasında klasörde oluşturulacak Read. TLog ve Write. tlog dosyalarını gerektirir.

Özel bir güncel denetim kullanmak için:

1. `NoVCDefaultBuildUpToDateCheckProvider` *Araç kümesi. targets* dosyasına özelliği ekleyerek varsayılan güncel denetimi devre dışı bırakın:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Kendi [ıbuilduptodatecheckprovider 'ı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)uygulayın.

## <a name="project-upgrade"></a>Proje yükseltme

### <a name="default-vcxproj-project-upgrader"></a>Default. vcxproj projesi yükselder

Varsayılan. vcxproj projesi yükseltilebilir der,, `PlatformToolset` `ApplicationTypeRevision` MSBuild Araç Takımı sürümünü ve .NET Framework 'ü değiştirir. Son ikisi her zaman Visual Studio sürümü varsayılanlarına değiştirilir, ancak `PlatformToolset` `ApplicationTypeRevision` özel MSBuild özellikleri tarafından denetlenebilir.

Yükselticide, projenin yükseltilip yükseltimeyeceğine karar vermek için bu ölçütler kullanılır:

1. Ve tanımlayan projeler için `ApplicationType` `ApplicationTypeRevision` , geçerli olandan daha yüksek bir düzeltme numarası olan bir klasör vardır.

1. Özelliği `_UpgradePlatformToolsetFor_<safe_toolset_name>` geçerli araç kümesi için tanımlanır ve değeri geçerli araç kümesiyle eşit değildir.

   Bu özellik adlarında, *\<safe_toolset_name>* bir alt çizgi () ile tüm alfasayısal olmayan karakterlerin değiştirildiği araç kümesi adını temsil eder **\_** .

Bir proje yükseltilecekse *çözüm yeniden hedefleme*öğesine katılıyorsa. Daha fazla bilgi için bkz. [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Projeler belirli bir araç takımını kullanırken **Çözüm Gezgini** proje adları eklemek istiyorsanız, bir `_PlatformToolsetShortNameFor_<safe_toolset_name>` özellik tanımlayın.

`_UpgradePlatformToolsetFor_<safe_toolset_name>`Ve `_PlatformToolsetShortNameFor_<safe_toolset_name>` özellik tanımlarının örnekleri için bkz. *Microsoft. cpp. default. props* dosyası. Kullanım örnekleri için bkz `$(VCTargetPath)` \\ . *Microsoft. cpp. platform. targets* dosyası.

### <a name="custom-project-upgrader"></a>Özel proje yükselder

Özel bir proje yükseltilmiş der nesnesi kullanmak için, aşağıda gösterildiği gibi bir MEF bileşeni uygulayın:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Kodunuz, default. vcxproj yükseltilebilir der nesnesini içeri aktarıp çağırabilir:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler`*Microsoft.VisualStudio.ProjectSystem.VS.dll* tanımlanmıştır ve şuna benzerdir `IVsRetargetProjectAsync` .

`VCProjectUpgraderObjectName`Proje sistemine özel bir yükseltilebilir der nesneniz kullanmasını söyleyen özelliği tanımlayın:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Proje yükseltmesini devre dışı bırak

Proje yükseltmelerini devre dışı bırakmak için bir `NoUpgrade` değer kullanın:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Proje önbelleği ve genişletilebilirlik

Visual Studio 2017 ' de büyük C++ çözümleriyle çalışırken performansı artırmak için [Proje önbelleği](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) tanıtılmıştır. Proje verileriyle doldurulmuş bir SQLite veritabanı olarak uygulanır ve ardından MSBuild veya CPS projelerini belleğe yüklemeden projeler yüklemek için kullanılır.

Önbellekten yüklenen. vcxproj projeleri için mevcut bir CPS nesnesi olmadığından, uzantının içeri veya oluşturulamaz olan MEF Bileşenleri `UnconfiguredProject` `ConfiguredProject` . Genişletilebilirlik 'i desteklemek için, Visual Studio bir projenin MEF uzantılarını kullanıp kullanmadığını (veya kullanmasından bağımsız olarak) algıladığında proje önbelleği kullanılmaz.

Bu proje türleri her zaman tam olarak yüklenir ve bellek içinde CPS nesnelerine sahiptir, bu nedenle bunlar için tüm MEF uzantıları oluşturulur:

- Başlangıç projeleri

- Özel bir proje yükselticisini olan projeler, yani bir `VCProjectUpgraderObjectName` özelliği tanımlar

- Masaüstü pencerelerini hedeflemiyor, yani bir özelliği tanımladıkları projeler `ApplicationType`

- Paylaşılan öğe projeleri (. vcxıtems) ve. vcxıtems projelerini içeri aktararak bunlara başvuran tüm projeler.

Bu koşullardan hiçbiri algılanmazsa, bir proje önbelleği oluşturulur. Önbellek, arabirimlerde sorguları yanıtlamak için gereken MSBuild projesinden tüm verileri içerir `get` `VCProjectEngine` . Bu, bir uzantı tarafından gerçekleştirilen MSBuild props ve hedefler dosya düzeyindeki tüm değişikliklerin yalnızca önbellekten yüklenen projelerde çalışması gerektiği anlamına gelir.

## <a name="shipping-your-extension"></a>Uzantınızı gönderme

VSıX dosyaları oluşturma hakkında daha fazla bilgi için bkz. [Visual Studio uzantılarını gönderme](../extensibility/shipping-visual-studio-extensions.md). Özel yükleme konumlarına dosya ekleme hakkında daha fazla bilgi için örneğin, altına dosya eklemek için, `$(VCTargetsPath)` bkz. [Extensions klasörünün dışına yükleme](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Ek kaynaklar

Microsoft derleme sistemi ([MSBuild](../msbuild/msbuild.md)), proje dosyaları için yapı altyapısını ve genişletilebilir XML tabanlı biçimi sağlar. Temel [MSBuild kavramları](../msbuild/msbuild-concepts.md) ve Visual C++ proje sistemini genişletmek Için [Visual C++ MSBuild](/cpp/build/reference/msbuild-visual-cpp-overview) 'in nasıl çalıştığı hakkında bilgi sahibi olmanız gerekir.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)), CPS ve Visual C++ proje sistemi tarafından kullanılan uzantı API 'lerini sağlar. MEF 'in CPS tarafından nasıl kullanılacağına ilişkin genel bakış için, bkz. [CPS ve MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) , [MEF 'e genel bakış](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Yapı adımlarını veya yeni dosya türlerini eklemek için mevcut derleme sistemini özelleştirebilirsiniz. Daha fazla bilgi için bkz. [MSBuild (Visual C++) genel bakış](/cpp/build/reference/msbuild-visual-cpp-overview) ve [Proje özellikleriyle çalışma](/cpp/build/working-with-project-properties).
