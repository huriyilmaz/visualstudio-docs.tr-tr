---
title: Programa Bağlanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739246"
---
# <a name="attach-to-the-program"></a>Programa ekle
Programlarınızı uygun bağlantı noktasına kaydettikten sonra hata ayıklama yı hata ayıklamak istediğiniz programa eklemeniz gerekir.

## <a name="choose-how-to-attach"></a>Nasıl ekeceğinizi seçin
 Oturum hata ayıklama yöneticisinin (SDM) debugged olan programa eklemeye çalıştığı üç yolu vardır.

1. [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemi (örneğin, yorumlanan dillerin tipik) aracılığıyla hata ayıklama altyapısı tarafından başlatılan programlar için, SDM, eklenen programla ilişkili [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesinden [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimini alır. SDM arabirimi elde `IDebugProgramNodeAttach2` edebilirse, SDM [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır. Yöntem, `IDebugProgramNodeAttach2::OnAttach` `S_OK` programa iliştirilmediğini ve programa iliştirmek için başka girişimlerde bulunulabileceğini belirtmek için döndürür.

2. SDM, bağlı olduğu programdan [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) arabirimini edinebiliyorsa, SDM [Ekle](../../extensibility/debugger/reference/idebugprogramex2-attach.md) yöntemini çağırır. Bu yaklaşım, bağlantı noktası tedarikçisi tarafından uzaktan başlatılan programlar için tipiktir.

3. Program `IDebugProgramNodeAttach2::OnAttach` veya `IDebugProgramEx2::Attach` yöntemlerle bağlanamıyorsa, SDM hata ayıklama altyapısını `CoCreateInstance` (zaten yüklenmemişse) işlevi arayarak yükler ve sonra [Ekle](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemini çağırır. Bu yaklaşım, bir bağlantı noktası tedarikçisi tarafından yerel olarak başlatılan programlar için tipiktir.

    Özel liman tedarikçisinin `IDebugEngine2::Attach` `IDebugProgramEx2::Attach` yöntemi uygulamasında araması da mümkündür. Genellikle bu durumda, özel bağlantı noktası tedarikçisi uzak makinede hata ayıklama motoru başlattı.

   Ek, oturum hata ayıklama yöneticisi (SDM) [Ekle](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemini aradığında elde edilir.

   Debugged olacak uygulama ile aynı işlemde DE çalıştırırsanız, o zaman [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)aşağıdaki yöntemleri uygulamanız gerekir:

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  `IDebugEngine2::Attach` Yöntem çağrıldıktan sonra, `IDebugEngine2::Attach` yöntemin uygulanmasında aşağıdaki adımları izleyin:

1. SDM'ye bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesi gönderin. Daha fazla bilgi için [bkz.](../../extensibility/debugger/sending-events.md)

2. Yönteme geçirilen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) nesnesi üzerinde `IDebugEngine2::Attach` [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini arayın.

     Bu, `GUID` programı tanımlamak için kullanılan bir döndürür. Yerel `GUID` programı DE'ye temsil eden nesnede depolanmalıdır ve `IDebugProgram2::GetProgramId` yöntem `IDebugProgram2` arabirimde çağrıldığında döndürülmelidir.

    > [!NOTE]
    > Arabirimi `IDebugProgramNodeAttach2` uygularsanız, programın yöntemi `GUID` ne olursa `IDebugProgramNodeAttach2::OnAttach` o kadar çok aktarılır. Bu `GUID` `GUID` `IDebugProgram2::GetProgramId` yöntem tarafından döndürülen program için kullanılır.

3. SDM'ye programı de'ye temsil etmek üzere yerel `IDebugProgram2` nesnenin oluşturulduğunu bildirmek için bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesnesi gönderin. Ayrıntılar [için, Etkinlikler Gönderme'ye](../../extensibility/debugger/sending-events.md)bakın.

    > [!NOTE]
    > Bu, yönteme `IDebugProgram2` geçirilen nesneyle `IDebugEngine2::Attach` aynı değildir. Daha önce `IDebugProgram2` geçirilen nesne yalnızca bağlantı noktası tarafından tanınan ve ayrı bir nesnedir.

## <a name="see-also"></a>Ayrıca bkz.
- [Başlatma tabanlı eki](../../extensibility/debugger/launch-based-attachment.md)
- [Etkinlik gönderme](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [İliştir](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [İliştir](../../extensibility/debugger/reference/idebugengine2-attach.md)
