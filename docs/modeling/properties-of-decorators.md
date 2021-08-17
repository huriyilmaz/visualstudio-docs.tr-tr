---
title: Dekoratörlerin Özellikleri
description: Dekoratörlerin diyagramda şekiller veya bağlayıcılar üzerinde görünen simgeler, metinler veya genişlet/daralt köşeli çift ayraçları olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: cc285e74acacc33cfb12fbbf3aade12b4bf156a69abaf5cf5ec27e3e3f3468e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370521"
---
# <a name="properties-of-decorators"></a>Dekoratörlerin Özellikleri
Dekoratörler, diyagramda şekiller veya bağlayıcılarda görünen simgeler, metinler veya genişlet/daralt köşeli çift ayraçlarıdır. Aşağıdaki tablolarda üç tür dekoratörün özellikleri gösterildi. Özelliklerden bazıları yalnızca şekil dekoratörlerde veya yalnızca bağlayıcı dekoratörlerde görünür.

 Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, bkz. Domain-Specific Dili [Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

## <a name="expandcollapse-decorator"></a>Dekoratörü Genişletme/Daraltma

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Dekoratörü Daralt'i genişletin|
|Name|Dekoratörün adı.|Expandcollapsedecorator|
|Notlar|Bu dekoratörle ilişkili resmi olmayan notlar.|\<none>|
|Horizontaloffset|Dekoratörün varsayılan konumuyla ilgili olarak inç olarak yatay uzaklık. (Yalnızca şekiller üzerinde.)|0|
|Verticaloffset|Dekoratörün varsayılan konumuyla ilgili dikey uzaklık inç olarak. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün çizgiden, varsayılan konumuyla (inç) uzaklığı. (Yalnızca bağlayıcılarda.)|0|
|OffsetFromShape|Dekoratörün, varsayılan konumundaki şekliyle inç olarak uzaklığı. (Yalnızca bağlayıcılarda.)|0|
|Konum|Dekoratörün varsayılan konumu.|SourceTop|

## <a name="icon-decorator"></a>Simge Dekoratör

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Defaultıcon|Görüntülenecek simgenin veya görüntü dosyasının yolu.|\<none>|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Simge Dekoratör|
|Name|Dekoratörün adı.|IconDecorator|
|Notlar|Dekoratörle ilişkili resmi olmayan notlar.|\<none>|
|Horizontaloffset|Dekoratörün varsayılan konumuyla ilgili olarak inç olarak yatay uzaklık. (Yalnızca şekiller üzerinde.)|0|
|Verticaloffset|Dekoratörün varsayılan konumuyla ilgili dikey uzaklık inç olarak. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün çizgiden, varsayılan konumuyla (inç) uzaklığı. (Yalnızca bağlayıcılarda.)|0|
|OffsetFromShape|Dekoratörün, varsayılan konumundaki şekliyle inç olarak uzaklığı. (Yalnızca bağlayıcılarda.)|0|
|Konum|Dekoratörün varsayılan konumu.|SourceTop|

## <a name="textdecorator"></a>Textdecorator

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Defaulttext|Görüntülenecek varsayılan metin.|Etiketle|
|DisplayName|Oluşturulan tasarımcıda görüntülenecek dekoratörün adı.|Etiketle|
|FontSize|Dekoratörde görüntülenen metnin yazı tipi boyutu.|8|
|Fontstyle|Dekoratörde görüntülenen metnin yazı tipi stili.|Düzenli|
|Name|Dekoratörün adı.|Etiketle|
|Notlar|Dekoratörle ilişkili resmi olmayan notlar.|\<none>|
|Horizontaloffset|Dekoratörün varsayılan konumuyla ilgili olarak inç olarak yatay uzaklık. (Yalnızca şekiller üzerinde.)|0|
|Verticaloffset|Dekoratörün varsayılan konumuyla ilgili dikey uzaklık inç olarak. (Yalnızca şekiller üzerinde.)|0|
|OffsetFromLine|Dekoratörün, varsayılan konumuna (inç olarak) göre, çizgi arasındaki fark. (Yalnızca bağlayıcılar üzerinde.)|0|
|OffsetFromShape|Dekoratörün şekilden, varsayılan konumuna göre inç cinsinden değeri. (Yalnızca bağlayıcılar üzerinde.)|0|
|Konum|Dekoratörün varsayılan konumu.|TargetBottom|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))