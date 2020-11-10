---
title: İş Akışı Tasarımcısında desteklenmeyen hata ayıklama senaryoları
description: İş Akışı Tasarımcısı desteklenmeyen hata ayıklama senaryoları hakkında bilgi edinin, örneğin, "kod düzenlendikten sonra yürütme devam ettirilemez."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: d9ce8d15e44fecca673fdaa9fccd70ff13eb6783
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433524"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>İş Akışı Tasarımcısında desteklenmeyen hata ayıklama senaryoları

İş Akışı Tasarımcısı aşağıdaki hata ayıklama senaryolarını desteklemez:

- Kod düzenlendikten sonra yürütme devam ettirilemez.

- Yürütme, iş akışında rastgele bir noktadan (bir sonraki küme) devam ettirilemez.

- İmleçle ulaşılana kadar yürütme devam ettirilemez (Imlece Çalıştır).

- İş akışı Tasarımcısı, tasarımcı kullanımı olmadan kodda oluşturulan iş akışlarının hatalarını ayıklamak için kullanılamaz.

- Windows Workflow Foundation (WF) daha önceki sürümlerinde oluşturulan iş akışları .NET Framework 4 veya sonraki sürümlerde ayıklanamaz.

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
