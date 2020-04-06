---
title: IDebugReference2::EnumChildren | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96b2fec782ce88dfb2200df35f56b35b304beda5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720626"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Başvurunun seçili çocuklarının listesini alın. Daha sonraki kullanımlar için ayrılmıştır.

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
[içinde] [Numaralandırılmış](../../../extensibility/debugger/reference/debugref-info-flags.md) [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapılarındaki alanların doldurulmasını belirten DEBUGREF_INFO_FLAGS numaralandırmadaki bayrakların birleşimi.

`dwRadix`\
[içinde] Herhangi bir sayısal bilgi biçimlendirmede kullanılacak radix.

`dwAttribFilter`\
[içinde] Hangi yapıların numaralandırılmak üzere seçeceğini seçmek için `pszNameFilter` parametre ile birlikte filtre olarak kullanılan [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) numaralandırma bayraklarının birleşimi.

`pszNameFilter`\
[içinde] Numaralandırılacak yapıları seçmek için `dwAttribFilter` parametreile birlikte kullanılan "MyX" gibi bir filtreyi belirten bir dize.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden maksimum süre. Süresiz beklemek için kullanın. `INFINITE`

`ppEnum`\
[çıkış] İstenen alt özelliklerin listesini içeren bir [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
