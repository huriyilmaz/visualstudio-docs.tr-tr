---
title: Görevi Kopyala | Microsoft Docs
description: dosya sistemindeki yeni bir dosya veya klasör konumuna dosya kopyalamak için MSBuild kopyalama görevini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 3b57372fd69e8c8076a19a3904454ac623cbedb7
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886455"
---
# <a name="copy-task"></a>Kopyalama görevi

Dosyaları, dosya sisteminde yeni bir konuma kopyalar.

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini `Copy` açıklar.

|Parametre|Açıklama|
|---------------|-----------------|
|`CopiedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Gerçekten kopyalanmamış, ancak zaten güncel olduğundan atlandığı için `SkipUnchangedFiles` `true` *, başarıyla* kopyalanan öğeleri içerir.|
|`DestinationFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Kaynak dosyaların kopyalanacağı dosyaların listesini belirtir. Bu listenin, `SourceFiles` parametresinde belirtilen liste ile bire bir eşlenir olması beklenir. Yani, `SourceFiles` içinde belirtilen ilk dosya `DestinationFiles` içinde belirtilen ilk konuma kopyalanır ve böyle devam eder.|
|`DestinationFolder`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Dosyaları kopyalamak istediğiniz dizini belirtir. Bu, bir dosya değil, bir dizin olmalıdır. Eğer dizin yoksa otomatik olarak oluşturulur.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Salt okunur dosyalar olarak işaretlenmiş olsa bile dosyaların üzerine yaz|
|`Retries`|İsteğe bağlı `Int32` parametre.<br /><br /> Eğer önceki tüm denemeler başarısız olursa, kopyalamanın kaç kere deneneceğini belirtir. Varsayılan olarak sıfırdır.<br /><br /> **Dikkat:** Yeniden denemeler kullanımı, yapı sürecinizdeki bir eşitleme sorununu maskeleyebilir.<br /><br /> **Note:** *Görev* varsayılanı sıfır yeniden deneme olsa da, varsayılan olarak sıfır dışı olan görev genellikle geçişi `$(CopyRetryCount)` kullanır.|
|`RetryDelayMilliseconds`|İsteğe bağlı `Int32` parametre.<br /><br /> Gerekli yeniden denemeler arasındaki gecikmeyi belirtir. Varsayılan olarak, CopyTask oluşturucusuna geçirilen RetryDelayMillisecondsDefault değerini kullanır.|
|`SkipUnchangedFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` ise, kaynak ve hedef arasında değişmeyen dosyaların kopyalanmasını atlar. `Copy` görevi, dosyalar aynı boyuta ve aynı son değiştirme tarihine sahipse bu dosyaları değişmemiş kabul eder. <br /><br /> **Note:**  Bu parametreyi ' a ayarlarsanız,, yalnızca kaynak dosyaların son değiştirilme zamanları hedef dosyaların son değiştirilme zamanından daha yeniyse görevi çalıştırdığı için `true` , kapsayan hedefte bağımlılık analizini kullanmamalısınız.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Kopyalanacak dosyaları belirtir.|
|`UseHardlinksIfPossible`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true` ise, dosyaları kopyalamak yerine kopyalanan dosyalar için Sabit Bağlantılar oluşturur.|

## <a name="warnings"></a>Uyarılar

Aşağıdakiler dahil olmak üzere uyarılar günlüğe kaydedilir:

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

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan <xref:Microsoft.Build.Utilities.Task> parametreleri <xref:Microsoft.Build.Tasks.TaskExtension> devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, öğe koleksiyonundaki öğeleri `MySourceFiles` *C:\myproject\destination* klasörüne kopyalar.

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

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek, yinelemeli bir kopyalamanın nasıl gerçekleştirileceğini gösterir. Bu proje, dizin yapısını koruyarak tüm dosyaları özyinelemeli olarak *C:\mysourcetree* 'den *c:\mydestinationtree* içine kopyalar.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CopyFiles">
        <ItemGroup>
            <!-- Because this ItemGroup is inside the target, this will enumerate
                 all files just before calling Copy. If the ItemGroup were outside
                 the target , it would enumerate the files during evaluation, before
                 the build starts, which may miss files created during the build. -->
            <MySourceFiles Include="c:\MySourceTree\**\*.*"/>
        </ItemGroup>

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
