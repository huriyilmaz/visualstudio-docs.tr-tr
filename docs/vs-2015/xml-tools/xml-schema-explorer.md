---
title: XML şema Gezgini | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e9f61c56dd7ff2a9c6c19afc20ed279a7fdf855
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669370"
---
# <a name="xml-schema-explorer"></a>XML Şema Gezgini
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML şema Gezgini, XML şeması tanım dili (XSD) şemaları ile çalışmanıza olanak tanımak için Microsoft Visual Studio ve XML Düzenleyicisi ile tümleşiktir. Bir XML şema dosyası açtığınızda, **şema kümesi** düğümü xml şema Gezgini 'nde görünür. Hedef dosyanız için dahil edilen, içeri aktarılan veya yeniden tanımlanmış şemaların yanı sıra bir `include` veya `import` bildirimiyle başvurulan tüm dosyalar da XML şema Gezgini 'nde görünür.

 XML şeması Gezgini şunları yapmanızı sağlar:

- Şema kümesine hızlı bir genel bakış alın.

- Gider ve ağaca gidin.

- Anahtar sözcük ve şemaya özgü aramalar gerçekleştirin. Daha fazla bilgi için bkz. [Şema kümesini arama](../xml-tools/searching-the-schema-set.md).

- Arama sonuçlarını grafik görünümüne veya Içerik modülle görünümüne ekleme

- Ağacı belge sırasına, türe veya ada göre sıralayın. Daha fazla bilgi için bkz. [sıralama, filtreleme ve gruplandırma](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- XML düzenleyicisini açın ve XSD dosyasındaki kod konumlarına atlayın. Daha fazla bilgi için bkz. [XML Düzenleyicisi Ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

- Genel öğeler için örnek XML oluşturun.

  XML şema Gezgini, bir ağaç görünümü aracılığıyla şema kümesinin hiyerarşik bir görünümünü sağlar. XML şeması Gezgini Ayrıca arama, filtreleme, gezinme ve sıralama sağlar. XML şema Gezgini 'ne erişmek için aşağıdakilerden birini yapın:

- [Başlangıç görünümü](../xml-tools/start-view.md)' nde, **XML şema Gezgini** bağlantısına tıklayın.

- [Grafik görünümünde](../xml-tools/graph-view.md) veya [içerik modeli görünümünde](../xml-tools/content-model-view.md) çalışıyorsanız ve çalışma ALANıNıZDA düğümleri varsa, XML şema Gezgini ' ni seçmek için bağlam menüsünü kullanın.

- Ayrıca **Görünüm** menüsünde XML şeması Gezgini ' ni de seçebilirsiniz.

- XML şeması Gezgini ' ne bir. xsd dosyasıyla ilişkilendirilmiş Visual Basic XML sabit değeri olan bir. vb dosyasından erişebilirsiniz. XML şeması Gezgininde şema kümesini görmek için, XML sabit değerinde bir xml düğümüne veya bir XML ad alanı içeri aktarma öğesine sağ tıklayın ve **şema Gezgini 'Nde göster** komutunu seçin. Daha fazla bilgi için bkz. xml [şema Gezgini Ile xml sabit değerlerini tümleştirme](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Ağaç görünümü
 XML şeması Gezgini, önceden derlenmiş şema kümesi bilgilerini bir ağaç yapısında görüntüler. Ağaç yapısı aşağıdaki gibi düzenlenmiştir:

- En üst düzeyde, şema kümesi düğümüdür.

- İkinci düzey ad alanlarını içerir.

- Üçüncü düzey dosyaları içerir.

- Dördüncü düzey genel düğümleri içerir. Bu öğe, gruplar, karmaşık türler, basit türler, öznitelikler, öznitelik grupları ve `include`, `import` ve `redefine` deyimlerini içerebilir.

  Aşağıda bir ağaç yapısına örnek verilmiştir:

  ![XML Şema Gezgini](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")

## <a name="selection-and-activation"></a>Seçim ve etkinleştirme
 Bir düğümü vurgulamak ve seçmek için şema Gezgini ' nde bir kez tıklayın.

 Bir düğümü etkinleştirmek için çift tıklayın veya düğüm seçildiğinde **ENTER** tuşuna basın.

- Bir düğümü etkinleştirmek, bu düğümün tanımlandığı dosyayı açar (dosya zaten açık değilse) ve dosyadaki düğümü seçer.

- Bir dosya düğümünü etkinleştirmek seçili dosyayı açar (zaten açık değilse) ve `<schema>` düğümünü vurgular.

- Bir SchemaSet veya Namespace düğümünü etkinleştirmek hiçbir şey yapmaz.

## <a name="draging-and-dropping-nodes"></a>Düğümleri drenaklama ve bırakma
 Genel düğümleri, dosya düğümlerini ve ad alanı düğümlerini bir XSD Tasarımcı görünümü üzerine sürükleyip bırakabilirsiniz. Geçerli Görünüm [Başlangıç görünümse](../xml-tools/start-view.md), görünümde bir düğümü sürüklemek [grafik görünümünü](../xml-tools/graph-view.md)açar. Geçerli görünüm, [Içerik modeli görünümü](../xml-tools/content-model-view.md) veya grafik görünümüdür, üzerine bir düğüm bıraktığınızda görünüm değişmeyecektir.

 Dosyaları görünümde bırakma, dosyadaki tüm genel düğümleri [XSD Designer çalışma alanına](../xml-tools/xml-schema-designer-workspace.md)ekler. Ad alanlarını görünümde bırakma, ad alanındaki tüm genel düğümleri çalışma alanına ekler. Çalışma alanı tüm görünümler arasında paylaşılır.

 Yerel düğümleri veya içeri aktarmaları sürükleyip bırakamazsınız.

## <a name="in-this-section"></a>Bu Bölümde

- [Şema Kümesini Arama](../xml-tools/searching-the-schema-set.md)

- [Sıralama, Filtreleme ve Gruplandırma](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)

- [Bağlam Menüleri](../xml-tools/context-menus-xml-schema-explorer.md)

- [XML Değişmez Değerlerinin XML Şeması Gezgini ile Tümleştirilmesi](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl Yapılır: XML Şema Gezgininden Çalışma Alanına Düğüm Ekleme](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
