---
title: 'Test Alanı 4: Giriş | Microsoft Docs'
description: Bu kaynak denetimi eklentisi test alanı, Check In komutunu kullanarak güncelleştirilmiş öğelerin sürüm deposuna gönderilmesini kapsar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 779a00bb93899414cda04ea5b6a3a5e15bea686f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158768"
---
# <a name="test-area-4-check-in"></a>Test Alanı 4: İade Etme
Bu kaynak denetimi eklentisi test alanı, iade komutu aracılığıyla güncelleştirilmiş öğelerin sürüm deposuna **gönderilmesini** kapsar.

## <a name="command-menu-access"></a>Komut Menüsü Erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı menü yolları test çalışmalarında kullanılır.

##### <a name="check-in"></a>Teslim etme:
 **Dosyası,** **Kaynak Denetimi**, **Iade Edin.**

 **dosyasını** **açın, iade edin.**

 Kısayol menüsü, **Iade Edin.**

## <a name="common-expected-behavior"></a>Ortak Beklenen Davranış

- Kaynak denetimi altında bir çözüme veya projeye  eklenen projeler ve dosyalar, Iade Edildi iletişim kutusunda ve **Bekleyen IadeLer penceresinde** görünür.

- Giriş sonrasında, eklenen öğeler kaynak denetiminde görünür.

- Iade edildikten sonra güncelleştirilmiş öğelerin depoda düzgün bir şekilde sürümü güncelleştirilir.

## <a name="test-cases"></a>Test Çalışmaları
 Checkin test alanı için belirli test testleri aşağıda ve ardından ve listelemektedir.

### <a name="case-4a-modified-items"></a>Durum 4a: Değiştirilen öğeler
 Değiştirilmiş kaynak denetimi altındaki bir dosyayı güncelleştirmek için iade eyleminin kullanımı açık bir şekilde anlattır.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kullanıma alınmış bir metin dosyasını değiştirme, yalnızca dosyayı iade edin **(Iade Edin iletişim** kutusu)|1. Metin dosyasıyla yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Metin dosyasını kontrol edin ve değiştirebilirsiniz.<br />4. Iade Edin iletişim kutusu aracılığıyla iade edin **(** Dosya, **Kaynak Denetimi**, **Iade Edin**).|Ortak Beklenen Davranış.|
|Kullanıma alınmış bir metin dosyasını değiştirme, Yalnızca dosyayı iade edin **(Bekleyen IadeLer** penceresi)|1. Metin dosyasıyla yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Metin dosyasını kontrol edin ve değiştirebilirsiniz.<br />4. Bekleyen IadeLer **penceresi aracılığıyla iade** edin.|Ortak Beklenen Davranış.|

### <a name="case-4b-adding-files"></a>Olay 4b: Dosya ekleme
 Bir projeye veya bir çözüme bir öğe eklerken, proje veya çözüm de değişsin. Bu nedenle üst dosya da kullanıma alınmış olur ve eklemenin tamamlanması için iade edilmelidir.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Metin dosyası ekleme ve her şeyi iade edin **(Giriş'i Aç** iletişim kutusu)|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeye bir metin dosyası ekleyin.<br />4. İstendiğinde projeyi iade etme onay kutusunu kabul edin.<br />5. içinde çözümü seçin **Çözüm Gezgini.**<br />6. Iade Edin **iletişim kutusundan iade** edin.|Ortak Beklenen Davranış.|
|Metin dosyası ekleme ve her şeyi iade edin **(Bekleyen Iadeler** penceresi)|1. Yeni bir proje oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Projeye bir metin dosyası ekleyin.<br />4. İstendiğinde projeyi iade etme onay kutusunu kabul edin.<br />5. Bekleyen IadeLer **penceresinden çözümü iade** edin.|Ortak Beklenen Davranış|

### <a name="case-4c-adding-projects"></a>Olay 4c: Proje ekleme
 Bir çözüme proje eklerken çözümün de değişmesi gerekir. Bu nedenle çözüm dosyası da kullanıma alınmış olur ve eklemenin tamamlanması için iade edilmelidir.

|Eylem|Test Adımları|Doğrulandı Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimi altındaki boş bir çözüme proje ekleme **(Iade Edin iletişim** kutusu)|1. Boş bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Yeni bir proje ekleyin.<br />4. İstendiğinde çözümün çıkış çıkışlarını kabul edin.<br />5. Iade Edin **iletişim kutusundan iade** edin.|Ortak Beklenen Davranış.|
|Kaynak denetimi altında boş bir çözüme proje ekleme (**Bekleyen Iadeler** penceresi)|1. Boş bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Yeni bir proje ekleyin.<br />4. İstendiğinde çözümün çıkış çıkışlarını kabul edin.<br />5. Bekleyen IadeLer **penceresinden çözümü iade** edin.|Ortak Beklenen Davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
