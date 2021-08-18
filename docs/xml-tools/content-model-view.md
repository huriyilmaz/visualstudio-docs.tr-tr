---
title: XML Şema Tasarımcısı İçerik Modeli Görünümü
description: Yerel ve genel şema düğümlerinin ve bileşenlerinin grafik gösterimini sağlayan XAML Şema Tasarımcısı'nda İçerik Modeli Görünümü hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: d2f9f642ef030778f94fd621b3eb122624e6586b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091961"
---
# <a name="content-model-view"></a>İçerik Modeli Görünümü

İçerik Modeli Görünümü, basit ve karmaşık türler, öğeler, model grupları, öznitelikler ve öznitelik grupları dahil olmak üzere yerel ve genel şema düğümlerinin ve bileşenlerinin grafik gösterimini sağlar. XML yorumları ve işleme yönergeleri İçerik Modeli Görünümünde görüntü olamaz. İçerik Modeli Görünümü iki panel  içerir: [XML](../xml-tools/xml-schema-designer-workspace.md)şema tasarımcısı çalışma alanında düğümlerin listesini içeren çalışma alanı paneli ve Çalışma Alanı **panelinde** seçilen şema düğümlerinin içerik modelini gördüğünüz tasarım yüzeyi. İçerik Modeli Görünümü, XML Şema Tasarımcısı araç çubuğunu ve içerik eşleme çubuğunu da içerir.

Aşağıdaki görüntüde, Çalışma **Alanı** paneli altı şema düğümü içerir. Düğüm `purchaseOrder` Çalışma Alanı **panelinde seçilidir** ve tasarım yüzeyinde görüntülenir.

