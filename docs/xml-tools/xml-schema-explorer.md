---
title: XML Şema Gezgini
description: Visual Studio ve XML düzenleyicisi ile tümleştirilmiş XML Şema Gezgini'nin özellikleri hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: c731b4d8f6542fd73debe1b1b77ff624c27aa175
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130149"
---
# <a name="xml-schema-explorer"></a>XML Şema Gezgini

**XML Şema Gezgini,** XML Microsoft Visual Studio dili (XSD) şemaları ile çalışmana olanak sağlamak için xml düzenleyicisiyle tümleştirilmiştir. Bir XML Şeması dosyasını açsanız, **Şema Kümesi düğümü** XML Şema **Gezgini'nde görünür.** Hedef dosyanız için dahil edilen, içe aktarılan veya yeniden tanımlanmamış şemaların yanı sıra bir veya deyimi aracılığıyla başvurulan tüm dosyalar XML Şema `include` `import` Gezgini'nde de **görünür.**

**XML Şema Gezgini** şunları yapabilirsiniz:

- Şema kümesine hızlı bir genel bakış elde.

- Ağaçta gözatma ve gezinme.

- Anahtar sözcük ve şemaya özgü aramalar gerçekleştirin. Daha fazla bilgi için [bkz. Şema kümesinde arama.](../xml-tools/searching-the-schema-set.md)

- Arama sonuçlarını Graph Görünümü'ne ekleme

- Ağacı belge sırasına, türüne veya adına göre sırala. Daha fazla bilgi için [bkz. Sıralama, filtreleme ve gruplama.](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)

- XML düzenleyicisini açın ve XSD dosyasındaki kod konumlara atlayın. Daha fazla bilgi için [bkz. XML düzenleyicisiyle tümleştirme.](../xml-tools/integration-with-xml-editor.md)

- Genel öğeler için örnek XML oluşturma.

**XML Şema Gezgini,** ağaç görünümü aracılığıyla ayarlanmış şemanın hiyerarşik bir görünümünü sağlar. **XML Şema Gezgini arama,** filtreleme, gezinti ve sıralama da sağlar. XML Şema **Gezgini'ne erişmek** için, aşağıdakilerden birini yapın:

- Başlangıç [Görünümü'ndeyebilirsiniz,](../xml-tools/start-view.md)XML Şema **Gezgini bağlantısına** tıklayın.

- [Graph](../xml-tools/graph-view.md) Görünümü'nde veya İçerik Modeli [](../xml-tools/content-model-view.md) Görünümü'ndey ve çalışma alanınız içinde düğümler varsa, XML Şema Gezgini'ni seçmek için bağlam (sağ tıklama) **menüsünü kullanın.**

- Xml Şema **Gezgini'ni Görünüm menüsünden** de **seçebilirsiniz.**

- XML Şema **Gezgini'ne** bir .xsd dosyasıyla ilişkilendirilmiş Visual Basic XML değişmez sabiti olan bir *.vb* *dosyasından erişebilirsiniz.* XML Şema Gezgini'nde ayarlanmış şemayı görmek **için, XML** değişmez verisi veya XML ad alanı içeri aktarmada xml düğümüne sağ tıklayın ve Şema Gezgini'nde Göster **komutunu** seçin. Daha fazla bilgi için [bkz. XML değişmez değişmezlerinin XML Şema Gezgini ile tümleşmesi.](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)

## <a name="tree-view"></a>Ağacı Görünümü
**XML Şema Gezgini,** önceden derlenmiş şema kümesi bilgilerini bir ağaç yapısında görüntüler. Ağaç yapısı aşağıdaki gibi düzenlenmiştir:

- En üst düzeyde şema kümesi düğümü vardır.

- İkinci düzey ad alanlarını içerir.

- Üçüncü düzey dosyaları içerir.

- Dördüncü düzey genel düğümleri içerir. Bu öğeler, gruplar, karmaşık türler, basit türler, öznitelikler, öznitelik grupları ve `include` , `import` ve `redefine` deyimlerini içerebilir.

Aşağıda, ağaç yapısına bir örnek ve ardından ve bir örnek ve ardından ve bir ağaç yapısı ve bir ağaç yapısı ve daha sonra ve daha sonra 2.

![XML Şema Gezgini](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Seçim ve etkinleştirme
Bir düğümü vurgulamak ve seçmek için Şema Gezgini'nde bir kez tıklayın.

Bir düğümü etkinleştirmek için düğüme çift tıklayın veya düğüm **seçildiğinde Enter** tuşuna basın.

- Bir düğümün etkinleştirerek bu düğümün tanımlandığı dosya açılır (dosya henüz açık durumda değilse) ve dosyada düğümü seçer.

- Bir dosya düğümünü etkinleştirmek seçilen dosyayı açar (henüz açık değilse) ve düğümü `<schema>` vurgular.

- SchemaSet veya ad alanı düğümünü etkinleştirmek hiçbir şey yapmadı.

## <a name="drag-and-drop-nodes"></a>Düğümleri sürükleyip bırakma
Genel düğümleri, dosya düğümlerini ve ad alanı düğümlerini bir XSD Tasarımcısı görünümüne sürükleyip bırakın. Geçerli görünüm Başlangıç Görünümü [ise,](../xml-tools/start-view.md)bir düğümü görünüme sürüklemek, [Görünüm'Graph açar.](../xml-tools/graph-view.md) Geçerli görünüm İçerik Modeli Görünümü [veya](../xml-tools/content-model-view.md) Graph Görünümü ise, üzerine bir düğüm bıraksanız görünüm değişmez.

Görünümdeki dosyaları bırakmak, dosyada yer alan tüm genel düğümleri [XSD Designer](../xml-tools/xml-schema-designer-workspace.md)çalışma alanına ekler. Görünüme ad alanlarını bırakmak, ad alanında yer alan tüm genel düğümleri çalışma alanına ekler. Çalışma alanı tüm görünümler arasında paylaşılır.

 Yerel düğümleri veya içeri aktarmaları sürükleyip bırakamazsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: XML Şema Gezgini'nde çalışma alanına düğüm ekleme](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
