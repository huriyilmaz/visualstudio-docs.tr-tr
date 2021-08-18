---
description: Bir dizi nesnesi oluşturur.
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 822a00dcfb4b4ba6a5b9739135ae756f92d2fe7437d8f9dcc8407fd17624a2fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417268"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Bir dizi nesnesi oluşturur. Bu dizi, ilkel ya da nesne örneği değerleri içerebilir.

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
'ndaki Yeni dizi nesnesinin türünü gösteren [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) numaralandırmasından bir değer belirtir.

`pClassField`\
'ndaki Nesne örneği değerlerinin dizisini oluşturmak için bir nesnenin sınıfını temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi. Temel nesnelerin bir dizisini oluşturuyorsanız, bu parametre null bir değerdir.

`dwRank`\
'ndaki Dizinin boyut derecesi veya sayısı.

`dwDims`\
'ndaki Dizinin her boyutunun boyutları.

`dwLowBounds`\
'ndaki Her boyutun kaynağı (genellikle 0 veya 1).

`ppObject`\
dışı Yeni oluşturulan diziyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnesi döndürür. Bu aslında bir [Ihata ayıklama Garrayobject](../../../extensibility/debugger/reference/idebugarrayobject.md) nesnesidir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi tarafından temsil edilen işleve bir dizi parametresini temsil eden bir nesne oluşturmak için bu yöntemi çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
