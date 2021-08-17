---
title: XML Şema Tasarımcısı Graph Görünümü
description: Genel şema Graph ve düğümler arasındaki ilişkilerin grafik gösterimini sağlayan XML Şema Tasarımcısı'nda Genel Görünüm hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 82e5b51628bd4589b27095c7591a7d4683faaa55
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025166"
---
# <a name="graph-view"></a>Graph görünümü

Graph Görünümü, genel şema düğümlerinin ve düğümler arasındaki ilişkilerin grafik gösterimini sağlar. Graph Görünümü'nin tasarım yüzeyinde ayarlanmış şema düzenini değiştirmesine izin vermeyebilirsiniz. Graph Görünümü, XML Şema Tasarımcısı araç çubuğunu ve breadcrumb çubuğunu da içerir.

Aşağıdaki görüntüde, tasarım Graph genel düğüme sahip bir Görünüm görünümü yer almaktadır.

![XML Şema Tasarımcısı Graph Görünümü](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Tasarım yüzeyi

Graph Görünümü'nin tasarım yüzeyi, XML şema tasarımcısı çalışma [alanının içeriğini görüntüler.](../xml-tools/xml-schema-designer-workspace.md) Çalışma alanı şema kümesinden herhangi bir genel düğüm içeriyorsa, düğümler Tasarım yüzeyini görüntüle Graph düğümler üzerinde gösterilir ve ilişkileri olan düğümler arasında oklar çizilir.

Graph Görünümü'nde bir düğüme çift tıklar, XML düzenleyicisini getirir.

Seçili düğümleri çalışma alanında silmek için XSD Tasarımcısı araç çubuğunu veya Sil **anahtarını** kullanın.

Tasarım yüzeyi boşsa XML düzenleyicisi, **XML** Şema Gezgini ve filigran gösterilir. Filigran, *tüm* XSD Tasarımcısı görünümlerinin bağlantılarının listesidir.

![XSD Tasarımcısı; Graph Görünüm](../xml-tools/media/xsdgraphviewwatermark.gif)

Şema kümesinde hatalar varsa, listenin sonunda şu metin görüntülenir: "Kümede hataları görüntülemek ve düzeltmek için Hata Listesini kullanın."

## <a name="breadcrumb-bar"></a>Breadcrumb çubuğu

Graph View(Görünüm) altındaki breadcrumb çubuğu, seçilen düğümün şema kümesinde nerede olduğunu gösterir. Birden çok öğe seçilirse, breadcrumb çubuğu boş olur.

## <a name="context-right-click-menu"></a>Bağlam (sağ tıklama) menüsü

Aşağıdaki tabloda Görünüm tasarım yüzeyindeki tüm düğümler için kullanılabilen Graph açık bulunmaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**XML Şema Gezgini'nde göster**|Odağı Şema Gezgini'ne koyar ve şema kümesi düğümünü vurgular.|
|**Görünümde Graph Göster**|Graph Görünümüne (gri görünür) geçişler.|
|**Örnek XML Oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası üretir.|
|**Çalışma Alanını Temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma Alanı'dan kaldırma**|Seçilen düğümleri çalışma alanında ve tasarım yüzeyinden kaldırır.|
|**Çalışma Alanı'dan seçim dışında tüm seçenekleri kaldırma**|Çalışma alanı ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Diyagramı Görüntü Olarak Dışarı Aktarma**|Tasarım yüzeyini bir XPS dosyasına kaydeder.|
|**Hepsini Seç**|Tasarım yüzeyindeki tüm düğümleri seçer.|
|**Kodu Görüntüle**|Seçilen düğümü içeren dosyayı XML düzenleyicisinde açar. XML Şema Gezgini'nde **seçilen öğe** de XML düzenleyicisinde seçilir.|
|**Özellikler Penceresi**|Özellikler **penceresini** açar (henüz açık değilse). Bu pencerede düğümle ilgili bilgiler görüntülenir.|

Yukarıda açıklanan ortak seçeneklere ek olarak, genel öğeler için bağlam menüsünde de aşağıdaki seçenekler vardır:

|Seçenek|Açıklama|
|-|-----------------|
|**Tür Tanımı Ekleme**|Diyagrama temel türü ekler.|
|**Tüm Başvuruları Ekle**|Öğesine başvuran tüm düğümleri ekler ve aralarındaki ilişkileri belirtmek için oklar çizer.|
|**Değiştirme Grubu Üyeleri Ekleme**|Tüm değiştirme grubu üyelerini ekler. Öğe bir değiştirme grubunun baş veya üyesi ise bu seçenek görünümde görünür.|
|**Örnek XML Oluşturma**|Genel öğe için örnek bir XML dosyası üretir.|

Yukarıda açıklanan yaygın seçeneklere ek olarak, genel basit ve genel karmaşık türler için bağlam menüsünde de aşağıdaki seçenekler vardır:

|Seçenek|Açıklama|
|-|-----------------|
|**Temel Tür Ekleme**|Seçilen tür genel bir türden türetildiyse, seçilen türün temel türünü ekler.|
|**Tüm Başvuruları Ekle**|Seçilen türün tüm başvurularını ekler. Bu, seçilen türün öğelerini ve özniteliklerini ve seçilen türden türetilen türleri içerir.|
|**Türetilen Tüm Türleri Ekle**|Seçilen türden doğrudan ve dolaylı olarak türetilen tüm türleri ekler.|
|**Tüm ÜstLeri Ekle**|Tüm üst (temel) türleri ekler.|

Yukarıda açıklanan ortak seçeneklere ek olarak, genel gruplar ve öznitelik grupları için bağlam menüsü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm Başvuruları Ekle**|Gruba başvuran tüm düğümleri ekler ve aralarındaki ilişkileri belirtmek için oklar çizer.|
|**Tüm Üyeleri Ekle**|Grubun tüm üyelerini ekler ve aralarındaki ilişkileri göstermek için oklar çizer.|

Yukarıda açıklanan ortak seçeneklere ek olarak, genel özniteliklerin bağlam menüsünde de aşağıdaki seçenekler vardır:

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm Başvuruları Ekle**|Gruba başvuran tüm düğümleri ekler ve aralarındaki ilişkileri belirtmek için oklar çizer.|

## <a name="properties-window"></a>Özellik penceresi

Özellikler penceresini ilk kez açmak için bağlam (sağ tıklama) **menüsünü** kullanın. Varsayılan olarak Özellikler **penceresi,** uygulamanın sağ alt köşesinde Visual Studio. İçerik Modeli Görünümünde işlenen bir düğüme tıklarken, bu düğümün özellikleri Özellikler Penceresinde **görüntülenir.**

## <a name="xsd-toolbar"></a>XSD araç çubuğu

Aşağıdaki XSD Araç Çubuğu düğmeleri, Graph etkin olduğunda etkinleştirilir.

![XML Şema Tasarımcısı Araç Çubuğu](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç Görünümünü Göster**|Başlangıç [Görünümü'ne geçişler.](../xml-tools/start-view.md) Bu görünüme, Ctrl 1 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**İçerik Modeli Görünümünü Göster**|İçerik Modeli [Görünümüne geçişler.](../xml-tools/content-model-view.md) Bu görünüme, Ctrl 2 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**Görünüm Graph Göster**|görünüme [Graph.](../xml-tools/graph-view.md) Bu görünüme, Ctrl 3 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**Çalışma Alanını Temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma Alanı'dan kaldırma**|Seçilen düğümleri çalışma alanında ve tasarım yüzeyinden kaldırır.|
|**Çalışma Alanı'dan seçim dışında tüm seçenekleri kaldırma**|Çalışma alanı ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır. Bu seçenek, İçerik Modeli Görünümü'ne ve Graph etkinleştirilir.|
|**Soldan Sağa**|Graph Görünümü'nde düzeni, düğümlerin soldan sağa hiyerarşik gösterimine değiştirir. Bu seçenenlere klavye kısayolu kullanılarak erişilebilir: **Sağ alt** + **ok.**|
|**Sağdan Sola**|Graph Görünümü'nde düzeni, düğümlerin sağdan sola hiyerarşik gösterimine değiştirir. Bu seçenence klavye kısayolu kullanılarak erişilebilir: **Alt** + **sol ok.**|
|**Üstten Aşağıya**|Graph Görünümü'nde düzeni, düğümlerin üst-alt hiyerarşik gösterimine değiştirir. Bu seçenenlere klavye kısayolu kullanılarak erişilebilir: **Alt** + **aşağı ok.**|
|**Aşağıdan Yukarıya**|Graph Görünümü'nde düzeni, düğümlerin alttan en üste hiyerarşik gösterimine değiştirir. Bu seçenence klavye kısayolu kullanılarak erişilebilir: **Alt** + **yukarı ok.**|

## <a name="panscroll"></a>Kaydır/Kaydır

Tasarım yüzeyini kaydırma çubuklarını kullanarak veya fareye tıklar ve sürüklerken **Ctrl** tuşunu basılı tutarak kaydırabilirsiniz. Tıklama ve sürükleme kullanarak tasarım yüzeyini kaydırıyorsanız, imleç dört yönde işaret eden dört çapraz ok olarak değişir.

## <a name="undoredo"></a>Geri Al/Tekrarla

Geri alma/yenidendo özelliği, aşağıdaki eylemler Graph Görünüm'de etkinleştirilir:

- Sürükleyip bırakarak tek bir düğüm ekleme.

- Şema Gezgini'nde veya Başlangıç Görünümü sorgularında arama sonuçları penceresinden birden çok düğüm ekleme.

- Tek veya birden çok düğümü silme.

## <a name="zoom"></a>Zoom

Yakınlaştırma, Graph View'ın sağ alt köşesinde kullanılabilir.

Yakınlaştırma aşağıdaki yollarla denetlenebilir:

- **Ctrl tuşunu basılı tutarak** ve fare görünüm yüzeyinin üzerine geldiğinde fare tekerleğini Graph döndürerek.

- Kaydırıcı denetimi kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Yakınlaştırma kaydırıcısı seçiliyken opaktır, üzerine gelin veya yakınlaştırmak için fare tekerleğiyle **Ctrl** tuşunu kullanın; diğer tüm zamanlarda saydamdır.

## <a name="xml-editor-integration"></a>XML düzenleyicisi tümleştirmesi

Bir düğüme tıklar ve Kodu Görüntüle bağlamını (sağ tıklama) kullanarak Graph Görünümü ile XML düzenleyicisi arasında geçiş yapabilirsiniz.

XML düzenleyicisinde ayarlanmış şemada değişiklik yaptısanız, değişiklikler Graph Görünümü'nde eşitlenir. Daha fazla bilgi için [bkz. XML düzenleyicisiyle tümleştirme.](../xml-tools/integration-with-xml-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Yüzeyi](../xml-tools/xml-schema-designer-workspace.md)
