---
title: EnsureVSTOComponent işlevi
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
ms.openlocfilehash: cf55fc6669edd33d1b8896ee85f33ab2c04e844f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543591"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent işlevi
  Bu API, Office altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.

## <a name="syntax"></a>Söz dizimi

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*pProject*|Kullanmayın.|

## <a name="return-value"></a>Döndürülen değer
 İşlev başarılı olursa, **S_OK**döndürür. İşlev başarısız olursa, bir hata kodu döndürür.
