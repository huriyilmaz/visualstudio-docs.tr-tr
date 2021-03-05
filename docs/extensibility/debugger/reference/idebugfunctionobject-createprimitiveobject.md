---
description: Basit bir tamsayı gibi temel bir veri nesnesi oluşturur.
title: 'IDebugFunctionObject:: CreatePrimitiveObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eed6bf305667b98e16f4a112b1196456269e5b3c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165547"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Basit bir tamsayı gibi temel bir veri nesnesi oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`ot`\
'ndaki Oluşturulacak temel türünü temsil eden [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) numaralandırmasından bir değer.

`ppObject`\
dışı Yeni oluşturulan nesneyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi tarafından temsil edilen işlevin parametresi olan bir temel nesneyi temsil eden bir nesne oluşturmak için bu yöntemi çağırın. Örneğin, ifade dizesi "myString (5)" ise, bu yöntem, 5 tamsayısını temsil eden bir nesne oluşturmak için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
