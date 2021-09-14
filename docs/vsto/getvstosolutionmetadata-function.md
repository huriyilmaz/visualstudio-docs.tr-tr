---
title: GetVstoSolutionMetadata işlevi
description: getvstosolutionmetadata apı 'sinin Office altyapısını nasıl desteklediğini öğrenin ve doğrudan kodunuzdan kullanılmaya yönelik değildir.
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
ms.openlocfilehash: 14cf1d9ab6c8c3a734caa737b99a5edaededb94f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725605"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata işlevi
  bu apı Office altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Kullanmayın.|
|*Ppsolutionınfo*|Kullanmayın.|

## <a name="return-value"></a>Döndürülen değer
 İşlev başarılı olursa, **S_OK** döndürür. İşlev başarısız olursa, bir hata kodu döndürür.
