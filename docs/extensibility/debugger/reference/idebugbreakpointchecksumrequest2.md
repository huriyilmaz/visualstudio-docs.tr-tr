---
title: IDebugBreakpointChecksumRequest2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 632c3611f6c03a47a7d46e985eb6aa2685864a7f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735120"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Kesme noktası isteği için belge denetimini temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata Ayıklama [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] paketi tarafından uygulanır ve hata ayıklama motorları tarafından tüketilir.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugBreakpointChecksumRequest2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Kullanılacak checksum algoritmasının benzersiz tanımlayıcısı verilen bir kesme noktası isteği için belge denetimleri alır.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Bu belge için checksum etkin olup olmadığını belirler.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
