---
description: Hatayı açıklayan kesme noktası hata çözümünü alır.
title: 'IDebugErrorBreakpoint2:: GetBreakpointResolution | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
ms.assetid: 1c2324ed-2a11-4e63-8f3a-f420c7a4018b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b6d7aea0c0ff9cbacf4085203a8908d30628bacf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153189"
---
# <a name="idebugerrorbreakpoint2getbreakpointresolution"></a>IDebugErrorBreakpoint2::GetBreakpointResolution
Hatayı açıklayan kesme noktası hata çözümünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetBreakpointResolution( 
   IDebugErrorBreakpointResolution2** ppErrorResolution
);
```

```csharp
int GetBreakpointResolution( 
   out IDebugErrorBreakpointResolution2 ppErrorResolution
);
```

## <a name="parameters"></a>Parametreler
`ppErrorResolution`\
dışı Hatayı açıklayan bir [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