![XML Şema Tasarımcısı İçerik Modeli Görünümü](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Çalışma alanı paneli

Çalışma alanına düğümler ekledikten sonra, düğüm listesi İçerik Modeli **Görünümü'nin Çalışma** Alanı panelinde görünür. Çalışma Alanı panelinde düğümleri **seçerek** İçerik Modeli Görünümü tasarım yüzeyinde görünürler. Çalışma alanı düğümlerini silmek için XSD Tasarımcısı araç çubuğunu, **Çalışma** alanı paneli sağ tıklama menüsünü veya Sil **anahtarını** kullanın.

Düğüm ekleme hakkında bilgi için XML şema tasarımcısı çalışma alanında "Çalışma Alanına Düğüm Ekleme" [bölümüne bakın.](../xml-tools/xml-schema-designer-workspace.md)

## <a name="design-surface"></a>Tasarım yüzeyi

Çalışma Alanı panelinde bir **düğüm** seçildiğinde, düğümün ayrıntılarını görüntüleyebilirsiniz İçerik Modeli Görünümü tasarım yüzeyine eklenir.

Bir düğümün içerik modeli, öğelerin ve özniteliklerin ağaç düğümleri olarak görünmesiyle birlikte genişletilebilir bir grafik ağacı ile temsil edildi. Varsayılan olarak, yalnızca bir düzey genişletilir. Compositors, tür adları, gruplar ve diğer kapsayıcılar gibi diğer bilgiler, içine alınan öğeler ve öznitelikler boyunca dikey bir çıtaya (genişletilirken) yerleştirilir. Dikey bir çıta çift tıklarken çubuk yatay hale gelir ve ağaç daraltılmış olur. Bir yatay çıta çift tıklarken dikey hale gelir ve ağaç genişler. Dikey çubuğun seçimi kapsayıcının tüm düğümlerini seçer. Bir öğe genişletilebilir veya daraltılmışsa, genişleticiler bir düğümün sağ üzerinde görünür.

Tasarım yüzeyi boşsa XML düzenleyicisi, **XML** Şema Gezgini ve filigran gösterilir. Filigran, *tüm* XSD Tasarımcısı görünümlerinin bağlantılarının listesidir. Şema kümesinde hatalar varsa, listenin sonunda şu metin görüntülenir: "Kümede hataları görüntülemek ve düzeltmek için Hata Listesini kullanın."

## <a name="breadcrumb-bar"></a>Breadcrumb çubuğu

İçerik Modeli Görünümü'nin altındaki içerikcrumb çubuğu, seçilen düğümün şema kümesinde nerede olduğunu gösterir.

## <a name="context-menus"></a>Bağlam menüleri

Tasarım yüzeyinde veya Çalışma Alanı panelinde bir öğeye **sağ tıklarken** bir bağlam menüsü görüntülenir. Aşağıdaki tabloda İçerik Modeli Görünümü tasarım yüzeyi için kullanılabilen seçenekler açık almaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**XML Şema Gezgini'nde göster**|Odağı Şema Gezgini'ne koyar ve şema kümesi düğümünü vurgular.|
|**Görünümde Graph Göster**|Graph Görünümüne geçişler.|
|**Örnek XML Oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası üretir.|
|**Belgeleri Göster**|Ek Açıklama/Belge düğümü içeriğini gösterir veya gizler.|
|**Diyagramı Görüntü Olarak Dışarı Aktarma**|Tasarım yüzeyini bir XPS dosyasına kaydeder.|
|**Kodu Görüntüle**|Seçilen düğümü içeren dosyayı XML düzenleyicisinde açar. XML Şema Gezgini'nde **seçilen öğe** XML düzenleyicisinde de seçilir.|
|**Özellikler Penceresi**|Özellikler **penceresini** açar (henüz açık değilse). Bu pencerede düğümle ilgili bilgiler görüntülenir.|

Aşağıdaki tabloda Çalışma Alanı paneli için kullanılabilen seçenekler **açık** almaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**XML Şema Gezgini'nde göster**|Odağı Şema Gezgini'ne koyar ve şema kümesi düğümünü vurgular.|
|**Görünümde Graph Göster**|Graph Görünümüne geçişler.|
|**Çalışma Alanını Temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma Alanı'dan kaldırma**|Seçilen düğümleri çalışma alanında ve tasarım yüzeyinden kaldırır.|
|**Çalışma Alanı'dan seçim dışında tüm seçenekleri kaldırma**|Çalışma alanı ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Örnek XML Oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası üretir.|
|**Hepsini Seç**|Çalışma Alanı panelindeki tüm **düğümleri** seçer.|
|**Kodu Görüntüle**|Seçilen düğümü içeren dosyayı XML düzenleyicisinde açar. XML Şema Gezgini'nde **seçilen öğe** XML düzenleyicisinde de seçilir.|
|**Özellikler Penceresi**|Özellikler **penceresini** açar (henüz açık değilse). Bu pencerede düğümle ilgili bilgiler görüntülenir.|

## <a name="properties-window"></a>Özellik penceresi

Özellikler penceresini ilk kez açmak için sağ tıklama (bağlam) **menüsünü** kullanın. Varsayılan olarak, **Özellikler** penceresi uygulamanın sağ alt köşesinde Visual Studio. İçerik Modeli Görünümünde işlenen bir düğüme tıklarken, bu düğümün özellikleri Özellikler Penceresinde **görüntülenir.**

## <a name="xsd-designer-toolbar"></a>XSD tasarımcısı araç çubuğu

İçerik Modeli Görünümü etkin olduğunda aşağıdaki XSD Tasarımcısı Araç Çubuğu düğmeleri etkinleştirilir.

![XML Şema Tasarımcısı Araç Çubuğu](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç Görünümünü Göster**|Başlangıç [Görünümü'ne geçişler.](../xml-tools/start-view.md) Bu görünüme, Ctrl 1 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**İçerik Modeli Görünümünü Göster**|İçerik Modeli [Görünümüne geçişler.](../xml-tools/content-model-view.md) Bu görünüme, Ctrl 2 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**Görünüm Graph Göster**|görünüme [Graph.](../xml-tools/graph-view.md) Bu görünüme, Ctrl 3 klavye **kısayolu** + **kullanılarak erişilebilir.**|
|**Çalışma Alanını Temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma Alanı'dan kaldırma**|Seçilen düğümleri çalışma alanında ve tasarım yüzeyinden kaldırır.|
|**Çalışma Alanı'dan seçim dışında tüm seçenekleri kaldırma**|Çalışma alanı ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Belgeleri Göster**|Ek açıklama/belge düğümü içeriğini gösterir veya gizler.|

## <a name="panscroll"></a>Kaydır/KAYDIR

Tasarım yüzeyini, kaydırma çubuklarını kullanarak ya da tıklamakta ve fareyle sürüklerken **CTRL** tuşunu basılı tutarak kaydırabilirsiniz. Tasarım yüzeyini tıklama ve sürükleme kullanarak kaydırdığınızda, imleç dört yönü işaret eden dört çapraz oka dönüşür.

## <a name="undoredo"></a>Geri Al/Yinele

Geri Al/Yinele özelliği, aşağıdaki eylemler için Içerik modeli görünümünde etkinleştirilir:

- Sürükleyip bırakarak tek bir düğüm ekleme.

- Şema Gezgini 'nde arama sonuçları penceresinden birden çok düğüm ekleme.

- Başlangıç görünümünden düğüm ekleme.

- Tek veya birden çok düğüm siliniyor.

## <a name="zoom"></a>Zoom

Yakınlaştırma, Içerik modeli görünümünün sağ alt köşesinde bulunur.

Yakınlaştırma, aşağıdaki yollarla denetlenebilir:

- **CTRL** tuşunu basılı tutarak fare tekerleği, Içerik modeli görünüm yüzeyi üzerine getirildiğinde fare tekerleğini döndürürken.

- Kaydırıcı denetimini kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Yakınlaştırma kaydırıcısı, seçtiğinizde yakınlaştırılır, üzerine gelin veya yakınlaştırmak için fare tekerleği ile **CTRL** tuşlarını kullanın; Tüm diğer zamanlarda saydamdır.

## <a name="xml-editor-integration"></a>XML düzenleyici tümleştirmesi

Sağ tıklama (bağlam) menüsünü kullanarak **XSD Tasarımcısı** ile XML Düzenleyicisi arasında geri ve ileri geçiş yapabilirsiniz.

XML düzenleyicisinde şema kümesinde değişiklik yaparsanız, değişiklikler Içerik modeli görünümünde eşitlenir. Daha fazla bilgi için bkz. [XML Düzenleyicisi Ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML şema Tasarımcısı çalışma alanı](../xml-tools/xml-schema-designer-workspace.md)
