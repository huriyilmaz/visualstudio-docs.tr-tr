---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718892"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Sembol yükleme işlemiyle ilgili sonuçları almak için olay işleyicisi tarafından çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parametreler
`pModule`\
[çıkış] Sembollerin yüklendiği modülü temsil eden bir IDebugModule3 nesnesi.

`pbstrDebugMessage`\
[içinde, dışarı] Modülden herhangi bir hata iletisi içeren bir dize döndürür. Hata yoksa, bu dize yalnızca modülün adını içerir, ancak hiçbir zaman boş olmaz.

> [!NOTE]
> [C++] `pbstrDebugMessage` ile `NULL` serbest bırakılamaz `SysFreeString`ve serbest bırakılmalıdır.

`pdwModuleInfoFlags`\
[çıkış] Herhangi bir sembollerin yüklenip yüklenmediğini gösteren [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) numaralandırmadan gelen bayrakların birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir işleyici, bir modül için hata ayıklama simgelerini yükleme girişiminde bulunulduktan sonra [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) olayını aldığında, işleyici bu yükün sonuçlarını belirlemek için bu yöntemi arayabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
