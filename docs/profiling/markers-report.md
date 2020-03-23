---
title: İşaretçiler Raporu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9502d2cf0081985cfbee2283af820c06d681ad9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "64808265"
---
# <a name="markers-report"></a>İşaretçiler Raporu
İşaretçiler Raporu, görüntülenen zaman dilimindeki işaretçileri listeler.  Kaydırma veya yakınlaştırma veya şeritleri gizleme, işaretçilerin görünmesine veya kaybolmasına neden olabilir. Rapor, her işaretçi hakkında şu bilgileri içerir:

- Başladığı zaman, izin başlangıcına göre.

- Süresi. Bir an temsil ettikleri için süre bayraklar ve iletiler için sıfırdır.

- Onu oluşturan iş parçacığının kimliği.

- Onu oluşturan Windows için Olay İzleme (ETW) sağlayıcısı.

- Yazıldığı işaret serisi.

- Ait olduğu olaylar kategorisi.

- Önemi düzeyi.

- Türü (yayılma alanı, bayrak veya ileti).

- Neyi temsil edenüst düzey bir açıklama

  İşaretçiler Raporunu CSV dosyası olarak kaydetmek için **Dışa** Aktarma düğmesini seçin. CSV dosyasındaki verileri diğer uygulamalar veya araçlarla kullanabilirsiniz.

> [!NOTE]
> İşaretçiler Raporu 1.000 işaretçi görüntüleyebilir. Tüm işaretçileri görmek için raporun tamamını bir CSV dosyasına aktarın.