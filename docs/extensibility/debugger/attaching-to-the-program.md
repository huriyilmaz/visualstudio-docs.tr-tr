---
title: Program | Microsoft Docs
description: Program Visual Studio bağlantı noktasına kaydedildikten sonra hata ayıklayıcı eklemenin nasıl uygulandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 70576204c655725ea68908424b6caad145cf21f0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627686"
---
# <a name="attach-to-the-program"></a>Programa ekleme
Programlarınızı uygun bağlantı noktasına kaydettikten sonra hata ayıklayıcıyı hata ayıklamak istediğiniz programa ekleysiniz.

## <a name="choose-how-to-attach"></a>Eklemeyi seçme
 Oturum hata ayıklama yöneticisinin (SDM) hata ayıklama yapılan programa eklemeye çalışması üç yol vardır.

1. Hata ayıklama altyapısı tarafından [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemiyle başlatılan programlar için (örneğin, yorumlanmış dillerin tipik bir örneği), SDM, ekli programla ilişkilendirilmiş [IDebugProgramNodeAttach2 nesnesinden IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimini elde eder. [](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) SDM arabirimini elde etmek `IDebugProgramNodeAttach2` için SDM [onAttach yöntemini](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) çağırar. yöntemi, programa ekleme yaptığını ve programa eklemek için başka girişimlerde bulun buluna olduğunu `IDebugProgramNodeAttach2::OnAttach` `S_OK` belirtmek için döndürür.

2. SDM, bağlı olan [programdan IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) arabirimini edinebilmişse, SDM [Attach yöntemini](../../extensibility/debugger/reference/idebugprogramex2-attach.md) çağrır. Bu yaklaşım, bağlantı noktası sağlayıcı tarafından uzaktan başlatılan programlar için tipik bir yaklaşımdır.

3. Program veya yöntemleri aracılığıyla eklenemiyorsa, SDM işlevi çağırarak hata ayıklama altyapısını yükler (henüz yüklenmemişse) ve ardından `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` Attach `CoCreateInstance` [yöntemini](../../extensibility/debugger/reference/idebugengine2-attach.md) çağırarak. Bu yaklaşım, bir bağlantı noktası sağlayıcı tarafından yerel olarak başlatılan programlar için tipik bir yaklaşımdır.

    Özel bir bağlantı noktası tedarikçinin yöntemi özel bağlantı `IDebugEngine2::Attach` noktası sağlayıcının uygulamasında yöntemini çağırarak da `IDebugProgramEx2::Attach` mümkündür. Bu durumda genellikle özel bağlantı noktası sağlayıcı uzak makinede hata ayıklama altyapısını başlatıyor.

   Oturum hata ayıklama yöneticisi (SDM) Attach yöntemini çağırarak ek [elde](../../extensibility/debugger/reference/idebugengine2-attach.md) edilir.

   DE'nizi hata ayıklanacak uygulamayla aynı işlemde çalıştırıyorsanız, aşağıdaki [IDebugProgramNode2 yöntemlerini uygulamanız gerekir:](../../extensibility/debugger/reference/idebugprogramnode2.md)

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  yöntemi `IDebugEngine2::Attach` çağrıldıktan sonra yöntemi uygulamanıza şu adımları `IDebugEngine2::Attach` uygulayın:

1. [SDM'ye bir IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesi gönderin. Daha fazla bilgi için [bkz. Olayları gönderme.](../../extensibility/debugger/sending-events.md)

2. Yöntemine geçirilen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) nesnesi üzerinde [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini `IDebugEngine2::Attach` çağırma.

     Bu, `GUID` programı tanımlamak için kullanılan bir döndürür. , yerel programı DE'ye temsil eden nesnesinde depolanmış olmalı ve arabirimde yöntem çağrıldında `GUID` `IDebugProgram2::GetProgramId` `IDebugProgram2` döndürüldü.

    > [!NOTE]
    > Arabirimini `IDebugProgramNodeAttach2` kullanırsanız programın `GUID` yöntemine `IDebugProgramNodeAttach2::OnAttach` geçirebilirsiniz. Bu, `GUID` yöntemi tarafından döndürülen program için `GUID` `IDebugProgram2::GetProgramId` kullanılır.

3. SDM'ye programı DE'ye temsil etmek için yerel nesnenin oluşturuluşunu bildirmek için [bir IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) `IDebugProgram2` olay nesnesi gönderin. Ayrıntılar için bkz. [Olayları Gönderme.](../../extensibility/debugger/sending-events.md)

    > [!NOTE]
    > Bu, `IDebugProgram2` yöntemine geçirilen nesneyle aynı `IDebugEngine2::Attach` değildir. Daha önce geçirilen `IDebugProgram2` nesne yalnızca bağlantı noktası tarafından tanınır ve ayrı bir nesnedir.

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
