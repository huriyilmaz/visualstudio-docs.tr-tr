---
title: RoslynCodeTaskFactory ile MSBuild satır Içi görevleri | Microsoft Docs
description: Satır içi görevler olarak kullanılmak üzere bellek içi görev derlemeleri oluşturmak için platformlar arası Roslyn derleyicileri kullanan MSBuild RoslynCodeTaskFactory hakkında bilgi edinin.
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
ms.openlocfilehash: 336c23a5e1357e8e425a74c0954d3c0e28f8a930
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049129"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory ile MSBuild satır içi görevleri

[CodeTaskFactory](../msbuild/msbuild-inline-tasks.md)' ye benzer şekilde, roslyncodetaskfactory, iç satır görevleri olarak kullanılmak üzere bellek içi görev derlemeleri oluşturmak için platformlar arası Roslyn derleyicileri kullanır.  RoslynCodeTaskFactory görevlerinin hedefi .NET Standard ve .NET Framework ve .NET Core çalışma zamanlarının yanı sıra Linux ve Mac OS gibi diğer platformlar üzerinde de çalışabilir.

>[!NOTE]
>RoslynCodeTaskFactory yalnızca MSBuild 15,8 ve üzeri sürümlerde kullanılabilir. MSBuild sürümleri Visual Studio sürümlerini izleyerek Visual Studio 2017 sürüm 15,8 ve üzeri sürümlerde RoslynCodeTaskFactory kullanılabilir.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory ile bir satır içi görevin yapısı

 RoslynCodeTaskFactory satır içi görevleri, .NET Standard hedeflemediği tek fark olan [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md)ile aynı şekilde bildirilmiştir.  Satır içi görev ve `UsingTask` Bu öğeyi içeren öğe, genellikle bir *. targets* dosyasına dahil edilir ve gereken şekilde diğer proje dosyalarına aktarılır. Temel bir satır içi görev aşağıda verilmiştir. Hiçbir şey yapmediğine dikkat edin.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
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

- `AssemblyFile`Özniteliği, satır içi görev fabrikasının konumunu verir. Alternatif olarak, `AssemblyName` genellikle genel derleme önbelleğinde (GAC) bulunan satır içi görev fabrikası sınıfının tam adını belirtmek için özniteliğini kullanabilirsiniz.

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

## <a name="hello-world"></a>Hello World

 RoslynCodeTaskFactory ile daha sağlam bir satır içi görev aşağıda verilmiştir. HelloWorld görevinde "Hello, World!" görüntülenir Varsayılan hata günlüğü cihazında, genellikle sistem konsolu veya Visual Studio **çıktı** penceresidir. `Reference`Örnekteki öğesi yalnızca çizim için dahil edilmiştir.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
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

`Code`Öğesinde `Type` veya özniteliği varsa `Fragment` `Method` , özellikler her parametre için otomatik olarak oluşturulur.  RoslynCodeTaskFactory içinde, `Code` öğesinin özniteliği varsa, `Type` `Class` `ParameterGroup` kaynak koddan çıkarıldığından (bunun farklılığı `CodeTaskFactory` ), öğesini belirtmeniz gerekmez. Aksi halde, özellikler, görev kaynak kodunda açıkça bildirilmelidir ve parametre tanımlarıyla tam olarak eşleşmesi gerekir.

## <a name="example"></a>Örnek

 Aşağıdaki satır içi görev bazı iletileri günlüğe kaydeder ve bir dize döndürür.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Bu satır içi görevler, yolları birleştirebilir ve dosya adını alabilir.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="provide-backward-compatibility"></a>Geriye dönük uyumluluk sağla

`RoslynCodeTaskFactory` İlk olarak MSBuild sürüm 15,8 ' de kullanıma sunuldu. Visual Studio 'nun önceki sürümlerini ve MSBuild 'i desteklemek istediğiniz bir durumunuz olduğunu varsayalım, ancak `RoslynCodeTaskFactory` `CodeTaskFactory` was, ancak aynı derleme betiğini kullanmak istiyorsunuz. `Choose` `$(MSBuildVersion)` `RoslynCodeTaskFactory` Aşağıdaki örnekte olduğu gibi, veya için geri dönmeksizin derleme zamanına karar vermek üzere özelliğini kullanan bir yapı kullanabilirsiniz `CodeTaskFactory` :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [İzlenecek yol: satır içi görev oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)
