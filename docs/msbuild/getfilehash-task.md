---
title: GetFileHash Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77578655"
---
# <a name="getfilehash-task"></a>GetFileHash görev

Bir dosyanın veya dosya kümesinin içeriğinin denetimlerini hesaplar.

Bu görev 15.8'de eklendi, ancak 16.0'ın altındaki MSBuild sürümleri için kullanmak için geçici [bir geçici çözüm](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) gerektirir.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevparametreleri `GetFileHash` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br />Dosyalanacak.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]`çıkış parametresi.<br /><br />Dosya `Files` karmasına ek meta veri kümesi içeren giriş.|
|`Hash`|`String`çıkış parametresi.<br /><br />Dosyanın karma. Bu çıktı yalnızca tam olarak bir öğe geçtiyse ayarlanır.|
|`Algorithm`|İsteğe bağlı `String` parametre.<br /><br />Algoritma. İzin verilen `SHA256` `SHA384`değerler: , , `SHA512`. Varsayılan `SHA256`= .|
|`MetadataName`|İsteğe bağlı `String` parametre.<br /><br />Karmanın her öğede depolandığı meta veri adı. Varsayılan `FileHash`değer.|
|`HashEncoding`|İsteğe bağlı `String` parametre.<br /><br />Oluşturulan hashes için kullanılacak kodlama. Varsayılan `hex`değer. İzin verilen `hex` `base64`değerler = , .|

## <a name="example"></a>Örnek

Aşağıdaki `FilesToHash` örnekte, `GetFileHash` öğelerin denetim umlarını belirlemek ve yazdırmak için görev kullanır.

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