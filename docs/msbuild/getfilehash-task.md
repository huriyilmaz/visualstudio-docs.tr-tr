---
title: GetFileHash görevi | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8f3de9a4f2fe848e1cbd41e14e82498845ca2cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77578655"
---
# <a name="getfilehash-task"></a>GetFileHash görevi

Bir dosyanın veya dosya kümesinin içeriklerinin sağlama toplamlarını hesaplar.

Bu görev 15,8 ' ye eklenmiştir, ancak 16,0 ' nin altındaki MSBuild sürümleri için kullanmak üzere [geçici bir çözüm](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) gerektirir.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tablo, görevin parametrelerini açıklar `GetFileHash` .

|Parametre|Açıklama|
|---------------|-----------------|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br />Karma hale getirilen dosyalar.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br />`Files`Dosya karması olarak ayarlanan ek meta verileri içeren giriş.|
|`Hash`|`String` çıkış parametresi.<br /><br />Dosyanın karması. Bu çıktı yalnızca tam olarak bir öğe geçirilirse ayarlanır.|
|`Algorithm`|İsteğe bağlı `String` parametre.<br /><br />Algoritma. İzin verilen değerler: `SHA256` , `SHA384` , `SHA512` . Varsayılan = `SHA256` .|
|`MetadataName`|İsteğe bağlı `String` parametre.<br /><br />Her öğede karma 'in depolandığı meta veri adı. Varsayılan olarak olur `FileHash` .|
|`HashEncoding`|İsteğe bağlı `String` parametre.<br /><br />Oluşturulan karmaları için kullanılacak kodlama. Varsayılan olarak olur `hex` . İzin verilen değerler = `hex` , `base64` .|

## <a name="example"></a>Örnek

Aşağıdaki örnek, `GetFileHash` öğelerin sağlama toplamını belirlemede ve yazdırmak için görevini kullanır `FilesToHash` .

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)