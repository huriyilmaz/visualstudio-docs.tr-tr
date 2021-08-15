---
title: XML Şema Tasarımcısı Graph Görünümü
description: Genel şema Graph ve düğümler arasındaki ilişkilerin grafik gösterimini sağlayan XML Şema Tasarımcısı'nda Graph Görünümü hakkında bilgi öğrenin.
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

Graph Görünümü, genel şema düğümlerinin ve düğümler arasındaki ilişkilerin grafik gösterimini sağlar. Graph Görünümü'nin tasarım yüzeyinde ayarlanmış şema düzenini değiştirmesine izin vermeyebilirsiniz. Graph Görünümü, XML Şema Tasarımcısı araç çubuğunu ve breadcrumb çubuğunu da içerir.

Aşağıdaki görüntüde, tasarım Graph genel düğüme sahip bir Görünüm görünümü yer almaktadır.

![XML Şema Tasarımcısı Graph Görünümü](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Tasarım yüzeyi

Graph Görünümü'nin tasarım yüzeyi, XML şema tasarımcısı çalışma [alanının içeriğini görüntüler.](../xml-tools/xml-schema-designer-workspace.md) Çalışma alanı şema kümesinden herhangi bir genel düğüm içeriyorsa, düğümler Tasarım yüzeyini görüntüle Graph düğümler üzerinde gösterilir ve ilişkileri olan düğümler arasında oklar çizilir.

Görünümde bir düğüme çift Graph XML düzenleyicisi açılır.

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
|**Görünümde Graph Göster**|Graph Görünümüne geçiş (gri).|
|**Örnek XML Oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası üretir.|
|**Çalışma Alanını Temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma Alanı'dan kaldırma**|Seçilen düğümleri çalışma alanında ve tasarım yüzeyinden kaldırır.|
|**Çalışma Alanı'dan seçim dışında tüm seçenekleri kaldırma**|Çalışma alanı ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Diyagramı Görüntü Olarak Dışarı Aktarma**|Tasarım yüzeyini bir XPS dosyasına kaydeder.|
|**Hepsini Seç**|Tasarım yüzeyindeki tüm düğümleri seçer.|
|**Kodu Görüntüle**|Seçilen düğümü içeren dosyayı XML düzenleyicisinde açar. XML Şema Gezgini'nde **seçilen öğe** XML düzenleyicisinde de seçilir.|
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

Özellikler penceresini ilk kez açmak için bağlam (sağ tıklama) **menüsünü** kullanın. Varsayılan olarak Özellikler **penceresi,** uygulamanın sağ alt köşesinde Visual Studio. İçerik Modeli Görünümü'ne işlenen bir düğüme tıklarken, bu düğümün özellikleri Özellikler Penceresinde **görüntülenir.**

## <a name="xsd-toolbar"></a>XSD araç çubuğu

Aşağıdaki XSD Araç Çubuğu düğmeleri, Graph etkin olduğunda etkinleştirilir.

![XML Şema Tasarımcısı Araç Çubuğu](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç Görünümünü Göster**|Başlangıç [Görünümü'ne geçişler.](../xml-tools/start-view.md) Bu görünüme, Ctrl 1 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**İçerik Modeli Görünümünü Göster**|İçerik Modeli [Görünümüne geçişler.](../xml-tools/content-model-view.md) Bu görünüme, Ctrl 2 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**Görünüm Graph Göster**|görünüme [Graph.](../xml-tools/graph-view.md) Bu görünüme klavye kısayolu kullanılarak erişilebilir: **CTRL** + **3**.|
|**Çalışma alanını temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma alanından Kaldır**|Seçili düğümleri çalışma alanından ve tasarım yüzeyinden kaldırır.|
|**Seçimi çalışma alanından Tümünü Kaldır**|Çalışma alanından ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır. bu seçenek, içerik modeli görünümünde ve Graph görünümünde etkinleştirilir.|
|**Soldan sağa**|Graph görünümündeki yerleşimi, düğümlerin soldan sağa hiyerarşik gösterimine değiştirir. Bu seçeneğe, klavye kısayolu: **alt** + **sağ ok** kullanılarak erişilebilir.|
|**Sağdan sola**|Graph görünümündeki düzeni düğümlerin sağdan sola hiyerarşik bir gösterimine dönüştürür. Bu seçeneğe klavye kısayolu kullanılarak erişilebilir: **alt** + **sol ok**.|
|**Yukarıdan aşağıya**|Graph görünümündeki düzeni düğümlerin üst-alt hiyerarşik gösterimine dönüştürür. Bu seçeneğe klavye kısayolu kullanılarak erişilebilir: **alt** + **aşağı ok**.|
|**Aşağıdan yukarıya**|Graph görünümündeki düzeni düğümlerin yukarıdan yukarıya hiyerarşik gösterimine dönüştürür. Bu seçeneğe, klavye kısayolu: **alt** + **yukarı ok** kullanılarak erişilebilir.|

## <a name="panscroll"></a>Kaydır/KAYDIR

Tasarım yüzeyini, kaydırma çubuklarını kullanarak ya da tıklamakta ve fareyle sürüklerken **CTRL** tuşunu basılı tutarak kaydırabilirsiniz. Tasarım yüzeyini tıklama ve sürükleme kullanarak kaydırdığınızda, imleç dört yönü işaret eden dört çapraz geçiş olacak şekilde değişir.

## <a name="undoredo"></a>Geri Al/Yinele

geri al/yinele özelliği, aşağıdaki eylemler için Graph görünümünde etkinleştirilir:

- Sürükleyip bırakarak tek bir düğüm ekleme.

- Şema Gezgini 'nde arama sonuçları penceresinden birden çok düğüm ekleme veya görünüm sorguları başlatma.

- Tek veya birden çok düğüm siliniyor.

## <a name="zoom"></a>Zoom

yakınlaştırma Graph görünümünün sağ alt köşesinde bulunur.

Yakınlaştırma, aşağıdaki yollarla denetlenebilir:

- **Ctrl** tuşunu basılı tutarak ve fare Graph görünüm yüzeyi üzerine getirildiğinde fare tekerleğini döndürürken.

- Kaydırıcı denetimini kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Yakınlaştırma kaydırıcısı, seçtiğinizde yakınlaştırılır, üzerine gelin veya yakınlaştırmak için fare tekerleği ile **CTRL** tuşlarını kullanın; Tüm diğer zamanlarda saydamdır.

## <a name="xml-editor-integration"></a>XML düzenleyici tümleştirmesi

bir düğüme tıklayarak ve kod bağlamını görüntüle (sağ tıklama) menüsünü kullanarak Graph görünümü ile XML düzenleyicisi arasında geri ve ileri geçiş yapabilirsiniz.

XML düzenleyicisinde şema kümesinde değişiklik yaparsanız, değişiklikler Graph görünümünde eşitlenir. Daha fazla bilgi için bkz. [XML Düzenleyicisi Ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Yüzeyi](../xml-tools/xml-schema-designer-workspace.md)
