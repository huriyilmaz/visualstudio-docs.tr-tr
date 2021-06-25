---
description: Bu işlev, bir grup kaynak denetimi işlemini son olarak verir.
title: SccEndBatch İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ff596f19d3a98b929f9346bbf579e0ad1258c5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904597"
---
# <a name="sccendbatch-function"></a>SccEndBatch işlevi
Bu işlev, bir grup kaynak denetimi işlemini son olarak verir. Bu toplu işler iç içe geçmiş olabilir.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Toplu işlem başarıyla sonuçlandı.|
|SCC_E_UNKNOWNERROR|Belirtilmeyen hata.|

## <a name="remarks"></a>Açıklamalar
 Kaynak denetimi toplu işleri, birden çok proje veya birden çok bağlam üzerinde aynı kaynak denetimi işlemlerini yürütmek için kullanılır. Toplu işlem sırasında kullanıcı deneyiminden yedekli iletişim kutularını ortadan kaldırmak için toplu işler kullanılabilir. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) ve işlevi, bir işlem başlangıcını ve sonunu `SccEndBatch` göstermek için çift olarak kullanılır. Bunlar iç içe olamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
