---
description: Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.
title: Idebugsymbolproviderdirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 77755fa34bd6053427b9fccb470c5b82b1496422
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029573"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Hata ayıklama adresi verilen uygulama etki alanı tanımlayıcısını alır.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Sembol grubundaki modüller hakkındaki bilgileri alır.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Sembol sağlayıcısının üye olduğu sembol grubu hakkındaki bilgileri alır.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Meta veri içeri aktarma bilgilerini alır.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Belirtilen hata ayıklama adresinde yöntemi hakkındaki bilgileri alır.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Yönetilmeyen kod için bir sembol okuyucu alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim diğer sembol sağlayıcısı arabirimlerinin çoğu yerine kullanılabilir. Meta verilere ve arabirimlere doğrudan erişim sağlar `CorSym` .

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
