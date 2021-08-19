---
title: Hata ayıklama desteklenmeyen senaryolar
description: İş Akışı Tasarımcısı'de desteklenmeyen hata ayıklama senaryoları hakkında bilgi İş Akışı Tasarımcısı örneğin, "Kod düzenlendikten sonra yürütme devam edeleyemez."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: fbc2e7c2c465196bfc4781bf7cda7e3d0bd9dd8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098937"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>İş Akışı Tasarımcısında desteklenmeyen hata ayıklama senaryoları

Aşağıdaki İş Akışı Tasarımcısı hata ayıklama senaryolarını desteklemez:

- Kod düzenlendikten sonra yürütme devamamaz.

- Yürütme, iş akışında rastgele bir noktadan devamamaz (Sonrakini Ayarla).

- İmleç ulaşıncaya kadar yürütme devamamaz (İmleçte Çalıştır).

- İş akışı tasarımcısı, tasarımcı kullanılmadan kodda oluşturulan iş akışlarının hata ayıklaması için kullanılamaz.

- Windows Workflow Foundation'ın (WF) önceki sürümlerinde oluşturulan iş akışları 4 veya .NET Framework hata ayık olamaz.

- Kesme noktaları etkinlikler veya düğümler arasındaki bağlantılarda <xref:System.Activities.Statements.Flowchart> tanımlanmalıdır.

- Hata ayıklama sırasında pano kullanılamaz.

- Etkinlikler kopyalanır veya yapıştırıldıklarda kesme noktaları korunur.

- İş akışı kesme noktaları, çağrı yığını penceresinde ayar kullanılamaz.

- Tasarımcıda kesme noktaları oluştururken, Yeni **Kesme Noktası** **iletişim** kutusundaki Satır **ve** Karakter ayarları kullanılmaz.

- Kesme noktası penceresi veya kısayol menüsü, iş akışı hata ayıklaması için aşağıdaki sütunları veya seçenekleri desteklemez:

  - Koşul

  - Isabet Sayısı

  - Ne Zaman Isabet

  - İşlev

  - Veriler

  - İşleme

  - Parçalara Ayır'a gidin
