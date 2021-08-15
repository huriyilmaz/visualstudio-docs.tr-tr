---
description: Oluşturucusu olmayan bir nesne oluşturur.
title: 'IDebugFunctionObject:: CreateObjectNoConstructor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 498d0e629d16e3d606db67b25e7f53cb1472e187604c225372163667a7af093d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238872"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Oluşturucusu olmayan bir nesne oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametreler
`pClassObject`\
'ndaki Oluşturulacak nesnenin türünü temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi.

`ppObject`\
dışı Yeni oluşturulan nesneyi temsil eden bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir yapının (bir Oluşturucu gerektirmeyen), [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimi tarafından temsil edilen işlevin parametresi olan bir örneğini temsil eden bir nesne oluşturmak için bu yöntemi çağırın.

 Nesne parametresi bir Oluşturucu gerektiriyorsa, [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) metodunu çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
