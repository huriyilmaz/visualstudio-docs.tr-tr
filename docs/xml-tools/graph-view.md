---
title: XML şema Tasarımcısı grafik görünümü
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b19f8f64bc4fe63d111f4d5c61e96d6fff88a14b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646046"
---
# <a name="graph-view"></a>Grafik görünümü

Grafik görünümü, genel şema düğümlerinin ve düğümler arasındaki ilişkilerin grafik gösterimini sağlar. Grafik görünümünün, Tasarım yüzeyinde şema kümesinin düzenini değiştirdiğine izin vermez. Grafik görünümü ayrıca XML şema Tasarımcısı araç çubuğunu ve içerik haritası çubuğunu da içerir.

Aşağıdaki görüntüde, Tasarım yüzeyinde altı genel düğüm ile grafik görünümü gösterilmektedir.

![XML şema Tasarımcısı grafik görünümü](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Tasarım yüzeyi

Grafik görünümünün tasarım yüzeyi, [XML şema Tasarımcısı çalışma alanının](../xml-tools/xml-schema-designer-workspace.md)içeriğini görüntüler. Çalışma alanı, şema kümesinden herhangi bir genel düğüm içeriyorsa, düğümler grafik görünümü tasarım yüzeyinde gösterilir ve bir ilişki olan düğümler arasında oklar çizilir.

Grafik görünümünde bir düğüme çift tıkladığınızda XML Düzenleyicisi görüntülenir.

Seçili düğümleri çalışma alanından silmek için, XSD Tasarımcı araç çubuğunu veya **Delete** tuşunu kullanın.

Tasarım yüzeyi boşsa, XML Düzenleyicisi, **XML şema Gezgini**ve filigran gösterilir. *Filigran* , tüm XSD tasarımcı görünümlerinin bağlantılarının listesidir.

![XSD Tasarımcısı; Grafik görünümü](../xml-tools/media/xsdgraphviewwatermark.gif)

Şema kümesinde hatalar varsa, listenin sonunda aşağıdaki metin görüntülenir: "küme içindeki hataları görüntülemek ve onarmak için Hata Listesi kullanın."

## <a name="breadcrumb-bar"></a>İçerik haritası çubuğu

Grafik görünümünün alt kısmındaki içerik haritası çubuğu, seçili düğümün şema kümesinde bulunduğu yeri gösterir. Birden çok öğe seçilirse, içerik haritası çubuğu boş olur.

## <a name="context-right-click-menu"></a>Bağlam (sağ tıklama) menüsü

Aşağıdaki tabloda, grafik görünümü tasarım yüzeyindeki tüm düğümler için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**XML şema Gezgini 'nde göster**|Şema Gezginine odaklankoyar ve şema kümesi düğümünü vurgular.|
|**Grafik görünümünde göster**|Grafik görünümüne geçiş yapar (gri).|
|**Örnek XML oluştur**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası oluşturur.|
|**Çalışma alanını temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma alanından Kaldır**|Seçili düğümleri çalışma alanından ve tasarım yüzeyinden kaldırır.|
|**Seçimi çalışma alanından Tümünü Kaldır**|Çalışma alanından ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır.|
|**Diyagramı görüntü olarak dışarı aktar**|Tasarım yüzeyini bir XPS dosyasına kaydeder.|
|**Tümünü Seç**|Tasarım yüzeyinde tüm düğümleri seçer.|
|**Kodu görüntüle**|XML düzenleyicisinde Seçili düğümü içeren dosyayı açar. XML **şeması Gezgini** 'nde seçilen öğe, XML düzenleyicisinde de seçilidir.|
|**Özellik Penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

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

İlk olarak **Özellikler** penceresini açmak için bağlam (sağ tıklama) menüsünü kullanın. Varsayılan olarak, **Özellikler** penceresi Visual Studio 'nun sağ alt köşesinde görüntülenir. Içerik modeli görünümünde işlenen bir düğüme tıkladığınızda, bu düğümün özellikleri **Özellikler** penceresinde görüntülenir.

## <a name="xsd-toolbar"></a>XSD araç çubuğu

Grafik görünümü etkinken aşağıdaki XSD araç çubuğu düğmeleri etkinleştirilir.

![XML şema Tasarımcısı araç çubuğu](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç görünümünü göster**|[Başlangıç görünümüne](../xml-tools/start-view.md)geçer. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **Ctrl** +**1**.|
|**Içerik modeli görünümünü göster**|[Içerik modeli görünümüne](../xml-tools/content-model-view.md)geçiş yapar. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **Ctrl** +**2**.|
|**Graf görünümünü göster**|[Grafik görünümüne](../xml-tools/graph-view.md)geçer. Bu görünüme klavye kısayolu kullanılarak erişilebilir: **Ctrl** +**3**.|
|**Çalışma alanını temizle**|Çalışma alanını ve tasarım yüzeyini temizler.|
|**Çalışma alanından Kaldır**|Seçili düğümleri çalışma alanından ve tasarım yüzeyinden kaldırır.|
|**Seçimi çalışma alanından Tümünü Kaldır**|Çalışma alanından ve tasarım yüzeyinden seçilmemiş düğümleri kaldırır. Bu seçenek, Içerik modeli görünümünde ve grafik görünümünde etkinleştirilir.|
|**Soldan sağa**|Grafik görünümündeki düzeni düğümlerin soldan sağa hiyerarşik gösterimine dönüştürür. Bu seçeneğe, klavye kısayolu: **Alt** +**sağ ok**kullanılarak erişilebilir.|
|**Sağdan sola**|Grafik görünümündeki düzeni düğümlerin sağdan sola hiyerarşik gösterimine dönüştürür. Bu seçeneğe klavye kısayolu kullanılarak erişilebilir: **Alt** +**sol ok**.|
|**Yukarıdan aşağıya**|Grafik görünümündeki düzeni düğümlerin üst-alt hiyerarşik gösterimine dönüştürür. Bu seçeneğe klavye kısayolu kullanılarak erişilebilir: **alt** +**aşağı ok**.|
|**Aşağıdan yukarıya**|Grafik görünümündeki düzeni düğümlerin aşağıdan yukarıya hiyerarşik gösterimine dönüştürür. Bu seçeneğe, klavye kısayolu: **Alt** +**yukarı ok**kullanılarak erişilebilir.|

## <a name="panscroll"></a>Kaydır/KAYDIR

Tasarım yüzeyini, kaydırma çubuklarını kullanarak ya da tıklamakta ve fareyle sürüklerken **CTRL** tuşunu basılı tutarak kaydırabilirsiniz. Tasarım yüzeyini tıklama ve sürükleme kullanarak kaydırdığınızda, imleç dört yönü işaret eden dört çapraz geçiş olacak şekilde değişir.

## <a name="undoredo"></a>Geri Al/Yinele

Geri Al/Yinele özelliği, aşağıdaki eylemler için grafik görünümünde etkinleştirilir:

- Sürükleyip bırakarak tek bir düğüm ekleme.

- Şema Gezgini 'nde arama sonuçları penceresinden birden çok düğüm ekleme veya görünüm sorguları başlatma.

- Tek veya birden çok düğüm siliniyor.

## <a name="zoom"></a>Yakınlaştır

Yakınlaştırma, grafik görünümünün sağ alt köşesinde bulunur.

Yakınlaştırma, aşağıdaki yollarla denetlenebilir:

- **CTRL** tuşunu basılı tutarak ve fare, grafik görünümü yüzeyinin üzerine getirildiğinde fare tekerleğini döndürürken.

- Kaydırıcı denetimini kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Yakınlaştırma kaydırıcısı, seçtiğinizde yakınlaştırılır, üzerine gelin veya yakınlaştırmak için fare tekerleği ile **CTRL** tuşlarını kullanın; Tüm diğer zamanlarda saydamdır.

## <a name="xml-editor-integration"></a>XML düzenleyici tümleştirmesi

Bir düğüme tıklayarak ve kod bağlamını görüntüle (sağ tıklama) menüsünü kullanarak grafik görünümü ile XML Düzenleyicisi arasında geri ve ileri geçiş yapabilirsiniz.

XML düzenleyicisinde şema kümesinde değişiklik yaparsanız, değişiklikler grafik görünümünde eşitlenir. Daha fazla bilgi için bkz. [XML Düzenleyicisi Ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Yüzeyi](../xml-tools/xml-schema-designer-workspace.md)