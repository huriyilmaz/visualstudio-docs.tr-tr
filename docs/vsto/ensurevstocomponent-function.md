---
title: EnsureVSTOComponent işlevi
description: EnsureVSTOComponent API'sini Office ve doğrudan kodunuzdan kullanılmaya yönelik olmadığını öğrenin.
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
ms.openlocfilehash: c7de049c7388d71078dae1d4a14a1427b78c4cc5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026453"
---
# <a name="ensurevstocomponent-function"></a>EnsureVSTOComponent işlevi
  Bu API, Office altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yöneliktir.

## <a name="syntax"></a>Sözdizimi

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*pProject*|kullanma.|

## <a name="return-value"></a>Döndürülen değer
 İşlev başarılı olursa, işlevi **S_OK.** İşlev başarısız olursa bir hata kodu döndürür.
