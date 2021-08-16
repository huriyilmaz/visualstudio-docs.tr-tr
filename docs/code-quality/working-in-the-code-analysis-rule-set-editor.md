---
title: Kod Analizi Kural Kümesi Düzenleyicisini Kullanma
ms.date: 04/04/2018
description: Kural kümelerini düzenlemeyi ve görüntülemeyi öğrenin Visual Studio. Kural önem derecesi ayarlama, özel bir kümede kurallar belirtme ve kural kümesi kılavuzunda verileri ayarlama hakkında bilgi.
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: e3d5985411fe58852a004d6f74d0015f07732d3de243895642492282a50367df
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347954"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Kod analizi kural kümesi düzenleyicisini kullanma

Kod analizi kural kümesi düzenleyicisi, özel bir kural kümesine dahil edilen kuralları belirtmenize ve kural ihlallerinin önem derecelerini ayarlamanızı sağlar.

Aşağıdaki tabloda önem derecesi seçenekleri yer alır:

|Eylem (Önem Derecesi)|Açıklama|
|-|-|
|Uyarı|Hata Listesinde ve derleme **zamanında** bir uyarı üretir.|
|Hata|Hem Hata Listesinde hem **de derleme** zamanında bir hata üretir.|
|Bilgi|Hata Listesinde bir **ileti üretir.**|
|Gizli|İhlal kullanıcıya görünür değildir. Ancak, IDE'ye ihlal bildirildi.|
|Hiçbiri|Kural gizlendi. Davranış, kuralın kural kümesinden kaldırılmasıyla aynıdır.|

Düzenleyici kuralları, kuralları belirttiğiniz kural kümesi alanına göre gruplara alan bir ağaç yapısında görüntüler. Kural kümesinden kural eklemek veya kaldırmak için aşağıdaki adımlardan birini veya daha fazlasını gerçekleştirin:

- Gruptaki tüm kuralları eklemek veya kaldırmak için grup düğümünün onay kutusunu seçin veya temizleyin. Bir grup seçerek tüm kurallar Uyarı eylemine **ayarlanır.**

   > [!TIP]
   > Kuralların Grupla açılan listesinde nasıl **gruplandıklarını** değiştirebilirsiniz.

- Bir **grubun** Eylem alanına tıklayın, gruptaki tüm kurallara uygulanacak eylemi belirtin.

- Tek bir kuralın onay kutusunu seçin veya temizleyin. Bir kuralın onay kutusunu işaretle, kural Uyarı eylemi **olarak** ayarlanır.

## <a name="toolbar"></a>Araç Çubuğu

Kural kümesi kılavuzunda görünen verileri grup etmek, filtrelemek ve aramak için kural kümesi düzenleyicisinin araç çubuğunu kullanabilirsiniz.

Aşağıdaki tabloda kural kümesi düzenleyicisinin araç çubuğundaki denetimler açık almaktadır.

|Araç çubuğu denetimi|Açıklama|
|---------------------|-----------------|
|**Tümünü Genişlet**|Tüm gruplarda kuralları gösterir.|
|**Tümünü Daralt**|Tüm gruplarda kuralları gizler.|
|**Grupla**|Kuralların gruplandır olduğu alanı belirtir. Kuralları **\<None>** gruplar olmadan göstermek için tıklayın.|
|**Sütun Seçenekleri**|Görüntülenecek kural alanlarını belirtir.|
|**Geçerli çözüm için geçerli olan kuralları gizleme**|Çözümle aynı Hedef Türüne sahip olan kuralları gösterir veya gizler.|
|**Hata oluşturan kuralları Code Analysis göster**|Hata eylemine atanan kuralları gösterir veya gizler.|
|**Uyarı oluşturmak için Code Analysis göster**|Uyarı eylemine atanan kuralları gösterir veya gizler.|
|**Etkinleştirilmemiş kuralları göster**|Hiçbiri eylemine atanan kuralları gösterir veya gizler.|
|**Alt kural kümelerini ekleme veya kaldırma**|Seçilen kural kümelerini ekler veya kaldırır.|
|**Arama kuralları**|Belirttiğiniz dize için tüm alan değerlerini arar.|

## <a name="rule-set-fields"></a>Kural kümesi alanları

Kural kümesi alanları bir kural kümesiyle ilgili bilgileri görüntüler ve kural listesini sıralamak ve grup etmek için kullanılabilir. Alanları görüntülemek veya gizlemek için kural **Sütun Seçenekleri** araç çubuğundaKimlik alanlarını seçin ve sonra göster veya gizleyecek alanların onay kutularını seçin veya temizleyin.

Aşağıdaki tabloda bir kural kümesi alanlarının açıklaması ve ardından aşağıdakiler yer almaktadır:

|Alan|Açıklama|
|-----------|-----------------|
|**ID**|Kuralın tanımlayıcısı.|
|**Kategori**|Kod analizi kuralları, kural kümelerinde üyeliklerine ek olarak kategoriye göre de gruplanmıştır. Daha fazla bilgi için [bkz. Kod analizi uyarıları.](/dotnet/fundamentals/code-analysis/quality-rules/index)|
|**Ad**|Kuralın başlığı.|
|**Ad Alanı**|Kuralın ad alanı.|
|**Hedef Tür**|Kuralın yerel, yönetilen veya veritabanı kodu için olup olmadığını gösterir.|
|**Eylem**|Kod analizi çalıştırması içinde kural ihlal edildiklerde yapılan eylem. Eylem alanını **düzenleyebilirsiniz.**|
|**Kaynak Kural Kümeleri**|Kuralı içeren kural kümesi.|

## <a name="sort-and-filter-rule-sets"></a>Kural kümelerini sıralama ve filtreleme

Kural kümesi kılavuzundaki sütun üst bilgilerinden, kuralları alanın değerlerine göre sıralar ve filtrelersiniz.

- Kural kümesi listelerini sıralamak için sıralamak istediğiniz alanın sütun üst bilgilerini seçin. Kural kümeleri gruplanmışsa, her grup tek tek sıralanmış.

- Kural kümelerini bir alanın değerine göre filtrelemek için, filtrelemek istediğiniz alanın sütun başlığındaki filtre düğmesini seçin. Göstermek istediğiniz değerlerin onay kutularını seçin ve gizlemek istediğiniz değerlerin onay kutularını temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel kural kümesi oluşturma](../code-quality/how-to-create-a-custom-rule-set.md)
