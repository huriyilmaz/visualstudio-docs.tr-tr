---
title: Yürütme Denetimi | Microsoft Docs
description: De'nin IDE ile kullanıcıdan yanıt beklemesi anlamına gelen olayları durdurma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 26a063fd6eac65efd5f6d1dea46b764c0594cbb85e064ecee9078599fdd9ec85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262938"
---
# <a name="control-of-execution"></a>Yürütme denetimi
Hata ayıklama altyapısı (DE) genellikle son başlangıç olayı olarak aşağıdaki olaylardan birini gönderir:

- Yeni başlatılan bir programa ekıyorsanız giriş noktası olayı

- Zaten çalışan bir programa iliştirilen yükleme tamamlandı olayı

  Bu iki olay da olayları durduruyor, yani DE IDE ile kullanıcıdan yanıt bekler. Daha fazla bilgi için bkz. [İşletim modları.](../../extensibility/debugger/operational-modes.md)

## <a name="stopping-event"></a>Olay durduruluyor
 Hata ayıklama oturumuna bir durdurma olayı gönder geldiğinde:

1. Geçerli yönerge işaretçisini içeren program ve iş parçacığı olay arabiriminden edinebilirsiniz.

2. IDE geçerli kaynak kodu dosyasını ve konumunu belirler ve düzenleyicide vurgulanmış olarak görüntülenir.

3. Hata ayıklama oturumu genellikle programın Continue yöntemini çağırarak bu ilk durdurma olayına **yanıt** verir.

4. Program daha sonra kesme noktası gibi bir durdurma koşuluyla karşılaşana kadar çalışır. Bu durumda DE, hata ayıklama oturumuna bir kesme noktası olayı gönderir. Kesme noktası olayı bir durdurma olayıdır ve DE yeniden bir kullanıcı yanıtı bekler.

5. Kullanıcı bir işleve adım atarak veya işlevden çıkmayı seçerse, IDE hata ayıklama oturumuna programın yöntemini çağırmasını `Step` ister. IDE daha sonra adım birimini (yönerge, deyim veya satır) ve adım türünü (işleve adım atarak, tekrarla veya işlevden çıkararak) iletir. Adım tamamlandığında DE, hata ayıklama oturumuna bir adım tamamlama olayı gönderir ve bu bir durdurma olayıdır.

    -veya-

    Kullanıcı geçerli yönerge işaretçisini yürütmeye devam ederse, IDE hata ayıklama oturumundan programın Execute yöntemini **çağırmasını** istenir. Program, sonraki durdurma koşuluyla karşılaşana kadar yürütmeyi sürdürür.

    -veya-

    Hata ayıklama oturumu belirli bir durdurma olayı yoksaymaksa, hata ayıklama oturumu programın **Continue** yöntemini çağırar. Program, durdurma koşuluyla karşılaştığında bir işleve adımlandı, bitti veya işlevin dışında kaldı ise adıma devam eder.

   Program aracılığıyla, DE bir durdurma koşuluyla karşılaştığında, [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) gibi durdurma olaylarını bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi aracılığıyla oturum hata ayıklama yöneticisine (SDM) gönderir. DE, programı ve geçerli yönerge işaretçisini içeren iş parçacığını temsil eden [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ve [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) arabirimlerini iletir. SDM, en üst yığın çerçevesini almak [için IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) ve geçerli yönerge işaretçisiyle ilişkili belge bağlamını almak için [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) çağrısında bulundu. Bu belge bağlamı genellikle bir kaynak kodu dosya adı, satırı ve sütun numarasıdır. IDE, geçerli yönerge işaretçisini içeren kaynak kodu vurgulamak için bunları kullanır.

   SDM genellikle [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)çağrısıyla bu ilk durdurma olayına yanıt verir. Program daha sonra bir kesme noktası isabet gibi bir durdurma koşuluyla karşılaşana kadar çalışır; bu durumda DE, SDM'ye [bir IDebugBreakpointEvent2 Arabirimi](../../extensibility/debugger/reference/idebugbreakpointevent2.md) gönderir. Kesme noktası olayı bir durdurma olayıdır ve DE yeniden bir kullanıcı yanıtı bekler.

   Kullanıcı bir işleve adımlamayı, bu işlevden çıkmayı veya işlevden çıkmayı seçerse, IDE SDM'den [IDebugProgram2::Step'i çağırmasını ister.](../../extensibility/debugger/reference/idebugprogram2-step.md) IDE daha sonra [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (yönerge, deyim veya satır) ve [STEPKIND](../../extensibility/debugger/reference/stepkind.md)'i (işlevin içine, üzerine veya dışında) iletir. Adım tamamlandığında DE, SDM'ye durdurma olayı olan [bir IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabirimi gönderir.

   Kullanıcı geçerli yönerge işaretçisi ile yürütmeye devam ederse, IDE SDM'den [IDebugProgram2::Execute'u çağırmasını isterse.](../../extensibility/debugger/reference/idebugprogram2-execute.md) Program, sonraki durdurma koşuluyla karşılaşana kadar yürütmeyi sürdürür.

   Hata ayıklama paketi belirli bir durdurma olayı yoksaymaksa, hata ayıklama paketi [IDebugProgram2::Continue'i](../../extensibility/debugger/reference/idebugprogram2-continue.md)çağıran SDM'i çağırar. Program, durdurma koşuluyla karşılaştığında bir işleve adımlandı, bitti veya işlevin dışında kaldı ise adıma devam eder. Bu, programın nasıl devam edeceğini bildiği için bir adımlama durumuna sahip olduğunu ifade eder.

   SDM'nin , Yürütme ve Devam'a ettiği çağrılar zaman uyumsuz olur; bu da SDM'nin çağrının hızlı bir şekilde `Step` dönmesini beklemesi anlamına gelir.   DE, SDM'ye aynı iş parçacığında, Yürüt veya Devam'dan önce bir durdurma olayı `Step` gönderirse, SDM yanıt vermez. 

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
