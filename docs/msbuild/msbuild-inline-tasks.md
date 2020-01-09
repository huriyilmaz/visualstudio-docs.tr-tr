---
title: MSBuild satır Içi görevleri | Microsoft Docs
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
ms.openlocfilehash: 4f5f19d756d669a7b3e9e5d32a89c598c7edc9d3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593661"
---
# <a name="msbuild-inline-tasks"></a>MSBuild satır içi görevleri
MSBuild görevleri genellikle <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan bir sınıf derlenerek oluşturulur. Daha fazla bilgi için bkz. [Görevler](../msbuild/msbuild-tasks.md).

 .NET Framework sürüm 4 ' te başlayarak, proje dosyasında görevleri satır içinde oluşturabilirsiniz. Görevi barındırmak için ayrı bir derleme oluşturmanız gerekmez. Bu, kaynak kodu izlemeyi daha kolay hale getirir ve görevi dağıtmayı kolaylaştırır. Kaynak kodu betiğe tümleştirilir.

 MSBuild 15,8 ' de [Roslyncodetaskfactory](../msbuild/msbuild-roslyncodetaskfactory.md) , .NET Standard platformlar arası satır içi görevler oluşturabilecek şekilde eklenmiştir.  .NET Core 'da satır içi görevler kullanmanız gerekiyorsa, RoslynCodeTaskFactory ' yi kullanmanız gerekir.
## <a name="the-structure-of-an-inline-task"></a>Satır içi görevin yapısı
 Bir Inline görevi [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi tarafından içerilir. Satır içi görev ve onu içeren `UsingTask` öğesi, genellikle bir *. targets* dosyasına dahil edilir ve gerektiği şekilde diğer proje dosyalarına içeri aktarılır. Temel bir satır içi görev aşağıda verilmiştir. Hiçbir şey yapmediğine dikkat edin.

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

## <a name="helloworld"></a>HelloWorld
 Daha sağlam bir satır içi görev aşağıda verilmiştir. HelloWorld görevinde "Hello, World!" görüntülenir Varsayılan hata günlüğü cihazında, genellikle sistem konsolu veya Visual Studio **çıktı** penceresidir. Örnekteki `Reference` öğesi yalnızca çizim için dahil edilmiştir.

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
