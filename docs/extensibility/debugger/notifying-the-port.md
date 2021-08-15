---
title: Bağlantı noktasına bildiriliyor | Microsoft Docs
description: Program başlatıldıktan sonra bağlantı noktasının nasıl bildirileceğini öğrenin. Bu makale ayrıntılı bir açıklama içerir.
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
ms.openlocfilehash: eedd180f00844c6f38dd57b1c106d51a77b8ad1557bbcff21ddf15bb9be597c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342719"
---
# <a name="notify-the-port"></a>Bağlantı noktasına bildir
Bir program başlatıldıktan sonra, bağlantı noktasına aşağıdaki şekilde bildirilmesi gerekir:

1. Bir bağlantı noktası yeni bir program düğümü aldığında, bir program oluşturma olayını hata ayıklama oturumuna geri gönderir. Olay, programı temsil eden bir arabirimle birlikte taşınır.

2. Hata ayıklama oturumu programı, iliştireme bir hata ayıklama altyapısının (DE) tanımlayıcısı için sorgular.

3. Hata ayıklama oturumu, bu program için izin verilen DEs listesinde DE olup olmadığını denetler. Hata ayıklama oturumu bu listeyi çözümün etkin program ayarlarından alır, başlangıçta hata ayıklama paketi tarafından kendisine geçirilir.

    DE, izin verilen listede olmalıdır, aksi takdirde DE programa iliştirilmeyecektir.

   Programlı olarak, bir bağlantı noktası ilk olarak yeni bir program düğümü aldığında, programı temsil eden bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimi oluşturur.

> [!NOTE]
> Bu `IDebugProgram2` , daha sonra hata ayıklama altyapısı (de) tarafından oluşturulan arabirimle karıştırılmamalıdır.

 Bağlantı noktası bir COM arabirimi aracılığıyla oturum hata ayıklama Yöneticisi 'ne (SDM) bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) program oluşturma olayı gönderir `IConnectionPoint` .

> [!NOTE]
> Bu, `IDebugProgramCreateEvent2` daha sonra de tarafından gönderilen arabirimiyle karıştırılmamalıdır.

 Olay arabiriminin kendisiyle birlikte bağlantı noktası, sırasıyla bağlantı noktasını, işlemi ve programı temsil eden [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)ve [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) arabirimlerini gönderir. SDM, programda hata ayıklayacağınız DE GUID 'sini almak için [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) çağırır. GUID ilk olarak [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabiriminden elde edildi.

 SDM, izin verilen DEs listesinde DE olup olmadığını denetler. SDM Bu listeyi çözümün etkin program ayarlarından alır, başlangıçta hata ayıklama paketi tarafından kendisine geçirilir. DE, izin verilen listede olmalıdır, aksi takdirde programa eklenmez.

 DE kimliği bilindiğinde, SDM programa eklenmeye hazırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Program başlatma](../../extensibility/debugger/launching-a-program.md)
- [Bir başlatma işleminden sonra iliştirme](../../extensibility/debugger/attaching-after-a-launch.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
