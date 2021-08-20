---
title: Görev Yazma | Microsoft Docs
description: Derleme işlemi sırasında çalışan kodu sağlamak için kendi görevlerinizi nasıl MSBuild öğrenin.
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
ms.openlocfilehash: cb9d35c236210b9fa7eb1ceacfc5aa205b49ee70
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142734"
---
# <a name="task-writing"></a>Görev yazma

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevler hedeflerde yer almaktadır. Tipik görevlerin bir kitaplığı MSBuild ve kendi görevlerinizi de oluşturabilirsiniz. 'a dahil edilen görevlerin kitaplığı hakkında daha fazla bilgi MSBuild bkz. [Görev başvurusu.](../msbuild/msbuild-task-reference.md)

## <a name="tasks"></a>Görevler

 Görevlere örnek olarak [bir](../msbuild/copy-task.md)veya daha fazla dosya kopyalanan Copy , dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve C# kaynak kodu dosyalarını derleye [Csc](../msbuild/csc-task.md)yer almaktadır. Her görev,Microsoft.Build.Framework.dllderlemesinde tanımlanan arabirimini uygulayan <xref:Microsoft.Build.Framework.ITask> bir *.NET sınıfı olarak* uygulanır.

 Bir görevi uygulamak için kullanabileceğiniz iki yaklaşım vardır:

- Arabirimi doğrudan <xref:Microsoft.Build.Framework.ITask> uygulama.

- Sınıfını, derleme derlemesinde tanımlanan <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfından *Microsoft.Build.Utilities.dll* türetin. Görev, ITask'ı kullanır ve bazı ITask üyelerinin varsayılan uygulamalarını sağlar. Ayrıca, günlüğe kaydetme daha kolaydır.

Her iki durumda da, sınıfınıza görev çalıştır olduğunda çağrılan yöntem `Execute` olan adlı bir yöntem eklemeniz gerekir. Bu yöntem hiçbir parametre alır ve bir değer `Boolean` döndürür: `true` görev başarılı olursa veya `false` başarısız olursa. Aşağıdaki örnek, hiçbir eylem gerçekleştiren ve döndüren bir görevi `true` gösterir.

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

 Aşağıdaki proje dosyası bu görevi çalıştırır:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Görevler çalıştırıca, görev sınıfında .NET özellikleri sanız proje dosyasından da girişler alırlar. MSBuild, görevin yöntemini çağırmadan hemen önce bu özellikleri `Execute` ayarlar. Bir dize özelliği oluşturmak için, aşağıdaki gibi görev kodunu kullanın:

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

 Aşağıdaki proje dosyası bu görevi çalıştırır ve verilen `MyProperty` değere ayarlar:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Görevleri kaydetme

 Proje bir görevi çalıştıracaksa, MSBuild sınıfını içeren derlemenin nasıl bulun gerektiğini biliyor olması gerekir. Görevler [UsingTask öğesi (MSBuild) kullanılarak kaydedilir.](../msbuild/usingtask-element-msbuild.md)

 Microsoft.Common.Tasks MSBuild dosyası, *microsoft.common.tasks* ile sağlanan tüm görevleri kaydeden öğelerin listesini içeren `UsingTask` bir proje MSBuild. Bu dosya her proje oluşturulurken otomatik olarak eklenir. *Microsoft.Common.Tasks'a* kayıtlı bir görev de geçerli proje dosyasına kaydedilmişse, geçerli proje dosyası önceliklidir; Başka bir ifadeyle, aynı adı sahip kendi göreviniz ile varsayılan bir görevi geçersiz kılarak.

> [!TIP]
> *Microsoft.Common.Tasks* içeriğini görüntüerek MSBuild görevlerin listesini görüntüebilirsiniz.

## <a name="raise-events-from-a-task"></a>Bir görevden olay yükseltme

 Göreviniz yardımcı sınıfından türetilen, herhangi bir kayıtlı günlük kaydı tarafından yakalanacak ve görüntülenecek olayları yükseltmek için sınıfında aşağıdaki yardımcı yöntemlerden <xref:Microsoft.Build.Utilities.Task> <xref:Microsoft.Build.Utilities.Task> herhangi birini kullanabilirsiniz:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Göreviniz doğrudan <xref:Microsoft.Build.Framework.ITask> uygulanıyorsa bu tür olayları yine de yükseltebilirsiniz, ancak IBuildEngine arabirimini kullansanız gerekir. Aşağıdaki örnek, ITask uygulayan ve özel bir olay yükselten bir görevi gösterir:

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

## <a name="require-task-parameters-to-be-set"></a>Görev parametrelerinin ayarlanmış olması gerektir

 Görevi çalıştıran herhangi bir proje dosyasının bu özellikler için değerler ayarlaması veya derlemenin başarısız olması için belirli görev özelliklerini "gerekli" olarak işaretlebilirsiniz. özniteliğini `[Required]` görevinizin .NET özelliğine aşağıdaki gibi uygulama:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 özniteliği, `[Required]` ad alanı içinde tarafından <xref:Microsoft.Build.Framework.RequiredAttribute> <xref:Microsoft.Build.Framework> tanımlanır.

## <a name="how-msbuild-invokes-a-task"></a>MSBuild görev nasıl çağrılır?

Bir görev çağrılırken, MSBuild önce görev sınıfını oluşturur, ardından proje dosyasındaki görev öğesinde ayarlanmış görev parametreleri için bu nesnenin özellik ayarıcılarını çağırır. Görev öğesi bir parametre belirtmezseniz veya öğesinde belirtilen ifade boş bir dize olarak değerlendirilirse özellik ayarıcı çağrılır.

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

yalnızca için ayarıcı `Input3` çağrılır.

Bir görev, parametre-özellik ayarıcı çağırmanın herhangi bir göreli sırasına bağlı değildir.

### <a name="task-parameter-types"></a>Görev parametre türleri

Bu MSBuild , ve türüne sahip özellikleri `string` yerel `bool` olarak ele `ITaskItem` `ITaskItem[]` almaktadır. Bir görev farklı türde bir parametre kabul ederse, MSBuild (tüm özellik ve öğe başvuruları genişletilmiş olarak) hedef türüne dönüştürmek <xref:System.Convert.ChangeType%2A> `string` için çağrılır. Dönüştürme herhangi bir giriş parametresi için başarısız MSBuild bir hata yayır ve görevin yöntemini `Execute()` çağırmaz.

## <a name="example-1"></a>Örnek 1

### <a name="description"></a>Açıklama

Aşağıdaki C# sınıfı, yardımcı sınıftan türeten bir <xref:Microsoft.Build.Utilities.Task> görevi gösterir. Bu `true` görev, başarılı olduğunu belirten döndürür.

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

### <a name="description"></a>Açıklama

Aşağıdaki C# sınıfı arabirimi uygulayan bir görevi <xref:Microsoft.Build.Framework.ITask> gösterir. Bu `true` görev, başarılı olduğunu belirten döndürür.

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

### <a name="description"></a>Açıklama

Bu C# sınıfı, yardımcı sınıftan türeten <xref:Microsoft.Build.Utilities.Task> bir görevi gösterir. Gerekli bir dize özelliğine sahip ve tüm kayıtlı günlükçiler tarafından görüntülenen bir olay döndürür.

### <a name="code"></a>Kod

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs" id="Snippet1":::

## <a name="example-4"></a>Örnek 4

### <a name="description"></a>Açıklama

Aşağıdaki örnekte, önceki örnek görevi (SimpleTask3) iptal eden bir proje dosyası gösterir.

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
