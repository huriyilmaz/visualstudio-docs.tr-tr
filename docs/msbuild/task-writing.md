---
title: Görev yazma | Microsoft Docs
description: MSBuild yapı işlemi sırasında çalışan kodu sağlamak için kendi görevlerinizi nasıl oluşturabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: da50fb9934439d309235a5230cf2e60fba08ad1d
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130211447"
---
# <a name="task-writing"></a>Görev yazma

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevler, hedefler ' de yer alır. tipik görevler kitaplığı MSBuild eklenmiştir ve kendi görevlerinizi de oluşturabilirsiniz. MSBuild eklenen görevlerin kitaplığı hakkında daha fazla bilgi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Görevler

 Görev örnekleri, bir veya daha fazla dosyayı kopyalayan, bir dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve C# kaynak kodu dosyalarını derleyen [CSC](../msbuild/csc-task.md) ['yi içerir.](../msbuild/copy-task.md) Her görev, <xref:Microsoft.Build.Framework.ITask> *Microsoft.Build.Framework.dll* derlemesinde tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır.

 Bir görevi uygularken kullanabileceğiniz iki yaklaşım vardır:

- <xref:Microsoft.Build.Framework.ITask>Arabirimi doğrudan uygulayın.

- <xref:Microsoft.Build.Utilities.Task> *Microsoft.Build.Utilities.dll* derlemesinde tanımlanan yardımcı sınıftan sınıfınızı türetirsiniz. Görev ITask 'ı uygular ve bazı ITask üyelerinin varsayılan uygulamalarını sağlar. Ayrıca günlüğe kaydetme daha kolay.

Her iki durumda da, `Execute` görev çalıştırıldığında çağrılan yöntemi olan adlı bir yöntemi sınıfınıza eklemeniz gerekir. Bu yöntem hiçbir parametre alır ve bir `Boolean` değer döndürür: `true` görev başarılı olursa veya `false` başarısız olursa. Aşağıdaki örnek, hiçbir eylem gerçekleştirmeyen ve başarıyla tamamlayan bir görevi gösterir (döndürür `true` ).

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 Şu proje dosyası bu görevi çalıştırır:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Görevler çalıştırıldığında, görev sınıfında .NET özellikleri oluşturursanız proje dosyasından de giriş alabilir. MSBuild, görevin metodunu çağırmadan önce bu özellikleri hemen ayarlar `Execute` . Bir dize özelliği oluşturmak için, şöyle bir görev kodu kullanın:

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 Aşağıdaki proje dosyası bu görevi çalıştırır ve `MyProperty` belirtilen değere ayarlar:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Görevleri Kaydet

 bir proje bir görevi çalıştıracaksanız, MSBuild görev sınıfını içeren derlemeyi bulmayı ve çalıştırmayı bilmelidir. Görevler [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)kullanılarak kaydedilir.

görevinde çalışma zamanına özgü bağımlılıklar varsa, bu görevin [, `Architecture` `Runtime` usingtask içinde ve/veya belirterek](../msbuild/configure-tasks.md)görevi belirli bir ortamda çalıştırması gerektiğini MSBuild bildirmeniz gerekir.

*Microsoft. Common. tasks* MSBuild dosyası, `UsingTask` [MSBuild birlikte sağlanan tüm görevleri](../msbuild/msbuild-task-reference.md)kaydeden öğelerin bir listesini içeren bir proje dosyasıdır. Bu dosya, herhangi bir proje oluşturulurken otomatik olarak eklenir. *Microsoft. Common. Tasks* ' de kayıtlı bir görev aynı zamanda geçerli proje dosyasında kayıtlıysa, geçerli proje dosyası önceliğe sahip olur, böylece, aynı ada sahip olan kendi göreviniz ile varsayılan bir görevi geçersiz kılabilirsiniz.

> [!TIP]
> *Microsoft. Common. görevlerinin* içeriğini görüntüleyerek MSBuild belirli bir sürümü ile sağlanan görevlerin bir listesini görebilirsiniz.

