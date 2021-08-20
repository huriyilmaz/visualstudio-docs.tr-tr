---
description: Visual Studio kullanıcı arabirimine, güvenlik duvarının uzaktan hata ayıklamayı engellemediğinden emin olmak için DCOM kullanan bir hata ayıklama altyapısını sağlar.
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
ms.openlocfilehash: 899413fa9064b463732fd2985bb0ddaf8dddf5a4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088750"
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
