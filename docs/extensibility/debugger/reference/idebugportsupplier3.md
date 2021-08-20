---
description: Bu arabirim, bir arayanın bir bağlantı noktası üreticisinin, hata ayıklayıcının etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) koruyup koruyamayacağını belirlemesine izin verir ve ardından bu korunan bağlantı noktalarının bir listesini alın.
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 56d4d0dd0f7ddef677c8e32696deaea41678a621
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160003"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Bu arabirim, bir arayanın bir bağlantı noktası üreticisinin, hata ayıklayıcının etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) koruyup koruyamayacağını belirlemesine izin verir ve ardından bu korunan bağlantı noktalarının bir listesini alın.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi kalıcı veya bağlantı noktası bilgilerinin diske kaydedilmesini desteklemek için uygular. Bu arabirimin [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimiyle aynı nesne üzerinde uygulanması gerekir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [](/cpp/atl/queryinterface) `IDebugPortSupplier2` Bu arabirimi edinmek için arabirimdeki QueryInterface 'i çağırın.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) arabiriminden devralınan yöntemlere ek olarak, bu arabirim aşağıdakileri destekler:

|Yöntem|Açıklama|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Bağlantı noktası üreticisinin, hata ayıklayıcının etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) kalıcı yapıp yapamayacağını döndürür.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Bu bağlantı noktası sağlayıcısı tarafından diske yazılan tüm bağlantı noktalarını numaralandırmak için kullanılabilecek bir nesne döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bir bağlantı noktası tedarikçide bağlantı noktalarını etkinleştirmeleri arasında kalıcı hale getirebiliyorsanız, bu arabirimi uygulamalıdır. Bağlantı noktası sağlayıcısı örneği oluşturulduğunda bağlantı noktaları yüklenmelidir ve bağlantı noktası sağlayıcısı yok edildiğinde diske yazılır.

 Bir hata ayıklama altyapısı genellikle bir bağlantı noktası sağlayıcısıyla etkileşime girmiyor ve bu arabirim için hiçbir kullanımı olmayacaktır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
