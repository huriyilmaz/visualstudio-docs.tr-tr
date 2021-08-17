---
title: XML şema tasarımcısı Graph görünümü
description: genel şema düğümlerinin grafik temsilini ve düğümler arasındaki ilişkileri sağlayan XML şema tasarımcısında Graph görünümü hakkında bilgi edinin.
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
ms.openlocfilehash: 92a5a93fd83dd0bfb2bc1bcef31bb52d26d02baa78612def6221696bb12ca3d9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351082"
---
# <a name="graph-view"></a>Graph görünümü

Graph görünümü, genel şema düğümlerinin ve düğümler arasındaki ilişkilerin grafik gösterimini sağlar. Graph görünümünün, tasarım yüzeyinde şema kümesinin düzenini değiştirme izni olmadığına unutmayın. Graph görünümü XML şema tasarımcısı araç çubuğunu ve içerik haritası çubuğunu da içerir.

aşağıdaki görüntüde, tasarım yüzeyinde altı genel düğüm ile Graph görünümü gösterilmektedir.

![XML şema tasarımcısı Graph görünümü](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Tasarım yüzeyi

Graph görünümünün tasarım yüzeyi, [XML şema tasarımcısı çalışma alanının](../xml-tools/xml-schema-designer-workspace.md)içeriğini görüntüler. çalışma alanı, şema kümesinden herhangi bir genel düğüm içeriyorsa, düğümler Graph görünümü tasarım yüzeyinde gösterilir ve her türlü ilişki olan düğümler arasında oklar çizilir.

Graph görünümünde bir düğüme çift tıkladığınızda XML düzenleyicisi görüntülenir.

Seçili düğümleri çalışma alanından silmek için, XSD Tasarımcı araç çubuğunu veya **Delete** tuşunu kullanın.

Tasarım yüzeyi boşsa, XML Düzenleyicisi, **XML şema Gezgini** ve filigran gösterilir. *Filigran* , tüm XSD tasarımcı görünümlerinin bağlantılarının listesidir.

![XSD Tasarımcısı; Graph Görünümü](../xml-tools/media/xsdgraphviewwatermark.gif)

Şema kümesinde hatalar varsa, listenin sonunda aşağıdaki metin görüntülenir: "küme içindeki hataları görüntülemek ve onarmak için Hata Listesi kullanın."

## <a name="breadcrumb-bar"></a>İçerik haritası çubuğu

Graph görünümünün alt tarafındaki içerik haritası çubuğu, seçili düğümün şema kümesinde bulunduğu yeri gösterir. Birden çok öğe seçilirse, içerik haritası çubuğu boş olur.

## <a name="context-right-click-menu"></a>Bağlam (sağ tıklama) menüsü

aşağıdaki tabloda Graph görünümü tasarım yüzeyindeki tüm düğümler için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**XML şema Gezgini 'nde göster**|Şema Gezginine odaklankoyar ve şema kümesi düğümünü vurgular.|
|**Graph görünümünde göster**|Graph görünümüne geçiş yapar (gri).|
|**Örnek XML oluştur**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası oluşturur.|
|**Çalışma alanını temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma alanından Kaldır**|Seçili düğümleri çalışma alanından ve tasarım yüzeyinden kaldırır.|
|**Seçimi çalışma alanından Tümünü Kaldır**|Çalışma alanından ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Diyagramı görüntü olarak dışarı aktar**|Tasarım yüzeyini bir XPS dosyasına kaydeder.|
|**Tümünü Seç**|Tasarım yüzeyinde tüm düğümleri seçer.|
|**Kodu Görüntüle**|XML düzenleyicisinde Seçili düğümü içeren dosyayı açar. XML **şeması Gezgini** 'nde seçilen öğe, XML düzenleyicisinde de seçilidir.|
|**Özellikler penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

Yukarıda açıklanan ortak seçeneklere ek olarak, genel öğelerin bağlam menüsü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tür tanımı Ekle**|Temel türü diyagrama ekler.|
|**Tüm başvuruları Ekle**|Öğeye başvuran tüm düğümleri ekler ve aralarındaki ilişkileri göstermek için oklar çizer.|
|**Değiştirme grubu üyeleri Ekle**|Tüm değiştirme grubu üyelerini ekler. Bu seçenek, öğe bir değiştirme grubunun Head veya üyesiyse görünümde görüntülenir.|
|**Örnek XML oluştur**|Genel öğe için örnek bir XML dosyası oluşturur.|

Yukarıda açıklanan ortak seçeneklere ek olarak, genel basit ve genel karmaşık türlerin bağlam menüsü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Taban türü Ekle**|Seçilen tür genel bir türden türetildiyse, seçilen türün temel türünü ekler.|
|**Tüm başvuruları Ekle**|Seçilen türdeki tüm başvuruları ekler. Bu, seçilen türden öğeleri ve öznitelikleri ve seçilen türden türetilmiş türleri içerir.|
|**Tüm türetilmiş türleri ekle**|Seçilen türden doğrudan ve dolaylı olarak türetilen tüm türleri ekler.|
|**Tüm üst öğeleri ekle**|Tüm üst (taban) türlerini ekler.|

Yukarıda açıklanan ortak seçeneklere ek olarak, genel gruplar ve öznitelik grupları için de bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm başvuruları Ekle**|Gruba başvuran tüm düğümleri ekler ve aralarındaki ilişkileri göstermek için oklar çizer.|
|**Tüm üyeleri Ekle**|Grubun tüm üyelerini ekler ve aralarındaki ilişkileri göstermek için oklar çizer.|

Yukarıda açıklanan ortak seçeneklere ek olarak, genel özniteliklerin bağlam menüsü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm başvuruları Ekle**|Gruba başvuran tüm düğümleri ekler ve aralarındaki ilişkileri göstermek için oklar çizer.|

## <a name="properties-window"></a>Özellik penceresi

İlk olarak **Özellikler** penceresini açmak için bağlam (sağ tıklama) menüsünü kullanın. Varsayılan olarak, **Özellikler** penceresi Visual Studio sağ alt köşesinde görüntülenir. Içerik modeli görünümünde işlenen bir düğüme tıkladığınızda, bu düğümün özellikleri **Özellikler** penceresinde görüntülenir.

## <a name="xsd-toolbar"></a>XSD araç çubuğu

Graph görünümü etkinken aşağıdaki XSD araç çubuğu düğmeleri etkinleştirilir.

![XML şema Tasarımcısı araç çubuğu](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç görünümünü göster**|[Başlangıç görünümüne](../xml-tools/start-view.md)geçer. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **CTRL** + **1**.|
|**Içerik modeli görünümünü göster**|[Içerik modeli görünümüne](../xml-tools/content-model-view.md)geçiş yapar. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **CTRL** + **2**.|
|**Graph görünümünü göster**|[Graph görünümüne](../xml-tools/graph-view.md)geçer. Bu görünüme, Ctrl 3 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**Çalışma Alanını Temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma Alanı'dan kaldırma**|Seçilen düğümleri çalışma alanında ve tasarım yüzeyinden kaldırır.|
|**Çalışma Alanı'dan seçim dışında tüm seçenekleri kaldırma**|Çalışma alanı ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır. Bu seçenek, İçerik Modeli Görünümü'ne ve Graph etkinleştirilir.|
|**Soldan Sağa**|Graph Görünümü'nde düzeni, düğümlerin soldan sağa hiyerarşik gösterimine değiştirir. Bu seçenenlere klavye kısayolu kullanılarak erişilebilir: **Sağ alt** + **ok.**|
|**Sağdan Sola**|Graph Görünümü'nde düzeni, düğümlerin sağdan sola hiyerarşik gösterimine değiştirir. Bu seçenence klavye kısayolu kullanılarak erişilebilir: **Alt** + **sol ok.**|
|**Üstten Aşağıya**|Graph Görünümü'nde düzeni, düğümlerin üst-alt hiyerarşik gösterimine değiştirir. Bu seçenenlere klavye kısayolu kullanılarak erişilebilir: **Alt** + **aşağı ok.**|
|**Aşağıdan Yukarıya**|Graph Görünümü'nde düzeni, düğümlerin alt-üst hiyerarşik gösterimine değiştirir. Bu seçenence klavye kısayolu kullanılarak erişilebilir: **Alt** + **yukarı ok.**|

## <a name="panscroll"></a>Kaydır/Kaydır

Tasarım yüzeyini kaydırma çubuklarını kullanarak veya fareye tıklar ve sürüklerken **Ctrl** tuşunu basılı tutarak kaydırabilirsiniz. Tıklama ve sürükleme kullanarak tasarım yüzeyini kaydırıyorsanız, imleç dört yönde işaret eden dört çapraz ok olarak değişir.

## <a name="undoredo"></a>Geri Al/Tekrarla

Geri alma/yenidendo özelliği, aşağıdaki eylemler Graph Görünüm'de etkinleştirilir:

- Sürükleyip bırakarak tek bir düğüm ekleme.

- Şema Gezgini'nde veya Başlangıç Görünümü sorgularında arama sonuçları penceresinden birden çok düğüm ekleme.

- Tek veya birden çok düğümü silme.

## <a name="zoom"></a>Zoom

Yakınlaştırma, Graph Görünümü'nin sağ alt köşesinde mevcuttur.

Yakınlaştırma aşağıdaki yollarla denetlenebilir:

- **Ctrl tuşunu basılı tutarak** ve fare görünüm yüzeyinin üzerine geldiğinde fare tekerleğini Graph döndürerek.

- Kaydırıcı denetimi kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Yakınlaştırma kaydırıcısı seçiliyken opaktır, üzerine gelin veya yakınlaştırmak için fare tekerleğiyle **Ctrl** tuşunu kullanın; diğer tüm zamanlarda saydamdır.

## <a name="xml-editor-integration"></a>XML düzenleyicisi tümleştirmesi

Bir düğüme tıklar ve Kodu Görüntüle bağlamını (sağ tıklama) kullanarak Graph Görünümü ile XML düzenleyicisi arasında geçiş yapabilirsiniz.

XML düzenleyicisinde ayarlanmış şemada değişiklik yaptısanız, değişiklikler Graph Görünümü'nde eşitlenir. Daha fazla bilgi için [bkz. XML düzenleyicisiyle tümleştirme.](../xml-tools/integration-with-xml-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Yüzeyi](../xml-tools/xml-schema-designer-workspace.md)
