---
title: 'Idebugciltçi:: GetFunctionObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7128c97c60b5743ea9759a9449b82e4e909a686
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939038"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Bu yöntem, işlev parametreleri oluşturmak için kullanılan bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parametreler
`ppFunction`\
dışı İşlev parametreleri oluşturmak için kullanılan [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
