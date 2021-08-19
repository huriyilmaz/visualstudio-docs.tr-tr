---
title: 'Test Alanı 6: Silme | Microsoft Docs'
description: Bu kaynak denetimi test alanı, kaynak denetimi Çözüm Gezgini için Visual Studio silme eylemlerini kapsar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dd27a0ac99faf9ec2ab4b53fcbae31257e72202f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158755"
---
# <a name="test-area-6-delete"></a>Test Alanı 6: Sil
Bu kaynak denetimi eklentisi test alanı silme eylemlerini kapsar.

 Kaynak denetimi, içinde silme eylemlerine yanıt **Çözüm Gezgini.**

 Silinebilir öğelerin listesi aşağıda ve ardından görüntülenir:

- Dosyalar

- Klasörler

- Project

  Proje türüne bağlı olarak Projeyi kaldırma  (dosyaları diskte bırakır) veya  Projeyi silme (diskte dosyaları kaldırır) seçeneğiniz olabilir. Eylemlerden biri projeyi veya öğeyi öğesinden **Çözüm Gezgini.**

## <a name="expected-behavior"></a>Beklenen Davranış
 Silme testi alanında test testleri için beklenen davranış şudur:

- Silinen öğe artık öğesi içinde **Çözüm Gezgini.**

- Silinen projenin veya öğenin üst öğesi gerektiğinde kullanıma alınmış (büyük olasılıkla bir istem ile).)

- Kullanıma alınmış veya eklenen bir öğeyi sildikten sonra, bekleyen Iadeler **penceresinde GÖRÜNMEZ.**

- Öğe, silme sonrasında bile kaynak denetim deposu içinde mevcut olur ve el ile temizlenir.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|İstemci projesini silme|1. İstemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projenin tamamını çözümden kaldırma|Ortak Beklenen Davranış.|
|Boş bir dosyayı silme|1. İstemci projesi oluşturun.<br />2. Projeye sıfır bir byte dosyası ekleyin.<br />3. Çözümü kaynak denetimine ekleyin.<br />4. Dosyayı seçin, silin.|Ortak Beklenen Davranış.|
|Tek dosya içeren bir klasörü silme|1. Tek proje çözümü oluşturun.<br />2. Klasör ekleyin.<br />3. Klasöre bir dosya ekleyin.<br />4. Çözümü kaynak denetimine ekleyin.<br />5. İstemleri önlemek için projeyi kontrol edin.<br />6. Klasörü silin.|Ortak Beklenen Davranış.|
|Dosya Sistemi Web projesini silme|1. Bir Dosya Sistemi Web projesi oluşturun (GÖZAT düğmesini kullanarak bir UNC yolu belirtin).<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projenin tamamını çözümden kaldırın.<br />4. Yerel bir Web projesi için 1 ile 3 arasında adımları tekrarlayın (kodda farklı yollar üzerinde alıştırmalar ama aynı dış arabirim ve davranışa sahiptir).|Ortak Beklenen Davranış.|
|Dosya Sistemi Web projesinden dosya silme|1. Dosya Sistemi Web projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeden bir dosyayı silin.<br />4. Yerel bir Web projesi için 1 ile 3 arasında adımları tekrarlayın (kodda farklı yollar üzerinde alıştırmalar ama aynı dış arabirim ve davranışa sahiptir).|Ortak Beklenen Davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
