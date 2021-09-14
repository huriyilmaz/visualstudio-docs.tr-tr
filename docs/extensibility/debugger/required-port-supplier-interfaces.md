---
title: Gerekli Bağlantı Noktası Tedarikçi Arabirimleri | Microsoft Docs
description: Bir bağlantı noktası sağlayıcının çalıştırması gereken arabirimler hakkında bilgi edinmek. Bağlantı noktası tedarikçisi bağlantı noktaları sağlar ve bunları uygulamaz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e82150e613235bca066d80a99ba975c7556d4466
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634662"
---
# <a name="required-port-supplier-interfaces"></a>Gerekli bağlantı noktası tedarikçi arabirimleri
Bir bağlantı noktası sağlayıcının [IDebugPortSupplier2 arabirimini uygulaması](../../extensibility/debugger/reference/idebugportsupplier2.md) gerekir. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Bağlantı noktası tedarikçisi bağlantı noktaları sağlar ve bunları uygulamaz. Bu nedenle aşağıdaki arabirimleri çalıştırması gerekir:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Bağlantı noktasını açıklar ve bağlantı noktası üzerinde çalışan tüm işlemleri numaralar.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Bağlantı noktası üzerinde işlemleri başlatmayı ve sonlandırmayı sağlar.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Bu bağlantı noktası bağlamında çalışan programlar için program düğümü oluşturma ve yok etme hakkında bildirim sağlayan bir mekanizma sağlar. Daha fazla bilgi için [bkz. Program düğümleri.](../../extensibility/debugger/program-nodes.md)

- `IConnectionPointContainer`

  [IDebugPortEvents2 için bir bağlantı noktası sağlar.](../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="port-supplier-operation"></a>Bağlantı noktası sağlayıcı işlemi
 İşlem ve programlar bir bağlantı noktası üzerinde oluşturulduğunda ve yok edilirken [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) havuzu bildirimleri alır. Bir işlem oluşturulduğunda [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) ve bağlantı noktası üzerinde bir işlem yok edilirken [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) göndermek için bir bağlantı noktası gereklidir. Bir program oluşturulduğunda [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) ve bağlantı noktası üzerinde çalışan bir işlemde program yok edilirken [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) göndermek için de bir bağlantı noktası gereklidir.

 Bir bağlantı noktası genellikle sırasıyla [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) ve [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemlerine yanıt olarak program oluşturma ve yok etme olaylarını gönderir.

 Bir bağlantı noktası hem fiziksel işlemleri hem de mantıksal programları başlataya ve sonlandırana kadar, hata ayıklama altyapısı tarafından aşağıdaki arabirimlerin de uygulanması gerekir:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Fiziksel işlemi açıklar. En azından aşağıdaki yöntemlerin uygulanması gerekir:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  SDM'nin kendisini bir işleme eklemesi ve işlemden ayırması için bir yol sağlar.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Mantıksal programı açıklar. En azından aşağıdaki yöntemlerin uygulanması gerekir:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  SDM'nin bu programa eklemesi için bir yol sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktası sağlayıcı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)
