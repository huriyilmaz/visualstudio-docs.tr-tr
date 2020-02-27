---
title: RoslynCodeTaskFactory ile MSBuild satır Içi görevleri | Microsoft Docs
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
ms.openlocfilehash: ead738042b15c955aadb458c527253f3759b934e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633232"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory ile MSBuild satır içi görevleri

[CodeTaskFactory](../msbuild/msbuild-inline-tasks.md)' ye benzer şekilde, roslyncodetaskfactory, iç satır görevleri olarak kullanılmak üzere bellek içi görev derlemeleri oluşturmak için platformlar arası Roslyn derleyicileri kullanır.  RoslynCodeTaskFactory görevlerinin hedefi .NET Standard ve .NET Framework ve .NET Core çalışma zamanlarının yanı sıra Linux ve Mac OS gibi diğer platformlar üzerinde de çalışabilir.

>[!NOTE]
>RoslynCodeTaskFactory yalnızca MSBuild 15,8 ve üzeri sürümlerde kullanılabilir.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory ile bir satır içi görevin yapısı

 RoslynCodeTaskFactory satır içi görevleri, .NET Standard hedeflemediği tek fark olan [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md)ile aynı şekilde bildirilmiştir.  Satır içi görev ve onu içeren `UsingTask` öğesi, genellikle bir *. targets* dosyasına dahil edilir ve gerektiği şekilde diğer proje dosyalarına içeri aktarılır. Temel bir satır içi görev aşağıda verilmiştir. Hiçbir şey yapmediğine dikkat edin.

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

 Örnekteki `UsingTask` öğesi, görevi ve onu derleyen satır içi görev fabrikasını tanımlayan üç özniteliğe sahiptir.

- `TaskName` özniteliği görevi, bu durumda `DoNothing`adlandırır.

- `TaskFactory` özniteliği, satır içi görev fabrikasını uygulayan sınıfı adlandırır.

- `AssemblyFile` özniteliği, satır içi görev fabrikasının konumunu verir. Alternatif olarak, genellikle genel derleme önbelleğinde (GAC) bulunan satır içi görev fabrikası sınıfının tam adını belirtmek için `AssemblyName` özniteliğini kullanabilirsiniz.

`DoNothing` görevinin kalan öğeleri boştur ve bir satır içi görevin sırasını ve yapısını göstermek için verilmiştir. Daha sonra bu konunun ilerleyen kısımlarında daha sağlam bir örnek sunulmaktadır.

