---
title: Görev yazma | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631846"
---
# <a name="task-writing"></a>Görev yazma

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevler, hedefler ' de yer alır. Tipik görevler kitaplığı MSBuild 'e dahildir ve ayrıca kendi görevlerinizi de oluşturabilirsiniz. MSBuild 'e dahil edilen görevlerin Kitaplığı hakkında daha fazla bilgi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Görevler

 Görev örnekleri, bir veya daha fazla dosyayı kopyalayan, bir dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve kaynak kodu dosyalarını derleyen C# [CSC](../msbuild/csc-task.md) ['yi içerir.](../msbuild/copy-task.md) Her görev, *Microsoft. Build. Framework. dll* derlemesinde tanımlanan <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan bir .NET sınıfı olarak uygulanır.

 Bir görevi uygularken kullanabileceğiniz iki yaklaşım vardır:

- <xref:Microsoft.Build.Framework.ITask> arabirimini doğrudan uygulayın.

- *Microsoft. Build. Utilities. dll* derlemesinde tanımlanan <xref:Microsoft.Build.Utilities.Task>yardımcı sınıfından sınıfınızı türetirsiniz. Görev ITask 'ı uygular ve bazı ITask üyelerinin varsayılan uygulamalarını sağlar. Ayrıca günlüğe kaydetme daha kolay.

Her iki durumda da, görev çalıştırıldığında çağrılan yöntemi olan `Execute`adlı bir yöntemi sınıfınıza eklemeniz gerekir. Bu yöntem hiçbir parametre alır ve `Boolean` bir değer döndürür: görev başarılı olduysa veya `false` `true`. Aşağıdaki örnek, hiçbir eylem gerçekleştirmeyen ve `true`döndüren bir görevi gösterir.

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

 Görevler çalıştırıldığında, görev sınıfında .NET özellikleri oluşturursanız proje dosyasından de giriş alabilir. MSBuild, bu özellikleri görevin `Execute` yöntemi çağrılmadan hemen önce ayarlar. Bir dize özelliği oluşturmak için, şöyle bir görev kodu kullanın:

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

 Aşağıdaki proje dosyası bu görevi çalıştırır ve `MyProperty` verilen değere ayarlar:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Görevleri Kaydet

 Bir proje bir görevi çalıştıracaksanız, MSBuild 'in görev sınıfını içeren derlemeyi nasıl bulacağınızı bilmelidir. Görevler [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)kullanılarak kaydedilir.

 MSBuild dosyası *Microsoft. Common. Tasks* , MSBuild ile sağlanan tüm görevleri kaydeden `UsingTask` öğelerinin listesini içeren bir proje dosyasıdır. Bu dosya, her proje oluşturulurken otomatik olarak eklenir. *Microsoft. Common. Tasks* ' de kayıtlı bir görev aynı zamanda geçerli proje dosyasında kayıtlıysa, geçerli proje dosyası önceliklidir; diğer bir deyişle, aynı ada sahip olan kendi görevinizdeki varsayılan görevi geçersiz kılabilirsiniz.

> [!TIP]
> *Microsoft. Common. görevlerinin*Içeriğini görüntüleyerek MSBuild ile sağlanan görevlerin bir listesini görebilirsiniz.

## <a name="raise-events-from-a-task"></a>Bir görevden olay oluştur

 Göreviniz <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfından türetilirse, kayıtlı Günlükçüler tarafından yakalanıp gösterilecek olayları yükseltmek için <xref:Microsoft.Build.Utilities.Task> sınıfında aşağıdaki yardımcı yöntemlerden herhangi birini kullanabilirsiniz:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Göreviniz doğrudan <xref:Microsoft.Build.Framework.ITask> uygularsa bu tür olayları yine de oluşturabilirsiniz, ancak IBuildEngine arabirimini kullanmanız gerekir. Aşağıdaki örnek, ITask uygulayan ve özel bir olay başlatan bir görevi gösterir:

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

 Belirli görev özelliklerini "gerekli" olarak işaretleyebilirsiniz. böylece, görevi çalıştıran herhangi bir proje dosyasının bu özelliklerin değerlerini ayarlaması gerekir, aksi durumda derleme başarısız olur. `[Required]` özniteliğini, görevdeki .NET özelliğine aşağıdaki şekilde uygulayın:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 `[Required]` özniteliği, <xref:Microsoft.Build.Framework> ad alanındaki <xref:Microsoft.Build.Framework.RequiredAttribute> tarafından tanımlanır.

## <a name="how-msbuild-invokes-a-task"></a>MSBuild bir görevi nasıl çağırır

Bir görevi çağırırken, MSBuild önce görev sınıfını örnekleyerek, ardından bu nesnenin proje dosyasındaki görev öğesinde ayarlanan görev parametreleri için özellik ayarlayıcıları ' nı çağırır. Görev öğesi bir parametre belirtmezse veya öğede belirtilen ifade boş bir dize olarak değerlendirilirse, Özellik ayarlayıcısı çağrılmaz.

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

yalnızca `Input3` ayarlayıcısı çağrılır.

Bir görev, parametre özelliği ayarlayıcısı çağrısının herhangi bir göreli sırasına bağlı olmamalıdır.

### <a name="task-parameter-types"></a>Görev parametresi türleri

MSBuild yerel olarak `string`, `bool`, `ITaskItem` ve `ITaskItem[]`türündeki özellikleri işler. Bir görev farklı türde bir parametreyi kabul ediyorsa, MSBuild, `string` (tüm özellik ve öğe başvuruları genişletilmiş) hedef türüne dönüştürmek için <xref:System.Convert.ChangeType%2A> çağırır. Herhangi bir giriş parametresi için dönüştürme başarısız olursa, MSBuild bir hata yayar ve görevin `Execute()` yöntemini çağırmaz.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki C# sınıf, <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfından türetilen bir görevi gösterir. Bu görev, başarılı olduğunu belirten `true`döndürür.

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

Aşağıdaki C# sınıf, <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan bir görevi gösterir. Bu görev, başarılı olduğunu belirten `true`döndürür.

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

Bu C# sınıf, <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfından türetilen bir görevi gösterir. Gerekli bir dize özelliğine sahiptir ve tüm kayıtlı Günlükçüler tarafından görüntülenen bir olay oluşturur.

### <a name="code"></a>Kod

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

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
