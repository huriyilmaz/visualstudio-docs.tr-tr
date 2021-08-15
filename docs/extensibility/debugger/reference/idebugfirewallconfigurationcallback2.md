---
description: Güvenlik duvarının uzaktan hata ayıklamayı engellemey olduğundan emin olmak için Visual Studio kullanıcı arabirimini istemek için DCOM kullanan bir hata ayıklama altyapısını sağlar.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 18dd45fa041732f733d121d7304650ea82cf5983a76fa58e434b088ba8fcb684
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402772"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Kullanıcı arabiriminden güvenlik duvarının uzaktan hata ayıklamayı engellemey olduğundan emin olmak için DCOM [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] kullanan bir hata ayıklama altyapısını sağlar.

## <a name="syntax"></a>Syntax

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Oturum hata ayıklama yöneticisinin bağlantı noktası nesnesi tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugFirewallConfigurationCallback2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Güvenlik duvarının uzaktan hata ayıklamayı engellemez.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
