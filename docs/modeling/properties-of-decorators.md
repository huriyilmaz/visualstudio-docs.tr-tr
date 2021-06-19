---
title: Dekoratörlerin Özellikleri
description: Dekoratların, diyagramdaki şekiller veya bağlayıcılar üzerinde görünebilen simgeler, metin veya genişletme/daraltma köşeli çift ayraçları olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f3436bb800142e7c85594f4b05cef6fb45c4489
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390808"
---
# <a name="properties-of-decorators"></a>Dekoratörlerin Özellikleri
Dekoratörler, diyagramdaki şekiller veya bağlayıcılar üzerinde görünebilen simgelerle, metin veya genişletme/daraltma köşeli ayraçlardır. Aşağıdaki tablolarda, üç dekoratörün çeşitinin özellikleri gösterilmektedir. Bazı özellikler yalnızca şekil dekoratlarını veya yalnızca bağlayıcı dekoratlarını üzerinde görünür.

 Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Dekoratör Genişlet/Daralt

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Daraltma dekoratörü Genişlet|
|Name|Dekoratörün adı.|ExpandCollapseDecorator|
|Notlar|Bu dekoratör ile ilişkili resmi olmayan notlar.|\<none>|
|Horizontalkayması|Dekoratörün varsayılan konumuna göre inç cinsinden yatay konum. (Yalnızca şekiller üzerinde.)|0|
|Verticalsapmayı|Dekoratörün varsayılan konumuna göre inç cinsinden dikey konum. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün, varsayılan konumuna (inç olarak) göre, çizgi arasındaki fark. (Yalnızca bağlayıcılar üzerinde.)|0|
|OffsetFromShape|Dekoratörün şekilden, varsayılan konumuna göre inç cinsinden değeri. (Yalnızca bağlayıcılar üzerinde.)|0|
|Konum|Dekoratörün varsayılan konumu.|SourceTop|

## <a name="icon-decorator"></a>Simge dekoratör

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|DefaultIcon|Görüntülenecek simgenin veya resim dosyasının yolu.|\<none>|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratör adı.|Simge dekoratör|
|Name|Dekoratörün adı.|Şeklindeki IconDecorator|
|Notlar|Dekoratör ile ilişkili resmi olmayan notlar.|\<none>|
|Horizontalkayması|Dekoratörün varsayılan konumuna göre inç cinsinden yatay konum. (Yalnızca şekiller üzerinde.)|0|
|Verticalsapmayı|Dekoratörün varsayılan konumuna göre inç cinsinden dikey konum. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün, varsayılan konumuna (inç olarak) göre, çizgi arasındaki fark. (Yalnızca bağlayıcılar üzerinde.)|0|
|OffsetFromShape|Dekoratörün şekilden, varsayılan konumuna göre inç cinsinden değeri. (Yalnızca bağlayıcılar üzerinde.)|0|
|Konum|Dekoratörün varsayılan konumu.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Ise DefaultText|Görüntülenecek varsayılan metin.|Etiketle|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratör adı.|Etiketle|
|FontSize|Dekoratör içinde görüntülenen metnin yazı tipi boyutu.|8|
|FontStyle|Dekoratör içinde görüntülenen metnin yazı tipi stili.|Düzenli|
|Name|Dekoratörün adı.|Etiketle|
|Notlar|Dekoratör ile ilişkili resmi olmayan notlar.|\<none>|
|Horizontalkayması|Dekoratörün varsayılan konumuna göre inç cinsinden yatay konum. (Yalnızca şekiller üzerinde.)|0|
|Verticalsapmayı|Dekoratörün varsayılan konumuna göre inç cinsinden dikey konum. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün çizgiden, varsayılan konumundan inç olarak uzaklığı. (Yalnızca bağlayıcılarda.)|0|
|OffsetFromShape|Dekoratörün, varsayılan konumundaki şekliyle inç olarak uzaklığı. (Yalnızca bağlayıcılarda.)|0|
|Konum|Dekoratörün varsayılan konumu.|TargetBottom|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))