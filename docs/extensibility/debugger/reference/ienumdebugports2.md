---
description: Bu arabirim, bir makinenin veya bağlantı noktası sağlayıcının bağlantı noktalarını numaralar.
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 243fcf1476f2f278ebed550805fcdfc9cf82d03300a1df70ad2c1c833ac3cdc8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121291694"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Bu arabirim, bir makinenin veya bağlantı noktası sağlayıcının bağlantı noktalarını numaralar.

## <a name="syntax"></a>Syntax

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Özel bir bağlantı noktası sağlayıcı, sağlayıcı tarafından oluşturulan bağlantı noktalarının listesini temsil etmek için bu arabirimi uygulamaya almaktadır. Visual Studio kendi bağlantı noktası tedarikçisini desteklemek için bu arabirimi uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bağlantı noktası sağlayıcı tarafından oluşturulan bağlantı noktalarının listesini temsil eden bu arabirimi almak için [EnumPorts'u](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) arayın. Diske kaydedilmiş bağlantı noktalarının listesini temsil eden bu arabirimi elde etmek için [EnumPersistedPorts'u](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) arayın.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IEnumDebugPorts2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Bir numaralama dizisinde belirtilen sayıda bağlantı noktası alma.|
|[Atla](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Bir numaralama dizisinde belirtilen sayıda bağlantı noktasını atlar.|
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Numaralayıcıda bağlantı noktalarının sayısını alır.|

## <a name="remarks"></a>Açıklamalar
 Visual Studio işlemlere eklemek için kullanılan bağlantı noktalarının listesini doldurmak için bu arabirimi kullanır.

 Hata ayıklama altyapısı genellikle bu arabirimi kullanmaz.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
