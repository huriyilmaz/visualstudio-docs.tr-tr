---
title: XML Şema Gezgini
description: Visual Studio ve XML Düzenleyicisi ile tümleştirilmiş XML şema Gezgini özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31edea44741249c5d75a53e291c766824dc3b8ea
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351303"
---
# <a name="xml-schema-explorer"></a>XML Şema Gezgini

XML **şema Gezgini** , XML şeması tanım DILI (xsd) şemaları ile çalışmanıza olanak tanımak için MICROSOFT VISUAL STUDIO ve XML Düzenleyicisi ile tümleşiktir. Bir XML şema dosyası açtığınızda, **şema kümesi** düğümü **XML şema Gezgini** 'nde görünür. Hedef dosyanız için dahil edilen, içeri aktarılan veya yeniden tanımlanmış şemaların yanı sıra bir veya ifadesiyle başvurulan tüm dosyalar `include` `import` da **XML şema Gezgini** 'nde görünür.

**XML şeması Gezgini** şunları yapmanızı sağlar:

- Şema kümesine hızlı bir genel bakış alın.

- Gider ve ağaca gidin.

- Anahtar sözcük ve şemaya özgü aramalar gerçekleştirin. Daha fazla bilgi için bkz. [Şema kümesini arama](../xml-tools/searching-the-schema-set.md).

- Arama sonuçlarını grafik görünümü veya Içerik modeli görünümüne ekleme

- Ağacı belge sırasına, türe veya ada göre sıralayın. Daha fazla bilgi için bkz. [sıralama, filtreleme ve gruplandırma](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- XML düzenleyicisini açın ve XSD dosyasındaki kod konumlarına atlayın. Daha fazla bilgi için bkz. [XML Düzenleyicisi Ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

- Genel öğeler için örnek XML oluşturun.

**XML şema Gezgini** , bir ağaç görünümü aracılığıyla şema kümesinin hiyerarşik bir görünümünü sağlar. **XML şeması Gezgini** Ayrıca arama, filtreleme, gezinme ve sıralama sağlar. **XML şema Gezgini** 'ne erişmek için aşağıdakilerden birini yapın:

- [Başlangıç görünümü](../xml-tools/start-view.md)' nde, **XML şema Gezgini** bağlantısına tıklayın.

- [Grafik görünümü](../xml-tools/graph-view.md) veya [içerik modeli görünümünde](../xml-tools/content-model-view.md) çalışıyorsanız ve çalışma alanınızda düğümleri varsa, **XML şema Gezginini** seçmek için bağlam (sağ tıklama) menüsünü kullanın.

- Ayrıca, **Görünüm** menüsünden **XML şema Gezginini** seçebilirsiniz.

- **XML şema** Gezginine, bir *. xsd* dosyasıyla ilişkilendirilmiş Visual Basic xml sabit değeri olan bir *. vb* dosyasından erişebilirsiniz. **XML şeması Gezgininde** şema kümesini görmek için, XML sabit değerinde bir xml düğümüne veya bir XML ad alanı içeri aktarma öğesine sağ tıklayın ve **şema Gezgini 'nde göster** komutunu seçin. Daha fazla bilgi için bkz. xml [şema Gezgini Ile xml sabit değerlerini tümleştirme](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Ağacı Görünümü
**XML şeması Gezgini** , önceden derlenmiş şema kümesi bilgilerini bir ağaç yapısında görüntüler. Ağaç yapısı aşağıdaki gibi düzenlenmiştir:

- En üst düzeyde, şema kümesi düğümüdür.

- İkinci düzey ad alanlarını içerir.

- Üçüncü düzey dosyaları içerir.

- Dördüncü düzey genel düğümleri içerir. Bu öğe, gruplar, karmaşık türler, basit türler, öznitelikler, öznitelik grupları, ve `include` , `import` ve `redefine` deyimleri içerebilir.

Aşağıda bir ağaç yapısına örnek verilmiştir:

![XML Şema Gezgini](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Seçim ve etkinleştirme
Bir düğümü vurgulamak ve seçmek için şema Gezgini ' nde bir kez tıklayın.

Bir düğümü etkinleştirmek için çift tıklayın veya düğüm seçildiğinde **ENTER** tuşuna basın.

- Bir düğümü etkinleştirmek, bu düğümün tanımlandığı dosyayı açar (dosya zaten açık değilse) ve dosyadaki düğümü seçer.

- Bir dosya düğümünü etkinleştirmek seçili dosyayı açar (zaten açık değilse) ve `<schema>` düğümü vurgular.

- Bir SchemaSet veya Namespace düğümünü etkinleştirmek hiçbir şey yapmaz.

## <a name="drag-and-drop-nodes"></a>Sürükle ve bırak düğümleri
Genel düğümleri, dosya düğümlerini ve ad alanı düğümlerini bir XSD Tasarımcı görünümü üzerine sürükleyip bırakabilirsiniz. Geçerli Görünüm [Başlangıç görünümse](../xml-tools/start-view.md), görünümde bir düğümü sürüklemek [grafik görünümünü](../xml-tools/graph-view.md)açar. Geçerli görünüm, [Içerik modeli görünümü](../xml-tools/content-model-view.md) veya grafik görünümüdür, üzerine bir düğüm bıraktığınızda görünüm değişmeyecektir.

Dosyaları görünümde bırakma, dosyadaki tüm genel düğümleri [XSD Designer çalışma alanına](../xml-tools/xml-schema-designer-workspace.md)ekler. Ad alanlarını görünümde bırakma, ad alanındaki tüm genel düğümleri çalışma alanına ekler. Çalışma alanı tüm görünümler arasında paylaşılır.

 Yerel düğümleri veya içeri aktarmaları sürükleyip bırakamazsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: XML şema Gezgini 'nden çalışma alanına düğüm ekleme](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
