---
title: Hata ayıklama desteklenmeyen senaryolar
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
ms.openlocfilehash: 4e98e2a75905f4c0a4c007691a99961dbcf1477c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996272"
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
