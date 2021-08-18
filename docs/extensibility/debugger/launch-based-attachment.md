---
title: Başlatma Tabanlı Ek | Microsoft Docs
description: Otomatik olan ve el ile ekinki gibi bir yolu izleyen bir programa başlatma tabanlı ek hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f3839c1edb8b8406e5b5ae0645205f0316b88d62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065169"
---
# <a name="launch-based-attachment"></a>Başlatma tabanlı ek
Bir programın başlatma tabanlı eki otomatiktir. Programı barındıran işlem SDM tarafından başlatılan başlatma tabanlı ek, el ile ek yöntemine benzer bir yolu izler. Bilgi için [bkz. Programa ekleme.](../../extensibility/debugger/attaching-to-the-program.md)

## <a name="the-attaching-process"></a>Ekleme işlemi
 Temel fark, Attach çağrısının ardından aşağıdaki **gibi olayların** sırasıdır:

1. **SDM'ye bir IDebugEngineCreateEvent2** olay nesnesi gönderin. Ayrıntılar için [bkz. Olayları gönderme.](../../extensibility/debugger/sending-events.md)

2. Attach `IDebugProgram2::GetProgramId` yöntemine geçirilen **IDebugProgram2** arabiriminde **yöntemini** çağırma.

3. SDM'ye programı DE'ye temsil etmek için yerel **IDebugProgram2** nesnesinin oluşturulmuş olduğunu bildirmek için bir **IDebugProgramCreateEvent2** olay nesnesi gönderin.

4. SDM'ye başlatılan işlem için yeni bir iş parçacığının oluşturuluşunu bildirmek için [bir IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin.

## <a name="see-also"></a>Ayrıca bkz.
- [Gerekli olayları gönderme](../../extensibility/debugger/sending-the-required-events.md)
- [Bir programın hata ayıklamasını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
