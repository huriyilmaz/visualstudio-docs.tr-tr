---
description: Oluşturucuyu kullanarak bir nesne oluşturur.
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
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
ms.openlocfilehash: 3477d95d583520db8faca131a3ad96b3fff7195f2ca5840f7a5752f3ddd685d2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377580"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Oluşturucuyu kullanarak bir nesne oluşturur.

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
'ndaki Oluşturulacak nesnenin oluşturucusunu temsil eden bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi.

`dwArgs`\
'ndaki Dizideki parametrelerin sayısı `pArg` . Oluşturucuya geçirilen parametre sayısını temsil eder.

`pArg`\
'ndaki Oluşturucuya geçirilen parametreleri temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri dizisi.

`ppObject`\
dışı `IDebugObject` Yeni oluşturulan nesneyi temsil eden bir döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi tarafından temsil edilen işlevin parametresi olan bir sınıfın (veya bir Oluşturucu gerektiren diğer karmaşık türün) bir örneğini temsil eden bir nesne oluşturmak için bu yöntemi çağırın.

 Nesne parametresi bir Oluşturucu gerektirmiyorsa, [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
