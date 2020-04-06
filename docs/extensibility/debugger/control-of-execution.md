---
title: Yürütme kontrolü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739082"
---
# <a name="control-of-execution"></a>Yürütmenin kontrolü
Hata ayıklama altyapısı (DE) genellikle son başlangıç olayı olarak aşağıdaki olaylardan birini gönderir:

- Yeni başlatılan bir programa bağlıysa, giriş noktası olayı

- Zaten çalışan bir programa bağlıyorsanız, yükleme tam olay

  Her iki olay da olayları durdurur, yani DE IDE yoluyla kullanıcıdan yanıt bekler. Daha fazla bilgi için [Bkz. Operasyonel modlar.](../../extensibility/debugger/operational-modes.md)

## <a name="stopping-event"></a>Etkinliği durdurma
 Hata ayıklama oturumuna durdurma olayı gönderildiğinde:

1. Geçerli yönerge işaretçisini içeren program ve iş parçacığı olay arabiriminden elde edilebilir.

2. IDE, düzenleyicide vurgulandığı gibi görüntülediği geçerli kaynak kodu dosyasını ve konumunu belirler.

3. Hata ayıklama oturumu genellikle programın **Continue** yöntemini arayarak bu ilk durdurma olayına yanıt verir.

4. Program daha sonra kesme noktası vurmak gibi bir durdurma koşuluyla karşılaşına kadar çalışır. Bu durumda, DE hata ayıklama oturumuna bir kesme noktası olayı gönderir. Kesme noktası olayı bir durdurma olayıdır ve DE yine bir kullanıcı yanıtı bekler.

5. Kullanıcı bir işleve, bir işleve adım atmayı veya dışarı çıkmayı seçerse, IDE `Step` hata ayıklama oturumunu programın yöntemini çağırmak için ister. IDE daha sonra adım birimini (yönerge, deyim veya satır) ve adım türünü (işlevin içine, üzerine veya dışına adım atılıp atılmayacağı) geçer. Adım tamamlandığında, DE hata ayıklama oturumuna bir adım tam olay gönderir, bu bir durdurma olayıdır.

    -veya-

    Kullanıcı geçerli yönerge işaretçisinden yürütmeye devam etmeyi seçerse, IDE hata ayıklama oturumunu programın **Yürüt metodunu** çağırmak için ister. Program, bir sonraki durdurma koşuluyla karşılaşına kadar yürütmeye devam eder.

    -veya-

    Hata ayıklama oturumu belirli bir durdurma olayını yok saymak sayılsa, hata ayıklama oturumu programın **Devam** yöntemini çağırır. Program durdurma koşuluyla karşılaştığında bir işleve, üzerine veya dışına adım atıyorsa, adımı sürdürür.

   Programlı olarak, DE bir durdurma koşuluyla karşılaştığında, [iDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) gibi durdurma olaylarını bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi ile oturum hata ayıklama yöneticisine (SDM) gönderir. DE, programı ve geçerli yönerge işaretçisini içeren iş parçacığı temsil eden [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ve [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) arabirimlerini geçer. SDM, üst yığın çerçevesini almak için [IDebugThread2::EnumFrameInfo'yu](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) çağırır ve geçerli yönerge işaretçisiyle ilişkili belge bağlamını almak için [IDebugStackFrame2'yi çağırır.](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) Bu belge bağlamı genellikle bir kaynak kodu dosya adı, satır ve sütun numarasıdır. IDE, geçerli yönerge işaretçisini içeren kaynak kodu vurgulamak için bunları kullanır.

   SDM genellikle bu ilk durdurma olayına [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)' ı arayarak yanıt verir. Program daha sonra, bir kesme noktası vurmak gibi bir durdurma koşuluyla karşılaşına kadar çalışır ve bu durumda DE SDM'ye bir [IDebugBreakpointEvent2 Arabirimi](../../extensibility/debugger/reference/idebugbreakpointevent2.md) gönderir. Kesme noktası olayı bir durdurma olayıdır ve DE yine bir kullanıcı yanıtı bekler.

   Kullanıcı bir işleve, bir fonksiyona adım atmayı, aşmayı veya dışarı çıkmayı seçerse, IDE SDM'den [IDebugProgram2::Step'i](../../extensibility/debugger/reference/idebugprogram2-step.md)çağırmasını ister. IDE daha sonra [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (yönerge, deyim veya satır) ve [STEPKIND](../../extensibility/debugger/reference/stepkind.md), yani, içine adım, üzerinde veya işlevin dışına geçer. Adım tamamlandığında, DE SDM'ye bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabirimi gönderir, bu da durdurma olayıdır.

   Kullanıcı geçerli yönerge işaretçisinden yürütmeye devam etmeyi seçerse, IDE SDM'den [IDebugProgram2::Execute'i](../../extensibility/debugger/reference/idebugprogram2-execute.md)aramasını ister. Program, bir sonraki durdurma koşuluyla karşılaşına kadar yürütmeye devam eder.

   Hata ayıklama paketi belirli bir durdurma olayını yok saymak için ise, hata ayıklama paketi [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2-continue.md)çağıran SDM çağırır::Devam . Program durdurma koşuluyla karşılaştığında bir işleve, üzerine veya dışına adım atıyorsa, adımı sürdürür. Bu, programın bir basamak durumu koruduğu, böylece nasıl devam edeceğini bildiği anlamına gelir.

   SDM'nin yaptığı `Step`çağrılar , **Yürüt ve** **Devam** asynchronous'u, yani SDM çağrının hızlı bir şekilde dönmesini bekler. DE, SDM'ye aynı iş parçacığı üzerinde `Step`bir durdurma olayı gönderirse , **Yürüt veya** **Devam** döndürür, SDM askıda kalır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
