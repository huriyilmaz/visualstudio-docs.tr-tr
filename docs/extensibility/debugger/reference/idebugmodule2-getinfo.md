---
description: Bu modülle ilgili bilgileri alır.
title: 'IDebugModule2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69286a7bf50c32aa3aa720deff78ee957f53fc65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065664"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Bu modülle ilgili bilgileri alır.

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
'ndaki [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi `pInfo` .

`pInfo`\
[in, out] Modülün açıklamasıyla doldurulmuş [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısı, **modüller** penceresinde görüntülenen modülün adını içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
