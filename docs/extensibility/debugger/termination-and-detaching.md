---
title: Sonlandırma ve ayırma | Microsoft Docs
description: Normal sonlandırma, hata ayıklamakta olan bir programın, kesme noktaları, özel durumlar, çalışma zamanı hataları veya sonsuz döngüler olmadan tamamlanmasında çalıştığı anlamına gelir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 40a559a110792e5c010d37164ab1db96277ca544
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626366"
---
# <a name="termination-and-detaching"></a>Sonlandırma ve ayırma
Aşağıdaki bölümde normal sonlandırma açıklanmaktadır.

## <a name="discussion"></a>Tartışma
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) arabirimi devam ettikten sonra, hata ayıklama için bir kesme noktası, özel durum, çalışma zamanı hatası veya hatalı döngüler yoksa, hata ayıklamakta olan programın çalışmasının tamamlanması gerekir. Bu işlem normal sonlandırmada olur.

 Normal sonlandırmayı uygulamak için bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) göndermeniz gerekir. Normal sonlandırma, [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) yönteminin çalıştırılmasını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
