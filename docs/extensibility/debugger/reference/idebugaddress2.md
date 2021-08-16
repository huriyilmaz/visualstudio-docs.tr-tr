---
description: Bu arabirim, adresi bu arabirimle temsil edilen nesnenin sahibi olan işlem kimliğine erişim sağlar.
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: be12b088771484f1202fbb4cc806ae041d6d23778aa2e7efcb2ceee2cf1d1dd0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403188"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Bu arabirim, adresi bu arabirimle temsil edilen nesnenin sahibi olan işlem kimliğine erişim sağlar.

## <a name="syntax"></a>Syntax

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Sembol sağlayıcısı bu arabirimi [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimini uygulayan aynı nesne üzerinde kullanır. Bu arabirim, bu adresle ilgili nesnenin sahibi olan işlem kimliğine erişim sağlar.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabiriminden almak için [QueryInterface](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 [Bu arabirim, IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabiriminden devralınan yöntemlere ek olarak aşağıdaki yöntemi de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Bu arabirim tarafından temsil edilen nesnenin sahibi olan işlem kimliğini alın.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
