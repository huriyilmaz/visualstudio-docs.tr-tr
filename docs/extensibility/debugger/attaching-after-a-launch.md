---
title: Başlatma Sonrasında Ekleme | Microsoft Docs
description: Bir program başlatıcıda hata ayıklama oturumu, hata ayıklama altyapısını programa eklemeye hazırdır. Hata ayıklama altyapısıyla iletişim için bir tasarım yaklaşımı seçin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3f16df10717ae0d13ac4add90d25ea5be7d3208c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111859"
---
# <a name="attach-after-a-launch"></a>Başlatmadan sonra ekleme
Program başladıktan sonra hata ayıklama oturumu, hata ayıklama altyapısını (DE) ilgili programa eklemeye hazırdır.

## <a name="design-decisions"></a>Tasarım kararları
 Paylaşılan adres alanı içinde iletişim daha kolay olduğundan, iki tasarım yaklaşımı arasında seçim yapmak gerekir: hata ayıklama oturumu ile DE arasında iletişim ayarlama. Veya DE ile program arasındaki iletişimi ayarlayın. Aşağıdakiler arasında seçim yapın:

- Hata ayıklama oturumu ile DE arasındaki iletişimi ayarlamak daha mantıklı olursa, hata ayıklama oturumu DE'nin bir kez daha oluşturur ve DE'den programa eklemesi için bunu sorar. Bu tasarım, hata ayıklama oturumunu ve DE'i bir adres alanı ve çalışma zamanı ortamı ile programı birlikte başka bir adreste bırakır.

- DE ile program arasındaki iletişimi ayarlamak daha mantıklı olursa, çalışma zamanı ortamı DE'nin birlikte oluşturur. Bu tasarım, SDM'i bir adres alanı ve DE, çalışma zamanı ortamı ve program birlikte başka bir adres alanı içinde bırakır. Bu tasarım, betik dillerini çalıştırmak için yorumlayıcı ile uygulanan bir DE'nin tipik bir tasarımıdır.

    > [!NOTE]
    > DE'nin programa nasıl ekli olduğu uygulamaya bağlıdır. DE ile program arasındaki iletişim de uygulamaya bağlıdır.

## <a name="implementation"></a>Uygulama
 Program aracılığıyla, oturum hata ayıklama yöneticisi (SDM) başlatılan programı temsil eden [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) [](../../extensibility/debugger/reference/idebugprogram2-attach.md) nesnesini ilk aldığında Attach yöntemini çağırarak, daha sonra hata ayıklama olaylarını SDM'ye geri geçirmede kullanılan [bir IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi iletir. Yöntem `IDebugProgram2::Attach` daha sonra [OnAttach yöntemini](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) çağırar. SDM'nin arabirimi nasıl aldığı hakkında daha fazla bilgi `IDebugProgram2` için [bkz. Bağlantı noktasını bildirme.](../../extensibility/debugger/notifying-the-port.md)

 DE'nizin hata ayıklamakta olduğu programla aynı adres alanda çalışması gerekirse: DE genellikle betik çalıştıran bir yorumlayıcının parçası olduğundan yöntemi `IDebugProgramNodeAttach2::OnAttach` `S_FALSE` döndürür. `S_FALSE`dönüş, ekleme işlemini tamamlamış olduğunu gösterir.

 Ancak DE, SDM'nin adres alanı içinde çalışıyorsa: yöntemi döndürür veya hata ayıklamış olduğunu programla ilişkili `IDebugProgramNodeAttach2::OnAttach` `S_OK` [IDebugProgramNode2 nesnesinde IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnode2.md) [](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimi uygulanmaz. Bu durumda, [attach işlemini](../../extensibility/debugger/reference/idebugengine2-attach.md) tamamlamak için Sonunda Attach yöntemi çağrılır.

 İkinci durumda, yöntemine geçirilen nesnede [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini çağırmanız, yerel program nesnesinde depolamanız ve bu nesnede daha sonra yöntem çağrıldı olduğunda bunu geri `IDebugProgram2` `IDebugEngine2::Attach` `GUID` `GUID` `IDebugProgram2::GetProgramId` dönmeniz gerekir. `GUID`çeşitli hata ayıklama bileşenlerinde programı benzersiz olarak tanımlamak için kullanılır.

 döndüren yönteminde, program için kullanmak üzere yöntemi bu yönteme geçirildi ve yerel program nesnesinde ayar `IDebugProgramNodeAttach2::OnAttach` `S_FALSE` `GUID` `IDebugProgramNodeAttach2::OnAttach` `GUID` yöntemdir.

 DE artık programa ekli ve başlangıç olaylarını göndermeye hazırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Doğrudan bir programa ekleme](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Bağlantı noktasını bildirme](../../extensibility/debugger/notifying-the-port.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [İliştir](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [İliştir](../../extensibility/debugger/reference/idebugengine2-attach.md)
