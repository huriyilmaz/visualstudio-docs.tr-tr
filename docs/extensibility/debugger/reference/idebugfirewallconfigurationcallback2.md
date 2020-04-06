---
title: IDebugFirewallConfigurationCallback2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728719"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Güvenlik duvarının uzaktan hata ayıklamayı [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] engellemeyeceğinden emin olmak için UI'den sormak için DCOM kullanan bir hata ayıklama altyapısı sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Oturum hata ayıklama yöneticisinin bağlantı noktası nesnesi tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda `IDebugFirewallConfigurationCallback2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Güvenlik duvarının uzaktan hata ayıklamayı engellememesi için istekte.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
