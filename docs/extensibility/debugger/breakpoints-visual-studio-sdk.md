---
title: kesme noktaları (Visual Studio SDK) | Microsoft Docs
description: 'Üç kesme noktası türü hakkında bilgi edinin: bekleyen, bağlantılı ve hata. Bu makalede, türleri uygulamak için kullanılan arabirimler listelenmektedir.'
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636486"
---
# <a name="breakpoints-visual-studio-sdk"></a>Kesme Noktaları (Visual Studio SDK)
Üç kesme noktası türü vardır: bekleyen, bağlantılı ve hata.

 **Bekleyen bir kesme noktası:**

- Bir veya daha fazla programda bir veya daha fazla kod bağlamına bir kesme noktası bağlamak için gereken tüm bilgileri içeren bir soyutlamadır. Hata ayıklamakta olan bir programın kodun yüklenmesine neden olması, hata ayıklama altyapısı, bağlanıp bağlanamayacağını görmek için tüm bekleyen kesme noktalarını denetler.

   Bekleyen bir kesme noktasının kendisi hiçbir şekilde koda bağlanmaz, ancak bunun yerine topladığı ve oluşturduğu tüm bağlı kesme noktalarını içerdiğini söyluyor.

- Bir [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) arabirimi tarafından temsil edilir.

  **Bir bağlantılı kesme noktası:**

- , İle ilişkili veya tek bir kod bağlamı ile bağlantılı bir kesme noktası için soyutlamadır. Her bir bağlantılı kesme noktası, bekleyen bir kesme noktasına yanıt olarak oluşturulur. Ancak, bekleyen bir kesme noktası, birden fazla bağlantılı kesme noktası oluşturabilir.

   Kod kaldırıldığında, bağlı bir kesme noktası ilişkisiz ve atılır.

- Bir [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) arabirimi tarafından temsil edilir.

  **Hata kesme noktası:**

- , Bekleyen bir kesme noktasını bir kod bağlamına bağlamaya çalışırken bir hatayı açıklamak için soyutlamadır. Hata kesme noktası, konumda veya kesme noktası ifadesinin kendisinde bir hata olduğunu açıklar. Daha fazla bilgi için bkz. [bağlama kesme noktaları](../../extensibility/debugger/binding-breakpoints.md).

   Kesme noktası hatası bir hata ya da uyarı olabilir.

- Bir [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Kod bağlamı](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
