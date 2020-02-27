---
title: RegisterAssembly görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c95606a00e86ffd187162e444f2c710c5cc3a0e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632894"
---
# <a name="registerassembly-task"></a>RegisterAssembly görevi

Belirtilen derleme içindeki meta verileri okur ve gerekli girdileri kayıt defterine ekler ve bu da COM istemcilerinin saydam olarak .NET Framework sınıfları oluşturmalarına olanak tanır. Bu görevin davranışı, [Regasm. exe (derleme kayıt aracı)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)ile benzerdir, ancak aynı değildir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `RegisterAssembly` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> COM 'a kaydedilecek derlemeleri belirtir.|
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> `RegisterAssembly` görevi ve [UnregisterAssembly](../msbuild/unregisterassembly-task.md) görevi arasındaki durum hakkında bilgi içerir. Bu bilgiler `UnregisterAssembly` görevin, `RegisterAssembly` görevinde kaydettirilemedi bir derlemenin kaydını silmeye çalışmasını engeller.|
|`CreateCodeBase`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, kayıt defterinde, genel derleme önbelleğinde yüklü olmayan bir derlemenin dosya yolunu belirten bir kod temeli girişi oluşturur. Sonrasında genel derleme önbelleğine kaydettiriyor olduğunuz derlemeyi yükleyecekseniz bu seçeneği belirtmemelisiniz.|
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Belirtilen derlemeden oluşturulacak tür kitaplığını belirtir. Oluşturulan tür kitaplığı, derleme içinde tanımlanan erişilebilir türlerin tanımlarını içerir. Tür kitaplığı yalnızca aşağıdaki koşullardan biri doğru olduğunda üretilir:<br /><br /> -Bu ada sahip bir tür kitaplığı bu konumda yok.<br />-Bir tür kitaplığı var, ancak geçirilen derlemeden daha eski.<br /><br /> Tür kitaplığı geçilen derlemeden daha yeniyse, yeni bir tane oluşturulmaz, ancak derleme yine de kaydedilir.<br /><br /> Bu parametre belirtilmişse, `Assemblies` parametresi ile aynı sayıda öğe olması gerekir, aksi takdirde görev başarısız olur. Hiçbir giriş belirtilmemişse, görev varsayılan olarak derlemenin adı olur ve öğenin uzantısını *. tlb*olarak değiştirir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `MyAssemblies` öğesi koleksiyonu tarafından belirtilen derlemeyi kaydetmek için `RegisterAssembly` görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyAssemblies Include="MyAssembly.dll" />
    <ItemGroup>

    <Target Name="RegisterAssemblies">
        <RegisterAssembly
            Assemblies="@(MyAssemblies)" >
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
