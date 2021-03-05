---
description: Kesme noktası isteği için bir belge sağlama toplamını temsil eder.
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6bb0bdd70d2d4d1d56e341bc8f21ef1127433219
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173716"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Kesme noktası isteği için bir belge sağlama toplamını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Hata ayıklama paketi tarafından uygulanır ve hata ayıklama motorları tarafından kullanılır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugBreakpointChecksumRequest2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Kullanılacak sağlama toplamı algoritmasının benzersiz tanımlayıcısı verilen kesme noktası isteği için belge sağlama toplamını alır.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Bu belge için sağlama toplamı etkinleştirilip etkinleştirilmediğini belirler.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
