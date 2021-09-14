---
description: Yönetilen koda özgü yöntemlerle bir COM+ sembol sağlayıcısını temsil eder ve IDebugComPlusSymbolProvider'ı genişleter.
title: IDebugComPlusSymbolProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e2ab4ec66d61f67a70e4738ed9eeb59b1f8aac8a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725265"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Yönetilen koda özgü yöntemlerle bir COM+ sembol sağlayıcısını temsil eder ve **IDebugComPlusSymbolProvider**[IDebugComPlusSymbolProvider'ı genişleter.](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

## <a name="syntax"></a>Syntax

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>Yöntemler
 [Bu arabirim, IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Belirtilen yöntemin satır bilgilerine sahip olup olmadığını belirler.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Verilen bir türün adını alan.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Belirteci verilen bir türü alır.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Belirtilen hata ayıklama adresinin bir sıra noktası olup olmadığını belirler.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Belirtilen geri çağırma yöntemini kullanarak hata ayıklama sembollerini yükler.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|**ICorDebugModule** nesnesine göre bir veri akışından hata ayıklama sembolleri yükleme.|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|**ICorDebugModule nesnesine verilen hata ayıklama sembollerini** yükler.|

## <a name="requirements"></a>Gereksinimler
 Üst Bilgi: Sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
