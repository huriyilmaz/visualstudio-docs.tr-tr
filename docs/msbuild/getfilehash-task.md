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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578655"
---
# <a name="getfilehash-task"></a>GetFileHash görevi

Bir dosyanın veya dosya kümesinin içeriklerinin sağlama toplamlarını hesaplar.

Bu görev 15,8 ' ye eklenmiştir, ancak 16,0 ' nin altındaki MSBuild sürümleri için kullanmak üzere [geçici bir çözüm](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) gerektirir.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda `GetFileHash` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br />Karma hale getirilen dosyalar.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br />Dosya karması olarak ayarlanan ek meta verileri içeren `Files` girişi.|
|`Hash`|`String` çıktı parametresi.<br /><br />Dosyanın karması. Bu çıktı yalnızca tam olarak bir öğe geçirilirse ayarlanır.|
|`Algorithm`|İsteğe bağlı `String` parametresi.<br /><br />Algoritma. İzin verilen değerler: `SHA256`, `SHA384`, `SHA512`. Varsayılan = `SHA256`.|
|`MetadataName`|İsteğe bağlı `String` parametresi.<br /><br />Her öğede karma 'in depolandığı meta veri adı. `FileHash` değerini varsayılan olarak alır.|
|`HashEncoding`|İsteğe bağlı `String` parametresi.<br /><br />Oluşturulan karmaları için kullanılacak kodlama. `hex` değerini varsayılan olarak alır. İzin verilen değerler = `hex`, `base64`.|

## <a name="example"></a>Örnek

Aşağıdaki örnek, `FilesToHash` öğelerinin sağlama toplamını öğrenmek ve yazdırmak için `GetFileHash` görevini kullanır.

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