- `ParameterGroup` öğesi isteğe bağlıdır. Belirtildiğinde, görevin parametrelerini bildirir. Giriş ve çıkış parametreleri hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında [giriş ve çıkış parametreleri](#input-and-output-parameters) bölümüne bakın.

- `Task` öğesi, görev kaynak kodunu açıklar ve içerir.

- `Reference` öğesi, kodunuzda kullandığınız .NET derlemelerine başvuruları belirtir. Bu, Visual Studio 'da bir projeye başvuru ekleme ile eşdeğerdir. `Include` özniteliği başvurulan derlemenin yolunu belirtir.

- `Using` öğesi erişmek istediğiniz ad alanlarını listeler. Bu, Visual C#'teki `Using` ifadeye benzer. `Namespace` özniteliği dahil edilecek ad alanını belirtir.

`Reference` ve `Using` öğeleri dilden bağımsız değildir. Satır içi görevler desteklenen .NET CodeDom dillerinin herhangi birine (örneğin, Visual Basic veya görsel C#) yazılabilir.

> [!NOTE]
> `Task` öğesinin içerdiği öğeler, görev fabrikasına, bu durumda kod görev fabrikasına özgüdür.

### <a name="code-element"></a>Kod öğesi

`Task` öğesi içinde görünecek Son alt öğe `Code` öğesidir. `Code` öğesi, bir görevde derlenmek istediğiniz kodu içerir veya konumlandırır. `Code` öğesine yerleştirdiğiniz öğe, görevi nasıl yazmak istediğinize bağlıdır.

`Language` özniteliği, kodunuzun yazıldığı dili belirtir. Kabul edilebilir değerler C#, Visual Basic için `vb` `cs`.

`Type` özniteliği `Code` öğesinde bulunan kodun türünü belirtir.

- `Type` değeri `Class`ise, `Code` öğesi <xref:Microsoft.Build.Framework.ITask> arabiriminden türetilen bir sınıf için kod içerir.

- `Type` değeri `Method`ise, kod <xref:Microsoft.Build.Framework.ITask> arabiriminin `Execute` yönteminin bir geçersiz kılmayı tanımlar.

- `Type` değeri `Fragment`, kod `Execute` yönteminin içeriğini tanımlar, ancak imza veya `return` ifadesiyle değil.

Kod genellikle `<![CDATA[` işaretleyicisi ve `]]>` işaretleyicisi arasında görüntülenir. Kod CDATA bölümünde olduğundan, kaçış ayrılmış karakterleri (örneğin, "\<" veya ">") konusunda endişelenmeniz gerekmez.

Alternatif olarak, görevin kodunu içeren bir dosyanın konumunu belirtmek için `Code` öğesinin `Source` özniteliğini kullanabilirsiniz. Kaynak dosyadaki kodun, `Type` özniteliği tarafından belirtilen türde olması gerekir. `Source` özniteliği varsa, varsayılan `Type` değeri `Class`olur. `Source` yoksa, varsayılan değer `Fragment`.

> [!NOTE]
> Kaynak dosyada görev sınıfını tanımlarken, sınıf adı karşılık gelen [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesinin `TaskName` özniteliğiyle kabul etmelidir.

## <a name="hello-world"></a>Hello World

 RoslynCodeTaskFactory ile daha sağlam bir satır içi görev aşağıda verilmiştir. HelloWorld görevinde "Hello, World!" görüntülenir Varsayılan hata günlüğü cihazında, genellikle sistem konsolu veya Visual Studio **çıktı** penceresidir. Örnekteki `Reference` öğesi yalnızca çizim için dahil edilmiştir.

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

HelloWorld *. targets*adlı bir dosyaya HelloWorld görevini kaydedebilir ve ardından bunu bir projeden aşağıdaki şekilde çağırabilirsiniz.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Giriş ve çıkış parametreleri

 Satır içi görev parametreleri bir `ParameterGroup` öğesinin alt öğeleridir. Her parametre, kendisini tanımlayan öğenin adını alır. Aşağıdaki kod `Text`parametresini tanımlar.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametrelerde bu özniteliklerin bir veya daha fazlası olabilir:

- `Required` varsayılan olarak `false` isteğe bağlı bir özniteliktir. `true`, parametresi zorunludur ve görev çağrılmadan önce bir değer verilmelidir.

- `ParameterType` varsayılan olarak `System.String` isteğe bağlı bir özniteliktir. System. Convert. ChangeType kullanarak bir öğe ya da bir dizeden dönüştürülebilen bir değer olan herhangi bir tamamen nitelenmiş türe ayarlanabilir. (Başka bir deyişle, bir dış görevden ve bu bilgisayardan geçirilebilecek herhangi bir tür.)

- `Output` varsayılan olarak `false` isteğe bağlı bir özniteliktir. `true`, Execute yönteminden dönmeden önce parametreye bir değer verilmelidir.

Örneğin,

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

Şu üç parametreyi tanımlar:

- `Expression`, System. String türünde gerekli bir giriş parametresidir.

- `Files`, gerekli bir öğe listesi giriş parametresidir.

- `Tally`, System. Int32 türünde bir çıkış parametresidir.

`Code` öğesinde `Fragment` veya `Method``Type` özniteliği varsa, özellikler her parametre için otomatik olarak oluşturulur. Aksi halde, özellikler, görev kaynak kodunda açıkça bildirilmelidir ve parametre tanımlarıyla tam olarak eşleşmesi gerekir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [İzlenecek yol: satır içi görev oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)
