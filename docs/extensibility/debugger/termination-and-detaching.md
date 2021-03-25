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
ms.workload:
- vssdk
ms.openlocfilehash: 8662809b50dbfec3046af1d0d6b6fa151c3a33e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057838"
---
# <a name="termination-and-detaching"></a>Sonlandırma ve ayırma
Aşağıdaki bölümde normal sonlandırma açıklanmaktadır.

## <a name="discussion"></a>Tartışma
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) arabirimi devam ettikten sonra, hata ayıklama için bir kesme noktası, özel durum, çalışma zamanı hatası veya hatalı döngüler yoksa, hata ayıklamakta olan programın çalışmasının tamamlanması gerekir. Bu işlem normal sonlandırmada olur.

 Normal sonlandırmayı uygulamak için bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) göndermeniz gerekir. Normal sonlandırma, [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) yönteminin çalıştırılmasını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
