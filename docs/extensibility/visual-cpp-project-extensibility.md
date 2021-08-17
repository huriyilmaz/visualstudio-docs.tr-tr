---
description: .vcxproj dosyaları için Visual C++ proje sistemi kullanılır.
title: Visual C++ proje genişletilebilirliği
ms.date: 04/23/2019
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 96f9199cf93603b288dd5f92817349ec69a0fcddd36ebdfa21625803190849cd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400548"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio C++ Project sistem genişletilebilirliği ve araç kümesi tümleştirmesi

.vcxproj dosyaları için Visual C++ proje sistemi kullanılır. Visual Studio Common Project [System(CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) tabanlıdır ve yeni araç kümeleri, derleme mimarileri ve hedef platformların kolayca tümleşmesi için ek, C++ özel genişletilebilirlik noktaları sağlar.

## <a name="c-msbuild-targets-structure"></a>C++ MSBuild hedef yapısı

Tüm .vcxproj dosyaları şu dosyaları içeri aktarın:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Bu dosyalar kendi kendilerine çok az şey tanımlar. Bunun yerine, bu özellik değerlerine göre diğer dosyaları içeri aktarmaktadır:

- `$(ApplicationType)`

   Örnekler: Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Bu, major.minor[.build[.revision]] formunun geçerli bir sürüm dizesi olmalıdır.

   Örnekler: 1.0, 10.0.0.0

- `$(Platform)`

   Geçmiş nedenlerden dolayı "Platform" adlı derleme mimarisi.

   Örnekler: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Örnekler: v140, v141, v141_xp, llvm

Bu özellik değerleri kök klasör altında klasör `$(VCTargetsPath)` adlarını belirtir:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Uygulama Türü*\\ \
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

Platformlar `$(VCTargetsPath)` \\  \\ klasörü boş `$(ApplicationType)` olduğunda, Windows Desktop projeleri için kullanılır.

### <a name="add-a-new-platform-toolset"></a>Yeni bir platform araç kümesi ekleme

Mevcut Win32 platformu için "MyToolset" gibi yeni bir araç kümesi  eklemek için, `$(VCTargetsPath)` *\\ \\ Platformlar Win32 \\ PlatformToolsets \\* altında bir MyToolset klasörü oluşturun ve *içinde Toolset.props* ve *Toolset.targets* dosyaları oluşturun.

*PlatformToolsets altındaki her* klasör adı, **Project özellikler** iletişim  kutusunda, aşağıda gösterildiği gibi belirtilen platform için kullanılabilir platform araç kümesi olarak görünür:

![Proje Özellik Sayfaları iletişim kutusundaki Platform Araç Seti özelliği](media/vc-project-extensibility-platform-toolset-property.png "Proje özellik sayfaları iletişim kutusunda platform araç takımı özelliği")

Bu araç setini destekleyen her mevcut platform klasöründe benzer *MyToolset* klasörleri ve *Toolset.props* ve *Toolset.targets* dosyaları oluşturun.

### <a name="add-a-new-platform"></a>Yeni platform ekleme

"MyPlatform" gibi yeni bir platform eklemek için Platformlar altında bir *MyPlatform* klasörü oluşturun ve `$(VCTargetsPath)` *\\ \\* *platformda Platform.default.props,* *Platform.props* ve *Platform.targets* dosyaları oluşturun. Ayrıca bir `$(VCTargetsPath)` *\\ \\ Platformlar*<strong><em>MyPlatform</em></strong>*\\ PlatformToolsets \\* klasörü oluşturun ve içinde en az bir araç kümesi oluşturun.

Her biri için Platformlar *klasörünün* altındaki tüm klasör adları ve bir proje için `$(ApplicationType)` kullanılabilir Platform seçenekleri `$(ApplicationTypeRevision)` **olarak** IDE'de görünür.

![Yeni Platform iletişim kutusunda Yeni Project seçeneği](media/vc-project-extensibility-new-project-platform.png "yeni Project platform iletişim kutusunda yeni platform seçeneği")

### <a name="add-a-new-application-type"></a>Yeni uygulama türü ekleme

Yeni bir uygulama türü eklemek için Uygulama Türü altında *bir MyApplicationType* klasörü oluşturun `$(VCTargetsPath)` *\\ \\* ve içinde *bir Defaults.props* dosyası oluşturun. Bir uygulama türü için en az bir düzeltme gereklidir, bu nedenle bir `$(VCTargetsPath)` *\\ Uygulama Türü \\ MyApplicationType \\ 1.0 klasörü* de oluşturun ve içinde bir *Defaults.props* dosyası oluşturun. Ayrıca bir `$(VCTargetsPath)` *\\ ApplicationType \\ MyApplicationType \\ 1.0 \\ Platforms klasörü* ve içinde en az bir platform oluşturmanız gerekir.

`$(ApplicationType)` ve `$(ApplicationTypeRevision)` özellikleri kullanıcı arabiriminde görünmez. Bunlar proje şablonlarında tanımlanır ve proje oluşturulduktan sonra değiştirilemez.

## <a name="the-vcxproj-import-tree"></a>.vcxproj içeri aktarma ağacı

Microsoft C++ props ve targets dosyaları için basitleştirilmiş bir içeri aktarma ağacı şöyledir:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Varsayılan* \\ \* . *props (props)* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama Türü* \\ `$(ApplicationType)` \\ *Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` Türü \\ *Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Uygulama* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` Türü \\  \\ `$(Platform)` Platformlar \\ *Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Varsayılan* \\ \* . *props (props)*

Windows Masaüstü projeleri `$(ApplicationType)` tanımlamaz, bu nedenle yalnızca içeri aktarlar

> `$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Varsayılan* \\ \* . *props (props)* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ `$(Platform)` Platformlar \\ *Platform.default.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Varsayılan* \\ \* . *props (props)*

platform klasörü `$(_PlatformFolder)` konumlarını tutmak için `$(Platform)` özelliğini kullan kullanırsınız. Bu özellik şu şekildedir:

> `$(VCTargetsPath)`\\*Platform*\\`$(Platform)`

Windows Desktop uygulamaları için ve

> `$(VCTargetsPath)`\\*Uygulama* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` Türü \\ *Platformlar*\\`$(Platform)`

diğer her şey için.

Props dosyaları şu sırayla içe aktarılır:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *props (props)* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` \\ *Toolset.props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *props (props)*

Hedef dosyalar şu sırayla içe aktarılır:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *hedefler* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets* \\ `$(PlatformToolset)` \\ *Toolset.target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *hedefler*

Araçet'iniz için bazı varsayılan özellikleri tanımlamanız gerekirse, uygun ImportBefore ve ImportAfter klasörlerine dosya eklersiniz.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Toolset.props ve Toolset.targets dosyaları yazma

*Toolset.props* ve *Toolset.targets* dosyaları, bu araç kümesi kullanılırken derleme sırasında ne olduğu üzerinde tam denetime sahip olur. Ayrıca kullanılabilir hata ayıklayıcıları, Özellik Sayfaları iletişim kutusundaki içerik gibi  bazı IDE kullanıcı arabirimini ve proje davranışının diğer bazı yönlerini de kontrol altına almalarını sağlar.

Bir araç kümesi derleme işleminin tamamını geçersiz kılacak olsa da, genellikle araç kümesinizin yalnızca bazı derleme adımlarını değiştirmesini veya eklemesini ya da mevcut derleme işleminin bir parçası olarak farklı derleme araçlarını kullanmasını istersiniz. Bu hedefi gerçekleştirmek için araç setinizin içeri aktarabilirsiniz bir dizi ortak destek ve hedef dosyası vardır. Araç kümesinizin ne yapmalarını istediğinize bağlı olarak, bu dosyalar içeri aktarma olarak veya örnek olarak kullanmak için yararlı olabilir:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

  Bu dosya, yerel derleme işleminin ana bölümlerini tanımlar ve şunları da içeri aktarır:

  - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

  - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

  - `$(MSBuildToolsPath)`\\*Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Microsoft derleyicilerini ve hedef kümelerini kullanan araç kümeleri için varsayılanları Windows.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Bu dosya, Windows SDK konumunu belirler ve bu sdk'yı hedef alan uygulamalar için bazı önemli Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Araç kümesine özgü hedefleri varsayılan C++ derleme işlemiyle tümleştirin

Varsayılan C++ derleme işlemi *Microsoft.CppCommon.targets içinde tanımlanır.* Hedeflerde belirli bir derleme aracı çağrılmaz; ana derleme adımlarını, bunların sıralarını ve bağımlılıklarını belirtir.

C++ derlemesi, aşağıdaki hedefler tarafından temsil edilen üç ana adıma sahip:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Her derleme adımı bağımsız olarak yürütülebilir, çünkü bir adımda çalışan hedefler, farklı bir adımın parçası olarak çalışan hedeflerde tanımlanan öğe gruplarına ve özelliklerine güvenebilir. Bu bölüm, belirli derleme performansı iyileştirmelerini sağlar. Varsayılan olarak kullanılmasa da, bu ayrımı kabul etmek yine de teşvik edilecektir.

Her adımın içinde çalıştır edilen hedefler şu özelliklerle denetlenr:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Her adımda Before ve After özellikleri de vardır.

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

Her adımda *yer alan hedef örnekleri için Microsoft.CppBuild.targets* dosyasına bakın:

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

`ClCompile` ve diğer derleme aracına özgü hedefler, *Microsoft. CppBuild. targets* içinde boş hedefler olarak tanımlanmıştır:

```xml
<Target Name="ClCompile"/>
```

`ClCompile`Hedef boş olduğu için, bir araç kümesi tarafından geçersiz kılınmadığı müddetçe gerçek bir yapı eylemi gerçekleştirilmez. Araç takımı hedefleri hedefi geçersiz kılabilir `ClCompile` , diğer bir deyişle, `ClCompile` *Microsoft. cppbuild. targets* alındıktan sonra başka bir tanım içerebilir:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Visual Studio, platformlar arası destek uygulanmadan önce oluşturulan adına karşın, `ClCompile` hedefin CL.exe çağırmak zorunda değildir. ayrıca, uygun MSBuild görevlerini kullanarak clang, gcc veya diğer derleyiciler çağırabilir.

`ClCompile`Hedef, `SelectClCompile` tek dosya derleme komutunun IDE 'de çalışması için gerekli olan, hedef dışında hiçbir bağımlılığı içermemelidir.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>araç kümesi hedeflerinde kullanılacak görevleri MSBuild

gerçek bir yapı aracını çağırmak için hedefin bir MSBuild görevi çağırması gerekir. Çalıştırmak için bir komut satırı belirtmenize izin veren temel bir [Exec görevi](../msbuild/exec-task.md) vardır. Ancak, derleme araçlarının genellikle birçok seçeneği, girişi vardır. ve artımlı derlemeler izlemek için çıkış yapar, bu nedenle bunlar için özel görevlere sahip olmak daha mantıklı olur. örneğin, `CL` görev MSBuild özellikleri CL.exe anahtarlara çevirir, bunları bir yanıt dosyasına yazar ve CL.exe çağırır. Ayrıca, daha sonra Artımlı derlemeler için tüm giriş ve çıkış dosyalarını izler. Daha fazla bilgi için bkz. [Artımlı derlemeler ve güncel denetimler](#incremental-builds-and-up-to-date-checks).

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

1. bu görevi nadiren kullanıyorsanız veya birkaç saniyelik derleme için önemi yoksa, MSBuild ' inline ' görevlerini kullanabilirsiniz:

   - Xaml görevi (özel bir yapı kuralı)

     Xaml görev bildiriminin bir örneği için bkz `$(VCTargetsPath)` \\ . *buildcustomizations* \\ *masm.xml* ve kullanımı için bkz `$(VCTargetsPath)` \\ . *buildcustomizations* \\ *Masd. targets*.

   - [Kod görevi](../msbuild/msbuild-inline-tasks.md)

1. daha iyi görev performansı istiyorsanız veya yalnızca daha karmaşık işlevlere ihtiyacınız varsa, normal MSBuild [görev yazma](../msbuild/task-writing.md) işlemini kullanın.

   Aracın tüm giriş ve çıkışları,,, ve durumlarında olduğu gibi araç komut satırında listelenmiyorsa `CL` `MIDL` `RC` ve otomatik giriş ve çıkış dosyası izlemeyi ve. TLog dosyası oluşturmayı istiyorsanız, görevi sınıftan türetirsiniz `Microsoft.Build.CPPTasks.TrackedVCToolTask` . Mevcut olduğunda, temel [araç görev](/dotnet/api/microsoft.build.utilities.tooltask) sınıfı için belgeler olsa da, sınıfının ayrıntıları için örnek veya belge yoktur `TrackedVCToolTask` . Bu, belirli bir ilgi çekici olursa sesinizi [geliştirici Community](https://aka.ms/feedback/suggest?space=62)bir isteğe ekleyin.

## <a name="incremental-builds-and-up-to-date-checks"></a>Artımlı derlemeler ve güncel denetimler

artımlı derleme hedeflerinin varsayılan MSBuild, `Inputs` ve `Outputs` özniteliklerini kullanır. bunları belirtirseniz MSBuild, yalnızca girdilerden herhangi birinin tüm çıkışlardan daha yeni bir zaman damgasına sahip olması durumunda hedefi çağırır. kaynak dosyalar genellikle diğer dosyaları içerdiğinden veya içeri aktarırken ve derleme araçları araç seçeneklerine bağlı olarak farklı çıktılar ürettiğinden, MSBuild hedeflerinde tüm olası giriş ve çıkışları belirtmek zordur.

Bu sorunu yönetmek için C++ derlemesi artımlı derlemeleri desteklemek için farklı bir teknik kullanır. Çoğu hedef giriş ve çıkışları belirtmez ve sonuç olarak her zaman derleme sırasında çalıştırılır. Hedefler tarafından çağrılan görevler,. TLog uzantısına sahip olan *TLog* dosyaları için tüm girişler ve çıktılar hakkındaki bilgileri yazar. . TLog dosyaları, daha sonra nelerin değiştirildiğini ve yeniden oluşturulması gerektiğini ve güncel olduğunu denetlemek için derlemeler tarafından kullanılır. . TLog dosyaları aynı zamanda IDE 'de varsayılan derleme güncel denetimi için tek kaynaktır.

Tüm giriş ve çıkışları öğrenmek için, yerel araç görevleri tracker.exe ve MSBuild tarafından sunulan [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) sınıfını kullanır.

Microsoft.Build.CPPTasks.Common.dll `TrackedVCToolTask` ortak soyut temel sınıfı tanımlar. Yerel araç görevlerinin çoğu bu sınıftan türetilir.

Visual Studio 2017 güncelleştirme 15,8 ' den başlayarak, `GetOutOfDateItems` bilinen giriş ve çıkışlarla özel hedefler için. tlog dosyaları oluşturmak üzere Microsoft.Cpp.Common.Tasks.dll uygulanan görevi kullanabilirsiniz.
Alternatif olarak, görevi kullanarak da oluşturabilirsiniz `WriteLinesToFile` . `_WriteMasmTlogs` `$(VCTargetsPath)` \\ Örnek olarak *buildcustomizations* \\ *Masd. targets* içindeki hedefe bakın.

## <a name="tlog-files"></a>. TLog dosyaları

Üç tür. TLog dosyası vardır: *okuma*, *yazma* ve *komut satırı*. Okuma ve yazma. TLog dosyaları Artımlı derlemeler ve IDE 'deki güncel denetim tarafından kullanılır. Komut satırı. TLog dosyaları yalnızca artımlı derlemelerde kullanılır.

MSBuild. tlog dosyalarını okumak ve yazmak için bu yardımcı sınıfları sağlar:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[Düz TrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) sınıfı hem okuma hem de yazma. TLog dosyalarına erişmek ve çıktılardan daha yeni olan girişleri belirlemek için kullanılabilir veya bir çıktı eksikse. Bu, güncel denetiminde kullanılır.

Komut satırı. TLog dosyaları, derlemede kullanılan komut satırlarıyla ilgili bilgiler içerir. bunlar yalnızca artımlı derlemeler için, güncel denetimler için kullanılır, böylece iç biçim bunları üreten MSBuild görevi tarafından belirlenir.

### <a name="read-tlog-format"></a>Oku. TLog biçimi

. Tlog dosyalarını *Oku* ( \* . Read. \* . tlog), kaynak dosyalarla ve bağımlılıklarıyla ilgili bilgiler içerir.

Satırın başındaki bir şapka ( **^** ) bir veya daha fazla kaynağı gösterir. Aynı bağımlılıkları paylaşan kaynaklar dikey çubukla ( **\|** ) ayrılır.

Bağımlılık dosyaları, her biri kendi satırı üzerinde kaynaklardan sonra listelenir. Tüm dosya adları tam yollardır.

Örneğin, proje kaynaklarınızın *F: \\ Test \\ ConsoleApplication1 \\ ConsoleApplication1* içinde bulunduğunu varsayın. Kaynak dosyanızda, *Class1. cpp*, bu şunları içeriyorsa,

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

Örneğin, ek bir kaynak dosyası *Class1. cpp* olan bir basit ConsoleApplication projesi için *LINK. Write. 1. TLog* dosyası şunları içerebilir:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Tasarım zamanı oluşturma

ıde 'de. vcxproj projeleri projeden ek bilgi almak ve çıkış dosyalarını yeniden oluşturmak için bir MSBuild hedefleri kümesi kullanır. Bu hedeflerin bazıları yalnızca tasarım zamanı yapılarında kullanılır, ancak çoğu düzenli derlemelerde ve tasarım zamanı yapılarında kullanılır.

Tasarım zamanı yapıları hakkında genel bilgi için bkz. [Tasarım zamanı derlemeler](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)için CPS belgeleri. Bu belge yalnızca Visual C++ projelerine kısmen uygulanabilir.

`CompileDesignTime` `Compile` Tasarım zamanı derlemeler belgelerinde bahsedilen ve hedefleri hiçbir zaman. vcxproj projeleri için çalıştırılmaz. Visual C++. vcxproj projeleri, IntelliSense bilgilerini almak için farklı tasarım zamanı hedefleri kullanır.

### <a name="design-time-targets-for-intellisense-information"></a>IntelliSense bilgileri için tasarım zamanı hedefleri

. Vcxproj projelerinde kullanılan tasarım zamanı hedefleri, `$(VCTargetsPath)` \\ *Microsoft. cpp. DesignTime. targets* içinde tanımlanmıştır.

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

Bu komut, sonunda hedefler ve görevler için performans özetine sahip, ayrıntılı bir yapı günlüğü olan *MSBuild. log* dosyası oluşturur.

`Condition ="'$(DesignTimeBuild)' != 'true'"`Tasarım zamanı yapıları için değil, yalnızca normal derlemeler için anlamlı olan tüm işlemlerde kullandığınızdan emin olun.

### <a name="design-time-targets-that-generate-sources"></a>Kaynak üreten tasarım zamanı hedefleri

*Bu özellik, masaüstü yerel projeleri için varsayılan olarak devre dışıdır ve önbelleğe alınmış projelerde Şu anda desteklenmemektedir*.

`GeneratorTarget`Bir proje öğesi için meta veriler tanımlanmışsa, proje yüklendiğinde ve kaynak dosya değiştirildiğinde hedef otomatik olarak çalıştırılır.

::: moniker range="vs-2017"

örneğin,. xaml dosyalarından. cpp veya. h dosyalarını otomatik olarak oluşturmak için, `$(VSInstallDir)` \\  \\ *microsoft* \\ *windowsxaml* \\ *v 15.0* \\ \* \\ *microsoft. Windows MSBuild. 'Sını. Xaml. CPP. targets* dosyaları şu varlıkları tanımlar:

::: moniker-end

::: moniker range=">=vs-2019"

örneğin,. xaml dosyalarından. cpp veya. h dosyalarını otomatik olarak oluşturmak için, `$(VSInstallDir)` \\  \\ *microsoft* \\ *windowsxaml* \\ *v 16.0* \\ \* \\ *microsoft. Windows MSBuild. 'Sını. Xaml. CPP. targets* dosyaları şu varlıkları tanımlar:

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

`Task.HostObject`Kaynak dosyalarının kaydedilmemiş içeriğini almak için kullanmak üzere, pkgdef içindeki verilen projeler için hedefler ve görevin [Msbuildhostobjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) olarak kaydedilmesi gerekir:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual Studio ıde 'de proje genişletilebilirliği Visual C++

Proje Visual C++, VS Project [Sistemi'ne dayalıdır](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)ve genişletilebilirlik noktalarını kullanır. Ancak, proje hiyerarşisi uygulaması CPS'Visual C++ değil özeldir, bu nedenle hiyerarşi genişletilebilirliği proje öğeleriyle sınırlıdır.

### <a name="project-property-pages"></a>Project sayfaları

Genel tasarım bilgileri için [bkz. VC++ Projeleri için Çerçeve Çoklu Hedefleme.](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/)

Basit bir terimle, C++ projesinin **Project** iletişim kutusunda gördüğünüz özellik sayfaları kural dosyaları *tarafından* tanımlanır. Kural dosyası, özellik sayfasında gösterilebilir bir özellik kümesi ve bunların proje dosyasına nasıl ve nereye kaydedeceklerini belirtir. Kural dosyaları, .xml biçimi kullanan dosyalardır. Bunları seri hale getirmede kullanılan türler [Microsoft.Build.Framework.XamlTypes içinde açıklanmıştır.](/dotnet/api/microsoft.build.framework.xamltypes) Projelerde kural dosyalarının kullanımı hakkında daha fazla bilgi için bkz. [Özellik Sayfası XML kural dosyaları.](/cpp/build/reference/property-page-xml-files)

Kural dosyaları öğe grubuna `PropertyPageSchema` eklenmiştir:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` meta veri sınırları kural görünürlüğü de kural türü tarafından denetlenen ve şu değerlerden biri olabilir:

`Project` | `File` | `PropertySheet`

CPS, bağlam türü için diğer değerleri destekler, ancak diğer Visual C++ kullanılmaz.

Kuralın birden fazla bağlamda görünür olması gerekirse, burada gösterildiği gibi bağlam değerlerini ayırmak için noktalı virgül (**;**) kullanın:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Kural biçimi ve ana türler

Kural biçimi basittir, bu nedenle bu bölüm yalnızca kuralın kullanıcı arabiriminde nasıl göründüğünü etkileyen öznitelikleri açıklar.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

özniteliği, `PageTemplate` kuralın Özellik Sayfaları iletişim kutusunda nasıl **görüntülenmiyor olduğunu** tanımlar. Özniteliğin şu değerlerden biri olabilir:

| Öznitelik | Açıklama |
|------------| - |
| `generic` | Tüm özellikler, Kategori başlıkları altında bir sayfada gösterilir<br/>Kural ve bağlamları `Project` için `PropertySheet` görünür olabilir, ancak için `File` görünmez.<br/><br/> Örnek: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Kategoriler alt sayfa olarak gösterilir.<br/>Kural tüm bağlamlarda görünebilir: `Project` , `PropertySheet` ve `File` .<br/>Kural, Project içinde tanımlanan öğeleri varsa, kural adı öğe grubuna dahil olmadığı sürece `ItemType` `Rule.DataSource` Özellikler'de `ProjectTools` görünür.<br/><br/>Örnek: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | Sayfa, Hata Ayıklama sayfasının bir parçası olarak gösterilir.<br/>Kategoriler şu anda yoksayılır.<br/>Kural adı Hata Ayıklama Başlatıcısı MEF nesnesinin özniteliğiyle `ExportDebugger` eşleşmeli.<br/><br/>Örnek: `$(VCTargetsPath)` \\ *1033* \\ *hata \_ ayıklayıcısı yerel \_windows.xml* |
| *Özel* | Özel şablon. Şablonun adı `ExportPropertyPageUIFactoryProvider` MEF nesnesinin özniteliğiyle `PropertyPageUIFactoryProvider` eşleşmeli. Bkz. **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Örnek: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Kural Property Grid tabanlı şablonlardan birini kullanıyorsa özellikleri için şu genişletilebilirlik noktalarını kullanabilir:

- [Özellik değeri düzenleyicileri](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Dinamik enum değerleri sağlayıcısı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Kuralı genişletme

Mevcut bir kuralı kullanmak ancak yalnızca birkaç özellik eklemeniz veya kaldırmanız (gizlemeniz) gerekirse bir Uzantı kuralı [oluşturabilirsiniz.](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md)

#### <a name="override-a-rule"></a>Kuralı geçersiz kılma

Araçet'inizin proje varsayılan kurallarının çoğunu kullanmalarını ama bunların yalnızca bir veya birkaçını değiştirmesini istiyor da olabilir. Örneğin, yalnızca C/C++ kuralını farklı derleyici anahtarlarını gösterecek şekilde değiştirmek istediğinizi diyelim. Var olan kuralla aynı ad ve görünen adla yeni bir kural s sağlamanın yanı sıra varsayılan cpp hedeflerinin içeri aktarın ardından bu kuralı öğe `PropertyPageSchema` grubuna dahil etmek için kullanabilirsiniz. Projede yalnızca adı verilen bir kural kullanılır ve öğe grubuna dahil edilen son `PropertyPageSchema` kural kazanır.

#### <a name="project-items"></a>Project öğeleri

Bu *ProjectItemsSchema.xml,* Project Items olarak kabul edilen Öğeler için ve değerlerini tanımlar ve yeni bir dosyanın hangi Öğe grubuna `ContentType` `ItemType` `FileExtension` ekli olduğunu belirlemek için öğeleri tanımlar.

Varsayılan ProjectItemsSchema `$(VCTargetsPath)` \\ *dosyası, 1033'te* \\ ** ProjectItemsSchema.xml. Bunu genişletmek için, aşağıdaki gibi yeni bir adla bir şema *MyProjectItemsSchema.xml:*

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

Ardından hedefler dosyasına şunları ekleyin:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Örnek: `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Hata ayıklayıcı

Visual Studio'daki Hata Ayıklama hizmeti, Hata Ayıklama altyapısı için genişletilebilirliği destekler. Daha fazla bilgi için şu örneklere bakın:

- [MIEngine, lldb hata ayıklamasını destekleyen açık kaynak projesi](https://github.com/Microsoft/MIEngine)

- [Visual Studio hata ayıklama altyapısı örneği](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Hata ayıklama oturumunun Hata Ayıklama altyapılarını ve diğer özelliklerini belirtmek için bir Hata Ayıklama [Başlatıcısı](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) MEF bileşeni uygulamalı ve bir kural `debugger` ekleyebilirsiniz. Örneğin, `$(VCTargetsPath)` \\ 1033 hata \\ ayıklayıcısı \_ yerel hata \_ ayıklayıcısıwindows.xml bakın.

### <a name="deploy"></a>Dağıtma

.vcxproj projeleri, Dağıtım Sağlayıcıları için Visual Studio Project Sistem [genişletilebilirliğini kullanır.](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md)

### <a name="build-up-to-date-check"></a>Güncel denetim oluşturma

Varsayılan olarak, derlemenin güncel denetimi, tüm derleme girişleri ve çıkışları için derleme sırasında klasörde oluşturulacak okuma .tlog ve yazma .tlog `$(TlogLocation)` dosyalarını gerektirir.

Özel bir güncel denetim kullanmak için:

1. Toolset.targets dosyasına özelliği ekleyerek varsayılan güncel denetimi `NoVCDefaultBuildUpToDateCheckProvider` *devre dışı* bırakma:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Kendi [IBuildUpToDateCheckProvider'ını uygulama.](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md)

## <a name="project-upgrade"></a>Project yükseltme

### <a name="default-vcxproj-project-upgrader"></a>Varsayılan .vcxproj proje yükselten

Varsayılan .vcxproj proje yükselten , `PlatformToolset` `ApplicationTypeRevision` , MSBuild ve .Net Framework sürümünü değiştirir. Son ikisi her zaman varsayılan Visual Studio olarak değiştirilir, ancak özel sürüm `PlatformToolset` `ApplicationTypeRevision` özellikleriyle denetlen MSBuild olabilir.

Yükselten, bir projenin yükseltilebilir olup olmadığını karar vermek için şu ölçütleri kullanır:

1. ve tanımlayan projeler `ApplicationType` `ApplicationTypeRevision` için, geçerli sürümden daha yüksek düzeltme numarasına sahip bir klasör bulunur.

1. özelliği `_UpgradePlatformToolsetFor_<safe_toolset_name>` geçerli araç kümesi için tanımlanır ve değeri geçerli araç kümesine eşit değildir.

   Bu özellik adlarında, tüm alfasayısal olmayan karakterlerin yerini alt çizgi () ile alan araç *\<safe_toolset_name>* takımı adını temsil **\_** eder.

Bir proje yükseltildikten sonra Çözüm Yeniden *Hedefleme'ye katılabilir.* Daha fazla bilgi için bkz. [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Projeler belirli bir araç seti Çözüm Gezgini **proje** adlarını bir özellik olarak `_PlatformToolsetShortNameFor_<safe_toolset_name>` donatma.

ve özellik `_UpgradePlatformToolsetFor_<safe_toolset_name>` `_PlatformToolsetShortNameFor_<safe_toolset_name>` tanımlarının örnekleri için *Bkz. Microsoft.Cpp.Default.props* dosyası. Kullanım örnekleri için `$(VCTargetPath)` \\ *Bkz. Microsoft.Cpp.Platform.targets* dosyası.

### <a name="custom-project-upgrader"></a>Özel proje yükselten

Özel bir proje yükselten nesnesi kullanmak için burada gösterildiği gibi bir MEF bileşeni kullanın:

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

Kodunuz varsayılan .vcxproj yükselten nesnesini içeri aktarabilir ve çağırabilir:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` , içinde *Microsoft.VisualStudio.ProjectSystem.VS.dll* ve ile `IVsRetargetProjectAsync` benzerdir.

Proje `VCProjectUpgraderObjectName` sistemine özel yükselten nesnenizi kullanmalarını söylemek için özelliğini tanımlayın:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Proje yükseltmesini devre dışı bırakma

Proje yükseltmelerini devre dışı bırakmak için bir değer `NoUpgrade` kullanın:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Project ve genişletilebilirlik

Visual Studio 2017'de büyük C++ çözümleriyle çalışırken performansı artırmak için [proje önbelleği](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) tanıtıldı. Proje verileriyle doldurulmuş bir SQLite veritabanı olarak uygulanır ve ardından projeleri belleğe yüklemeden MSBuild için kullanılır.

Önbellekten yüklenen .vcxproj projeleri için CPS nesneleri mevcut olduğundan, uzantının içeri aktaran veya oluşturulamıyor MEF `UnconfiguredProject` `ConfiguredProject` bileşenleri. Genişletilebilirliği desteklemek için proje önbelleği, bir projenin MEF uzantılarını kullanıp Visual Studio (veya kullanma olasılığı) algılayan proje önbelleğini kullanmaz.

Bu proje türleri her zaman tam olarak yüklenir ve CPS nesneleri bellektedir, bu nedenle tüm MEF uzantıları bunlar için oluşturulur:

- Başlangıç projeleri

- Özel proje yükseltene sahip projeler, yani bir özellik `VCProjectUpgraderObjectName` tanımlar

- Desktop Windows hedefini belirlemeen projeler, yani bir özellik `ApplicationType` tanımlar

- Paylaşılan Öğeler projeleri (.vcxitems) ve .vcxitems projelerini içeri aktararak bu projelere başvurulan tüm projeler.

Bu koşullardan hiçbiri algılanmazsa bir proje önbelleği oluşturulur. Önbellek, arabirimler üzerinde sorguları yanıtlamak MSBuild projesinde `get` yer alan tüm verileri `VCProjectEngine` içerir. Bu, uzantı tarafından yapılan MSBuild ve hedef dosya düzeyinde yapılan tüm değişikliklerin yalnızca önbellekten yüklenen projelerde çalışması gerektiği anlamına gelir.

## <a name="shipping-your-extension"></a>Uzantınızı gönderme

VSIX dosyaları oluşturma hakkında bilgi için bkz. [Gönderim Visual Studio Uzantıları.](../extensibility/shipping-visual-studio-extensions.md) Özel yükleme konumlarına dosya ekleme hakkında daha fazla bilgi için örneğin, altına dosya eklemek için, `$(VCTargetsPath)` bkz. [Extensions klasörünün dışına yükleme](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Ek kaynaklar

Microsoft derleme sistemi ([MSBuild](../msbuild/msbuild.md)), proje dosyaları için yapı altyapısını ve genişletilebilir XML tabanlı biçimi sağlar. temel [MSBuild kavramlarıyla](../msbuild/msbuild-concepts.md) ve Visual C++ proje sistemini genişletmek için [Visual C++ MSBuild](/cpp/build/reference/msbuild-visual-cpp-overview) nasıl çalıştığına ilişkin bilgi sahibi olmanız gerekir.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)), CPS ve Visual C++ proje sistemi tarafından kullanılan uzantı apı 'lerini sağlar. MEF 'in CPS tarafından nasıl kullanılacağına ilişkin genel bakış için, bkz. [CPS ve MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) , [MEF 'e genel bakış](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Yapı adımlarını veya yeni dosya türlerini eklemek için mevcut derleme sistemini özelleştirebilirsiniz. daha fazla bilgi için bkz. [MSBuild (Visual C++) genel bakış](/cpp/build/reference/msbuild-visual-cpp-overview) ve [proje özellikleriyle çalışma](/cpp/build/working-with-project-properties).
