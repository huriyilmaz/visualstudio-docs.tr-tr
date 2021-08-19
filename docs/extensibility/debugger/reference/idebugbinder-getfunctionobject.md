---
description: Bu yöntem, işlev parametrelerini oluşturmak için kullanılan bir IDebugFunctionObject nesnesini alır.
title: IDebugBinder::GetFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ecdff1d78326dd55f0b666b77611e3034e653014
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072830"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Bu yöntem, işlev [parametrelerini oluşturmak için kullanılan bir IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesini alır.

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
[out] İşlev [parametrelerini oluşturmak için kullanılan IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
