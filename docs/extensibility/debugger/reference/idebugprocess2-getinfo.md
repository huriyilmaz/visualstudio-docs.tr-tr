---
title: IDebugProcess2::GetInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f437c1a15b136d08ea7e57987c346844044228c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724028"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Sürecin bir açıklamasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Parametreler
`Fields`\
[içinde] Parametrenin hangi alanlarının dolduruleceğini belirten PROCESS_INFO_FIELDS numaralandırma değerlerinin birleşimi. [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) `pProcessInfo`

`pProcessInfo`\
[çıkış] İşlemin açıklamasıyla doldurulmuş [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) bir yapı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
