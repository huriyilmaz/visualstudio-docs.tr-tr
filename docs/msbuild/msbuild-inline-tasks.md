---
title: MSBuild satır Içi görevleri | Microsoft Docs
description: Microsoft. Build. Framework. ITask arabirimini uygulayan bir sınıf derleyerek MSBuild satır içi görevleri oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 848e9c8c4e3dcc7d364f2001393730fbcc56be7e
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046339"
---
# <a name="msbuild-inline-tasks"></a>MSBuild satır içi görevleri

MSBuild görevleri genellikle arabirimini uygulayan bir sınıf derlenerek oluşturulur <xref:Microsoft.Build.Framework.ITask> . Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

 .NET Framework sürüm 4 ' te başlayarak, proje dosyasında görevleri satır içinde oluşturabilirsiniz. Görevi barındırmak için ayrı bir derleme oluşturmanız gerekmez. Bu, kaynak kodu izlemeyi daha kolay hale getirir ve görevi dağıtmayı kolaylaştırır. Kaynak kodu betiğe tümleştirilir.

 MSBuild 15,8 ' de [Roslyncodetaskfactory](../msbuild/msbuild-roslyncodetaskfactory.md) , .NET Standard platformlar arası satır içi görevler oluşturabilecek şekilde eklenmiştir.  .NET Core 'da satır içi görevler kullanmanız gerekiyorsa, RoslynCodeTaskFactory ' yi kullanmanız gerekir.
