---
title: Test hatalarıyla ilgili yük testi günlüğünü kaydet
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cdae6abf3af71967357319addd755a31721053ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653415"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Nasıl yapılır: test hatalarının Yük Testi Düzenleyicisi kullanarak test günlüklerine kaydedilip kaydedilmediğini belirtme

**Yeni Yük Testi Sihirbazı**yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak için yük testi özelliklerini değiştirmek üzere **Yük Testi Düzenleyicisi** kullanabilirsiniz. Bkz. [Izlenecek yol: yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md). Test **başarısızlığının oturumunu kaydet** özelliğini değiştirerek yük testinde test başarısız olursa test günlüğü kaydedilip kaydedilmediğini belirtebilirsiniz.

> [!NOTE]
> Çalışma ayarları özelliklerinin ve açıklamalarının tüm listesi için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Bir senaryoda bir test başarısız olduğunda test günlüğünün kaydedilip kaydedilmediğini belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **çalışma ayarları** klasöründe, için en fazla test yinelemesi sayısını belirtmek istediğiniz çalışma ayarları düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler penceresi**' ni seçin.

     Çalışma ayarları kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. Test **başarısızlığını günlüğe kaydet** özelliğinde, senaryoda bir test hatası olması durumunda test günlüğünü kaydetmek istediğinizi belirtmek için **true** veya **false** ' ı seçin.

     Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet** ' i seçin.

     Günlüğe kaydedilen veriler Yük Testi Çözümleyicisi 'nin tablolar görünümü kullanılarak görüntülenebilir. Daha fazla bilgi için bkz. [Tablolar görünümünde Yük testi sonuçlarını ve hatalarını çözümleme](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını Düzenle](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)