---
title: Kırılma Noktaları (Visual Studio SDK) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739195"
---
# <a name="breakpoints-visual-studio-sdk"></a>Kesme Noktaları (Visual Studio SDK)
Üç tür kesme noktası vardır: beklemede, bağlı ve hata.

 **Bekleyen bir kesme noktası:**

- Bir veya daha fazla programdaki bir veya daha fazla kod bağlamına bir kesme noktası bağlamak için gereken tüm bilgileri içeren bir soyutlamadır. Hata ayıklama motoru, hata ayıklama kodunun yüklenmesine neden olan her programda, bağlanıp bağlanamayacaklarını görmek için bekleyen tüm kesme noktalarını denetler.

   Bekleyen bir kesme noktası nın kendisi asla koda bağlanmaz, daha çok toplar ve oluşturduğu tüm bağlı kesme noktalarını içerdiği söylenir.

- [Bir IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimi ile temsil edilir.

  **Bağlı bir kesme noktası:**

- Tek bir kod bağlamıyla ilişkili veya bağlı bir kesme noktası için soyutlamadır. Her bağlı kesme noktası bekleyen bir kesme noktasına yanıt olarak oluşturulur. Ancak bekleyen bir kesme noktası birden fazla bağlama kesme noktası oluşturabilir.

   Kod boşaltıldığında, bağlı bir kesme noktası bağlanmamış ve atılabilir.

- [Bir IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimi ile temsil edilir.

  **Bir hata kesme noktası:**

- Bekleyen bir kesme noktasını kod bağlamına bağlamaya çalışırken bir hatayı açıklamak için bir soyutlamadır. Hata kesme noktası, konumdaki veya kesme noktası ifadesinin kendisini açıklayan bir hatadır. Daha fazla bilgi için [Bağlama kesme noktalarına](../../extensibility/debugger/binding-breakpoints.md)bakın.

   Kesme noktası hatası bir hata veya bir uyarı olabilir.

- [Bir IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) arabirimi ile temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
