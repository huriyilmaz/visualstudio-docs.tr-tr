---
description: Yönetilen koda özgü yöntemlere sahip bir COM+ sembol sağlayıcısını temsil eder ve IDebugComPlusSymbolProvider 'ı genişletir.
title: IDebugComPlusSymbolProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 975dc6df875866a16fffc5d044ae82c996b84e35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077973"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Yönetilen koda özgü yöntemlere sahip bir COM+ sembol sağlayıcısını temsil eder ve **IDebugComPlusSymbolProvider**[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)'ı genişletir.

## <a name="syntax"></a>Syntax

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>Yöntemler
 Bu arabirim, [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Belirtilen yöntemin satır bilgilerine sahip olup olmadığını belirler.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Adı verilen bir tür alır.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Belirteci verilen bir tür alır.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Belirtilen hata ayıklama adresinin bir sıra noktası olup olmadığını belirler.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Belirtilen geri çağırma yöntemini kullanarak hata ayıklama sembolleri yükler.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|**ICorDebugModule** nesnesi verilen bir veri akışından hata ayıklama sembolleri yükleyin.|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|**ICorDebugModule** nesnesi verilen hata ayıklama sembollerini yükler.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
