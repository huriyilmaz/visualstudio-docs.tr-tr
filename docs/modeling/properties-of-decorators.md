---
title: Dekoratörlerin Özellikleri
description: Dekoratların, diyagramdaki şekiller veya bağlayıcılar üzerinde görünebilen simgeler, metin veya genişletme/daraltma köşeli çift ayraçları olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef863d0d3dab394c2ca427a27d039c19e5921a51
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360839"
---
# <a name="properties-of-decorators"></a>Dekoratörlerin Özellikleri
Dekoratörler, diyagramdaki şekiller veya bağlayıcılar üzerinde görünebilen simgelerle, metin veya genişletme/daraltma köşeli ayraçlardır. Aşağıdaki tablolarda, üç dekoratörün çeşitinin özellikleri gösterilmektedir. Bazı özellikler yalnızca şekil dekoratlarını veya yalnızca bağlayıcı dekoratlarını üzerinde görünür.

 Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Dekoratör Genişlet/Daralt

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Daraltma dekoratörü Genişlet|
|Ad|Dekoratörün adı.|ExpandCollapseDecorator|
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
|Ad|Dekoratörün adı.|Şeklindeki IconDecorator|
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
|Ad|Dekoratörün adı.|Etiketle|
|Notlar|Dekoratör ile ilişkili resmi olmayan notlar.|\<none>|
|Horizontalkayması|Dekoratörün varsayılan konumuna göre inç cinsinden yatay konum. (Yalnızca şekiller üzerinde.)|0|
|Verticalsapmayı|Dekoratörün varsayılan konumuna göre inç cinsinden dikey konum. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün, varsayılan konumuna (inç olarak) göre, çizgi arasındaki fark. (Yalnızca bağlayıcılar üzerinde.)|0|
|OffsetFromShape|Dekoratörün şekilden, varsayılan konumuna göre inç cinsinden değeri. (Yalnızca bağlayıcılar üzerinde.)|0|
|Konum|Dekoratörün varsayılan konumu.|TargetBottom|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))