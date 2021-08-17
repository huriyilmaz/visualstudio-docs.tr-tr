---
title: Kesme noktaları (Visual Studio SDK) | Microsoft Docs
description: 'Üç kesme noktası türü hakkında bilgi edinmek için: beklemede, sınırda ve hata. Bu makalede türleri uygulamak için kullanılan arabirimler listeleniyor.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6aa20a2329416a16fb33776ad6b20db951b58da9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073415"
---
# <a name="breakpoints-visual-studio-sdk"></a>Kesme Noktaları (Visual Studio SDK)
Üç kesme noktası türü vardır: beklemede, sınırda ve hata.

 **Bekleyen bir kesme noktası:**

- Bir veya daha fazla programda bir veya daha fazla kod bağlamına bir kesme noktası bağlamak için gereken tüm bilgileri içeren bir soyutlamadır. Bir programda hata ayıklaması yapılan her zaman kodun yüklenmeye neden olması, hata ayıklama altyapısı bekleyen tüm kesme noktalarına bakarak bunların bağlanap bağlanamayabileceklerini denetler.

   Bekleyen bir kesme noktası hiçbir zaman koda bağlamaz, bunun yerine toplar ve bu kesme noktası tarafından oluşturulan tüm sınır kesme noktaları içerdiği kabul eder.

- [IDebugPendingBreakpoint2 arabirimiyle temsil](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) edildi.

  **Bağlı bir kesme noktası:**

- Tek bir kod bağlamıyla ilişkili veya tek bir kod bağlamına bağlı olan bir kesme noktası soyutlamadır. Her bağlı kesme noktası, bekleyen bir kesme noktası yanıt olarak oluşturulur. Öte yandan bekleyen bir kesme noktası birden fazla bağlı kesme noktası oluştursa da.

   Kod kaldırılmışsa, bağlı bir kesme noktası sınırsız olabilir ve atılır.

- [IDebugBoundBreakpoint2 arabirimiyle temsil](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) edildi.

  **Hata kesme noktası:**

- Bekleyen bir kesme noktası kod bağlamına bağlamaya çalışırken bir hatayı açıklamaya bir soyutlamadır. Hata kesme noktası, konumdaki veya kesme noktası ifadesinin kendisinde bir hatayı açıklar. Daha fazla bilgi için [bkz. Bağlama kesme noktaları.](../../extensibility/debugger/binding-breakpoints.md)

   Kesme noktası hatası bir hata veya uyarı olabilir.

- Bir [IDebugErrorBreakpoint2 arabirimiyle temsil](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) edildi.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
