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
ms.openlocfilehash: 369584a815f671c8b7b4f8a99a5280626b493104
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595000"
---
# <a name="task-writing"></a>Görev yazma
Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevler, hedefler ' de yer alır. Tipik görevler kitaplığı [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]eklenmiştir ve kendi görevlerinizi de oluşturabilirsiniz. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]eklenen görevlerin Kitaplığı hakkında daha fazla bilgi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Görevler
 Görev örnekleri, bir veya daha fazla dosyayı kopyalayan, bir dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kaynak kodu dosyalarını derleyen [CSC](../msbuild/csc-task.md) ['yi içerir.](../msbuild/copy-task.md) Her görev, *Microsoft. Build. Framework. dll* derlemesinde tanımlanan <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan bir .NET sınıfı olarak uygulanır.

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

 Görevler çalıştırıldığında, görev sınıfında .NET özellikleri oluşturursanız proje dosyasından de giriş alabilir. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], görevin `Execute` metodunu çağırmadan önce bu özellikleri hemen ayarlar. Bir dize özelliği oluşturmak için, şöyle bir görev kodu kullanın:

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
 Bir proje bir görevi çalıştıracaksanız, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] görev sınıfını içeren derlemenin nasıl bulunacağını bilmelidir. Görevler [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)kullanılarak kaydedilir.

 *Microsoft. Common. Tasks* [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dosyası, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]ile sağlanan tüm görevleri kaydeden bir `UsingTask` öğelerinin listesini içeren bir proje dosyasıdır. Bu dosya, her proje oluşturulurken otomatik olarak eklenir. *Microsoft. Common. Tasks* ' de kayıtlı bir görev aynı zamanda geçerli proje dosyasında kayıtlıysa, geçerli proje dosyası önceliklidir; diğer bir deyişle, aynı ada sahip olan kendi görevinizdeki varsayılan görevi geçersiz kılabilirsiniz.

> [!TIP]
> *Microsoft. Common. görevlerinin*içeriğini görüntüleyerek [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sağlanan görevlerin bir listesini görebilirsiniz.

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

## <a name="how-includevstecmsbuildextensibilityinternalsincludesvstecmsbuild_mdmd-invokes-a-task"></a>[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bir görevi nasıl çağırır

Bir görevi çağırırken [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] önce görev sınıfını örnekleyerek, sonra proje dosyasındaki görev öğesinde ayarlanan görev parametreleri için o nesnenin özellik ayarlayıcıları ' nı çağırır. Görev öğesi bir parametre belirtmezse veya öğede belirtilen ifade boş bir dize olarak değerlendirilirse, Özellik ayarlayıcısı çağrılmaz.

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

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], `string`, `bool`, `ITaskItem` ve `ITaskItem[]`türündeki özellikleri yerel olarak işler. Bir görev farklı türde bir parametreyi kabul ederse [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], `string` (tüm özellik ve öğe başvuruları) hedef türüne dönüştürmek için <xref:System.Convert.ChangeType%2A> çağırır. Herhangi bir giriş parametresi için dönüştürme başarısız olursa, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bir hata yayar ve görevin `Execute()` yöntemini çağırmaz.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıfı, <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfından türetilen bir görevi gösterir. Bu görev, başarılı olduğunu belirten `true`döndürür.

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

Aşağıdaki [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıfı, <xref:Microsoft.Build.Framework.ITask> arabirimini uygulayan bir görevi gösterir. Bu görev, başarılı olduğunu belirten `true`döndürür.

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

Bu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıfı, <xref:Microsoft.Build.Utilities.Task> yardımcı sınıfından türetilen bir görevi gösterir. Gerekli bir dize özelliğine sahiptir ve tüm kayıtlı Günlükçüler tarafından görüntülenen bir olay oluşturur.

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
