---
title: Test hataları için yük testi günlüğü kaydetme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b47010a68520379afd8e0d969fa99169cb1ff0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588960"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Nasıl yapılır: Yük Testi Düzenleyicisi'ni kullanarak test günlüklerini test etmek için test hatalarının kaydedilip kaydedilen olmadığını belirtin

**Yeni Yük Testi Sihirbazı**ile yük testinizi oluşturduktan sonra, test ihtiyaçlarınızı ve hedeflerinizi karşılamak için yük testi özelliklerini değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor** Bkz. [Walkthrough: Bir yük testi oluşturun ve çalıştırın.](../test/walkthrough-create-and-run-a-load-test.md) Test Hatası özelliğini **Kaydet özelliğini** değiştirerek bir test bir yük testinde başarısız olursa test günlüğünün kaydedilip kaydedilen olmasını isteyip istemediğinibelirtebilirsiniz.

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi çalıştırma ayarları özelliklerine](../test/load-test-run-settings-properties.md)bakın.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Bir test bir senaryoda başarısız olduğunda test günlüğü kaydedilir olup olmadığını belirtmek için

1. Bir yük testi açın.

     **Yük Testi Düzenleyicisi** görüntülenir. Yük testi ağacı görüntülenir.

2. Yük testi ağaçları **Çalıştır Ayarları** klasöründe, en fazla test yinelemesayısını belirtmek istediğiniz çalışma ayarları düğümünü seçin.

3. **Görünüm** menüsünde **Özellikler Penceresi'ni**seçin.

     Çalışma ayarları kategorileri ve özellikleri **Özellikler** penceresinde görüntülenir.

4. Test **Hatası'nda Kaydet** Özelliği'nde, test günlüğünü senaryoda bir test hatası durumunda kaydetmek isteyip istemediğinizi belirtmek için **True** veya **False'u** seçin.

     Özelliği değiştirmeyi bitirdikten sonra **Dosya** menüsünde **Kaydet'i** seçin.

     Günlükte kaydedilen veriler, Yük Testi Çözümleyicisinin Tablolar görünümü kullanılarak görüntülenebilir. Daha fazla bilgi için bkz: [Tablolar görünümünde yük testi sonuçlarını ve hatalarını analiz](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)et.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını edin](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
