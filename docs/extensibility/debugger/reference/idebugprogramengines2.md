---
description: Bu arabirim, program düğümleri tarafından bu programda hata ayıklana tüm olası hata ayıklama altyapılarını (DE) belirtmek için kullanılır.
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: eedc4dd60ce3fbd8581e91ee14404abbe6454a62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126420"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Bu arabirim, program düğümleri tarafından bu programda hata ayıklana tüm olası hata ayıklama altyapılarını (DE) belirtmek için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE veya özel bir bağlantı noktası sağlayıcı bu arabirimi belirli bir program için kullanmak üzere belirli bir DE'nin kurulmasını desteklemek üzere [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) uygulayan aynı nesne üzerinde kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi almak için bir arabirimde [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` çağrısı yapmak.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugProgramEngines2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Bu programda hata ayıklayabilirsiniz tüm olası DE'leri gösterir.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Bu programda hata ayıklamak için kullanmak üzere DE'yi seçer.|

## <a name="remarks"></a>Açıklamalar
 Kullanıcı tarafından de seçildikten sonra, bu seçim SetEngine çağrılarak program [düğümüne kaydedilir.](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md) Seçilen [altyapı, GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)tarafından döndürülen altyapı olur.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
