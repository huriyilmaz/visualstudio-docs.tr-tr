---
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
ms.openlocfilehash: 69ad4328d2ae94a23ebaa9fb4fd0aa0d2cff7c74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930010"
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
