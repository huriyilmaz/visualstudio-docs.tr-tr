---
title: GetVstoSolutionMetadata işlevi
description: GetVstoSolutionMetadata API 'sinin Office altyapısını nasıl desteklediğini öğrenin ve doğrudan kodunuzdan kullanılmaya yönelik değildir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: eaf58f312afd379fb1f16d208c323777ec725231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860613"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata işlevi
  Bu API, Office altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.

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
