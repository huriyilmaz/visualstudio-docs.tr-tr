---
title: IDebugSymbolProviderDirect | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718908"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Meta verilere ve çekirdek sembol arabirimlerine doğrudan erişimi olan bir sembol sağlayıcısını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Hata ayıklama adresi verilen uygulama etki alanı tanımlayıcısını alır.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Sembol grubundaki modüller hakkında bilgi alır.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Sembol sağlayıcısının üyesi olduğu sembol grubu hakkındaki bilgileri alır.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Meta veri alma bilgilerini alır.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Belirtilen hata ayıklama adresindeyöntem le ilgili bilgileri alır.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Yönetilmeyen kod için bir sembol okuyucu alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, diğer sembol sağlayıcı arabirimlerinin çoğu yerine kullanılabilir. Meta verilere ve `CorSym` arabirimlere doğrudan erişim sağlar.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Ş.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
