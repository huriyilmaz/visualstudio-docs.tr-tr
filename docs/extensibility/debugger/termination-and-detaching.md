---
title: Fesih ve Ayırma | Microsoft Dokümanlar
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
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712492"
---
# <a name="termination-and-detaching"></a>Fesih ve ayırma
Aşağıdaki bölümde normal sonlandırma açıklanmaktadır.

## <a name="discussion"></a>Tartışma
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPoint2](../../extensibility/debugger/reference/idebugentrypointevent2.md) arabirimi devam ettikten sonra, uygulamada kesme noktaları, özel durumlar, çalışma zamanı hataları veya sonsuz döngüler yoksa, debugged olan program tamamlanmak üzere çalışır. Bu işlem normal sonlandırmadır.

 Normal sonlandırma uygulamak için bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) göndermeniz gerekir. Normal sonlandırma [iDebugProgramDestroyEvent2 çalıştırılması nı gerektirir::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) yöntemi.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
