---
title: 'IDebugEngine2:: RemoveAllSetExceptions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca4fbf706fb9172aea2ac7a1304f1643a0061dc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878961"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
IDE 'nin belirli bir çalışma zamanı mimarisi veya dili için ayarlamış olduğu özel durumların listesini kaldırır.

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
'ndaki Dil için GUID veya bir çalışma zamanı mimarisine özgü hata ayıklama altyapısının GUID 'SI.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından kaldırılan özel durumlar, daha önce [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) yöntemine yapılan çağrılar tarafından ayarlanmıştır.

 Belirli bir özel durumu kaldırmak için [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
