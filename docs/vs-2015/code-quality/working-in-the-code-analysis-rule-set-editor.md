---
title: Kod analizi kural kümesi düzenleyicisinde çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72621504"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Kod Çözümleme Kural Kümesi Düzenleyici'de Çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod analizi kural kümesi Düzenleyicisi, özel bir kural kümesine dahil edilen kuralları belirtmenize ve eylemi belirtmenize olanak sağlar. Kod analizi kural ihlaline karşılaştığında gerçekleştirilecek eylemi de belirtebilirsiniz.

|Eylem|Açıklama|
|------------|-----------------|
|**Warning**|**Hata listesi** penceresinde bir uyarı oluşturur.|
|**Hata:**|**Hata listesi** penceresinde bir hata oluşturur.|
|**Seçim**|Kuralı devre dışı bırakır.|

 Düzenleyici, kuralları belirttiğiniz bir kural kümesi alanına göre gruplandıran bir ağaç yapısında görüntüler. Kural kümesine kural eklemek veya kuralı kaldırmak için aşağıdaki adımlardan birini veya birkaçını yapın:

- Gruptaki tüm kuralları eklemek veya kaldırmak için Grup düğümünün onay kutusunu seçin veya temizleyin. Bir grup seçtiğinizde, tüm kurallar **Uyarı** eylemine ayarlanır.

- Bir grubun **eylem** alanına tıklayın ve sonra gruptaki tüm kurallara uygulanacak eylemi belirtin.

- Tek bir kuralın onay kutusunu seçin veya temizleyin. Bir kuralın onay kutusunu seçtiğinizde, kural uyarı eylemine ayarlanır.

## <a name="rule-set-editor-toolbar"></a>Kural kümesi Düzenleyici araç çubuğu
 Kural kümesi Düzenleyicisi ' nin araç çubuğunu, kural kümesi kılavuzunda görünen verileri gruplamak, filtrelemek ve aramak için kullanabilirsiniz.

 Aşağıdaki tabloda, kural kümesi düzenleyicisinin araç çubuğundaki denetimler açıklanmaktadır.

|ToolBar denetimi|Açıklama|
|---------------------|-----------------|
|**Tümünü Genişlet**|Tüm gruplardaki kuralları gösterir.|
|**Tümünü Daralt**|Tüm gruplardaki kuralları gizler.|
|**Gruplandırma ölçütü**|Kuralların gruplandırılacağı alanı belirtir. Kuralları gruplar olmadan göstermek için **\<None >** ' a tıklayın.|
|**Sütun Seçenekleri**|Görüntülenecek kural alanlarını belirtir.|
|**Geçerli çözüm için geçerli olmayan kuralları gizle**|Çözümle aynı hedef türünde olmayan kuralları gösterir veya gizler.|
|**Kod Analizi hataları oluşturabilen kuralları göster**|Hata eyleminin atandığı kuralları gösterir veya gizler.|
|**Kod Analizi uyarıları oluşturabileceğiniz kuralları göster**|Uyarı eylemine atanan kuralları gösterir veya gizler.|
|**Etkin olmayan kuralları göster**|Hiçbiri eyleminin atandığı kuralları gösterir veya gizler.|
|**Alt kural kümeleri ekleme veya kaldırma**|Seçili kural kümelerindeki kuralları ekler veya kaldırır.|
|**Arama kuralları**|Belirttiğiniz dize için tüm alan değerlerini arar.|

## <a name="rule-set-fields"></a>Kural kümesi alanları
 Kural kümesi alanları bir kural kümesi hakkındaki bilgileri görüntüler ve kural listesini sıralamak ve gruplandırmak için kullanılabilir. Alanları görüntülemek veya gizlemek için, kural kümesi Düzenleyicisi araç çubuğunda **sütun seçenekleri** ' a tıklayın ve ardından göstermek veya gizlemek istediğiniz alanların onay kutularını işaretleyin veya temizleyin.

 Aşağıdaki tabloda bir kural kümesinin alanları açıklanmaktadır.

|Alan|Açıklama|
|-----------|-----------------|
|**NUMARASıNı**|Kuralın tanımlayıcısı.|
|**Alan**|Kural kümelerinde üyeliklerine ek olarak, kod analizi kuralları da kategoriye göre gruplandırılır. Daha fazla bilgi için bkz. [yönetilen kod uyarıları Için kod analizi](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Ad**|Kuralın başlığı.|
|**Uzayına**|Kuralın ad alanı.|
|**Hedef türü**|Kuralın yerel, yönetilen veya veritabanı kodu için olup olmadığını gösterir.|
|**Ön**|Kod Analizi çalıştırmasında kural ihlal edildiğinde gerçekleştirilecek eylem.<br /><br /> **Uyarı** -bir uyarı oluşturur.<br /><br /> **Hata** -bir hata oluşturur.<br /><br /> **Hiçbiri** -kuralı devre dışı bırakır.<br /><br /> Eylem alanını düzenleyebilirsiniz. Değerin None olarak ayarlanması, kuralın onay kutusunun temizlenmesiyle aynıdır.|
|**Kaynak kural kümeleri**|Kuralı içeren kural kümesi.|

## <a name="sorting-and-filtering-rule-sets"></a>Kural kümelerini sıralama ve filtreleme
 Kural kümesi kılavuzunun sütun başlıklarından, kuralları alanın değerlerine göre sıralayabilir ve filtreleyebilirsiniz.

- Kural kümesi listelerini sıralamak için, sıralamak istediğiniz alanın sütun başlığına tıklayın. Kural kümeleri gruplandırılmışsa, her grup ayrı ayrı sıralanır.

- Kural kümelerini bir alanın değerine göre filtrelemek için, filtre uygulamak istediğiniz alanın sütun üstbilgisindeki filtre düğmesine tıklayın. Göstermek istediğiniz değerlerin onay kutularını seçin ve gizlemek istediğiniz değerlerin onay kutularını temizleyin.
