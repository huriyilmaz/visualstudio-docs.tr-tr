---
title: Gerekli bağlantı noktası sağlayıcısı arabirimleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a065389a6b9b67b8bce82394569ce65afb0f8d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821430"
---
# <a name="required-port-supplier-interfaces"></a>Gerekli Bağlantı Noktası Sağlayıcısı Arabirimleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir bağlantı noktası tedarikçinin [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimini uygulaması gerekir. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Bir bağlantı noktası sağlayıcısı bağlantı noktaları sağladığından, bunları da uygulamalıdır. Bu nedenle, aşağıdaki arabirimleri gerçekleştirmelidir:  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Bağlantı noktasını açıklar ve bağlantı noktası üzerinde çalışan tüm işlemlerin listesini oluşturabilir.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Bağlantı noktasında işlem başlatma ve sonlandırma sağlar.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Program düğümü oluşturma ve yok etme hakkında bilgilendirmek için bu bağlantı noktası bağlamında çalışan programlar için bir mekanizma sağlar. Daha fazla bilgi için bkz. [Program düğümleri](../../extensibility/debugger/program-nodes.md).  
  
- `IConnectionPointContainer`  
  
     [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md)için bir bağlantı noktası sağlar.  
  
## <a name="port-supplier-operation"></a>Bağlantı noktası sağlayıcısı Işlemi  
 Bir bağlantı noktasında işlem ve program oluşturulduğunda ve yok edildiğinde [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) havuzu bildirimleri alır. Bir işlem oluşturulduğunda [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) göndermek için bir bağlantı noktası gerekir ve bağlantı noktasında bir işlem yok edildiğinde [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) . Ayrıca, bir program oluşturulduğunda [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) göndermek için bir bağlantı noktası ve bir program bağlantı noktasında çalışan bir işlemde yok edildiğinde [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gerekir.  
  
 Bir bağlantı noktası genellikle, sırasıyla [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) ve [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemlerine yanıt olarak program oluşturma ve yok etme olayları gönderir.  
  
 Bir bağlantı noktası hem fiziksel işlemi hem de mantıksal programları başlatıp sonlandırabildiğinden, bu arabirimlerin de hata ayıklama altyapısı tarafından uygulanması gerekir:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı Noktası Sağlayıcısı Uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)
