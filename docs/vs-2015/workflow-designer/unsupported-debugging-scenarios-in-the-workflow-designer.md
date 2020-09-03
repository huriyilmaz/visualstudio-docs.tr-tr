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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606933"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>İş Akışı Tasarımcısında desteklenmeyen hata ayıklama senaryoları
İş Akışı Tasarımcısı [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] birçok yeni özellik ekledik, ancak desteklemediği bazı hata ayıklama senaryoları hala var. Bu belgede desteklenmeyen İş Akışı Tasarımcısı hata ayıklama senaryolarında ayrıntılar.

- Kod düzenlendikten sonra yürütme devam ettirilemez.

- Yürütme, iş akışında rastgele bir noktadan (bir sonraki küme) devam ettirilemez.

- İmleçle ulaşılana kadar yürütme devam ettirilemez (Imlece Çalıştır).

- İş akışı Tasarımcısı, tasarımcı kullanımı olmadan kodda oluşturulan iş akışlarının hatalarını ayıklamak için kullanılamaz.

- Önceki sürümlerinde oluşturulan iş akışlarının [!INCLUDE[wf](../includes/wf-md.md)] , tasarımcıda hata ayıklaması yapılamaz [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

- Kesme noktaları, etkinlikler veya düğümler arasındaki bağlantılarda tanımlanamaz <xref:System.Activities.Statements.Flowchart> .

- Pano hata ayıklama sırasında kullanılamaz.

- Etkinlikler kopyalandığında veya yapıştırılırken kesme noktaları korunmaz.

- Çağrı yığını penceresinde iş akışı kesme noktaları ayarlanamaz.

- Tasarımcıda kesme noktaları oluştururken, **Yeni kesme noktası** Iletişim kutusundaki **çizgi** ve **karakter** ayarları kullanılmaz.

- Kesme noktası penceresi veya kısayol menüsü, iş akışı hata ayıklaması için aşağıdaki sütunları veya seçenekleri desteklemez:

  - Koşul

  - İsabet sayısı

  - Isabet edildiğinde

  - İşlev

  - Veriler

  - İşleme

  - Ayrıştırılmış koda git
