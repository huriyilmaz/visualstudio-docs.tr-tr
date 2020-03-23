---
title: Görev Yazma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cbcf47ec83e1b900ba94ab3842c2cfa63fdcc5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631846"
---
# <a name="task-writing"></a>Görev yazma

Görevler, yapı işlemi sırasında çalışan kodu sağlar. Görevler hedeflerde bulunur. Tipik görevler kitaplığı MSBuild ile birlikte verilir ve kendi görevlerinizi de oluşturabilirsiniz. MSBuild ile birlikte verilen görevler kitaplığı hakkında daha fazla bilgi için [Görev başvurusuna](../msbuild/msbuild-task-reference.md)bakın.

## <a name="tasks"></a>Görevler

 Görevlere örnek olarak, bir veya daha fazla dosyayı kopyalayan [Kopya,](../msbuild/copy-task.md)dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve C# kaynak kod dosyalarını derleyen [Csc](../msbuild/csc-task.md)verilebilir. Her görev, *Microsoft.Build.Framework.dll* <xref:Microsoft.Build.Framework.ITask> derlemesinde tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır.

 Bir görevi uygularken kullanabileceğiniz iki yaklaşım vardır:

- Arayüzü <xref:Microsoft.Build.Framework.ITask> doğrudan uygulayın.

- *Microsoft.Build.Utilities.dll* <xref:Microsoft.Build.Utilities.Task>derlemesinde tanımlanan yardımcı sınıftan sınıfınızı türetin. Görev ITask uygular ve bazı ITask üyelerinin varsayılan uygulamalarını sağlar. Ayrıca, günlüğe kaydetme daha kolaydır.

Her iki durumda da, görev çalıştığında `Execute`çağrılan yöntem olan sınıfına adlı bir yöntem eklemeniz gerekir. Bu yöntem hiçbir parametre `Boolean` almaz `true` ve bir değer `false` döndürür: görev başarılı ysa veya başarısız olduysa. Aşağıdaki örnekte, hiçbir eylem gerçekleştirmeden `true`ve döndüren bir görev gösterilmektedir.

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

 Görevler çalıştırıldığında, görev sınıfında .NET özellikleri oluşturursanız proje dosyasından da giriş alabilirler. MSBuild, görev `Execute` yöntemini çağırmadan hemen önce bu özellikleri ayarlar. Bir dize özelliği oluşturmak için, görev kodunu kullanın:

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

 Aşağıdaki proje dosyası bu görevi `MyProperty` çalıştırır ve verilen değere ayarlar:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Görevleri kaydetme

 Bir proje bir görevi çalıştıracaksa, MSBuild görev sınıfını içeren derlemeyi nasıl bulacağını bilmelidir. Görevler [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)kullanılarak kaydedilir.

 MSBuild dosyası *Microsoft.Common.Tasks,* MSBuild ile birlikte `UsingTask` verilen tüm görevleri kaydeden öğelerin listesini içeren bir proje dosyasıdır. Bu dosya, her projeyi kurarken otomatik olarak dahil edilir. *Microsoft.Common.Tasks'de* kayıtlı bir görev de geçerli proje dosyasında kayıtlıysa, geçerli proje dosyası önceliklidir; diğer bir diğer adıyla, aynı ada sahip kendi görevinizle varsayılan bir görevi geçersiz kılabilirsiniz.

> [!TIP]
> *Microsoft.Common.Tasks'in*içeriğini görüntüleyerek MSBuild ile birlikte verilen görevlerin listesini görebilirsiniz.

## <a name="raise-events-from-a-task"></a>Görevden olayları yükseltme

 Göreviniz <xref:Microsoft.Build.Utilities.Task> yardımcı sınıftan geliyorsa, herhangi bir kayıtlı kaydedici tarafından yakalanacak ve görüntülenecek olayları yükseltmek için <xref:Microsoft.Build.Utilities.Task> sınıftaki aşağıdaki yardımcı yöntemlerden birini kullanabilirsiniz:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Göreviniz doğrudan <xref:Microsoft.Build.Framework.ITask> uygulanıyorsa, bu tür olayları yine de yükseltebilirsiniz, ancak IBuildEngine arabirimini kullanmanız gerekir. Aşağıdaki örnek, ITask'ı uygulayan ve özel bir olay yükselten bir görev gösterir:

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

## <a name="require-task-parameters-to-be-set"></a>Görev parametrelerinin ayarlanmasını zorunlu kılmasını gerektirin

 Görevi çalıştıran herhangi bir proje dosyasının bu özellikler için değerler ayarlaması veya yapının başarısız olması için belirli görev özelliklerini "gerekli" olarak işaretleyebilirsiniz. Görevinizdeki `[Required]` .NET özelliğine özniteliği aşağıdaki gibi uygulayın:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Öznitelik `[Required]` <xref:Microsoft.Build.Framework> ad alanında <xref:Microsoft.Build.Framework.RequiredAttribute> tanımlanır.

## <a name="how-msbuild-invokes-a-task"></a>MSBuild bir görevi nasıl çağırır?

Bir görevi çağırırken, MSBuild önce görev sınıfını anında ayarlar, ardından proje dosyasındaki görev öğesinde ayarlanan görev parametreleri için bu nesnenin özellik ayarlayıcılarını çağırır. Görev öğesi bir parametre belirtmezse veya öğede belirtilen ifade boş bir dize için değerlendirirse, özellik ayarlayıcısı çağrılmaz.

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

yalnızca ayarlayıcı `Input3` denir.

Bir görev parametre-özellik ayarlayıcı çağırma herhangi bir göreli sıraya bağlı olmamalıdır.

### <a name="task-parameter-types"></a>Görev parametresi türleri

MSBuild `string`yerel olarak türü , `bool` `ITaskItem` ve `ITaskItem[]`. Bir görev farklı bir türdeki bir parametreyi <xref:System.Convert.ChangeType%2A> kabul ederse, MSBuild (tüm özellik ve madde başvuruları genişletildiğinde) hedef türüne dönüştürmeyi `string` çağırır. Dönüştürme herhangi bir giriş parametresi için başarısız olursa, MSBuild bir hata `Execute()` yayan ve görevin yöntemini çağırmaz.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Bu aşağıdaki C# <xref:Microsoft.Build.Utilities.Task> sınıfı, yardımcı sınıftan kaynaklanan bir görev gösterir. Bu görev, başarılı olduğunu gösteren döndürür. `true`

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

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Bu aşağıdaki C# sınıfı <xref:Microsoft.Build.Framework.ITask> arabirimi uygulayan bir görev gösterir. Bu görev, başarılı olduğunu gösteren döndürür. `true`

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

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Bu C# <xref:Microsoft.Build.Utilities.Task> sınıfı, yardımcı sınıftan türeyen bir görevi gösterir. Gerekli bir dize özelliği vardır ve tüm kayıtlı kaydediciler tarafından görüntülenen bir olay yükseltir.

### <a name="code"></a>Kod

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnekte, önceki örnek görev olan SimpleTask3'ün çağıran bir proje dosyası gösterilmektedir.

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
