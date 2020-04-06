---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728605"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Bir dizi nesnesi oluşturur. Bu dizi ilkel veya nesne örnek değerleri içerebilir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`ot`\
[içinde] Yeni dizi nesnesinin türünü gösteren [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) numaralandırmadan bir değer belirtir.

`pClassField`\
[içinde] Nesne örneği değerleri dizisi oluşturuyorsa, nesnenin sınıfını temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi. İlkel nesneler dizisi oluşturuyorsanız, bu parametre null değeridir.

`dwRank`\
[içinde] Dizinin boyutlarının sıralaması veya sayısı.

`dwDims`\
[içinde] Dizinin her boyutunun boyutları.

`dwLowBounds`\
[içinde] Her boyutun kökeni (genellikle 0 veya 1).

`ppObject`\
[çıkış] Yeni oluşturulan diziyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi döndürür. Bu aslında bir [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) nesnesidir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi tarafından temsil edilen işleviçin bir dizi parametresini temsil eden bir nesne oluşturmak için bu yöntemi çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
