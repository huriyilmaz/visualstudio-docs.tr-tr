---
title: Programa iliştirme | Microsoft Docs
description: Program uygun bağlantı noktasına kaydedildikten sonra Visual Studio 'Nun bir programa ekleme hata ayıklayıcıyı nasıl uyguladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b1f411b6ca79fec85f4557ce379c341942e0b84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943480"
---
# <a name="attach-to-the-program"></a>Programa iliştirme
Programlarınızı uygun bağlantı noktasıyla kaydettikten sonra, hata ayıklayıcıyı hata ayıklamak istediğiniz programa bağlamanız gerekir.

## <a name="choose-how-to-attach"></a>Nasıl iliştirilmeyi seçin
 Oturum hata ayıklama Yöneticisi 'nin (SDM) hata ayıklamakta olan programa iliştirmeye çalıştığı üç yol vardır.

1. Hata ayıklama altyapısı tarafından [Launchaskıya alındı](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemiyle başlatılan programlar (örneğin, yorumlanan dillerin tipik olarak), SDM, eklendiği programla ilişkili [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesinden [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimini alır. SDM arabirimi alabiliyorsanız `IDebugProgramNodeAttach2` , SDM daha sonra [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır. `IDebugProgramNodeAttach2::OnAttach`Yöntemi, `S_OK` programa iliştirilmediğini ve programa eklemek için başka denemeler yapıldığını belirtmek için öğesini döndürür.

2. SDM, eklenen programdan [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) arabirimini elde edebılır, SDM [iliştirme](../../extensibility/debugger/reference/idebugprogramex2-attach.md) yöntemini çağırır. Bu yaklaşım, bağlantı noktası sağlayıcısı tarafından uzaktan başlatılan programlar için tipik bir noktadır.

3. Program veya yöntemleri aracılığıyla iliştirilemez `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` , SDM, işlevi çağırarak (henüz yüklenmediyse) hata ayıklama altyapısını yükler `CoCreateInstance` ve ardından [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemini çağırır. Bu yaklaşım, bir bağlantı noktası sağlayıcısı tarafından yerel olarak başlatılan programlar için tipik bir noktadır.

    Özel bir bağlantı noktası sağlayıcısının `IDebugEngine2::Attach` yöntemi için özel bağlantı noktası tedarikçinin uygulamasındaki yöntemini çağırması de mümkündür `IDebugProgramEx2::Attach` . Genellikle bu durumda, özel bağlantı noktası sağlayıcısı uzak makinede hata ayıklama altyapısını başlatır.

   Oturum hata ayıklama Yöneticisi (SDM) [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metodunu çağırdığında ek elde edilir.

   Aynı işlem içinde DE ayıklanabilecek uygulamayla çalıştırırsanız, aşağıdaki [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)yöntemlerini uygulamanız gerekir:

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  `IDebugEngine2::Attach`Yöntemi çağrıldıktan sonra, yöntemi uygulamanızda şu adımları uygulayın `IDebugEngine2::Attach` :

1. SDM 'ye bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) Event nesnesi gönderin. Daha fazla bilgi için bkz. [olayları gönderme](../../extensibility/debugger/sending-events.md).

2. Yöntemine geçirilen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) nesnesinde [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini çağırın `IDebugEngine2::Attach` .

     Bu `GUID` , programı tanımlamak için kullanılan bir döndürür. , `GUID` ' A yerel programı temsil eden nesnesinde depolanmalıdır ve `IDebugProgram2::GetProgramId` yöntemi arabirimde çağrıldığında döndürülmelidir `IDebugProgram2` .

    > [!NOTE]
    > `IDebugProgramNodeAttach2`Arabirimini uygularsanız program `GUID` `IDebugProgramNodeAttach2::OnAttach` yöntemine geçirilir. Bu `GUID` Yöntem tarafından döndürülen program için kullanılır `GUID` `IDebugProgram2::GetProgramId` .

3. Yerel nesnenin [](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , `IDebugProgram2` programı göstermek IÇIN oluşturulduğunu, SDM 'ye bildirmek için bir IDebugProgramCreateEvent2 olay nesnesi gönderin. Ayrıntılar için bkz. [olayları gönderme](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Bu, `IDebugProgram2` metoduna geçirilen nesne değildir `IDebugEngine2::Attach` . Daha önce geçirilen `IDebugProgram2` nesne yalnızca bağlantı noktası tarafından tanınır ve ayrı bir nesnedir.

## <a name="see-also"></a>Ayrıca bkz.
- [Başlatma tabanlı ek](../../extensibility/debugger/launch-based-attachment.md)
- [Olayları gönderme](../../extensibility/debugger/sending-events.md)
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
