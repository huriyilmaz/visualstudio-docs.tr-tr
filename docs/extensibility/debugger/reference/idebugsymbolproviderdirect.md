---
description: Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.
title: IDebugSymbolProviderDirect | Microsoft Docs
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
ms.openlocfilehash: b68924b470ce9cbf69f4dfb2fac231cb2a3e88362b5dce15419206482d90af9f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292018"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemleri kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Hata ayıklama adresi verilen uygulama etki alanı tanımlayıcısını verir.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Sembol grubunda modüller hakkında bilgi alınır.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Sembol sağlayıcısının üye olduğu sembol grubuyla ilgili bilgileri alınır.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Meta veri içeri aktarma bilgilerini alın.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Belirtilen hata ayıklama adresine yöntemiyle ilgili bilgileri alın.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Unmanaged code için bir sembol okuyucusu alma.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, diğer sembol sağlayıcısı arabirimlerinin çoğu yerine kullanılabilir. Meta verilere ve arabirimlere doğrudan `CorSym` erişim sağlar.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
