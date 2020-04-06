---
title: IDebugEngine2::RemoveSetException | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e811ce2e387c299ff3655799bf35185c1d2029b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730929"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Hata ayıklama altyapısı tarafından artık işlenmeyecek şekilde belirtilen özel durumu kaldırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametreler
`pException`\
[içinde] Kaldırılacak özel durumu açıklayan [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) bir yapı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaldırılan özel [durum, SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) yöntemine daha önce yapılan bir çağrı yla ayarlanmış olmalıdır.

 Tüm özel durumları aynı anda kaldırmak için [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
