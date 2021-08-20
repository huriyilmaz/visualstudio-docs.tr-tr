---
title: MSBuild Satır Içi Görevler | Microsoft Docs
description: Microsoft.Build.Framework.ITask arabirimini uygulayan bir sınıf derleerek satır içi görevlerin nasıl oluşturulacaklarını öğrenin. MSBuild
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5180ca730b8caba06e31cc3a17443988578b1877
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068926"
---
# <a name="msbuild-inline-tasks"></a>MSBuild satır içi görevleri

MSBuild görevleri genellikle arabirimi uygulayan bir sınıf oluşturularak <xref:Microsoft.Build.Framework.ITask> oluşturulur. Daha fazla bilgi için bkz. [Görevler.](../msbuild/msbuild-tasks.md)

 4. .NET Framework başlayarak proje dosyasında satır içi görevler oluşturabilirsiniz. Görevi barındırmak için ayrı bir derleme oluşturmanıza gerek yok. Bu, kaynak kodu izlemenizi ve görevi dağıtmayı kolaylaştırır. Kaynak kodu betikle tümleştirilmiştir.

 15.8 MSBuild de, platformlar arası satır içi görevler oluşturan [RoslynCodeTaskFactory](../msbuild/msbuild-roslyncodetaskfactory.md) .NET Standard eklendi.  .NET Core'da satır içi görevler kullanıyorsanız RoslynCodeTaskFactory'i kullansanız iyi olur.
## <a name="the-structure-of-an-inline-task"></a>Satır içi görevin yapısı

 Satır içi görev bir [UsingTask öğesi tarafından](../msbuild/usingtask-element-msbuild.md) içerir. Satır içi görev ve bunu içeren öğe genellikle bir .targets dosyasına dahil edilir ve `UsingTask` gerektiğinde diğer proje dosyalarına aktarılır.  Temel bir satır içi görev şu şekildedir. Hiçbir şey yapmadı.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="CodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 Örnekteki öğesi, görevi ve onu derleye satır içi görev `UsingTask` fabrikasını tanımlayan üç öznitelike sahiptir.

- özniteliği, `TaskName` görevi (bu durumda) olarak adlar. `DoNothing`

- özniteliği, `TaskFactory` satır içi görev fabrikasını uygulayan sınıfı olarak adlar.

- özniteliği, `AssemblyFile` satır içi görev fabrikasının konumunu verir. Alternatif olarak, özniteliğini kullanarak normalde içinde bulunan satır içi görev fabrikası sınıfının `AssemblyName` tam adını `$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll` belirtebilirsiniz.

Görevin kalan öğeleri boştur ve satır içi görevin sıralama ve `DoNothing` yapısını göstermek için sağlanır. Bu konunun ilerleyenlarında daha sağlam bir örnek ve sunulmuştur.

