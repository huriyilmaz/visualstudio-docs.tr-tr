---
title: 'Test alanı 4: Iade etme | Microsoft Docs'
description: Bu kaynak denetimi eklentisi test alanı, güncelleştirilmiş öğelerin sürüm deposuna gönderilmesini içerir.
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
ms.workload:
- vssdk
ms.openlocfilehash: b8de88b75b7013b75a35c9e92dc662598185e92b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080560"
---
# <a name="test-area-4-check-in"></a>Test Alanı 4: İade Etme
Bu kaynak denetimi eklentisi test alanı, güncelleştirilmiş öğelerin sürümü **Iade et** komutu aracılığıyla sürüm deposuna gönderilmesini içerir.

## <a name="command-menu-access"></a>Komut menüsü erişimi
 Aşağıdaki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı menü yolları test durumlarında kullanılır.

##### <a name="check-in"></a>Teslim etme:
 **Dosya**, **kaynak denetimi**, **iade et**.

 **Dosyasını** **İade** edin.

 Kısayol menüsü, **Iade et**.

## <a name="common-expected-behavior"></a>Yaygın beklenen davranış

- Kaynak denetimi altındaki bir çözüme veya projeye eklenen projeler ve dosyalar, **Iade etme** iletişim kutusunda ve **bekleyen checkins** penceresinde görünür.

- İade etme işleminden sonra eklenen öğeler kaynak denetiminde görünür.

- İade etme işleminden sonra, güncelleştirilmiş öğelerin depoda düzgün şekilde sürümü oluşturulur.

## <a name="test-cases"></a>Test Çalışmaları
 Iade etme test alanı için belirli test çalışmaları aşağıda verilmiştir.

### <a name="case-4a-modified-items"></a>Durum 4A: değiştirilen öğeler
 Değiştirilen kaynak denetimi altındaki bir dosyayı güncelleştirmek için iade etme eyleminin kullanımını açıklar.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Kullanıma alınmış bir metin dosyasını değiştirme, yalnızca dosya iade etme (**Iade etme** iletişim kutusu)|1. bir metin dosyası ile yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. metin dosyasını kullanıma alma ve değiştirme.<br />4. Iade etme iletişim kutusu (**Dosya**, **kaynak denetimi**, **iade etme**) aracılığıyla iade edin.|Ortak beklenen davranış.|
|Kullanıma alınmış bir metin dosyasını değiştirme, yalnızca dosyayı Iade etme (**checkins penceresi bekleniyor** )|1. bir metin dosyası ile yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. metin dosyasını kullanıma alma ve değiştirme.<br />4. **bekleyen checkins** penceresi aracılığıyla iade edin.|Ortak beklenen davranış.|

### <a name="case-4b-adding-files"></a>Durum 4B: dosya ekleme
 Bir projeye veya öğeye bir dosya eklerken, proje veya çözüm de aynı zamanda değişmelidir. Bu nedenle, ana dosya da kullanıma alındı ve eklemeyi tamamlaması için iade edilmiş olmalıdır.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Bir metin dosyası ekleyin ve her şeyi iade edin (**Iade et** iletişim kutusu)|1. yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. projeye bir metin dosyası ekleyin.<br />4. istenirse projenin kullanıma denetimini kabul edin.<br />5. **Çözüm Gezgini** çözüm seçin.<br />6. **Iade et** iletişim kutusundan iade edin.|Ortak beklenen davranış.|
|Bir metin dosyası ekleyin ve her şeyi iade edin (**checkins penceresi bekleniyor** )|1. yeni bir proje oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. projeye bir metin dosyası ekleyin.<br />4. istenirse projenin kullanıma denetimini kabul edin.<br />5. **bekleyen checkins** penceresinden çözümü iade edin.|Yaygın beklenen davranış|

### <a name="case-4c-adding-projects"></a>Durum 4c: proje ekleme
 Bir çözüme bir proje eklenirken çözüm de aynı zamanda değişmelidir. Bu nedenle, çözüm dosyası da kullanıma alındı ve ekleme işleminin tamamlanmasının ardından iade alınması gerekir.

|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimi altındaki boş bir çözüme bir proje ekleyin (**Iade et** iletişim kutusu)|1. boş bir çözüm oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. yeni bir proje ekleyin.<br />4. istenirse çözümü kullanıma alma kabul edin.<br />5. **Iade et** iletişim kutusundan iade edin.|Ortak beklenen davranış.|
|Kaynak denetimi altındaki boş bir çözüme proje ekleme (**checkins penceresi bekleniyor** )|1. boş bir çözüm oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. yeni bir proje ekleyin.<br />4. istenirse çözümü kullanıma alma kabul edin.<br />5. **bekleyen checkins** penceresinden çözümü iade edin.|Ortak beklenen davranış.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
