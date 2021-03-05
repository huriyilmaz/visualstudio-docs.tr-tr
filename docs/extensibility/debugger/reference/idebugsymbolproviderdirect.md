---
description: Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.
title: Idebugsymbolproviderdirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d60af5be925341e5421badb4c3e6e3dae97903b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149320"
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
