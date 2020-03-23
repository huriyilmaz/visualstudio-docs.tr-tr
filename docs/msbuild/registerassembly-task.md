---
title: RegisterAssembly Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632894"
---
# <a name="registerassembly-task"></a>RegisterAssembly görevi

Belirtilen derlemeiçindeki meta verileri okur ve kayıt defterine gerekli girişleri ekler, bu da COM istemcilerinin .NET Framework sınıflarını saydam olarak oluşturmasını sağlar. Bu görevin [davranışı, Regasm.exe (Montaj Kayıt aracı)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)ile aynı, ancak aynı değildir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `RegisterAssembly` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> COM'a kaydedilecek derlemeleri belirtir.|
|`AssemblyListFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Görev ve [Kayıt Dışı Montaj](../msbuild/unregisterassembly-task.md) görevi arasındaki durum hakkında bilgi içerir. `RegisterAssembly` Bu bilgiler, `UnregisterAssembly` görevin göreve kaydolmayan `RegisterAssembly` bir derlemeyi silmeye çalışmasının önüne çıkar.|
|`CreateCodeBase`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`genel derleme önbelleğinde yüklü olmayan bir derleme için dosya yolunu belirten kayıt defterinde bir codebase girişi oluşturur. Sonrasında genel derleme önbelleğine kaydettiriyor olduğunuz derlemeyi yükleyecekseniz bu seçeneği belirtmemelisiniz.|
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Belirtilen derlemeden oluşturmak üzere tür kitaplığını belirtir. Oluşturulan tür kitaplığı, derlemeiçinde tanımlanan erişilebilir türlerin tanımlarını içerir. Tür kitaplığı yalnızca aşağıdaki koşullardan biri doğruysa oluşturulur:<br /><br /> - Bu konumda bu adı taşıyan bir tür kitaplığı yok.<br />- Bir tür kitaplığı var, ancak meclisten daha eski.<br /><br /> Tür kitaplığı meclisten daha yeniyse, yenisi oluşturulmaz, ancak derleme yine de kaydedilir.<br /><br /> Bu parametre belirtilirse, `Assemblies` parametreyle aynı sayıda öğeye sahip olması gerekir veya görev başarısız olur. Giriş belirtilmemişse, görev varsayılan olarak derlemenin adına gelecek ve öğenin *uzantısını .tlb*olarak değiştirecektir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `RegisterAssembly` `MyAssemblies` madde koleksiyonu tarafından belirtilen derlemeyi kaydetmek için görevi kullanır.

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
