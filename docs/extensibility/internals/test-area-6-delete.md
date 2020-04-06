---
title: 'Test Alanı 6: Sil | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704503"
---
# <a name="test-area-6-delete"></a>Test Alanı 6: Silme
Bu kaynak denetimi eklentisi test alanı silme eylemlerini kapsar.

 Kaynak **denetimi, Solution Explorer'daki**silme eylemlerine yanıt verir.

 Silinebilecek öğelerin listesi aşağıda veda edilebilen öğelerin listesi verebilirsiniz:

- Dosyalar

- Klasörler

- Project

  Proje türüne bağlı olarak, projeyi **kaldırma** (dosyaları diskte bırakır) veya projeyi **silme** (diskteki dosyaları kaldırır) seçeneğiniz olabilir. Eylem, projeyi veya öğeyi **Çözüm Gezgini'nden**kaldırır.

## <a name="expected-behavior"></a>Beklenen Davranış
 Silme test alanındaki test çalışmaları için beklenen davranış:

- Silinen öğe artık **Çözüm Gezgini**içinde görünür.

- Silinen projenin veya öğenin üst öğesi gerektiğinde kullanıma gönderilir (büyük olasılıkla bir istemle.)

- Kullanıma alındıktan veya öğe ekledikten sonra **Bekleyen Denetimler** penceresinde GÖRÜNMEZ.

- Öğe, silinmeden sonra bile kaynak denetim deposunda hala bulunur ve el ile temizlenmesi gerekir.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|İstemci projesini silme|1. Bir istemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projenin tamamını çözümden kaldırma|Ortak Beklenen Davranış.|
|Boş bir dosyayı silme|1. Bir istemci projesi oluşturun.<br />2. Projeye sıfır bayt dosyası ekleyin.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Dosyayı seçin, silin.|Ortak Beklenen Davranış.|
|Bir dosyayla klasörü silme|1. Tek bir proje çözümü oluşturun.<br />2. Bir klasör ekleyin.<br />3. Klasöre bir dosya ekleyin.<br />4. Çözümü kaynak denetimine ekleyin.<br />5. İstemlerden kaçınmak için projeye göz atın.<br />6. Klasörü silin.|Ortak Beklenen Davranış.|
|Dosya Sistemi Web projesini silme|1. Dosya Sistemi Web projesi oluşturun (UNC yolunu belirtmek için Gözat düğmesini kullanın).<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projenin tamamını çözümden çıkarın.<br />4. Yerel bir Web projesi için 1'den 3'e kadar olan adımları yineleyin (kod boyunca farklı yollar çizer, ancak aynı dış arabirime ve davranışa sahiptir).|Ortak Beklenen Davranış.|
|Dosya Sistemi Web projesinden dosya silme|1. Bir Dosya Sistemi Web projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeden bir dosya silin.<br />4. Yerel bir Web projesi için 1'den 3'e kadar olan adımları yineleyin (kod boyunca farklı yollar çizer, ancak aynı dış arabirime ve davranışa sahiptir).|Ortak Beklenen Davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
