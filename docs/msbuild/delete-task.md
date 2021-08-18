---
title: Görev Yöneticisini | Microsoft Docs
description: Belirtilen dosyaları silmek için MSBuild Sil görevini kullanmayla ilgili parametreler ve önemli noktalar hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 1a56c62a9696b881895d233bea89f8e04de78697
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077653"
---
# <a name="delete-task"></a>Silme görevi

Belirtilen dosyaları siler.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `Delete` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DeletedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Başarıyla silinen dosyaları belirtir.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Silinecek dosyaları belirtir.|
|`TreatErrorsAsWarnings`|İsteğe `Boolean` bağlı parametre<br /><br /> ise, `true` hatalar uyarı olarak günlüğe kaydedilir. `false` varsayılan değerdir.|

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

> [!WARNING]
> Görevle joker karakterler kullanırken dikkatli `Delete` olun. Veya gibi ifadeler içeren yanlış dosyaları, özellikle de özelliğin boş bir dize olarak değerlendirmesi durumunda kolayca silebilirsiniz. Bu durumda parametre, sürücü kökünü değerlendirebilir ve silmek istediğinizden çok daha `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*` fazlasını `Files` silebilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hedefi *derlemek için ConsoleApp1.pdb* dosyasını `DeleteDebugSymbolFile` siler.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Silinen dosyaları izlemenizi gerekirse öğe adıyla `TaskParameter` `DeletedFiles` aşağıdaki şekilde ayarlayın:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Görevde doğrudan joker karakterler kullanmak yerine, silmek ve bu görev üzerinde `Delete` çalıştırmak için bir dosya `ItemGroup` `Delete` oluşturun. Ancak, dikkatli bir şekilde yer `ItemGroup` edin. Bir proje dosyasına en üst düzeye bir koysanız, derleme başlamadan önce bu dosya erkenden değerlendirilir, bu nedenle derleme işleminin bir parçası olarak inşa edilen dosyaları `ItemGroup` içermez. Bu nedenle, `ItemGroup` silinecek öğe listesini oluşturan öğelerini göreve yakın bir hedefte `Delete` ekleyin. Ayrıca, özelliğin boş olup olmadığını kontrol etmek için bir koşul da belirtebilirsiniz; böylece sürücünün kökünde başlayan bir yol ile bir öğe listesi oluşturmaz.

Görev, `Delete` dosyaları silmek için tasarlanmıştır. Bir dizini silmek için [RemoveDir kullanın.](removedir-task.md)

Görev `Delete` salt okunur dosyaları silme seçeneği sağlamaz. Salt okunur dosyaları silmek için, salt okunur dosyaları silmeyi etkinleştirmek üzere uygun seçenekle komutunu veya `Exec` `del` eşdeğerini çalıştırmak üzere görevi kullanabilirsiniz. Komut satırı üzerinde bir uzunluk sınırlaması olduğundan ve bu örnekte olduğu gibi dosya adlarını boşluklarla işlemeyi unutmayın çünkü giriş öğesi listesinin uzunluğuna dikkat edin:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Genel olarak, derleme betikleri yazarken silme işleminin mantıksal olarak bir işlem parçası olup olmadığını göz önünde `Clean` bulundurabilirsiniz. Bazı dosyaların normal bir işlem kapsamında temizlenecek şekilde ayarlaması gerekirse, bunları listeye ekleyebilirsiniz ve sonraki 'de `Clean` `@(FileWrites)` `Clean` silinirler. Daha fazla özel işleme gerekirse, veya özniteliğini ayarlayarak bir hedef tanımlayın ve bunun çalışması için belirtin ya da ya da hedeflerinin özel `BeforeTargets="Clean"` `AfterTargets="Clean"` sürümünü `BeforeClean` `AfterClean` tanımlayın. Bkz. [Derlemenizi özelleştirme.](customize-your-build.md)

## <a name="see-also"></a>Ayrıca bkz.

- [RemoveDir görevi](removedir-task.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
