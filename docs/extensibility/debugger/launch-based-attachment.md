---
title: Başlatma tabanlı ek | Microsoft Docs
description: Otomatik olan ve el ile ek gibi bir yolu izleyen bir programa başlatma tabanlı ek hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e041c692a833b7d0a1891c078388a3f5b2d11e4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606677"
---
# <a name="launch-based-attachment"></a>Başlatma tabanlı ek
Bir programa başlatma tabanlı ek otomatik. Programı barındıran işlem SDM tarafından başlatıldığında, başlatma tabanlı ek el ile ek yöntemine benzer bir yol izler. Bilgi için bkz. [programa iliştirme](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>İliştirme işlemi
 Ana fark, aşağıdaki gibi, **iliştirme** çağrısını izleyen olayların sırasıdır:

1. SDM 'ye bir **IDebugEngineCreateEvent2** Event nesnesi gönderin. Ayrıntılar için bkz. [olayları gönderme](../../extensibility/debugger/sending-events.md).

2. `IDebugProgram2::GetProgramId` **Attach** yöntemine geçirilen **IDebugProgram2** arabirimindeki yöntemi çağırın.

3. Yerel **IDebugProgram2** nesnesinin program tarafından da temsil etmek IÇIN oluşturulduğunu SDM 'ye bildirmek Için bir **IDebugProgramCreateEvent2** olay nesnesi gönderin.

4. SDM 'yi Başlatan işlem için yeni bir iş parçacığının oluşturulduğunu bildirmek için bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Gerekli olayları gönder](../../extensibility/debugger/sending-the-required-events.md)
- [Bir programın ayıklanamayacağını etkinleştir](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
