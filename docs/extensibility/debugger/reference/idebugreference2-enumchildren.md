---
description: Bir başvuruda seçili olan çocukların listesini almak.
title: IDebugReference2::EnumChildren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bab404519695b71c84c82216606b59529b1d4386
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725153"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Bir başvuruda seçili olan çocukların listesini almak. Daha sonraki kullanımlar için ayrılmıştır.

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
[in] Numaralandırılan [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) alanları belirten bir numaralandırılan DEBUG_REFERENCE_INFO bayrakların birleşimi. [](../../../extensibility/debugger/reference/debug-reference-info.md)

`dwRadix`\
[in] Herhangi bir sayısal bilgiyi biçimlendirmek için kullanılacak radyan.

`dwAttribFilter`\
[in] Numaralandırılan [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) seçmek için parametresiyle birlikte filtre olarak kullanılan bir filtre enumerasyonundan `pszNameFilter` bayrakların birleşimi.

`pszNameFilter`\
[in] Numaralandır kullanılacak yapıları seçmek için parametresiyle birlikte kullanılan "MyX" gibi bir `dwAttribFilter` filtreyi belirten dize.

`dwTimeout`\
[in] Bu yöntemden dönmeden önce bek süresi (milisaniye cinsinden). Süresiz `INFINITE` olarak beklemek için kullanın.

`ppEnum`\
[out] İstenen alt [özelliklerin listesini içeren bir IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Her zaman `E_NOTIMPL` döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
