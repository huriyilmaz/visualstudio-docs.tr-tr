---
title: 'IDebugReference2:: GetParent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c4ed767023fc8d1de65f75c8fb73e31004319024
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909616"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
Başvurunun üst başvurusunu alır. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetParent ( 
   IDebugReference2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugReference2 ppParent
);
```

## <a name="parameters"></a>Parametreler
`ppParent`\
dışı Bu özelliğin üst öğesini temsil eden bir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
