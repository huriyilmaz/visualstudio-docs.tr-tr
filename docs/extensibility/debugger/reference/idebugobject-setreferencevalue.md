---
description: Bu nesnenin başvuru değerini ayarlar.
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71f1b02a48d14c01c0a28433be3d0321c2fe3855e045af839e384808be9e52a9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121451802"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Bu nesnenin başvuru değerini ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parametreler
`pObject`\
'ndaki Yeni başvuru değerini temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, bu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesini, parametrede verilen nesnenin değerine bir başvuru yapar `pObject` ve önceki tüm başvuruları yerine getirir. Bu `IDebugObject` nesnenin zaten bir başvuru türü olması gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
