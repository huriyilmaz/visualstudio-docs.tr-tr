---
title: Hata ayıklayıcı olaylarını çağırma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3deef418620ab17297b4ef7e824a0d95c25e439e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904318"
---
# <a name="call-debugger-events"></a>Hata ayıklayıcı olaylarını çağırma
Hata ayıklama oturumlarındaki olaylar belirli bir sırada oluşur.

## <a name="discussion"></a>Tartışma
 Hata ayıklama altyapısı (DE) ve oturum hata ayıklama Yöneticisi (SDM) arasındaki çağrıların düzenini anlamak için, aşağıdaki, tipik bir hata ayıklama oturumunda gerçekleşen olayların arama sırasını temsil eder:

1. [Bir programa ekleme ve ayırma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Hata ayıklayıcı başlatılıyor](../../extensibility/debugger/launching-the-debugger.md)

3. [Program sonlandırılıyor](../../extensibility/debugger/terminating-a-program.md)

4. [Kesme noktası oluşturma](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Bir kesme noktası bağlandığında veya ilişkisiz duruma geldiğinde](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Kesme noktası hataları](../../extensibility/debugger/breakpoint-errors.md)

7. [Kesme noktasına vurun](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Kesme noktasını silme](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Kesme moduna giriliyor](../../extensibility/debugger/entering-break-mode.md)

10. [Kesme modunda adımla](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Kesme modunda ifade değerlendirmesi](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Özel durum işleme](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
