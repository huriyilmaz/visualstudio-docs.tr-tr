---
title: 'IDebugCustomAttribute:: GetParentField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9845954a2be9ec57edb6ca555fb89a6ad20f7d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842478"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Özel özniteliğin eklendiği alanı alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametreler
`ppField`\
dışı Özel özniteliğin eklendiği alanı temsil eden [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Üst öğenin ne tür bir alan olduğunu belirlemek için döndürülen [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesinde [getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
