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
ms.openlocfilehash: a2a406279d8e9123d342cd63d648206fd35c7b5f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033323"
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