## <a name="raise-events-from-a-task"></a>Bir görevden olay oluştur

 Göreviniz <xref:Microsoft.Build.Utilities.Task> yardımcı sınıftan türetilirse, <xref:Microsoft.Build.Utilities.Task> Tüm kayıtlı Günlükçüler tarafından yakalanıp görüntülenecek olayları yükseltmek için sınıfında aşağıdaki yardımcı yöntemlerden herhangi birini kullanabilirsiniz:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Göreviniz doğrudan uygularsa <xref:Microsoft.Build.Framework.ITask> Bu tür olayları yine de oluşturabilirsiniz, ancak IBuildEngine arabirimini kullanmanız gerekir. Aşağıdaki örnek, ITask uygulayan ve özel bir olay başlatan bir görevi gösterir:

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>Görev parametrelerinin ayarlanması gerekiyor

 Belirli görev özelliklerini "gerekli" olarak işaretleyebilirsiniz. böylece, görevi çalıştıran herhangi bir proje dosyasının bu özelliklerin değerlerini ayarlaması gerekir, aksi durumda derleme başarısız olur. `[Required]`Aşağıdaki gibi, görev içindeki .net özelliğine özniteliğini uygulayın:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 `[Required]`Özniteliği, <xref:Microsoft.Build.Framework.RequiredAttribute> <xref:Microsoft.Build.Framework> ad alanında tarafından tanımlanır.

## <a name="how-msbuild-invokes-a-task"></a>MSBuild bir görevi nasıl çağırır

bir görevi çağırırken MSBuild önce görev sınıfını örnekleyerek, sonra proje dosyasındaki görev öğesinde ayarlanan görev parametreleri için o nesnenin özellik ayarlayıcıları ' nı çağırır. Görev öğesi bir parametre belirtmezse veya öğede belirtilen ifade boş bir dize olarak değerlendirilirse, Özellik ayarlayıcısı çağrılmaz.

Örneğin, projede

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

yalnızca için ayarlayıcı `Input3` çağırılır.

Bir görev, parametre özelliği ayarlayıcısı çağrısının herhangi bir göreli sırasına bağlı olmamalıdır.

### <a name="task-parameter-types"></a>Görev parametresi türleri

MSBuild,, ve türündeki özellikleri yerel olarak işler `string` `bool` `ITaskItem` `ITaskItem[]` . bir görev farklı türde bir parametreyi kabul ederse, MSBuild <xref:System.Convert.ChangeType%2A> dönüştürme için çağırır `string` (tüm özellik ve öğe başvuruları ile) hedef türüne. herhangi bir giriş parametresi için dönüştürme başarısız olursa, MSBuild bir hata yayar ve görevin metodunu çağırmaz `Execute()` .

## <a name="example-1"></a>Örnek 1

### <a name="description"></a>Description

Aşağıdaki C# sınıfı, yardımcı sınıfından türetilen bir görevi gösterir <xref:Microsoft.Build.Utilities.Task> . Bu görev `true` , başarılı olduğunu belirten döndürür.

### <a name="code"></a>Kod

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-2"></a>Örnek 2

### <a name="description"></a>Description

Aşağıdaki C# sınıfı, arabirimini uygulayan bir görevi gösterir <xref:Microsoft.Build.Framework.ITask> . Bu görev `true` , başarılı olduğunu belirten döndürür.

### <a name="code"></a>Kod

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-3"></a>Örnek 3

### <a name="description"></a>Description

Bu C# sınıfı, yardımcı sınıftan türetilen bir görevi gösterir <xref:Microsoft.Build.Utilities.Task> . Gerekli bir dize özelliğine sahiptir ve tüm kayıtlı Günlükçüler tarafından görüntülenen bir olay oluşturur.

### <a name="code"></a>Kod

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs" id="Snippet1":::

## <a name="example-4"></a>Örnek 4

### <a name="description"></a>Description

Aşağıdaki örnek, SimpleTask3 önceki örnek görevi çağıran bir proje dosyası gösterir.

### <a name="code"></a>Kod

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
