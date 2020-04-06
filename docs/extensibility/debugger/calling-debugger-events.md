---
title: Arama Hata Ayıklama Etkinlikleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739170"
---
# <a name="call-debugger-events"></a>Hata ayıklama olaylarını arama
Hata ayıklama oturumlarında olaylar belirli bir sırada oluşur.

## <a name="discussion"></a>Tartışma
 Hata ayıklama altyapısı (DE) ve oturum hata ayıklama yöneticisi (SDM) arasındaki çağrıların modelini anlamak için, aşağıdaki ler tipik bir hata ayıklama oturumunda gerçekleşen olayların çağrı sırasını temsil eder:

1. [Bir programa ekleme ve ayırma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Hata ayıklamabaşlatma](../../extensibility/debugger/launching-the-debugger.md)

3. [Programı sonlandırma](../../extensibility/debugger/terminating-a-program.md)

4. [Kesme noktası oluşturma](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Bir kesme noktası bağlandığında veya bağlanmadığında](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Kesme noktası hataları](../../extensibility/debugger/breakpoint-errors.md)

7. [Bir kesme noktası vurmak](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Kesme noktasını silme](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Kesme moduna girme](../../extensibility/debugger/entering-break-mode.md)

10. [Kesme moduna girme](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Kesme modunda ifade değerlendirmesi](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Özel durum işleme](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
