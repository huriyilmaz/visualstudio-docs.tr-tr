---
description: IDE'nin belirli bir çalışma zamanı mimarisi veya dili için ayarlayş olduğu özel durumların listesini kaldırır.
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 231bb94681311956e300c312dd971bf8d6e7d07b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079161"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
IDE'nin belirli bir çalışma zamanı mimarisi veya dili için ayarlayş olduğu özel durumların listesini kaldırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>Parametreler
`guidType`\
[in] Dil için GUID veya bir çalışma zamanı mimarisine özgü hata ayıklama altyapısı için GUID.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından kaldırılan özel durumlar, [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) yöntemine yapılan önceki çağrılar tarafından ayarlanmıştır.

 Belirli bir özel durumu kaldırmak için [RemoveSetException yöntemini](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) çağırmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
