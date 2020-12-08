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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 205bde9352e2a037b4a08108d8cfce3460034e66
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845043"
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
