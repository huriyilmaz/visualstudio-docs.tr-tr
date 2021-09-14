---
description: Bu yöntem bir nesne konumu ya da bellek adresini bir bellek bağlamına dönüştürür.
title: 'Idebugciltçi:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48a4c9884f4625a938269715c5338d4040ccc8b3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627506"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Bu yöntem bir nesne konumu ya da bellek adresini bir bellek bağlamına dönüştürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametreler
`pField`\
'ndaki Bulacak nesneyi açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) . Varsa `NULL` , `dwConstant` bunun yerine kullanın.

`dwConstant`\
'ndaki 0x5000 gibi sabit bir bellek adresi.

`ppMemCxt`\
dışı Nesnenin adresini veya bellekteki adresi temsil eden [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) arabirimini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
