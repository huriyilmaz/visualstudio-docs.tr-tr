---
title: XML şema Tasarımcısı Içerik modeli görünümü
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67453571963ae22910842be0021e008632942de5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661536"
---
# <a name="content-model-view"></a>İçerik Modeli Görünümü

Içerik modeli görünümü, basit ve karmaşık türler, öğeler, model grupları, öznitelikler ve öznitelik grupları dahil olmak üzere yerel ve genel şema düğümlerinin ve bileşenlerinin grafik gösterimini sağlar. XML açıklamaları ve işleme yönergeleri Içerik modeli görünümünde görüntülenemez. Içerik modeli görünümü iki panel içerir: [XML şema Tasarımcısı çalışma alanındaki](../xml-tools/xml-schema-designer-workspace.md)düğümlerin listesini Içeren bir **çalışma alanı** bölmesi ve **çalışma alanında seçili şema düğümlerinin içerik modelini görebileceğiniz tasarım yüzeyi** paneli. Içerik modeli görünümü ayrıca XML şema Tasarımcısı araç çubuğunu ve içerik haritası çubuğunu da içerir.

Aşağıdaki görüntüde, **çalışma alanı** panelinde altı şema düğümü bulunur. @No__t_0 düğümü, **çalışma alanı** panelinde seçilir ve tasarım yüzeyinde görüntülenir.

