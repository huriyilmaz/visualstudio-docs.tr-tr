---
description: Visual Studio Kullanıcı arabirimine güvenlik duvarının uzaktan hata ayıklamayı engellememesini istemek için DCOM kullanan bir hata ayıklama altyapısı sağlar.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c67cc1ab9335cfeb197ca67937510b3137d6432c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073618"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Kullanıcı arabirimine, güvenlik duvarının uzaktan hata ayıklamayı engellememesini istemek IÇIN DCOM kullanan bir hata ayıklama altyapısı sağlar.

## <a name="syntax"></a>Syntax

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Oturum hata ayıklama yöneticisinin bağlantı noktası nesnesi tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugFirewallConfigurationCallback2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Güvenlik duvarının uzaktan hata ayıklamayı engellememe isteklerini ister.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
