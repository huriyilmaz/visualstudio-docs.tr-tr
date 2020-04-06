---
title: IDebugModule2::GetInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c68c583702d7def5a7bff3ee40a9b8b2c537bb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726955"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Bu modül hakkında bilgi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
[içinde] [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) numaralandırmadan hangi alanların dolduruleceğini belirten bayrakların `pInfo` birleşimi.

`pInfo`\
[içinde, dışarı] Modülün açıklamasıyla doldurulmuş [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) bir yapı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısı **Modüller** penceresinde görüntülenen modülün adını içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
