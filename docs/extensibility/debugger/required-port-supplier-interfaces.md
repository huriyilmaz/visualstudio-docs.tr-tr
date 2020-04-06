---
title: Gerekli Port Tedarikçi Arayüzleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713159"
---
# <a name="required-port-supplier-interfaces"></a>Gerekli bağlantı noktası tedarikçisi arayüzleri
Bir bağlantı noktası tedarikçisi [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimini uygulamalıdır. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Bir liman tedarikçisi limanları tedarik eder ve uygular. Bu nedenle, aşağıdaki arabirimleri çalıştırmak gerekir:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Bağlantı noktasını açıklar ve bağlantı noktasında çalışan tüm işlemleri doğrular.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Bağlantı noktasındaki işlemlerin başlatılması nı ve sonlandırmasını sağlar.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Program düğümü oluşturma ve imha bildirmek için bu bağlantı noktası bağlamında çalışan programlar için bir mekanizma sağlar. Daha fazla bilgi için [Program düğümlerine](../../extensibility/debugger/program-nodes.md)bakın.

- `IConnectionPointContainer`

  [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)için bir bağlantı noktası sağlar.

## <a name="port-supplier-operation"></a>Liman tedarikçisi operasyonu
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) lavabosu, işlem ve programlar bir bağlantı noktasında oluşturulduğunda ve yok edildiğinde bildirimler alır. Bir işlem oluşturulduğunda [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) göndermek için bir bağlantı noktası ve bağlantı noktasında bir işlem yok edildiğinde [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) gereklidir. Bir program oluşturulduğunda [iDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) göndermek için bir bağlantı noktası ve [iDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) bir program bağlantı noktası üzerinde çalışan bir işlem yok olduğunda gereklidir.

 Bağlantı noktası genellikle sırasıyla [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) ve [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemlerine yanıt olarak program oluşturma ve yok etme etkinlikleri gönderir.

 Bir bağlantı noktası hem fiziksel işlemleri hem de mantıksal programları başlatıp sonlandırabildiği için, hata ayıklama altyapısı tarafından aşağıdaki arabirimler de uygulanmalıdır:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Fiziksel süreci açıklar. En azından aşağıdaki yöntemler uygulanmalıdır:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessid](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  SDM'nin kendisini bir işlemden ayırması için bir yol sağlar.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Mantıksal programı açıklar. En azından aşağıdaki yöntemler uygulanmalıdır:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  SDM'nin bu programa eklenmesi için bir yol sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Liman tedarikçisinin uygulanması](../../extensibility/debugger/implementing-a-port-supplier.md)
