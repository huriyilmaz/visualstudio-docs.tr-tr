---
title: Yürütmenin denetimi | Microsoft Docs
description: Olayları durdurma hakkında bilgi edinin, bu da kullanıcının IDE aracılığıyla kullanıcıdan bir yanıt beklediği anlamına gelir.
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
ms.openlocfilehash: c93c767513592ff7e0fc2c971f7b1eeeca4873c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133282"
---
# <a name="control-of-execution"></a>Yürütmenin denetimi
Hata ayıklama altyapısı (DE) genellikle son başlatma olayı olarak aşağıdaki olaylardan birini gönderir:

- Yeni başlatılan bir programa eklenirken giriş noktası olayı

- Yük Tamam olayı, zaten çalışmakta olan bir programa eklenirken

  Bu olayların her ikisi de olayları durduruyor, yani Kullanıcı tarafından IDE aracılığıyla bir yanıt bekler. Daha fazla bilgi için bkz. [işletimsel modlar](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Olay durduruluyor
 Hata ayıklama oturumuna bir durdurma olayı gönderildiğinde:

1. Geçerli yönerge işaretçisini içeren program ve iş parçacığı olay arabiriminden elde edilebilir.

2. IDE, düzenleyicide vurgulanan şekilde görüntülenen geçerli kaynak kodu dosyasını ve konumunu belirler.

3. Hata ayıklama oturumu genellikle programın **Continue** metodunu çağırarak bu ilk durdurma olayına yanıt verir.

4. Daha sonra program, kesme noktasına vurarak bir durdurma koşuluyla karşılaşana kadar çalışır. Bu durumda, DE hata ayıklama oturumuna bir kesme noktası olayı gönderir. Kesme noktası olayı durdurma olayıdır ve bir kullanıcı yanıtı için DE bekler.

5. Kullanıcı bir işlevin içine, üzerine veya dışına adımla, IDE, hata ayıklama oturumunun programın yöntemini aramasını ister `Step` . Daha sonra IDE, adım birimini (yönerge, ifade veya satır) ve adım türünü (işlevin içine, üzerine veya dışına adımla) geçirir. Adım tamamlandığında, ve hata ayıklama oturumuna bir DE durdurma olayı olan bir adım Tamam olayı gönderir.

    -veya-

    Kullanıcı geçerli yönerge işaretçisinden yürütülmeye devam ederse, IDE, hata ayıklama oturumunun programın **Execute** metodunu çağırmasını ister. Program, bir sonraki durdurma koşuluyla karşılaşana kadar yürütmeyi sürdürür.

    -veya-

    Hata ayıklama oturumu belirli bir durdurma olayını yok sayıyorsa, hata ayıklama oturumu programın **Continue** yöntemini çağırır. Program durdurma koşuluyla karşılaştığı zaman bir işlevin içine, üzerine veya dışına adımlandıysa, adımla devam eder.

   Programlı olarak, bir durdurma koşuluyla karşılaştığında, [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) gibi durdurma olaylarını bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimi aracılığıyla oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir. DE, programı ve geçerli yönerge işaretçisini içeren iş parçacığını temsil eden [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) ve [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) arabirimlerini geçirir. SDM, en üstteki yığın çerçevesini almak için [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) çağırır ve geçerli yönerge işaretçiyle ilişkili belge bağlamını almak için [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) öğesini çağırır. Bu belge bağlamı genellikle kaynak kodu dosya adı, satır ve sütun numarasıdır. IDE, geçerli yönerge işaretçisini içeren kaynak kodunu vurgulamak için bunları kullanır.

   SDM genellikle [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)çağırarak bu ilk durdurma olayına yanıt verir. Daha sonra program, bir kesme noktasına vurarak (örneğin, SDM 'ye bir [IDebugBreakpointEvent2 arabirimi](../../extensibility/debugger/reference/idebugbreakpointevent2.md) gönderen) bir durdurma koşulu ile karşılaşana kadar çalışır. Kesme noktası olayı durdurma olayıdır ve bir kullanıcı yanıtı için DE bekler.

   Kullanıcı bir işlevin içine, üzerine veya dışına adımla, IDE, [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md)çağrısını yapmak için SDM 'yi uyarır. Daha sonra IDE, [Stepunit](../../extensibility/debugger/reference/stepunit.md) (yönerge, ekstre veya satır) ve [stepkind](../../extensibility/debugger/reference/stepkind.md), diğer bir deyişle, işlevinin işlevine mi, yoksa üzerinde mi yoksa dışına mı geçirilebileceğini geçirir. Adım tamamlandığında, DE bir durdurma olayı olan SDM 'ye bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) arabirimi gönderir.

   Kullanıcı geçerli yönerge işaretçisinden yürütülmeye devam etmek için, IDE, SDM 'nin [IDebugProgram2:: Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)çağrısını aramasını ister. Program, bir sonraki durdurma koşuluyla karşılaşana kadar yürütmeyi sürdürür.

   Hata ayıklama paketi belirli bir durdurma olayını yok sayıyorsa, hata ayıklama paketi [IDebugProgram2:: Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)ÖĞESINI çağıran SDM 'yi çağırır. Program durdurma koşuluyla karşılaştığı zaman bir işlevin içine, üzerine veya dışına adımlanıyor ise, bu adım devam eder. Bu, programın nasıl devam edebildiğini bilmesi için bir atlama durumu koruduğu anlamına gelir.

   SDM 'nin yaptığı çağrı `Step` , **yürütme** ve **devam etme** zaman uyumsuzdur ve bu, SDM 'nin çağrının hızlı dönmesini beklediği anlamına gelir. DE, SDM 'yi aynı iş parçacığında önce, yürütmeden veya devam etmeden önce durdurma olayı gönderirse, `Step` SDM yanıt vermeyi durduruyor.  

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
