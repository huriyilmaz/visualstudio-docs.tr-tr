---
title: Görevi Kopyala | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fd0033f5ef6f83ca29432f95d6b635fcd36116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634376"
---
# <a name="copy-task"></a>Kopyalama görevi

Dosyaları, dosya sisteminde yeni bir konuma kopyalar.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevparametreleri `Copy` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`CopiedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Gerçekte kopyalanamayan, ancak zaten güncel oldukları ve `SkipUnchangedFiles` güncel oldukları için atlananlar *da dahil olmak üzere,* başarıyla kopyalanan öğeleri `true`içerir.|
|`DestinationFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Kaynak dosyaların kopyalanacağı dosyaların listesini belirtir. Bu listenin, `SourceFiles` parametresinde belirtilen liste ile bire bir eşlenir olması beklenir. Yani, `SourceFiles` içinde belirtilen ilk dosya `DestinationFiles` içinde belirtilen ilk konuma kopyalanır ve böyle devam eder.|
|`DestinationFolder`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Dosyaları kopyalamak istediğiniz dizini belirtir. Bu, bir dosya değil, bir dizin olmalıdır. Eğer dizin yoksa otomatik olarak oluşturulur.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Salt okunur dosyalar olarak işaretlenmiş olsa bile dosyaların üzerine yaz|
|`Retries`|İsteğe bağlı `Int32` parametre.<br /><br /> Eğer önceki tüm denemeler başarısız olursa, kopyalamanın kaç kere deneneceğini belirtir. Varsayılan olarak sıfırdır.<br /><br /> **Not:** Yeniden denemelerin kullanımı, yapı işleminizdeki bir eşitleme sorununu maskeleyebilir.|
|`RetryDelayMilliseconds`|İsteğe bağlı `Int32` parametre.<br /><br /> Gerekli yeniden denemeler arasındaki gecikmeyi belirtir. Varsayılan olarak, CopyTask oluşturucusuna geçirilen RetryDelayMillisecondsDefault değerini kullanır.|
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` ise, kaynak ve hedef arasında değişmeyen dosyaların kopyalanmasını atlar. `Copy` görevi, dosyalar aynı boyuta ve aynı son değiştirme tarihine sahipse bu dosyaları değişmemiş kabul eder. <br /><br /> **Not:**  Bu parametreyi `true`, içeren hedefte bağımlılık çözümlemesi kullanmamalısınız, çünkü bu yalnızca kaynak dosyaların son değiştirilen süreleri hedef dosyaların son değiştirilen saatlerinden daha yeniyse bu görevi çalıştırar.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Kopyalanacak dosyaları belirtir.|
|`UseHardlinksIfPossible`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` ise, dosyaları kopyalamak yerine kopyalanan dosyalar için Sabit Bağlantılar oluşturur.|

## <a name="warnings"></a>Uyarılar

Uyarılar, şunlardır:

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>Açıklamalar

`DestinationFolder` veya `DestinationFiles` parametresinin belirtilmesi gerekir, ancak ikisi birden belirtilmemelidir. Eğer her ikisi de belirtilirse görev başarısız olur ve bir hata günlüğe kaydedilir.

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğe koleksiyonundaki `MySourceFiles` öğeleri *c:\MyProject\Destination*klasörüne kopyalar.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFolder="c:\MyProject\Destination"
        />
    </Target>

</Project>
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, yinelemeli bir kopyalamanın nasıl gerçekleştirileceğini gösterir. Bu proje, dizin yapısını korurken tüm dosyaları *c:\MySourceTree'den* *c:\MyDestinationTree'ye*kopyalar.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
    </ItemGroup>

    <Target Name="CopyFiles">
        <Copy
            SourceFiles="@(MySourceFiles)"
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
