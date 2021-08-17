---
title: İşaretçiler Rapor | Microsoft Docs
description: İşaretçiler Raporu'nın görüntülenen zaman çerçevesindeki işaretçileri nasıl listeleyeni ve kaydırmanın veya yakınlaştırmanın işaretçilerin görünmeye veya kaybolmasına nasıl neden olabileceğini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 127193c854942836993ccdfe26ffb6e3642684746a7309551fcb188fc98cfdfd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121426384"
---
# <a name="markers-report"></a>İşaretçiler Raporu
İşaretçiler Raporu görüntülenen zaman çerçevesindeki işaretçileri listeler.  Şeritleri kaydırma, yakınlaştırma veya gizleme, işaretçilerin görünmesine veya kaybolmasına neden olabilir. Rapor, her işaretçiyle ilgili şu bilgileri içerir:

- İzlemenin başlangıcına göre başladığı zaman.

- Süresi. Bayraklar ve iletiler için süre sıfırdır çünkü bir anlık değeri temsil eder.

- Onu oluşturan iş parçacığının kimliği.

- Bunu oluşturan Windows (ETW) sağlayıcısı için Olay İzleme.

- Yazıldığı işaretçi serisi.

- Ait olduğu olayların kategorisi.

- Önem düzeyi.

- Türü (span, bayrak veya ileti).

- Neyi temsil ettiğine ilişkin üst düzey bir açıklama

  **İşaretçiler** Raporunu CSV dosyası olarak kaydetmek için Dışarı Aktar düğmesini seçin. CSV dosyasındaki verileri diğer uygulamalar veya araçlarla kullanabilirsiniz.

> [!NOTE]
> İşaretçiler Raporu 1.000 işaretçi görüntüler. Tüm işaretçileri görmek için raporun tamamını csv dosyasına aktarın.