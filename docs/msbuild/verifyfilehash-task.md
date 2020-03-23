---
title: VerifyFileHash Görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53819a642edcdf0419dd445ac32dbde8d14ffb22
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579528"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash görev

Bir dosyanın beklenen dosya karmaile eşleştiğini doğrular. Karma eşleşmiyorsa, görev başarısız olur.

Bu görev 15.8'de eklendi, ancak 16.0'ın altındaki MSBuild sürümleri için kullanmak için geçici [bir geçici çözüm](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) gerektirir.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevparametreleri `VerifyFileHash` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli `String` parametre.<br /><br />Dosya nın işlenebilir ve doğrulanması gerekir.|
|`Hash`|Gerekli `String` parametre.<br /><br />Dosyanın beklenen karma.|
|`Algorithm`|İsteğe bağlı `String` parametre.<br /><br />Algoritma. İzin verilen `SHA256` `SHA384`değerler: , , `SHA512`. Varsayılan `SHA256`= .|
|`HashEncoding`|İsteğe bağlı `String` parametre.<br /><br />Oluşturulan hashes için kullanılacak kodlama. Varsayılan `hex`değer. İzin verilen `hex` `base64`değerler = , .|

## <a name="example"></a>Örnek

Aşağıdaki örnek, `VerifyFileHash` görevi kendi checksum doğrulamak için kullanır.

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

MSBuild 16.5 ve sonraki zamanlarda, karma eşleşmiyorsa yapının başarısız olmasını istemiyorsanız (örneğin, karma karşılaştırmayı denetim akışı için bir koşul olarak kullanıyorsanız), uyarıyı aşağıdaki kodu kullanarak bir iletiye indirebilirsiniz:

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
