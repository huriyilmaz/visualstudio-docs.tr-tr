---
title: Gerekli bağlantı noktası sağlayıcısı arabirimleri | Microsoft Docs
description: Bir bağlantı noktası tedarikçinin çalışması gereken arabirimler hakkında bilgi edinin. Bağlantı noktası sağlayıcısı, bağlantı noktaları sağlar ve bunları uygular.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087307"
---
# <a name="required-port-supplier-interfaces"></a>Gerekli bağlantı noktası sağlayıcısı arabirimleri
Bir bağlantı noktası tedarikçinin [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimini uygulaması gerekir. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Bağlantı noktası sağlayıcısı, bağlantı noktaları sağlar ve bunları uygular. Bu nedenle, aşağıdaki arabirimleri çalıştırmalıdır:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Bağlantı noktasını açıklar ve bağlantı noktası üzerinde çalışan tüm işlemi numaralandırır.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Bağlantı noktasında işlem başlatma ve sonlandırma sağlar.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Program düğümü oluşturma ve yok etme hakkında bilgilendirmek için bu bağlantı noktası bağlamında çalışan programlar için bir mekanizma sağlar. Daha fazla bilgi için bkz. [Program düğümleri](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)için bir bağlantı noktası sağlar.

## <a name="port-supplier-operation"></a>Bağlantı noktası sağlayıcısı işlemi
 Bir bağlantı noktasında işlem ve program oluşturulduğunda ve yok edildiğinde [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) havuzu bildirimleri alır. Bir işlem oluşturulduğunda [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) göndermek için bir bağlantı noktası gerekir ve bağlantı noktasında bir işlem yok edildiğinde [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) . Ayrıca, bir program oluşturulduğunda [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) göndermek için bir bağlantı noktası ve bir program bağlantı noktasında çalışan bir işlemde yok edildiğinde [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gerekir.

 Bir bağlantı noktası genellikle, sırasıyla [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) ve [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemlerine yanıt olarak program oluşturma ve yok etme olayları gönderir.

 Bir bağlantı noktası hem fiziksel işlemi hem de mantıksal programları başlatıp sonlandırabildiğinden, aşağıdaki arabirimlerin de hata ayıklama altyapısı tarafından uygulanması gerekir:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Fiziksel işlemi açıklar. En azından aşağıdaki yöntemlerin uygulanması gerekir:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  SDM 'nin bir işlemden kendisini ekleyip ayırabilmek için bir yol sağlar.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Mantıksal programı açıklar. En azından aşağıdaki yöntemlerin uygulanması gerekir:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  SDM 'nin bu programa eklenmesi için bir yol sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)
