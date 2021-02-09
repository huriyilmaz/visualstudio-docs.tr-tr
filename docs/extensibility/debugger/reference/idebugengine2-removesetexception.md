---
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29756b3be6d2c46d39b581dd3db0af61bfaa18f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878935"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Belirtilen özel durumu, artık hata ayıklama altyapısı tarafından işlenmemesi için kaldırır.

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
'ndaki Kaldırılacak özel durumu açıklayan [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaldırılmakta olan özel durum daha önce [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) metoduna daha önceki bir çağrı tarafından ayarlanmış olmalıdır.

 Tüm set özel durumlarını tek seferde kaldırmak için [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
