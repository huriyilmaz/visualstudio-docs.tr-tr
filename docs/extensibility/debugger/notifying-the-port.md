---
title: Bağlantı Noktası Bildirimi | Microsoft Docs
description: Program başlattıktan sonra bağlantı noktasının nasıl bildirileceklerini öğrenin. Bu makale ayrıntılı bir açıklama içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1aaa319f0c6cd545e1f319ab7c8c510f694529d7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725832"
---
# <a name="notify-the-port"></a>Bağlantı noktasına bildirme
Programı başlattıktan sonra bağlantı noktasına aşağıdaki gibi bildirilecek:

1. Bağlantı noktası yeni bir program düğümü aldığında, program oluşturma olayı hata ayıklama oturumuna geri gönderir. Olayı, programı temsil eden bir arabirimle birlikte taşır.

2. Hata ayıklama oturumu, programda iliştirilen bir hata ayıklama altyapısının (DE) tanımlayıcısını sorgular.

3. Hata ayıklama oturumu, DE'nin bu program için izin verilebilir DE'ler listesinde olup değildir. Hata ayıklama oturumu, çözümün etkin program ayarlarından bu listeyi alır ve başlangıçta hata ayıklama paketi tarafından bu listeye geçiritir.

    DE izin verilebilir listesinde yer alalır, yoksa DE programa bağlı olmaz.

   Program aracılığıyla, bir bağlantı noktası yeni bir program düğümü aldığında, programı temsil etmek için [bir IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimi oluşturur.

> [!NOTE]
> Bu, daha sonra hata ayıklama `IDebugProgram2` altyapısı (DE) tarafından oluşturulan arabirimle karıştırılmamalıdır.

 Bağlantı noktası bir COM arabirimi kullanarak oturum hata ayıklama yöneticisine (SDM) [bir IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) program oluşturma olayı `IConnectionPoint` gönderir.

> [!NOTE]
> Bu, daha sonra `IDebugProgramCreateEvent2` DE tarafından gönderilen arabirimle karıştırılmamalıdır.

 Olay arabiriminin kendisiyle birlikte, bağlantı noktası sırasıyla bağlantı noktasını, işlemi ve programı temsil eden [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)ve [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimlerini gönderir. SDM, programda hata ayıklayabilmesi için DE GUID'lerini almak için [IDebugProgram2::GetEngineInfo'yu](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) arar. GUID ilk olarak [IDebugProgramNode2 arabiriminden alındı.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 SDM, DE'nin izin verilebilir DE'ler listesinde olup olduğunu denetler. SDM, çözümün etkin program ayarlarından bu listeyi alır ve başlangıçta hata ayıklama paketi tarafından bu listeye geçiritir. DE izin verilebilir listede olmalı, yoksa programa bağlı olmaz.

 DE kimliği bilindiği zaman, SDM bunu programa eklemeye hazırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Programı başlatma](../../extensibility/debugger/launching-a-program.md)
- [Başlatmadan sonra ekleme](../../extensibility/debugger/attaching-after-a-launch.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
