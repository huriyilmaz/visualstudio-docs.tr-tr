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
ms.openlocfilehash: a0e13e1ea1eda0e0768a1982b56bd7eeb496a1a2fc49ee9a2be64ad8e47dc0ea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424196"
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
