---
title: RoslynCodeTaskFactory ile MSBuild Satır İçi Görevler | Microsoft Dokümanlar
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
ms.openlocfilehash: 658302de187d6bbeab67dedaaa816709f00436ed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865381"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory ile MSBuild satır içinde görevler

[CodeTaskFactory'ye](../msbuild/msbuild-inline-tasks.md)benzer şekilde, RoslynCodeTaskFactory, satır içi görevler olarak kullanılmak üzere bellek içi görev derlemeleri oluşturmak için çapraz platform Roslyn derleyicilerini kullanır.  RoslynCodeTaskFactory görevleri .NET Standard'ı hedef eder ve .NET Framework ve .NET Core çalışma saatlerini ve Linux ve Mac OS gibi diğer platformlarda çalışabilir.

>[!NOTE]
>RoslynCodeTaskFactory yalnızca MSBuild 15.8 ve üzeri olarak mevcuttur. MSBuild sürümleri Visual Studio sürümlerini takip, bu nedenle RoslynCodeTaskFactory Visual Studio 15.8 ve daha yüksek mevcuttur.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory ile satır içinde görevyapısı

 RoslynCodeTaskFactory satır altı görevleri [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md)ile aynı şekilde bildirilir, tek fark .NET Standard'ı hedeflemeleridir.  Satır satır görev `UsingTask` ve bunu içeren öğe genellikle bir *.targets* dosyasına dahil edilir ve gerektiğinde diğer proje dosyalarına aktarılır. Burada temel bir satır ara görevidir. Hiçbir şey etmediğine dikkat edin.

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

 Örnekteki öğe, `UsingTask` görevi açıklayan üç öznitelik ve onu derleyen satır içinde görev fabrikası vardır.

- Öznitelik, `TaskName` bu durumda görevi `DoNothing`adlandırır.

- Öznitelik, `TaskFactory` satır içinde görev fabrikasını uygulayan sınıfı adlandırır.

- Öznitelik `AssemblyFile` satır içinde görev fabrikasının konumunu verir. Alternatif olarak, genellikle `AssemblyName` genel montaj önbelleğinde (GAC) bulunan satır altı görev fabrikası sınıfının tam nitelikli adını belirtmek için özniteliği kullanabilirsiniz.

`DoNothing` Görevin kalan öğeleri boştur ve satır içinde görevin sırasını ve yapısını göstermek için sağlanır. Daha sağlam bir örnek daha sonra bu konuda sunulmaktadır.

- Öğe `ParameterGroup` isteğe bağlıdır. Belirtildiğinde, görev için parametreleri bildirir. Giriş ve çıktı parametreleri hakkında daha fazla bilgi için, bu konuda daha sonra [Giriş ve Çıkış Parametreleri'ne](#input-and-output-parameters) bakın.

- Öğe, `Task` görev kaynak kodunu açıklar ve içerir.

- Öğe, `Reference` kodunuzda kullanmakta olduğunuz .NET derlemelerine yapılan başvuruları belirtir. Bu, Visual Studio'daki bir projeye başvuru eklemeye eşdeğerdir. Öznitelik, `Include` başvurulan derlemenin yolunu belirtir.

- Öğe, `Using` erişmek istediğiniz ad alanlarını listeler. Bu, Visual `Using` C#'daki ifadeye benzer. Öznitelik, `Namespace` ad alanını içerecek şekilde belirtir.

`Reference`ve `Using` elementler dil-agnostiktir. Satır çizgisi görevler, desteklenen .NET CodeDom dillerinden herhangi birine(örneğin, Visual Basic veya Visual C#) yazılabilir.

> [!NOTE]
> Öğenin `Task` içerdiği öğeler görev fabrikasına, bu durumda kod görev fabrikasına özgüdir.

### <a name="code-element"></a>Kod öğesi

`Task` Öğe içinde görünen son alt öğe `Code` öğedir. Öğe, `Code` bir göreve derlemek istediğiniz kodu içerir veya bulur. Öğeye `Code` ne koyduğunuz, görevi nasıl yazmak istediğinize bağlıdır.

Öznitelik, `Language` kodunuzun yazıldığı dili belirtir. Kabul edilebilir `cs` değerler C#, `vb` Visual Basic içindir.

`Code` Öznitelik, `Type` öğede bulunan kod türünü belirtir.

- Değeri `Type` `Class`ise, `Code` öğe <xref:Microsoft.Build.Framework.ITask> arabirimden türetilen bir sınıfın kodunu içerir.

- Değeri `Type` `Method`ise, kod `Execute` <xref:Microsoft.Build.Framework.ITask> arabirimin yönteminin geçersiz kılınan tanımlar.

- Değeri `Type` `Fragment`ise, kod `Execute` yöntemin içeriğini tanımlar, ancak imza veya `return` deyim ihtir.

Kodun kendisi genellikle bir `<![CDATA[` işaretçi `]]>` ve bir işaretçi arasında görünür. Kod bir CDATA bölümünde olduğundan, ayrılmış karakterlerden kaçma konusunda endişelenmenize gerek yoktur, örneğin " "\<veya ">".

Alternatif olarak, görevinizin kodunu `Code` içeren bir dosyanın konumunu belirtmek için öğenin özniteliğini kullanabilirsiniz. `Source` Kaynak dosyadaki kod öznitelik tarafından `Type` belirtilen türde olmalıdır. `Source` Öznitelik varsa, varsayılan `Type` `Class`değeri. `Source` Yoksa, varsayılan `Fragment`değer.

> [!NOTE]
> Kaynak dosyadaki görev sınıfını tanımlarken, sınıf adının `TaskName` ilgili [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesinin özniteliğiyle aynı fikirde olması gerekir.

## <a name="hello-world"></a>Hello World

 Burada RoslynCodeTaskFactory ile daha sağlam bir satır altı görevdir. HelloWorld görev görüntüler "Merhaba, dünya!" genellikle sistem konsolu veya Visual Studio **Çıkış** penceresi olan varsayılan hata günlüğe kaydetme aygıtında. Örnekteki `Reference` öğe sadece illüstrasyon için dahildir.

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

HelloWorld görevini *HelloWorld.targets*adlı bir dosyaya kaydedebilir ve ardından aşağıdaki gibi bir projeden çağırabilirsiniz.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Giriş ve çıkış parametreleri

 Satır satır görev parametreleri `ParameterGroup` bir öğenin alt öğeleridir. Her parametre, onu tanımlayan öğenin adını alır. Aşağıdaki kod parametreyi `Text`tanımlar.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametreler bu özniteliklerden birine veya birkaçına sahip olabilir:

- `Required`varsayılan olarak isteğe `false` bağlı bir özniteliktir. Eğer `true`, sonra parametre gereklidir ve görevi aramadan önce bir değer verilmelidir.

- `ParameterType`varsayılan olarak isteğe `System.String` bağlı bir özniteliktir. System.Convert.ChangeType kullanılarak bir öğeye veya bir dizeye dönüştürülebilen bir değer olan tam nitelikli herhangi bir türe ayarlanabilir. (Başka bir deyişle, harici bir göreve ve dış görevden geçirilebilen herhangi bir tür.)

- `Output`varsayılan olarak isteğe `false` bağlı bir özniteliktir. If `true`, sonra parametre Yürüt metodundan dönmeden önce bir değer verilmelidir.

Örneğin,

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

bu üç parametreyi tanımlar:

- `Expression`System.String türünden gerekli bir giriş parametresitir.

- `Files`gerekli madde listesi giriş parametresidir.

- `Tally`System.Int32 tipinin bir çıkış parametresidir.

`Code` Öğe özniteliği `Type` varsa `Fragment` veya `Method`, sonra özellikleri otomatik olarak her parametre için oluşturulur.  RoslynCodeTaskFactory'de, `Code` `Type` öğe, kaynak kodundan çıkarılan (bu `ParameterGroup`bir fark) olduğu için, öğenin `CodeTaskFactory` `Class`özniteliği varsa, kaynak kodundan çıkarılan öğeyi belirtmeniz gerekmez. Aksi takdirde, özellikler görev kaynak kodunda açıkça belirtilmelidir ve parametre tanımlarıyla tam olarak eşleşmelidir.

## <a name="example"></a>Örnek

 Aşağıdaki satır başı görev bazı iletileri günlüğe kaydeder ve bir dize döndürür.

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

Bu satır satır görevleri yolları birleştirebilir ve dosya adını alabilir.

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
- [Walkthrough: Satır içinde görev oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)
