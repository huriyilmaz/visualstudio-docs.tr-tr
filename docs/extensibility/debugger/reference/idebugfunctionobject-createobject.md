---
description: Oluşturucu kullanarak bir nesnesi oluşturur.
title: IDebugFunctionObject::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d5385aff3c0b50239192a95efcf4789cc2f0900c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088737"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Oluşturucu kullanarak bir nesnesi oluşturur.

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
[in] Oluşturulacak nesnenin oluşturucusu temsil eden [bir IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi.

`dwArgs`\
[in] Dizide parametre `pArg` sayısı. Oluşturucuya geçirilen parametre sayısını temsil eder.

`pArg`\
[in] Oluşturucuya geçirilen parametreleri temsil eden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri dizisi.

`ppObject`\
[out] Yeni oluşturulan `IDebugObject` nesneyi temsil eden bir döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi tarafından temsil edilen işleve yönelik bir parametre olan bir sınıfın (veya oluşturucu gerektiren başka bir karmaşık türün) örneğini temsil eden bir nesne oluşturmak için bu yöntemi çağırır.

 Nesne parametresi bir oluşturucu gerektirmezse [CreateObjectNoConstructor yöntemini](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
