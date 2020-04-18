---
title: MSBuild Satır İçi Görevler | Microsoft Dokümanlar
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
ms.openlocfilehash: ab46aef69bd6356eda0925c492a029b43cc57295
ms.sourcegitcommit: 98421670ed0b8170aaa32d3d6f8681298f401a1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2020
ms.locfileid: "81638039"
---
# <a name="msbuild-inline-tasks"></a>MSBuild satır dışı görevler

MSBuild görevleri genellikle <xref:Microsoft.Build.Framework.ITask> arabirimi uygulayan bir sınıf derleyerek oluşturulur. Daha fazla bilgi için [Görevler'e](../msbuild/msbuild-tasks.md)bakın.

 .NET Framework sürüm 4'ten başlayarak, proje dosyasında satır satırgörev oluşturabilirsiniz. Görevi barındırmak için ayrı bir derleme oluşturmanız gerekmez. Bu, kaynak kodunu izlemeyi ve görevi dağıtmayı kolaylaştırır. Kaynak kodu komut dosyasına entegre edilmiştir.

 MSBuild 15.8'de,.NET Standart çapraz platform satır içi görevler oluşturabilen [RoslynCodeTaskFactory](../msbuild/msbuild-roslyncodetaskfactory.md) eklendi.  .NET Core'da satır satır görevlerini kullanmanız gerekiyorsa, RoslynCodeTaskFactory'yi kullanmanız gerekir.
## <a name="the-structure-of-an-inline-task"></a>Satır çizgisi görevin yapısı

 Satır çizgisi görev, [UsingTask](../msbuild/usingtask-element-msbuild.md) öğesi tarafından bulunur. Satır satır görev `UsingTask` ve bunu içeren öğe genellikle bir *.targets* dosyasına dahil edilir ve gerektiğinde diğer proje dosyalarına aktarılır. Burada temel bir satır ara görevidir. Hiçbir şey etmediğine dikkat edin.

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

 Örnekteki öğe, `UsingTask` görevi açıklayan üç öznitelik ve onu derleyen satır içinde görev fabrikası vardır.

- Öznitelik, `TaskName` bu durumda görevi `DoNothing`adlandırır.

- Öznitelik, `TaskFactory` satır içinde görev fabrikasını uygulayan sınıfı adlandırır.

- Öznitelik `AssemblyFile` satır içinde görev fabrikasının konumunu verir. Alternatif olarak, genellikle `AssemblyName` 'de `$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll`bulunan satır altı görev fabrikası sınıfının tam nitelikli adını belirtmek için özniteliği kullanabilirsiniz.

`DoNothing` Görevin kalan öğeleri boştur ve satır içinde görevin sırasını ve yapısını göstermek için sağlanır. Daha sağlam bir örnek daha sonra bu konuda sunulmaktadır.

- Öğe `ParameterGroup` isteğe bağlıdır. Belirtildiğinde, görev için parametreleri bildirir. Giriş ve çıktı parametreleri hakkında daha fazla bilgi için, daha sonra bu konuda [giriş ve çıkış parametrelerine](#input-and-output-parameters) bakın.

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

## <a name="helloworld"></a>Helloworld

 Burada daha sağlam bir satır altı görevdir. HelloWorld görev görüntüler "Merhaba, dünya!" genellikle sistem konsolu veya Visual Studio **Çıkış** penceresi olan varsayılan hata günlüğe kaydetme aygıtında. Örnekteki `Reference` öğe sadece illüstrasyon için dahildir.

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

`Code` Öğe özniteliği `Type` varsa `Fragment` veya `Method`, sonra özellikleri otomatik olarak her parametre için oluşturulur. Aksi takdirde, özellikler görev kaynak kodunda açıkça belirtilmelidir ve parametre tanımlarıyla tam olarak eşleşmelidir.

## <a name="example"></a>Örnek

 Aşağıdaki satır satır görevi, verilen dosyadaki bir belirteç oluşumunun her oluşumunu verilen değerle değiştirir.

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
- [Walkthrough: Satır içinde görev oluşturma](../msbuild/walkthrough-creating-an-inline-task.md)
