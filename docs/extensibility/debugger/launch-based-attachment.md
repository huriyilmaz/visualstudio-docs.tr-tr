---
title: Başlatma Tabanlı Eki | Microsoft Dokümanlar
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
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738466"
---
# <a name="launch-based-attachment"></a>Başlatma tabanlı eki
Bir programa başlatma tabanlı eki otomatiktir. Programı barındıran işlem SDM tarafından başlatıldığında, başlatma tabanlı eki, el ile bağlanma yöntemine benzer bir yol izler. Bilgi için [programa ekle'ye](../../extensibility/debugger/attaching-to-the-program.md)bakın.

## <a name="the-attaching-process"></a>Ekleme işlemi
 Temel fark, **Ekle** çağrısından sonraki olayların sırasıdır:

1. SDM'ye bir **IDebugEngineCreateEvent2** olay nesnesi gönderin. Ayrıntılar için [etkinlik Gönder'e](../../extensibility/debugger/sending-events.md)bakın.

2. **Ekle** `IDebugProgram2::GetProgramId` yöntemine geçen **IDebugProgram2** arabirimindeki metodu arayın.

3. SDM'ye programı de'ye temsil etmek üzere yerel **IDebugProgram2** nesnesinin oluşturulduğunu bildirmek için bir **IDebugProgramCreateEvent2** olay nesnesi gönderin.

4. SDM'ye başlatılan işlem için yeni bir iş parçacığı oluşturulduğunu bildirmek için bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Gerekli olayları gönderme](../../extensibility/debugger/sending-the-required-events.md)
- [Bir programın debutlanmasını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
