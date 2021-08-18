---
description: Bu arabirim, adresi bu arabirim tarafından temsil edilen nesneye sahip olan işlemin KIMLIĞINE erişim sağlar.
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
ms.openlocfilehash: ef1058f11cc377b9c1b0ccc3a37f0d4d1ad57014
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104436"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Bu arabirim, adresi bu arabirim tarafından temsil edilen nesneye sahip olan işlemin KIMLIĞINE erişim sağlar.

## <a name="syntax"></a>Syntax

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bir sembol sağlayıcısı, bu arabirimi [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimini uygulayan aynı nesne üzerinde uygular. Bu arabirim, bu adresle ilgili nesnenin sahibi olan işlemin KIMLIĞINE erişim sağlar.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabiriminden almak için [QueryInterface](/cpp/atl/queryinterface) kullanın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabiriminden devralınan yöntemlere ek olarak, bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Bu arabirim tarafından temsil edilen nesnenin sahibi olan işlemin KIMLIĞINI alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
