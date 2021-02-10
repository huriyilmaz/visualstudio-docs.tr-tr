---
title: 'Idebugciltçi:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c203e83a595562e604d8c32b09056c8544bfd1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938985"
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
