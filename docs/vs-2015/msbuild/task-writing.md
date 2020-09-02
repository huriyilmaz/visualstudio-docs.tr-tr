---
title: Görev yazma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaf927b1049709a04d8a883615d1997e9316599e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802804"
---
# <a name="task-writing"></a>Görev Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Görevler, hedefler ' de yer alır. Tipik görevlerin bir kitaplığı ile birlikte dahildir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ve ayrıca kendi görevlerinizi de oluşturabilirsiniz. İçinde yer alan görevlerin Kitaplığı hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Görevler  
 Görev [örnekleri, bir](../msbuild/copy-task.md)veya daha fazla dosyayı kopyalayan, bir dizin oluşturan [MakeDir](../msbuild/makedir-task.md)ve kaynak kodu dosyalarını derleyen [CSC](../msbuild/csc-task.md)'yi içerir [!INCLUDE[csprcs](../includes/csprcs-md.md)] . Her görev, <xref:Microsoft.Build.Framework.ITask> Microsoft.Build.Framework.dll derlemesinde tanımlanan arabirimi uygulayan bir .NET sınıfı olarak uygulanır.  
  
 Bir görevi uygularken kullanabileceğiniz iki yaklaşım vardır:  
  
- <xref:Microsoft.Build.Framework.ITask>Arabirimi doğrudan uygulayın.  
  
- Microsoft.Build.Utilities.dll derlemesinde tanımlanan yardımcı sınıfından sınıfınızı türetirsiniz <xref:Microsoft.Build.Utilities.Task> . Görev ITask 'ı uygular ve bazı ITask üyelerinin varsayılan uygulamalarını sağlar. Ayrıca günlüğe kaydetme daha kolay.  
  
  Her iki durumda da, `Execute` görev çalıştırıldığında çağrılan yöntemi olan adlı bir yöntemi sınıfınıza eklemeniz gerekir. Bu yöntem hiçbir parametre alır ve bir `Boolean` değer döndürür: `true` görev başarılı olursa veya `false` başarısız olursa. Aşağıdaki örnek, hiçbir eylem ve dönüş gerçekleştirmeyen bir görevi gösterir `true` .  
  
```  
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
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Görevler çalıştırıldığında, görev sınıfında .NET özellikleri oluşturursanız proje dosyasından de giriş alabilir. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görevin metodunu çağırmadan önce bu özellikleri hemen ayarlar `Execute` . Bir dize özelliği oluşturmak için, şöyle bir görev kodu kullanın:  
  
```  
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
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Aşağıdaki proje dosyası bu görevi çalıştırır ve `MyProperty` belirtilen değere ayarlar:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Görevleri kaydetme  
 Bir proje bir görevi çalıştıracaksanız, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] görev sınıfını içeren derlemeyi bulmayı bilmelidir. Görevler [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md)kullanılarak kaydedilir.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Microsoft. Common. Tasks dosyası, `UsingTask` ile sağlanan tüm görevleri kaydeden öğelerin listesini içeren bir proje dosyasıdır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Bu dosya, her proje oluşturulurken otomatik olarak eklenir. Microsoft. Common. Tasks ' de kayıtlı bir görev aynı zamanda geçerli proje dosyasında kayıtlıysa, geçerli proje dosyası önceliklidir; diğer bir deyişle, aynı ada sahip olan kendi görevinizdeki varsayılan görevi geçersiz kılabilirsiniz.  
  
> [!TIP]
> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Microsoft. Common. görevlerinin içeriğini görüntüleyerek, ile sağlanan görevlerin bir listesini görebilirsiniz.  
  
## <a name="raising-events-from-a-task"></a>Bir görevden olayları oluşturma  
 Göreviniz <xref:Microsoft.Build.Utilities.Task> yardımcı sınıftan türetilirse, <xref:Microsoft.Build.Utilities.Task> Tüm kayıtlı Günlükçüler tarafından yakalanıp görüntülenecek olayları yükseltmek için sınıfında aşağıdaki yardımcı yöntemlerden herhangi birini kullanabilirsiniz:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Göreviniz doğrudan uygularsa <xref:Microsoft.Build.Framework.ITask> Bu tür olayları yine de oluşturabilirsiniz, ancak IBuildEngine arabirimini kullanmanız gerekir. Aşağıdaki örnek, ITask uygulayan ve özel bir olay başlatan bir görevi gösterir:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
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
  
## <a name="requiring-task-parameters-to-be-set"></a>Görev parametrelerinin ayarlanması gerekli  
 Belirli görev özelliklerini "gerekli" olarak işaretleyebilirsiniz. böylece, görevi çalıştıran herhangi bir proje dosyasının bu özelliklerin değerlerini ayarlaması gerekir, aksi durumda derleme başarısız olur. `[Required]`Aşağıdaki gibi, görev içindeki .net özelliğine özniteliğini uygulayın:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]`Özniteliği, <xref:Microsoft.Build.Framework.RequiredAttribute> <xref:Microsoft.Build.Framework> ad alanında tarafından tanımlanır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki [!INCLUDE[csprcs](../includes/csprcs-md.md)] sınıf, yardımcı sınıfından türetilen bir görevi gösterir <xref:Microsoft.Build.Utilities.Task> . Bu görev `true` , başarılı olduğunu belirten döndürür.  
  
### <a name="code"></a>Kod  
  
```  
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
  
### <a name="description"></a>Description  
 Aşağıdaki [!INCLUDE[csprcs](../includes/csprcs-md.md)] sınıf, arabirimini uygulayan bir görevi gösterir <xref:Microsoft.Build.Framework.ITask> . Bu görev `true` , başarılı olduğunu belirten döndürür.  
  
### <a name="code"></a>Kod  
  
```  
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
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Bu [!INCLUDE[csprcs](../includes/csprcs-md.md)] sınıf, yardımcı sınıfından türetilen bir görevi gösterir <xref:Microsoft.Build.Utilities.Task> . Gerekli bir dize özelliğine sahiptir ve tüm kayıtlı Günlükçüler tarafından görüntülenen bir olay oluşturur.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Description  
 Aşağıdaki örnek, SimpleTask3 önceki örnek görevi çağıran bir proje dosyası gösterir.  
  
### <a name="code"></a>Kod  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
