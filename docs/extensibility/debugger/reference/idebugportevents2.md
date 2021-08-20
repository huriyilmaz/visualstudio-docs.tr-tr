---
description: Bu arabirim bir dinleyiciye (genellikle oturum hata ayıklama yöneticisi [SDM] veya bir hata ayıklama altyapısı) belirli bir bağlantı noktası üzerinde işlem ve program oluşturma ve yok etme hakkında bilgi sağlar.
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 571c82cbb84686dd863e431c9956aa077b16f976
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132983"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Bu arabirim bir dinleyiciye (genellikle oturum hata ayıklama yöneticisi [SDM] veya bir hata ayıklama altyapısı) belirli bir bağlantı noktası üzerinde işlem ve program oluşturma ve yok etme hakkında bilgi sağlar. Bu bilgiler, bağlantı noktası üzerinde çalışan işlemlerin ve programların gerçek zamanlı bir görünümünü sunmak için kullanılabilir.

## <a name="syntax"></a>Syntax

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Visual Studio genellikle program oluşturma ve yok etme hakkında bildirim almak için bu arabirimi uygulamaya alır. Hata ayıklama altyapısı, bu tür bağlantı noktası olaylarını dinlemek için bu arabirimi de gerçekleştirebilirsiniz.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Tüm [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimleri bir arabirim için <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> sorgulandırabilirsiniz. Ardından, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> `IDebugPortEvents2` arabirimini almak için <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> arabiriminde için yöntemi <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> çağrılır. Son <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> olarak, olayları <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Event yöntemi aracılığıyla göndermek için arabiriminde yöntemi [çağrılır.](../../../extensibility/debugger/reference/idebugportevents2-event.md)

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemini `IDebugPortEvents2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Bağlantı noktası üzerinde işlemlerin ve programların oluşturulmasını ve yok edilmesi açıklayan olayları gönderir.|

## <a name="remarks"></a>Açıklamalar
 `IDebugPortEvents2` , SDM tarafından zaten hata ayıklanmış olan bir işlemde çalıştıran programlarda hata ayıklamak için de kullanılır.

 Bağlantı noktası olayları bu arabirim tarafından SDM'ye geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
