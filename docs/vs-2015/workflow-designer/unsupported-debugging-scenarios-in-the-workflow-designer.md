---
title: İş Akışı Tasarımcısı desteklenmeyen hata ayıklama senaryoları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdbe68b416560b85580e3dd30e5f8138b7cd08fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606933"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>İş Akışı Tasarımcısında desteklenmeyen hata ayıklama senaryoları
İş Akışı Tasarımcısı [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] birçok yeni özellik ekledi, ancak hala desteklemediği bazı hata ayıklama senaryoları vardır. Bu belgede desteklenmeyen İş Akışı Tasarımcısı hata ayıklama senaryolarında ayrıntılar.

- Kod düzenlendikten sonra yürütme devam ettirilemez.

- Yürütme, iş akışında rastgele bir noktadan (bir sonraki küme) devam ettirilemez.

- İmleçle ulaşılana kadar yürütme devam ettirilemez (Imlece Çalıştır).

- İş akışı Tasarımcısı, tasarımcı kullanımı olmadan kodda oluşturulan iş akışlarının hatalarını ayıklamak için kullanılamaz.

- @No__t_0 önceki sürümlerinde oluşturulan iş akışlarının [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] tasarımcısında hata ayıklaması yapılamaz.

- Kesme noktaları, etkinlikler veya <xref:System.Activities.Statements.Flowchart> düğümleri arasındaki bağlantılarda tanımlanamaz.

- Pano hata ayıklama sırasında kullanılamaz.

- Etkinlikler kopyalandığında veya yapıştırılırken kesme noktaları korunmaz.

- Çağrı yığını penceresinde iş akışı kesme noktaları ayarlanamaz.

- Tasarımcıda kesme noktaları oluştururken, **Yeni kesme noktası** Iletişim kutusundaki **çizgi** ve **karakter** ayarları kullanılmaz.

- Kesme noktası penceresi veya kısayol menüsü, iş akışı hata ayıklaması için aşağıdaki sütunları veya seçenekleri desteklemez:

  - Koşul

  - İsabet sayısı

  - Isabet edildiğinde

  - İşlev

  - Veri

  - İşlem

  - Ayrıştırılmış koda git
