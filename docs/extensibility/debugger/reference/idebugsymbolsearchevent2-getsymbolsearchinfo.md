---
title: 'IDebugSymbolSearchEvent2:: GetSymbolSearchInfo | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718892"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Bir sembol yükleme işlemi hakkındaki sonuçları almak için bir olay işleyicisi tarafından çağırılır.

## <a name="syntax"></a>Söz dizimi

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
dışı Sembollerin yüklendiği modülü temsil eden bir IDebugModule3 nesnesi.

`pbstrDebugMessage`\
[in, out] Modülden herhangi bir hata iletisi içeren bir dize döndürür. Hata yoksa, bu dize yalnızca modülün adını içerir, ancak hiçbir şekilde boştur.

> [!NOTE]
> [C++] `pbstrDebugMessage` `NULL` ile serbest bırakılmalıdır `SysFreeString` .

`pdwModuleInfoFlags`\
dışı [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) numaralandırmasından herhangi bir sembolün yüklenip yüklenmediğini gösteren bayrakların birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir işleyici, bir modül için hata ayıklama sembolleri yükleme denemesinden sonra [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) olayını aldığında, işleyicinin bu yükün sonuçlarını belirlemesi için thismetodunu çağırabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
