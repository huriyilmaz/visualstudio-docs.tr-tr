---
title: İşaret raporu | Microsoft Docs
description: Işaretleyiciler raporunun görüntülenen zaman çerçevesinde işaretleyicileri nasıl listeleyeceğinizi ve kaydırma ya da yakınlaştırma işaretlerinin görünme veya kaybolmasının nasıl neden olabileceğini öğrenin.
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
ms.openlocfilehash: 7e95cf3b14f804c481ff03ec6fbf72b360efedc7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722119"
---
# <a name="markers-report"></a>İşaretçiler Raporu
Işaretçiler raporu, görünen zaman çerçevesinde işaretçileri listeler.  Yolları kaydırma veya büyütme ya da gizleme, işaretleyicilerin görünmesine veya kaybolmasına neden olabilir. Rapor, her işaretleyici hakkında şu bilgileri içerir:

- İzlemenin başlangıcına göre başladığı zaman.

- Süresi. Bir anlık temsil ettiğinden, bayraklar ve mesajlar için süre sıfırdır.

- Kendisini oluşturan iş parçacığının KIMLIĞI.

- Onu oluşturan Windows (ETW) sağlayıcısı için olay Izleme.

- Yazıldığı işaretleyici serisi.

- Ait olduğu olayların kategorisi.

- Önem düzeyi.

- Türü (span, flag veya Message).

- Temsil edilecek özellikler için üst düzey bir açıklama

  Işaretleyiciler raporunu bir CSV dosyası olarak kaydetmek için **dışarı aktar** düğmesini seçin. CSV dosyasındaki verileri diğer uygulamalarla veya araçlarla kullanabilirsiniz.

> [!NOTE]
> Işaretçiler raporu 1.000 işaretçileri gösterebilir. Tüm işaretçileri görmek için, tam raporu bir CSV dosyasına dışarı aktarın.