---
title: GetFileHash Görev | Microsoft Docs
description: Bir dosyanın veya dosya MSBuild sağlama toplamlarını hesaplamak için GetFileHash görevini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: dcd5bbeb94db4e75f11333149c075c6b204eed57
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085071"
---
# <a name="getfilehash-task"></a>GetFileHash görevi

Bir dosyanın veya dosya kümesi içeriğinin sağlama toplamlarını hesaplama.

Bu görev 15.8'de eklendi, [](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) ancak 16.0'ın altındaki sürümler için MSBuild geçici bir çözüm gerektirir.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevin parametreleri açık `GetFileHash` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br />Karmaya konu olacak dosyalar.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` output parametresi.<br /><br />Dosya `Files` karması olarak ayarlanmış ek meta veriye sahip giriş.|
|`Hash`|`String` output parametresi.<br /><br />Dosyanın karması. Bu çıkış yalnızca yalnızca geçirilen bir öğe varsa ayarlanır.|
|`Algorithm`|İsteğe `String` bağlı parametre.<br /><br />Algoritma. İzin verilen değerler: `SHA256` , `SHA384` , `SHA512` . Default = `SHA256` .|
|`MetadataName`|İsteğe `String` bağlı parametre.<br /><br />Karmanın her öğede depolandığı meta veri adı. Varsayılan olarak `FileHash` kullanılır.|
|`HashEncoding`|İsteğe `String` bağlı parametre.<br /><br />Oluşturulan karmalar için kullanılacak kodlama. Varsayılan olarak `hex` kullanılır. İzin verilen değerler = `hex` , `base64` .|

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğelerin `GetFileHash` sağlamalarını belirlemek ve yazdırmak için görevini `FilesToHash` kullanır.

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