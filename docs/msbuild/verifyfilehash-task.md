---
title: VerifyFileHash görevi | Microsoft Docs
description: MSBuild 'in, bir dosyanın beklenen dosya karması ile eşleşip eşleşmediğini doğrulamak için VerifyFileHash görevini nasıl kullandığını öğrenin ve eşleşmezse başarısız olur.
ms.custom: SEO-VS-2020
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfd6bb88a5bfbbffb7c99f7f43036cf9fee4d6ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908799"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash görevi

Bir dosyanın beklenen dosya karmasıyla eşleştiğini doğrular. Karma eşleşmezse, görev başarısız olur.

Bu görev 15,8 ' ye eklenmiştir, ancak 16,0 ' nin altındaki MSBuild sürümleri için kullanmak üzere [geçici bir çözüm](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) gerektirir.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tablo, görevin parametrelerini açıklar `VerifyFileHash` .

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli `String` parametre.<br /><br />Karma hale getirilen ve doğrulanacak dosya.|
|`Hash`|Gerekli `String` parametre.<br /><br />Dosyanın beklenen karması.|
|`Algorithm`|İsteğe bağlı `String` parametre.<br /><br />Algoritma. İzin verilen değerler: `SHA256` , `SHA384` , `SHA512` . Varsayılan = `SHA256` .|
|`HashEncoding`|İsteğe bağlı `String` parametre.<br /><br />Oluşturulan karmaları için kullanılacak kodlama. Varsayılan olarak olur `hex` . İzin verilen değerler = `hex` , `base64` .|

## <a name="example"></a>Örnek

Aşağıdaki örnek, `VerifyFileHash` kendi sağlama toplamını doğrulamak için görevini kullanır.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

MSBuild 16,5 ve üzeri sürümlerde, karma ile eşleşmediği zaman, denetim akışı için bir koşul olarak karma karşılaştırma kullanıyorsanız, aşağıdaki kodu kullanarak uyarının bir iletiye indirgenmesini sağlayabilirsiniz:

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
