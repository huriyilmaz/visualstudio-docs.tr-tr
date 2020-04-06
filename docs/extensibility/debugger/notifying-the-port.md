---
title: Limana Bildirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738317"
---
# <a name="notify-the-port"></a>Bağlantı noktasını bildirin
Bir program başlatıldıktan sonra, bağlantı noktası aşağıdaki gibi bildirilmelidir:

1. Bir bağlantı noktası yeni bir program düğümü aldığında, hata ayıklama oturumuna bir program oluşturma olayı gönderir. Olay, programı temsil eden bir arabirimi de beraberinde taşır.

2. Hata ayıklama oturumu, ekinde olabilecek bir hata ayıklama altyapısının (DE) tanımlayıcısı için programı sorgular.

3. Hata ayıklama oturumu, DE'nin bu program için izin verilen DEs listesinde olup olmadığını denetler. Hata ayıklama oturumu, bu listeyi çözümün özgün olarak hata ayıklama paketi tarafından geçirilen etkin program ayarlarından alır.

    DE izin verilen ler listesinde olmalıdır, aksi takdirde DE programa iliştirilmez.

   Programlı olarak, bir bağlantı noktası ilk yeni bir program düğümü aldığında, programı temsil edecek bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimi oluşturur.

> [!NOTE]
> Bu hata ayıklama `IDebugProgram2` altyapısı (DE) tarafından daha sonra oluşturulan arabirim ile karıştırılmamalıdır.

 Bağlantı noktası, com `IConnectionPoint` arabirimi yoluyla oturum hata ayıklama yöneticisine (SDM) bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) program oluşturma olayını geri gönderir.

> [!NOTE]
> Bu, daha sonra `IDebugProgramCreateEvent2` DE tarafından gönderilen arabirim ile karıştırılmamalıdır.

 Olay arabiriminin kendisiyle birlikte, bağlantı noktası sırasıyla bağlantı noktasını, işlemi ve programı temsil eden [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)ve [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimlerini gönderir. SDM [iDebugProgram2 çağırır::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) programı hata ayıklamak olabilir DE GUID almak için. GUID ilk olarak [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabiriminden elde edilmiştir.

 SDM, DE'nin izin verilen DEs listesinde olup olmadığını denetler. SDM bu listeyi çözümün etkin program ayarlarından alır ve başlangıçta hata ayıklama paketi tarafından bu listeye aktarılır. DE izin verilen listede olmalıdır, aksi takdirde programa iliştirilmez.

 DE'nin kimliği bilindikten sonra, SDM onu programa iliştirmeye hazırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Program başlatma](../../extensibility/debugger/launching-a-program.md)
- [Başlatmadan sonra ekleme](../../extensibility/debugger/attaching-after-a-launch.md)
- [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md)