- öğesi `ParameterGroup` isteğe bağlıdır. Belirtilen, görev için parametreleri belirtir. Giriş ve çıkış parametreleri hakkında daha fazla bilgi için bu [konunun devamlarında yer alan Giriş ve](#input-and-output-parameters) çıkış parametreleri'ne bakın.

- öğesi `Task` görev kaynak kodunu açıklar ve içerir.

- `Reference`öğesi, kodunda kullanmakta olan .NET derlemelerine yapılan başvuruları belirtir. Bu, Visual Studio'da bir projeye başvuru eklemeye eşdeğerdir. özniteliği, `Include` başvurulan derlemenin yolunu belirtir.

- `Using`öğesi, erişmek istediğiniz ad alanlarını listeler. Bu, `Using` Visual C# içinde deyimine benzer. özniteliği, `Namespace` dahil etmek için ad alanını belirtir.

`Reference` ve `Using` öğeleri dilden bağımsızdır. Satır içi görevler desteklenen .NET CodeDom dillerinden herhangi biri (örneğin, Visual Basic veya Visual C# ile yazabilir.

> [!NOTE]
> öğesi tarafından yer alan `Task` öğeler görev fabrikasına, bu durumda ise kod görev fabrikasına özeldir.

### <a name="code-element"></a>Kod öğesi

 öğesi içinde görünecek son alt `Task` öğe `Code` öğesidir. `Code`öğesi, bir göreve derlensin istediğiniz kodu içerir veya yerini saptar. öğesine ne koymak `Code` istediğiniz, görevi nasıl yazmak istediğinize bağlıdır.

 `Language`özniteliği, kodunuzun yazıldığı dili belirtir. Kabul edilebilir değerler `cs` C# için, `vb` Visual Basic.

 `Type`özniteliği, öğesinde bulunan kod türünü `Code` belirtir.

- değeri `Type` ise, `Class` öğesi `Code` arabiriminden türeten bir sınıf için kod <xref:Microsoft.Build.Framework.ITask> içerir.

- değeri `Type` ise, `Method` kod arabiriminin yönteminin geçersiz `Execute` kılmayı <xref:Microsoft.Build.Framework.ITask> tanımlar.

- değeri ise kod yöntemin içeriğini tanımlar, ancak imzayı `Type` `Fragment` veya `Execute` deyimini `return` tanımlar.

Kodun kendisi genellikle bir işaretçi ile `<![CDATA[` işaretçi arasında `]]>` görünür. Kod bir CDATA bölümünde olduğundan ayrılmış karakterlerin kaçış karakteriyle ilgili endişelenmenize gerek yok, örneğin, " \<" or "> ".

Alternatif olarak, göreviniz için kodu içeren `Source` `Code` bir dosyanın konumunu belirtmek üzere öğesinin özniteliğini kullanabilirsiniz. Kaynak dosyada yer alan kodun özniteliği tarafından belirtilen türde olması `Type` gerekir. Öznitelik `Source` varsa, varsayılan değeri `Type` `Class` olur. yoksa `Source` varsayılan değer `Fragment` olur.

> [!NOTE]
> Kaynak dosyada görev sınıfını tanımlarken, sınıf adı karşılık gelen `TaskName` [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesinin özniteliğiyle aynı kabulmalıdır.

## <a name="helloworld"></a>Helloworld

 Burada daha sağlam bir satır içi görev ve bulunmaktadır. HelloWorld görevi "Hello, world!" varsayılan hata günlüğü cihazında( genellikle sistem konsolu veya Visual Studio **penceresidir.** Örnekteki `Reference` öğesi yalnızca çizim için dahil edilir.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="CodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 HelloWorld görevini *HelloWorld.targets* adlı bir dosyaya kaydedebilir ve ardından aşağıdaki gibi bir projeden çağırabilirsiniz.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Giriş ve çıkış parametreleri

 Satır içi görev parametreleri bir öğenin alt `ParameterGroup` öğeleridir. Her parametre, onu tanımlayan öğenin adını alır. Aşağıdaki kod parametresini `Text` tanımlar.

```xml
<ParameterGroup>
  <Text />
</ParameterGroup>
```

 Parametrelerde şu özniteliklerden biri veya daha fazlası olabilir:

- `Required` , varsayılan olarak isteğe bağlı `false` bir özniteliktir. ise, `true` parametresi gereklidir ve görev çağrılmadan önce bir değer ver gerekir.

- `ParameterType` , varsayılan olarak isteğe bağlı `System.String` bir özniteliktir. System.Convert.ChangeType kullanılarak bir dizeye veya dizeden dönüştürülecek bir öğe veya değer olan herhangi bir tam türe ayarlanmış olabilir. (Başka bir deyişle, dış göreve ve dış göreve geçirilen herhangi bir tür.)

- `Output` , varsayılan olarak isteğe bağlı `false` bir özniteliktir. ise, `true` Execute yönteminden dönmeden önce parametresine bir değer ver gerekir.

Örneğin,

```xml
<ParameterGroup>
  <Expression Required="true" />
  <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
  <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

şu üç parametreyi tanımlar:

- `Expression` , System.String türünde gerekli bir giriş parametresidir.

- `Files` gerekli bir öğe listesi giriş parametresidir.

- `Tally` , System.Int32 türünde bir çıkış parametresidir.

öğesi `Code` veya `Type` özniteliğine `Fragment` `Method` sahipse, özellikler her parametre için otomatik olarak oluşturulur. Aksi takdirde, özellikler görev kaynak kodunda açıkça bildir olmalı ve bunların parametre tanımlarıyla tam olarak eşleşmeli.

## <a name="example"></a>Örnek

 Aşağıdaki satır içi görev, verilen dosyada bir belirteci her oluşumunu verilen değerle değiştirir.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup>
      <Path ParameterType="System.String" Required="true" />
      <Token ParameterType="System.String" Required="true" />
      <Replacement ParameterType="System.String" Required="true" />
    </ParameterGroup>
    <Task>
      <Code Type="Fragment" Language="cs"><![CDATA[
string content = File.ReadAllText(Path);
content = content.Replace(Token, Replacement);
File.WriteAllText(Path, content);

]]></Code>
    </Task>
  </UsingTask>

  <Target Name='Demo' >
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Adım adım kılavuz: Satır içi görev oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)
