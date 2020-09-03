---
title: Görevi Sil | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eddb9804378a4c32de9d1b68f952bc715f32ffd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288916"
---
# <a name="delete-task"></a>Silme görevi

Belirtilen dosyaları siler.

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini açıklar `Delete` .

|Parametre|Açıklama|
|---------------|-----------------|
|`DeletedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Başarıyla silinen dosyaları belirtir.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Silinecek dosyaları belirtir.|
|`TreatErrorsAsWarnings`|İsteğe bağlı `Boolean` parametre<br /><br /> Varsa `true` , hatalar uyarı olarak günlüğe kaydedilir. Varsayılan değer: `false`.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Görevle joker karakter kullanırken dikkatli olun `Delete` . Ya da gibi ifadelerle yanlış dosyaları kolayca silebilirsiniz, `$(SomeProperty)\**\*.*` özellikle de `$(SomeProperty)/**/*.*` özellik boş bir dize olarak değerlendirilir, bu durumda `Files` parametre sürücünüzün köküne değerlendirilemiyor ve silmek istediğiniz kadar fazlasını silebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hedefi oluştururken *MyApp. pdb* dosyasını siler `DeleteDebugSymbolFile` .

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

Silinen dosyaları izlemeniz gerekiyorsa, `TaskParameter` `DeletedFiles` öğe adı ile olarak öğesini aşağıdaki gibi ayarlayın:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Görevde doğrudan joker karakter kullanmak yerine `Delete` , silinecek bir dosya oluşturun `ItemGroup` ve `Delete` Bu görevi çalıştırın. Ancak dikkatlice yerleştirdiğinizden emin olun `ItemGroup` . Bir `ItemGroup` proje dosyasına en üst düzeye yerleştirirseniz, derleme başlamadan önce, derleme işleminin bir parçası olarak oluşturulmuş herhangi bir dosya dahil değildir. Bu nedenle, `ItemGroup` bir hedef için göreve yakın bir şekilde silinecek öğelerin listesini oluşturan öğesini koyun `Delete` . Ayrıca, özelliğin boş olmadığını denetlemek için bir koşul belirtebilir ve bu sayede, sürücünün kökünde başlayan bir yol ile bir öğe listesi oluşturmayacağız.

`Delete`Görev, dosyaları silmeye yöneliktir. Bir dizini silmek istiyorsanız [RemoveDir](removedir-task.md)öğesini kullanın.

`Delete`Görev salt okunurdur dosyaları silmeye yönelik bir seçenek sağlamaz. Salt okuma dosyalarını silmek için, bu `Exec` görevi, `del` salt okuma dosyalarını silmeyi etkinleştirmek üzere uygun seçenekle komutu veya eşdeğerini çalıştırmak için kullanabilirsiniz. Komut satırında bir uzunluk sınırlaması olduğundan ve bu örnekte olduğu gibi boşluklar içeren dosya adlarını işlediğinizden emin olmak için, giriş öğesi listesinin uzunluğuna dikkat etmeniz gerekir:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Genel olarak, derleme betikleri yazarken, silmenin bir işlemin mantıksal olarak bir parçası olup olmadığını göz önünde bulundurun `Clean` . Bazı dosyaları normal bir işlemin bir parçası olarak temizlenecek şekilde ayarlamanız gerekiyorsa `Clean` , bunları `@(FileWrites)` listeye ekleyebilirsiniz ve bunlar bir sonraki adımda silinir `Clean` . Daha fazla özel işleme gerekliyse, bir hedef tanımlayın ve özniteliği `BeforeTargets="Clean"` ya da `AfterTargets="Clean"` ya da hedeflerinin özel sürümünüzü tanımlayarak çalıştırmak için belirtin `BeforeClean` `AfterClean` . Bkz. [yapınızı özelleştirme](customize-your-build.md).

## <a name="see-also"></a>Ayrıca bkz.

- [RemoveDir görevi](removedir-task.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
