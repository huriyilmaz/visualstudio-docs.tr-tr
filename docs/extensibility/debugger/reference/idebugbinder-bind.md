---
description: Bu yöntem, simgenin geçerli değerini içeren bellek bağlamını veya nesnesini alır.
title: 'Idebugciltçi:: bind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: de3cbb35245fad317014136177a4a410edfb25b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104397"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Bu yöntem, simgenin geçerli değerini içeren bellek bağlamını veya nesnesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`pContainer`\
'ndaki Tarafından başvurulan alt öğe içeren [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) `pField` .

`pField`\
'ndaki Simgeyi temsil eden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

`ppObject`\
dışı `IDebugObject` Simgenin örneğini temsil eden öğesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
