---
description: Bir başvurunun seçili alt öğelerinin listesini alır.
title: 'IDebugReference2:: EnumChildren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1481e58dd36e330bf9c4cff1644629bd93de55ac
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151382"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Bir başvurunun seçili alt öğelerinin listesini alır. Daha sonraki kullanımlar için ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`dwFields`\
'ndaki Numaralandırılmış [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapılardaki hangi alanların doldurulacağını belirten [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Numaralandırmadaki bayrakların birleşimi.

`dwRadix`\
'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak taban tabanı.

`dwAttribFilter`\
'ndaki [](../../../extensibility/debugger/reference/dbg-attrib-flags.md) `pszNameFilter` Hangi yapıların numaralandırılacağını seçmek için parametresiyle birlikte filtre olarak kullanılan DBG_ATTRIB_FLAGS numaralandırmasındaki bayrakların birleşimi.

`pszNameFilter`\
'ndaki "MyX" gibi bir filtre belirten bir dize, `dwAttribFilter` Numaralandırılacak yapıları seçmek için parametresiyle birlikte kullanılır.

`dwTimeout`\
'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süre (milisaniye cinsinden). `INFINITE`Sonsuza kadar beklemek için kullanın.

`ppEnum`\
dışı İstenen alt özelliklerin bir listesini içeren bir [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
