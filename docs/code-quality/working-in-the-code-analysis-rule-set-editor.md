---
title: Kod Analizi Kural Kümesi Düzenleyicisini Kullanma
ms.date: 04/04/2018
description: Visual Studio kural kümelerini düzenleme ve görüntüleme hakkında bilgi edinin. Kural önem derecesini ayarlama, özel bir küme içinde kuralları belirtme ve kural kümesi kılavuzundaki verileri ayarlama bölümüne bakın.
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

Kod analizi kural kümesi Düzenleyicisi, özel bir kural kümesine dahil edilen kuralları belirtmenize ve kural ihlallerinin önem derecesini ayarlamanıza olanak sağlar.

Aşağıdaki tabloda önem derecesi seçenekleri gösterilmektedir:

|Eylem (önem derecesi)|Açıklama|
|-|-|
|Uyarı|**Hata listesi** ve derleme zamanında bir uyarı oluşturur.|
|Hata|**Hata listesi** ve derleme zamanında bir hata oluşturur.|
|Bilgi|**Hata listesi** bir ileti oluşturur.|
|Gizli|İhlalin kullanıcıya görünür değil. Ancak, bu, ihlalin ihlal olduğu konusunda bilgilendirilir.|
|Hiçbiri|Kural bastırılır. Kural, kuralın kural kümesinden kaldırılmış olduğu durumla aynıdır.|

Düzenleyici, kuralları belirttiğiniz bir kural kümesi alanına göre gruplandıran bir ağaç yapısında görüntüler. Kural kümesine kural eklemek veya kuralı kaldırmak için aşağıdaki adımlardan birini veya birkaçını yapın:

- Gruptaki tüm kuralları eklemek veya kaldırmak için Grup düğümünün onay kutusunu seçin veya temizleyin. Bir grup seçtiğinizde, tüm kurallar **Uyarı** eylemine ayarlanır.

   > [!TIP]
   > Kuralların **grupta gruplandırma ölçütü** açılır.

- Bir grubun **eylem** alanına tıklayın, gruptaki tüm kurallara uygulanacak eylemi belirtin.

- Tek bir kuralın onay kutusunu seçin veya temizleyin. Bir kuralın onay kutusunu seçtiğinizde, kural **Uyarı** eylemine ayarlanır.

## <a name="toolbar"></a>Araç Çubuğu

Kural kümesi Düzenleyicisi ' nin araç çubuğunu, kural kümesi kılavuzunda görünen verileri gruplamak, filtrelemek ve aramak için kullanabilirsiniz.

Aşağıdaki tabloda, kural kümesi düzenleyicisinin araç çubuğundaki denetimler açıklanmaktadır.

|ToolBar denetimi|Açıklama|
|---------------------|-----------------|
|**Tümünü Genişlet**|Tüm gruplardaki kuralları gösterir.|
|**Tümünü Daralt**|Tüm gruplardaki kuralları gizler.|
|**Gruplandırma ölçütü**|Kuralların gruplandırılacağı alanı belirtir. **\<None>** Kuralları gruplar olmadan göstermek için tıklayın.|
|**Sütun Seçenekleri**|Görüntülenecek kural alanlarını belirtir.|
|**Geçerli çözüm için geçerli olmayan kuralları gizle**|Çözümle aynı hedef türünde olmayan kuralları gösterir veya gizler.|
|**Code Analysis hataları oluşturabilen kuralları göster**|Hata eyleminin atandığı kuralları gösterir veya gizler.|
|**Code Analysis uyarıları oluşturabilen kuralları göster**|Uyarı eylemine atanan kuralları gösterir veya gizler.|
|**Etkin olmayan kuralları göster**|Hiçbiri eyleminin atandığı kuralları gösterir veya gizler.|
|**Alt kural kümeleri ekleme veya kaldırma**|Seçili kural kümelerindeki kuralları ekler veya kaldırır.|
|**Arama kuralları**|Belirttiğiniz dize için tüm alan değerlerini arar.|

## <a name="rule-set-fields"></a>Kural kümesi alanları

Kural kümesi alanları bir kural kümesi hakkındaki bilgileri görüntüler ve kural listesini sıralamak ve gruplandırmak için kullanılabilir. Alanları görüntülemek veya gizlemek için, kural kümesi Düzenleyicisi araç çubuğunda **sütun seçenekleri** ' yi seçin ve ardından göstermek veya gizlemek istediğiniz alanların onay kutularını seçin veya temizleyin.

Aşağıdaki tabloda bir kural kümesi alanları açıklanmaktadır:

|Alan|Açıklama|
|-----------|-----------------|
|**ID**|Kuralın tanımlayıcısı.|
|**Kategori**|Kural kümelerinde üyeliklerine ek olarak, kod analizi kuralları da kategoriye göre gruplandırılır. Daha fazla bilgi için bkz. [Kod Analizi uyarıları](/dotnet/fundamentals/code-analysis/quality-rules/index).|
|**Ad**|Kuralın başlığı.|
|**Ad Alanı**|Kuralın ad alanı.|
|**Hedef türü**|Kuralın yerel, yönetilen veya veritabanı kodu için olup olmadığını gösterir.|
|**Eylem**|Kod Analizi çalıştırmasında kural ihlal edildiğinde gerçekleştirilecek eylem. **Eylem** alanını düzenleyebilirsiniz.|
|**Kaynak kural kümeleri**|Kuralı içeren kural kümesi.|

## <a name="sort-and-filter-rule-sets"></a>Kural kümelerini sıralama ve filtreleme

Kural kümesi kılavuzunun sütun başlıklarından, kuralları alanın değerlerine göre sıralayabilir ve filtreleyebilirsiniz.

- Kural kümesi listelerini sıralamak için, sıralamak istediğiniz alanın sütun başlığını seçin. Kural kümeleri gruplandırılmışsa, her grup ayrı ayrı sıralanır.

- Kural kümelerini bir alanın değerine göre filtrelemek için, filtre uygulamak istediğiniz alanın sütun üstbilgisindeki filtre düğmesini seçin. Göstermek istediğiniz değerlerin onay kutularını seçin ve gizlemek istediğiniz değerlerin onay kutularını temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel kural kümesi oluşturma](../code-quality/how-to-create-a-custom-rule-set.md)
