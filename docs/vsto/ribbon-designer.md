---
title: Şerit Tasarımcısı
description: bir Microsoft Office uygulamasının şeritlerine özel sekmeler, gruplar ve denetimler eklemek için şerit tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 16546308d19cd32ac7c701b733caec3bbf8cdff4a36dcc3424706d0d6bd98f2e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121243516"
---
# <a name="ribbon-designer"></a>Şerit Tasarımcısı
  Şerit Tasarımcısı görsel tasarım tuvaldir. bir Microsoft Office uygulamasının şeritlerine özel sekmeler, gruplar ve denetimler eklemek için şerit tasarımcısını kullanın.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Şerit tasarımcısını açmak için projenize bir **Şerit (görsel Tasarımcı)** öğesi ekleyin. Daha sonra aşağıdaki görevler için tasarım araçları 'nı kullanabilirsiniz:

- [Şerit düzeni tasarlama](#DesigningRibbonLayout)

- [Olayları işleme ve denetim özelliklerini ayarlama](#HandleEventsSetProperties)

- [Backstage görünümüne denetimler ekleme](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> Şerit Tasarımcısını kullanarak gerçekleştiremezsiniz bazı görevler vardır. Bu görevler ve bunları nasıl gerçekleştirebileceğiniz hakkında daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Bir projeye Şerit (görsel Tasarımcı) öğesi ekleme
 Şerit Tasarımcısını kullanmak için projenize yeni bir **Şerit (görsel Tasarımcı)** öğesi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).

 yeni bir **şerit (görsel tasarımcı)** öğesi eklediğinizde Visual Studio, projenize otomatik olarak aşağıdaki dosyaları ekler:

- Şerit kod dosyası. Bu dosya, **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesi için belirttiğiniz ada sahiptir. Şerit olaylarını işlemek için bu dosyaya kod ekleyin.

- Şerit Tasarımcısı kod dosyası. Bu dosya, Şerit Tasarımcısı tarafından oluşturulan kodu içerir ve doğrudan düzenlenmemelidir.

- Bir kaynak dosyası. Bu dosya Şeritteki her bir denetimin özellik değerlerini içerir.

  Başka bir projeden **Şerit (görsel Tasarımcı)** öğesi zaten varsa, **Varolan öğe Ekle** iletişim kutusunu kullanarak mevcut projenizde onu yeniden kullanabilirsiniz.

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> Şerit tasarlama
 Şerit tasarımcısını açmak için üç yol vardır:

- **Çözüm Gezgini**, Şerit kod dosyasına çift tıklayın.

- **Çözüm Gezgini**, Şerit kod dosyasına sağ tıklayın ve ardından **tasarımcıyı görüntüle**' ye tıklayın.

- **Çözüm Gezgini**, Şerit kod dosyasını seçin ve ardından **Görünüm** menüsünde **Tasarımcı** ' ya tıklayın.

  Şerit Tasarımcısı varsayılan bir sekme ve grup içerir. Varsayılan sekmeyi ve grubunu Şerit Tasarımcısından kaldırabilirsiniz. Varsayılan grubu kaldırmak için **Group1** öğesine sağ tıklayın ve ardından **Sil**' e tıklayın. Varsayılan sekmeyi kaldırmak için tasarım yüzeyinde boş bir alana sağ tıklayın ve ardından **Şerit sekmesini kaldır**' a tıklayın.

  Ayrıca Şerit Tasarımcısına özel sekmeler, gruplar ve denetimler ekleyebilirsiniz. bu denetimleri **araç kutusunda** **Office şerit denetimleri** grubunda bulabilirsiniz. **Office şerit denetimleri** grubundan şerit tasarımcısına denetim eklemenin üç yolu vardır:

- Bir denetimi Şerit Tasarımcısında uygun bir alana sürükleyin.

- Bir denetime tıklayın ve ardından Şerit Tasarımcısında uygun bir alana tıklayın.

- Tasarımcıda uygun bir alanı seçin ve ardından **araç kutusunda** bir denetime çift tıklayın.

### <a name="ribbon-design-workflow"></a>Şerit tasarım iş akışı
 Şerit yerleşimini tasarlamak için aşağıdaki temel adımları izleyin:

1. [Şerite özel bir sekme ekleyin](#AddTabToRibbon).

2. [Sekmeye gruplar ekleyin](#AddGroupsToTab).

3. [Gruplara denetimler ekleyin](#AddControlsToGroups).

   Denetimler yalnızca gruplara bırakılabilir; bir denetimi doğrudan bir sekmeye veya Şerite sürükleyemezsiniz. Gruplar yalnızca sekmelerde bırakılabilir; bir grubu doğrudan bir şeride sürükleyemezsiniz.

   Denetimleri doğru konumlara sürükleyerek düzenleyin. **Özellikler** penceresini kullanarak bir denetimin özelliklerini ayarlayabilirsiniz.

   Şerit üzerinde denetimleri bir sekmeden diğerine sürükleyemezsiniz. Bir denetimi başka bir sekmeye taşımak istiyorsanız, denetimi bir sekmeden kaldırmak için **Kes** komutunu kullanmanız ve sonra denetimi başka bir sekmeye yapıştırmanız gerekir. Denetimi keser ve yapıştırırsanız, olay işleyicisi çalışmayı durduruyor. Olay işleyicisini **Özellikler** penceresinde yeniden bağlayabilirsiniz. Daha fazla bilgi için bkz. [Özellikler penceresi](../ide/reference/properties-window.md).

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> Şerite özel sekmeler ekleme
 Şerite özel sekme eklemenin üç yolu vardır:

- **Araç kutusundan** bir sekme ekleyin.

- Şerit Tasarımcısına sağ tıklayın ve ardından **Şerit sekmesi Ekle**' ye tıklayın.

- **Sekme koleksiyonu düzenleyicisini** açın ve **Ekle**' ye tıklayın.

   **sekme koleksiyonu düzenleyicisini** açmak için, **özellikler** penceresinde, **sekmeler** özelliğini seçin ve ardından ![mobil tasarımcı elips ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil tasarımcı elips")üç nokta düğmesine tıklayın.

  Bir sekme ekledikten sonra, denetimleri içeren gruplar ekleyebilirsiniz.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Şeritten özel sekmeleri kaldır
 Şeritten özel bir sekme kaldırmanın üç yolu vardır:

- Tasarımcı öğesine sağ tıklayın ve ardından **Şerit sekmesini kaldır**' a tıklayın.

- **Özellikler** penceresinin **Komutlar** bölmesinde, **Şerit sekmesini kaldır**' ı tıklatın.

- **Sekme koleksiyonu düzenleyicisini** açın, sekmesini seçin ve **Kaldır**' ı tıklatın.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Şeritteki sekmenin konumunu değiştirme
 Şeritteki özel sekmelerin sırasını değiştirebilirsiniz. Şeritteki yerleşik bir sekmeden önce veya sonra özel sekmeler de yerleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Şeritteki yerleşik sekmeleri özelleştirme
 yerleşik sekme, zaten bir Microsoft Office uygulamasının şeridinde bulunan bir sekmedir. Örneğin, **veri** sekmesi Excel yerleşik bir sekmedir.

 Yerleşik bir sekmeye grup ve denetim ekleyebilirsiniz. Varsayılan olarak, bir özel grup yerleşik bir sekmede son grup olarak görünür, ancak bunu sekmedeki herhangi bir yerleşik gruptan önce veya sonra taşıyabilirsiniz.

 Yerleşik grupları kaldıramazsınız.

 Yerleşik bir sekmeyi özelleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> Bir sekmeye gruplar ekleme
 Gruplar Şeritteki denetimleri mantıksal olarak düzenler. Sekmelere gruplar ekleyin. Diğer tüm denetimleri gruba ekleyin.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> Gruplara denetim ekleme
 Bir gruba bir veya daha fazla denetim ekleyin. Aşağıdaki tabloda her bir denetim açıklanmaktadır.

|Denetim|Açıklama|
|-------------|-----------------|
|**Box**|Bir gruptaki denetimleri düzenleyen bir kapsayıcı. Ayırıcı, Grup veya sekme dışında bir kutuya herhangi bir denetim ekleyebilirsiniz. Bir kutu yatay veya dikey olabilir.|
|**Düğme**|Bir eylemi başlatan düğme. Bir gruba, düğme grubuna, açılan listeye, galeriye, menüye veya bölünmüş düğmeye düğme ekleyebilirsiniz.|
|**ButtonGroup**|Bir veya daha fazla düğme, iki durumlu düğme, menü, bölünmüş düğme ve galerinin bulunduğu bir grup. Bir grup veya menüye düğme grubu ekleyebilirsiniz.|
|**CheckBox**|Bir seçeneği açmak veya kapatmak için seçilen veya temizlenmiş bir kutu.|
|**ComboBox**|Liste kutusu eklenmiş bir düzenleme kutusu. Kullanıcılar kendi tercih edebilir veya seçebilir. Kutu geçerli seçimi görüntüler. <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A>şerit Office uygulamasına yüklenmeden önce veya sonra çalışma zamanında öğe eklemek ve kaldırmak için özelliğini kullanın.|
|**Listenin**|Kullanıcının seçebileceğiniz öğelerin listesi. Kullanıcı açılan listede yeni bir öğe yazamaz.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A>Listeye öğe eklemek için özelliğini kullanın. Çalışma zamanında öğeleri ekleyebilir ve kaldırabilirsiniz.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A>Listeye düğme eklemek için özelliğini kullanın. ancak, şerit Office uygulamasına yüklendikten sonra çalışma zamanında düğme ekleyemez ve kaldıramazsınız.|
|**EditBox**|Kullanıcının metin yazbileceği bir kutu.|
|**Galeri**|Kullanıcıların seçebileceğiniz görsel seçimlerden oluşan bir dizi veya kılavuz sunan bir menü. Menüdeki seçimlerin yerleşimini kontrol edebilirsiniz. <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> Galerinin öğe ve düğmelerini görüntüleyecek olan satır ve sütun sayısını belirtmek için ve özelliklerini kullanın.|
|**Etiketle**|Şeritteki denetimleri tanımlamak için kullanabileceğiniz metin.|
|**Menü**|Aşağıdaki denetimlerden herhangi birini içerebilen bir açılan liste:<br /><br /> -Düğme<br />-Onay kutusu<br />-Galeri<br />-Menü<br />-Böl düğmesi<br />-İki durumlu düğme<br />-Ayırıcı<br /><br /> Şerit tasarımcısında bir menüye denetim eklemek için menüdeki aşağı oka tıklayarak Menü tasarım yüzeyini kullanıma sunun. Daha sonra şerit denetimlerini **araç kutusundan** menü üzerine sürükleyebilirsiniz. Denetimleri düzenlemek için onları istediğiniz konumlara sürükleyin.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>şerit Office uygulamasına yüklendikten sonra öğesine denetim eklemek için, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> şerit yüklenmeden önce özelliği **true** olarak ayarlamanız gerekir. Bunun nasıl yapılacağı hakkında bilgi için bkz. [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md).|
|**Ayırıcı**|Bir listedeki öğeleri ayırmak için kullanılan ince bir çubuk. Bir gruba eklendiğinde çubuk dikey olur. Bir menüye eklendiğinde çubuk yatay olur.|
|**SplitButton**|İliştirilmiş bir menü içeren düğme. Bölünmüş bir düğme, aşağıdaki denetimlerden herhangi birini içerebilir:<br /><br /> -Düğme<br />-Onay kutusu<br />-Galeri<br />-Menü<br />-Böl düğmesi<br />-İki durumlu düğme<br />-Ayırıcı<br /><br /> Menü gibi, bölünmüş düğmenin kendi tasarım yüzeyi vardır. ancak, bir menünün aksine, yalnızca bir bölünmüş düğmedeki öğeleri, şerit Office uygulamasına yüklenmeden önce güncelleştirebilirsiniz. Bölünmüş düğmedeki öğeleri güncelleştirme hakkında daha fazla bilgi için bkz. [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Basılan veya basılmamış görüntülenen bir düğme.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> Olayları işleme ve özellikleri ayarlama
 Şerit Tasarımcısı, tasarım zamanında **Özellikler** penceresini kullanarak denetim özelliklerini ayarlamanıza olanak sağlar. Ayrıca, şerit, çalışma zamanında Şerit denetimlerinin özelliklerini almak ve ayarlamak için kullanabileceğiniz, türü kesin belirlenmiş bir nesne modeli kullanıma sunar.

 Denetimin varsayılan olayı için bir olay işleyicisi açmak üzere Tasarımcıda herhangi bir denetime çift tıklayabilirsiniz. **Özellikler** penceresini kullanarak diğer tüm denetim olayları için olay işleyicileri oluşturabilirsiniz.

 Şerit olayları ve özellikleri <xref:Microsoft.Office.Tools.Ribbon> ad alanında bulunur. **Şerit (görsel Tasarımcı)** öğesi, projedeki bu derlemeye otomatik olarak bir başvuru ekler ve Şerit kod dosyasının en üstüne uygun **using** veya **Imports** ifadesini ekler.

 Şerit olaylarını işleme ve çalışma zamanında Şerit denetimlerinin özelliklerini ayarlama hakkında daha fazla bilgi için bkz. [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md).

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Backstage görünümünü özelleştirme
 **Dosya** sekmesine tıkladığınızda açılan menüye denetim eklemek Için şerit tasarımcısını kullanabilirsiniz. Bu menü, Backstage görünümü olarak adlandırılır.

 Şerit Tasarımcısını kullanarak, yerleşik denetimlerden önce veya sonra Denetim konumlandırabilirsiniz. Yerleşik denetim, Backstage görünümünde zaten görüntülenen bir denetimdir. Denetimleri yerleşik denetimlerden önce veya sonra konumlandırmak istiyorsanız Şerit XML 'i kullanmanız gerekir. **Şerit (XML)** hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md). Backstage görünümünü özelleştirme hakkında daha fazla bilgi için bkz. [geliştiriciler için Office 2010 backstage görünümüne giriş](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) ve [geliştiriciler için Office 2010 backstage görünümünü özelleştirme](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Backstage görünümüne denetimler ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> Şerit tasarımcısında erişilebilirlik
 Şerit tasarımcısında denetimleri taşımak için klavye kısayollarını kullanabilirsiniz. Bazı klavye kısayolları tüm denetimler için geçerlidir ve bazıları yalnızca menülere sahip denetimler için geçerlidir.

 Tüm denetimler için uygulanan klavye kısayolları aşağıdaki tabloda gösterilmiştir.

|Eylem|Klavye kısayolu|
|------------|-----------------------|
|Listedeki bir denetimi önceki denetimden önce taşıyın.|**CTRL** + **Yukarı**<br /><br /> **CTRL** + **Sol**|
|Bir denetimi listedeki bir sonraki denetimden sonra taşıyın.|**CTRL** + **Aşağı**<br /><br /> **CTRL** + **Sağ**|
|Seçimi aynı gruptaki bir denetimden diğerine taşıyın. Açılır panel için, açılan paneldeki üst denetim ve denetimler arasında geçiş yapın.|**Yukarı**<br /><br /> **Aşağı**|
|Tüm denetimlerde ileri doğru yineleyin.|**Sekme**|
|Tüm denetimler boyunca ters yönde yineleme yapın.|**SHIFT** + **Sekme**|
|Seçili denetimi veya denetim kümesini silin.|**Silme**|
|Seçili denetimleri kopyalayın.|**CTRL** + **C**|
|Seçili denetimleri kesin.|**CTRL** + **X**|
|Denetimleri panodan yapıştırın.|**CTRL** + **V**|
|**Araç kutusunu** seçin.|**CTRL** + **Alt** + **X**|
|Ana bileşeni seçin.|**Esc**|

 yalnızca Microsoft Office menüsüne uygulanan klavye kısayolları <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> aşağıdaki tabloda gösterilmiştir.

|Eylem|Klavye kısayolu|
|------------|-----------------------|
|Açılır panel açıksa ve açılır panelde bir denetim seçili ise üst denetimi seçin.|**Tarafta**|
|Açılır panel açık ise ve üst denetim seçiliyse açılan paneli kapatın.|**Tarafta**|
|Açılır paneli açın.|**Right**|
|Açılır panel açıksa, açılan panelde ilk denetimi seçin.|**Right**|
|Açılan paneli kapatın.|**Esc**|

## <a name="see-also"></a>Ayrıca bkz.

- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Nasıl yapılır: Şerit Tasarımcısından Şerit XML 'ine şerit aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