![XML şema Tasarımcısı Içerik modeli görünümü](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Çalışma alanı bölmesi

Çalışma alanına düğümler ekledikten sonra düğümlerin listesi, Içerik modeli görünümündeki **çalışma alanı** panelinde görüntülenir. **Çalışma alanı** panelinde düğümleri seçtiğinizde, Içerik modeli görünümü tasarım yüzeyinde görünürler. Çalışma alanından düğümleri silmek için, XSD Tasarımcı araç çubuğunu, **çalışma alanı** panelini sağ tıklama menüsünü veya **Delete** tuşunu kullanın.

Düğüm ekleme hakkında daha fazla bilgi için, [XML şema Tasarımcısı çalışma](../xml-tools/xml-schema-designer-workspace.md)alanındaki "çalışma alanına düğüm ekleme" bölümüne bakın.

## <a name="design-surface"></a>Tasarım yüzeyi

**Çalışma alanı** panelinde bir düğüm seçildiğinde, düğüm ayrıntılarını görüntüleyebileceğiniz Içerik modeli görünümü tasarım yüzeyine eklenir.

Bir düğümün içerik modeli, ağaç düğümleri olarak görünen öğeleri ve öznitelikleri olan bir Genişletilebilir grafik ağacı tarafından temsil edilir. Varsayılan olarak, yalnızca bir düzey genişletilir. Kompozisyon, tür adları, gruplar ve diğer kapsayıcılar gibi diğer bilgiler, içerdikleri öğeler ve öznitelikler üzerinde dikey bir çubuğa (genişletildiklerinde) yerleştirilir. Dikey bir çubuğa çift tıkladığınızda, yatay olur ve ağaç daraltılır. Yatay çubuğa çift tıkladığınızda, dikey olur ve ağaç genişletilir. Dikey çubuğun seçilmesi kapsayıcıdaki tüm düğümleri seçer. Bir öğe genişletilirse veya daraltılabilse, bir düğümün sağında genişleticiler görüntülenir.

Tasarım yüzeyi boşsa, XML Düzenleyicisi, **XML şema Gezgini**ve filigran gösterilir. *Filigran* , tüm XSD tasarımcı görünümlerinin bağlantılarının listesidir. Şema kümesinde hatalar varsa, listenin sonunda aşağıdaki metin görüntülenir: "küme içindeki hataları görüntülemek ve onarmak için Hata Listesi kullanın."

## <a name="breadcrumb-bar"></a>İçerik haritası çubuğu

Içerik modeli görünümü altındaki Içerik Haritası çubuğu, seçili düğümün şema kümesinde bulunduğu yeri gösterir.

## <a name="context-menus"></a>Bağlam menüleri

Tasarım yüzeyi veya **çalışma alanı** panelinde bir öğeye sağ tıkladığınızda bir bağlam menüsü görüntülenir. Aşağıdaki tabloda, Içerik modeli görünümü tasarım yüzeyi için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**XML şema Gezgini 'nde göster**|Şema Gezginine odaklankoyar ve şema kümesi düğümünü vurgular.|
|**Grafik görünümünde göster**|Grafik görünümüne geçer.|
|**Örnek XML oluştur**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası oluşturur.|
|**Belgeleri göster**|Ek açıklama/belge düğümü içeriğini gösterir veya gizler.|
|**Diyagramı görüntü olarak dışarı aktar**|Tasarım yüzeyini bir XPS dosyasına kaydeder.|
|**Kodu görüntüle**|XML düzenleyicisinde Seçili düğümü içeren dosyayı açar. XML **şeması Gezgini** 'nde seçilen öğe, XML düzenleyicisinde de seçilidir.|
|**Özellik Penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

Aşağıdaki tabloda, **çalışma alanı** paneli için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**XML şema Gezgini 'nde göster**|Şema Gezginine odaklankoyar ve şema kümesi düğümünü vurgular.|
|**Grafik görünümünde göster**|Grafik görünümüne geçer.|
|**Çalışma alanını temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma alanından Kaldır**|Seçili düğümleri çalışma alanından ve tasarım yüzeyinden kaldırır.|
|**Seçimi çalışma alanından Tümünü Kaldır**|Çalışma alanından ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Örnek XML oluştur**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası oluşturur.|
|**Tümünü Seç**|**Çalışma alanı** panelinde tüm düğümleri seçer.|
|**Kodu görüntüle**|XML düzenleyicisinde Seçili düğümü içeren dosyayı açar. XML **şeması Gezgini** 'nde seçilen öğe, XML düzenleyicisinde de seçilidir.|
|**Özellik Penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

## <a name="properties-window"></a>Özellik penceresi

Sağ tıklama (bağlam) menüsünü kullanarak ilk olarak **Özellikler** penceresini açın. Varsayılan olarak, **Özellikler** penceresi Visual Studio 'nun sağ alt köşesinde görüntülenir. Içerik modeli görünümünde işlenen bir düğüme tıkladığınızda, bu düğümün özellikleri **Özellikler** penceresinde görüntülenir.

## <a name="xsd-designer-toolbar"></a>XSD Tasarımcı araç çubuğu

Içerik modeli görünümü etkinken aşağıdaki XSD Tasarımcı araç çubuğu düğmeleri etkinleştirilir.

![XML şema Tasarımcısı araç çubuğu](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç görünümünü göster**|[Başlangıç görünümüne](../xml-tools/start-view.md)geçer. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **Ctrl** +**1**.|
|**Içerik modeli görünümünü göster**|[Içerik modeli görünümüne](../xml-tools/content-model-view.md)geçiş yapar. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **Ctrl** +**2**.|
|**Graf görünümünü göster**|[Grafik görünümüne](../xml-tools/graph-view.md)geçer. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **Ctrl** +**3**.|
|**Çalışma alanını temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma alanından Kaldır**|Seçili düğümleri çalışma alanından ve tasarım yüzeyinden kaldırır.|
|**Seçimi çalışma alanından Tümünü Kaldır**|Çalışma alanından ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Belgeleri göster**|Ek açıklama/belge düğümü içeriğini gösterir veya gizler.|

## <a name="panscroll"></a>Kaydır/KAYDIR

Tasarım yüzeyini, kaydırma çubuklarını kullanarak ya da tıklamakta ve fareyle sürüklerken **CTRL** tuşunu basılı tutarak kaydırabilirsiniz. Tasarım yüzeyini tıklama ve sürükleme kullanarak kaydırdığınızda, imleç dört yönü işaret eden dört çapraz oka dönüşür.

## <a name="undoredo"></a>Geri Al/Yinele

Geri Al/Yinele özelliği, aşağıdaki eylemler için Içerik modeli görünümünde etkinleştirilir:

- Sürükleyip bırakarak tek bir düğüm ekleme.

- Şema Gezgini 'nde arama sonuçları penceresinden birden çok düğüm ekleme.

- Başlangıç görünümünden düğüm ekleme.

- Tek veya birden çok düğüm siliniyor.

## <a name="zoom"></a>Yakınlaştır

Yakınlaştırma, Içerik modeli görünümünün sağ alt köşesinde bulunur.

Yakınlaştırma, aşağıdaki yollarla denetlenebilir:

- **CTRL** tuşunu basılı tutarak fare tekerleği, Içerik modeli görünüm yüzeyi üzerine getirildiğinde fare tekerleğini döndürürken.

- Kaydırıcı denetimini kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Yakınlaştırma kaydırıcısı, seçtiğinizde yakınlaştırılır, üzerine gelin veya yakınlaştırmak için fare tekerleği ile **CTRL** tuşlarını kullanın; Tüm diğer zamanlarda saydamdır.

## <a name="xml-editor-integration"></a>XML düzenleyici tümleştirmesi

Sağ tıklama (bağlam) menüsünü kullanarak **XSD Tasarımcısı** ile XML Düzenleyicisi arasında geri ve ileri geçiş yapabilirsiniz.

XML düzenleyicisinde şema kümesinde değişiklik yaparsanız, değişiklikler Içerik modeli görünümünde eşitlenir. Daha fazla bilgi için bkz. [XML Düzenleyicisi Ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Tasarımcısı Çalışma Alanı](../xml-tools/xml-schema-designer-workspace.md)