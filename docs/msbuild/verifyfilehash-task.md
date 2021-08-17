---
title: VerifyFileHash Task | Microsoft Docs
description: Bir dosyanın MSBuild eş olmadığını ve eşleşmezse başarısız olduğunu doğrulamak için VerifyFileHash görevini nasıl kullandığını öğrenin.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e2680b9617f157aab3a3b96486e887842adc94a004994383f22d54751e2e55b2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334074"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash görevi

Bir dosyanın beklenen dosya karmasıyla eş olduğunu doğrular. Karma eşlemezse görev başarısız olur.

Bu görev 15.8'de eklendi, [](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) ancak 16.0'ın altındaki sürümler için MSBuild geçici bir çözüm gerektirir.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevin parametreleri açık `VerifyFileHash` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli `String` parametre.<br /><br />Karma ve doğrulanması gereken dosya.|
|`Hash`|Gerekli `String` parametre.<br /><br />Dosyanın beklenen karması.|
|`Algorithm`|İsteğe `String` bağlı parametre.<br /><br />Algoritma. İzin verilen değerler: `SHA256` , `SHA384` , `SHA512` . Default = `SHA256` .|
|`HashEncoding`|İsteğe `String` bağlı parametre.<br /><br />Oluşturulan karmalar için kullanılacak kodlama. Varsayılan olarak `hex` kullanılır. İzin verilen değerler = `hex` , `base64` .|

## <a name="example"></a>Örnek

Aşağıdaki örnek, kendi `VerifyFileHash` sağlamalarını doğrulamak için görevini kullanır.

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

MSBuild 16.5 ve sonraki bir sürümde, karma eşleşmezken derlemenin başarısız olması istemiyorsanız(örneğin, karma karşılaştırmayı denetim akışı için bir koşul olarak kullanıyorsanız, aşağıdaki kodu kullanarak uyarıyı iletiye düşürebilirsiniz):

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
