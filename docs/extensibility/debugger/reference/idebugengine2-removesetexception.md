---
description: Belirtilen özel durumu kaldırır, böylece artık hata ayıklama altyapısı tarafından işilmez.
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27987f582606f1978c90ff09f36c6e75714040ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111222"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Belirtilen özel durumu kaldırır, böylece artık hata ayıklama altyapısı tarafından işilmez.

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
[in] [Kaldırılacak EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) açıklayan bir özel durum yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaldırılan özel durum daha önce [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) yöntemine yapılan önceki bir çağrı tarafından ayarlanmış olması gerekir.

 Tüm küme özel durumlarını aynı anda kaldırmak için [RemoveAllSetExceptions yöntemini](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) çağırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
