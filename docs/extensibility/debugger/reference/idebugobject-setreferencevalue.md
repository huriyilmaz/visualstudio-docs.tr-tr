---
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726369"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Bu nesnenin başvuru değerini ayarlar.

## <a name="syntax"></a>Söz dizimi

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
