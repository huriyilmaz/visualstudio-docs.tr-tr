---
title: GetValidCompatibleFramework işlevi
description: getvalidcompatibleframework apı 'sinin Office altyapısını nasıl desteklediğini öğrenin ve doğrudan kodunuzdan kullanılmaya yönelik değildir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c97b2fae371fd5bd72860595ba5117786b7db808
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148252"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework işlevi
  bu apı Office altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|Kullanmayın.|
|*pbstrValidFrameworkTag*|Kullanmayın.|

## <a name="return-value"></a>Döndürülen değer
 İşlev başarılı olursa, **S_OK** döndürür. İşlev başarısız olursa, bir hata kodu döndürür.
