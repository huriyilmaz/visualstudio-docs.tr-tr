---
title: RegisterAssembly Görev | Microsoft Docs
description: Belirli bir MSBuild içindeki meta verileri okumak ve kayıt defterine gerekli girişleri eklemek için RegisterAssembly görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: dbcac044afdfa7439947ed1b4d22e466cb58391a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136696"
---
# <a name="registerassembly-task"></a>RegisterAssembly görevi

Belirtilen derleme içindeki meta verileri okur ve gerekli girdileri kayıt defterine ekler. Bu, COM istemcilerinin saydam olarak .NET Framework oluşturmalarını sağlar. Bu görevin davranışı,Regasm.exe (Derleme Kaydı [ aracı) ile benzer](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)ancak aynı değildir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `RegisterAssembly` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Assemblies`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> COM'a kaydedılacak derlemeleri belirtir.|
|`AssemblyListFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Görev ile `RegisterAssembly` [UnregisterAssembly](../msbuild/unregisterassembly-task.md) görevi arasındaki durum hakkında bilgi içerir. Bu bilgiler, görevin göreve kaydedemeyen bir derlemenin kaydını `UnregisterAssembly` silenleri `RegisterAssembly` engellemesini sağlar.|
|`CreateCodeBase`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, kayıt defterinde, genel derleme önbelleğine yüklenmemiş bir derlemenin dosya yolunu belirten bir kod temeli `true` girdisi oluşturur. Sonrasında genel derleme önbelleğine kaydettiriyor olduğunuz derlemeyi yükleyecekseniz bu seçeneği belirtmemelisiniz.|
|`TypeLibFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Belirtilen derlemeden oluşturulacak tür kitaplığını belirtir. Oluşturulan tür kitaplığı, derleme içinde tanımlanan erişilebilir türlerin tanımlarını içerir. Tür kitaplığı yalnızca aşağıdaki koşullardan biri doğruysa oluşturulur:<br /><br /> - Bu adı alan bir tür kitaplığı o konumda yok.<br />- Bir tür kitaplığı var ancak geçirilen derlemeden daha eski.<br /><br /> Tür kitaplığı geçirilen derlemeden daha yeni ise, yeni bir tane oluşturulmaz, ancak derleme yine de kaydedilir.<br /><br /> Bu parametre belirtilirse, parametreyle aynı sayıda öğeye sahip olması `Assemblies` gerekir, yoksa görev başarısız olur. Hiçbir giriş belirtilmezse, görev varsayılan olarak derlemenin adını kullanır ve öğenin uzantısını *.tlb olarak değiştirir.*|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğe `RegisterAssembly` koleksiyonu tarafından belirtilen derlemeyi kaydetmek için görevini `MyAssemblies` kullanır.

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
