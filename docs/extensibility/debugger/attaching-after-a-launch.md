---
title: Bir Lansmandan Sonra Takma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739290"
---
# <a name="attach-after-a-launch"></a>Başlatmadan sonra ekleme
Bir program başlattıktan sonra, hata ayıklama oturumu hata ayıklama altyapısını (DE) belirtilen programa iliştirmeye hazırdır.

## <a name="design-decisions"></a>Tasarım kararları
 Paylaşılan bir adres alanı içinde iletişim daha kolay olduğundan, iki tasarım yaklaşımı arasında seçim yapmanız gerekir: hata ayıklama oturumu ile DE arasındaki iletişimi ayarlayın. Veya DE ile program arasındaki iletişimi ayarlayın. Aşağıdakiler arasında seçim yapın:

- Hata ayıklama oturumu ile DE arasındaki iletişimi ayarlamak daha mantıklıysa, hata ayıklama oturumu DE'yi birlikte oluşturur ve DE'den programa eklenmesini ister. Bu tasarım hata ayıklama oturumunu ve DE'yi bir adres alanında, çalışma zamanı ortamını ve programı başka bir adresalanında bir arada bırakır.

- DE ve program arasındaki iletişimi kurmak daha mantıklıysa, çalışma zamanı ortamı DE'yi birlikte oluşturur. Bu tasarım, SDM'yi bir adres alanında ve DE, çalışma zamanı ortamında ve programı başka bir adreste bir arada bırakır. Bu tasarım, komut dosyası dillerini çalıştırmak için bir yorumlayıcı ile uygulanan bir DE tipiktir.

    > [!NOTE]
    > DE'nin programa nasıl iliştirilir, uygulamaya bağlıdır. DE ve program arasındaki iletişim de uygulamaya bağlıdır.

## <a name="implementation"></a>Uygulama
 Programlı olarak, oturum hata ayıklama yöneticisi (SDM) başlatılacak programı temsil eden [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) nesnesini ilk aldığında, daha sonra hata ayıklama olaylarını SDM'ye geçirmek için kullanılan bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesini geçirerek [Ekle](../../extensibility/debugger/reference/idebugprogram2-attach.md) yöntemini çağırır. Yöntem `IDebugProgram2::Attach` daha sonra [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır. SDM'nin `IDebugProgram2` arabirimi nasıl aldığı hakkında daha fazla bilgi için [bkz.](../../extensibility/debugger/notifying-the-port.md)

 DE'nizin hata ayıkladığınız programla aynı adres alanında çalışması gerekiyorsa: DE genellikle komut dosyası çalıştıran bir yorumlayıcının parçası olduğundan, `IDebugProgramNodeAttach2::OnAttach` yöntem döndürür. `S_FALSE` İade, `S_FALSE` ekleme işlemini tamamladığını gösterir.

 Ancak, DE SDM adres `IDebugProgramNodeAttach2::OnAttach` alanında çalışırsa: yöntem döndürür `S_OK`veya [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimi hata ayıklama programı ile ilişkili [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi üzerinde hiç uygulanmaz. Bu durumda, [ekle](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi sonunda ekleme işlemini tamamlamak için çağrılır.

 İkinci durumda, `IDebugEngine2::Attach` yönteme geçirilen `GUID` `GUID` `IDebugProgram2::GetProgramId` `IDebugProgram2` nesne üzerinde [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini aramanız, yerel program nesnesinde depolamanız ve yöntem daha sonra bu nesneye çağrıldığında bunu döndürmeniz gerekir. Program, `GUID` çeşitli hata ayıklama bileşenleri arasında benzersiz olarak tanımlamak için kullanılır.

 Döndürülen `IDebugProgramNodeAttach2::OnAttach` `S_FALSE`yöntem `GUID` durumunda, program için kullanılacak yöntem bu yönteme geçirilir ve `IDebugProgramNodeAttach2::OnAttach` yerel program `GUID` nesnesi üzerinde ayarlar yöntemidir.

 DE artık programa bağlı ve başlangıç olaylarını göndermeye hazır.

## <a name="see-also"></a>Ayrıca bkz.
- [Doğrudan bir programa bağlanma](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Bağlantı noktasını bildirme](../../extensibility/debugger/notifying-the-port.md)
- [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [İliştir](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [İliştir](../../extensibility/debugger/reference/idebugengine2-attach.md)
