---
description: Sembol yükleme işlemiyle ilgili sonuçları almak için olay işleyicisi tarafından çağrılır.
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ccf00b144da55323281db33a1ee23814d212a79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070929"
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
[out] Sembollerin yükleniyor olduğu modülü temsil eden bir IDebugModule3 nesnesi.

`pbstrDebugMessage`\
[in, out] Modülden gelen hata iletilerini içeren bir dize döndürür. Hata yoksa, bu dize yalnızca modülün adını içerir ancak hiçbir zaman boş olmaz.

> [!NOTE]
> [C++] `pbstrDebugMessage` olamaz `NULL` ve ile serbest bırakılamaları `SysFreeString` gerekir.

`pdwModuleInfoFlags`\
[out] Herhangi bir simgenin yük [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) işaret eden bir bayraklar birleşimi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir işleyici bir modül için hata ayıklama sembollerini yükleme girişiminde bulunduktan sonra [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) olayı aldığında, işleyici bu yükün sonuçlarını belirlemek için thismethod'u çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
