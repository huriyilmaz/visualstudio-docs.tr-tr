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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74ef32708374dd3fea4c181e85b9f67a239198ba
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995973"
---
# <a name="termination-and-detaching"></a>Sonlandırma ve ayırma
Aşağıdaki bölümde normal sonlandırma açıklanmaktadır.

## <a name="discussion"></a>Tartışma
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) arabirimi devam ettikten sonra, hata ayıklama için bir kesme noktası, özel durum, çalışma zamanı hatası veya hatalı döngüler yoksa, hata ayıklamakta olan programın çalışmasının tamamlanması gerekir. Bu işlem normal sonlandırmada olur.

 Normal sonlandırmayı uygulamak için bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) göndermeniz gerekir. Normal sonlandırma, [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) yönteminin çalıştırılmasını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
