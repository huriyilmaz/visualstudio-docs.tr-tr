---
title: IDebugFunctionObject::CreateObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728603"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Bir oluşturucu kullanarak bir nesne oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parametreler
`pConstructor`\
[içinde] Oluşturulacak nesnenin oluşturucuunu temsil eden bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi.

`dwArgs`\
[içinde] Dizideki `pArg` parametrelerin sayısı. Oluşturucuya geçirilen parametrelerin sayısını gösterir.

`pArg`\
[içinde] Oluşturucuya geçirilen parametreleri temsil eden [bir iDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesne dizisi.

`ppObject`\
[çıkış] Yeni `IDebugObject` oluşturulan nesneyi temsil eden bir nesne döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi tarafından temsil edilen işlevin parametresi olan bir sınıfın örneğini (veya kurucu gerektiren diğer karmaşık türü) temsil eden bir nesne oluşturmak için bu yöntemi çağırın.

 Nesne parametresi bir oluşturucu gerektirmiyorsa, [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