## <a name="the-structure-of-an-inline-task"></a>Satır içi görevin yapısı

 Bir Inline görevi [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi tarafından içerilir. Satır içi görev ve `UsingTask` Bu öğeyi içeren öğe, genellikle bir *. targets* dosyasına dahil edilir ve gereken şekilde diğer proje dosyalarına aktarılır. Temel bir satır içi görev aşağıda verilmiştir. Hiçbir şey yapmediğine dikkat edin.

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

 `UsingTask`Örnekteki öğesinde, görevi tanımlayan üç öznitelik ve onu derleyen satır içi görev fabrikası vardır.

- `TaskName`Özniteliği, bu durumda görevi adlandırır `DoNothing` .

- `TaskFactory`Özniteliği, satır içi görev fabrikasını uygulayan sınıfı adlandırır.

- `AssemblyFile`Özniteliği, satır içi görev fabrikasının konumunu verir. Alternatif olarak, `AssemblyName` genellikle içinde bulunan satır içi görev fabrikası sınıfının tam adını belirtmek için özniteliğini kullanabilirsiniz `$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll` .

Görevin kalan öğeleri `DoNothing` boştur ve bir satır içi görevin sırasını ve yapısını göstermek için verilmiştir. Daha sonra bu konunun ilerleyen kısımlarında daha sağlam bir örnek sunulmaktadır.

- `ParameterGroup`Öğesi isteğe bağlıdır. Belirtildiğinde, görevin parametrelerini bildirir. Giriş ve çıkış parametreleri hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında [giriş ve çıkış parametreleri](#input-and-output-parameters) bölümüne bakın.

- `Task`Öğesi, görev kaynak kodunu tanımlar ve içerir.

- `Reference`Öğesi, kodunuzda kullanmakta olduğunuz .NET derlemelerine başvuruları belirtir. Bu, Visual Studio 'da bir projeye başvuru ekleme ile eşdeğerdir. `Include`Öznitelik, başvurulan derlemenin yolunu belirtir.

- `Using`Öğesi, erişmek istediğiniz ad alanlarını listeler. Bu, `Using` Visual C# içindeki ifadeye benzer. `Namespace`Öznitelik, dahil edilecek ad alanını belirtir.

`Reference` ve `Using` öğeleri dilden bağımsız değildir. Satır içi görevler desteklenen .NET CodeDom dillerinin herhangi birinde yazılabilir (örneğin, Visual Basic veya Visual C#).

> [!NOTE]
> Öğesi tarafından içerilen öğeler, `Task` Bu durumda kod görev fabrikası olan görev fabrikasına özeldir.

### <a name="code-element"></a>Kod öğesi

 Öğesi içinde görünecek Son alt öğe öğesi `Task` `Code` . `Code`Öğesi, bir görevde derlenmek istediğiniz kodu içerir veya konumlandırır. `Code`Öğesine yerleştirdiğiniz öğe, görevi nasıl yazmak istediğinize bağlıdır.

 `Language`Özniteliği, kodunuzun yazıldığı dili belirtir. Visual Basic için kabul edilebilir değerler `cs` C# içindir `vb` .

 `Type`Özniteliği, öğesinde bulunan kodun türünü belirtir `Code` .

- Değeri `Type` ise `Class` , `Code` öğesi arabiriminden türetilen bir sınıf için kod içerir <xref:Microsoft.Build.Framework.ITask> .

- Değeri `Type` ise `Method` , kod, arabirimin yöntemini geçersiz kılmayı tanımlar `Execute` <xref:Microsoft.Build.Framework.ITask> .

- Değeri `Type` ise `Fragment` , kod yöntemin içeriğini tanımlar `Execute` , ancak imza veya `return` deyimin değil.

Kod genellikle bir `<![CDATA[` işaret ve işaret arasında görünür `]]>` . Kod CDATA bölümünde olduğundan, kaçış ayrılmış karakterleri hakkında endişelenmenize gerek kalmaz, örneğin, " \<" or "> ".

Alternatif olarak, `Source` `Code` görevin kodunu içeren bir dosyanın konumunu belirtmek için öğesinin özniteliğini kullanabilirsiniz. Kaynak dosyadaki kod, özniteliği tarafından belirtilen türde olmalıdır `Type` . `Source`Özniteliği varsa, varsayılan değeri `Type` olur `Class` . Yoksa `Source` , varsayılan değer olur `Fragment` .

> [!NOTE]
> Kaynak dosyada görev sınıfını tanımlarken, sınıf adı `TaskName` karşılık gelen [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesinin özniteliğiyle kabul etmelidir.

## <a name="helloworld"></a>HelloWorld

 Daha sağlam bir satır içi görev aşağıda verilmiştir. HelloWorld görevinde "Hello, World!" görüntülenir Varsayılan hata günlüğü cihazında, genellikle sistem konsolu veya Visual Studio **çıktı** penceresidir. `Reference`Örnekteki öğesi yalnızca çizim için dahil edilmiştir.

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

 HelloWorld *. targets* adlı bir dosyaya HelloWorld görevini kaydedebilir ve ardından bunu bir projeden aşağıdaki şekilde çağırabilirsiniz.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Giriş ve çıkış parametreleri

 Satır içi görev parametreleri bir öğenin alt öğeleridir `ParameterGroup` . Her parametre, kendisini tanımlayan öğenin adını alır. Aşağıdaki kod parametresini tanımlar `Text` .

```xml
<ParameterGroup>
  <Text />
</ParameterGroup>
```

 Parametrelerde bu özniteliklerin bir veya daha fazlası olabilir:

- `Required` , varsayılan olarak bir isteğe bağlı özniteliktir `false` . `true`Daha sonra parametresi zorunludur ve görev çağrılmadan önce bir değer verilmelidir.

- `ParameterType` , varsayılan olarak bir isteğe bağlı özniteliktir `System.String` . System. Convert. ChangeType kullanarak bir öğe ya da bir dizeden dönüştürülebilen bir değer olan herhangi bir tamamen nitelenmiş türe ayarlanabilir. (Başka bir deyişle, bir dış görevden ve bu bilgisayardan geçirilebilecek herhangi bir tür.)

- `Output` , varsayılan olarak bir isteğe bağlı özniteliktir `false` . İse `true` , Execute yönteminden dönmeden önce parametreye bir değer verilmelidir.

Örneğin,

```xml
<ParameterGroup>
  <Expression Required="true" />
  <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
  <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

Şu üç parametreyi tanımlar:

- `Expression` , System. String türünde gerekli bir giriş parametresidir.

- `Files` gerekli bir öğe listesi giriş parametresidir.

- `Tally` , System. Int32 türünde bir çıkış parametresidir.

`Code`Öğesinde `Type` veya özniteliği varsa `Fragment` `Method` , özellikler her parametre için otomatik olarak oluşturulur. Aksi halde, özellikler, görev kaynak kodunda açıkça bildirilmelidir ve parametre tanımlarıyla tam olarak eşleşmesi gerekir.

## <a name="example"></a>Örnek

 Aşağıdaki satır içi görev, verilen dosyadaki bir belirtecin her oluşumunu verilen değerle değiştirir.

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
- [İzlenecek yol: satır içi görev oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)
