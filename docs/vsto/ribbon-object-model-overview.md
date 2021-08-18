---
title: Şerit nesne modeline genel bakış
description: Çalışma zamanı Office için Visual Studio Araçları çalışma zamanında Şerit denetimlerinin özelliklerini almak ve ayarlamak için kullanabileceğiniz türü kesin olarak ayarlanmış bir nesne modelini nasıl ortaya çıkar olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f7d840db368f61c0e85b5b21d7ff1c0a32b4a472
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032218"
---
# <a name="ribbon-object-model-overview"></a>Şerit nesne modeline genel bakış
  , çalışma zamanında Şerit denetimlerinin özelliklerini almak ve ayarlamak için kullanabileceğiniz türü kesin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] olarak ayarlanmış bir nesne modelini gösterir. Örneğin, menü denetimlerini dinamik olarak doldurmak veya denetimleri bağlamsal olarak gösterebilirsiniz ve gizleyebilirsiniz. Ayrıca bir şerite sekmeler, gruplar ve denetimler de eklemenin yanı sıra yalnızca şerit uygulama tarafından yüklenmeden Office ebilirsiniz. Bilgi için [bkz. Salt okunur olan özellikleri ayarlama.](#SettingReadOnlyProperties)

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Bu Şerit nesne modeli temel olarak Şerit sınıfı, [Şerit olayları](#RibbonClass) [ve Şerit](#RibbonEvents)denetim [sınıflarını içerir.](#RibbonControlClasses)

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Şerit sınıfı
 Projeye yeni bir **Şerit (Görsel Tasarımcı)** öğesi eklerken, Visual Studio **bir Şerit** sınıfı ekler. **Şerit sınıfı** sınıfından <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> devralınır.

 Bu sınıf, Şerit kod dosyası ile Şerit Tasarımcısı kod dosyası arasında bölünmüş kısmi bir sınıf olarak görünür.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Şerit olayları
 **Şerit sınıfı** aşağıdaki üç olay içerir:

|Olay|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Uygulama şerit Office yüklenirken ortaya çıkar. Olay <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> işleyicisi Şerit kod dosyasına otomatik olarak eklenir. Şerit yüklenirken özel kod çalıştırmak için bu olay işleyicisini kullanın.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Şerit yüklenirken Şerit özelleştirmesinde görüntüleri önbelleğe alıcaz. Bu olay işleyicisinde Şerit görüntülerini önbelleğe almak için kod yazarsanız küçük bir performans kazancı eldeabilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Şerit örneği kapanıyor.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Şerit denetimleri
 Ad alanı, Araç Kutusunun Şerit Denetimleri grubunda gördüğünüz <xref:Microsoft.Office.Tools.Ribbon> **her Office için** bir **tür içerir.**

 Aşağıdaki tabloda her denetimin türü `Ribbon` gösterir. Her denetimin açıklaması için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

|Denetim adı|Sınıf adı|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Düğme**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Açılır**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**Editbox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galeri**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Grup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Etiketle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menü**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Ayırıcı**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**Splitbutton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Sekme**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Ad alanı, ad alanı denetim sınıflarının adları ile ad çakışması önlemek için bu türler için <xref:Microsoft.Office.Tools.Ribbon> "Şerit" ön eklerini <xref:System.Windows.Forms> kullanır.

 Şerit Tasarımcısı'nda bir denetim eklerken Şerit Tasarımcısı, bu denetimin sınıfını Şerit Tasarımcısı kod dosyasında bir alan olarak belirtir.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Şerit denetimlerinin özelliklerini kullanan ortak görevler
 Her denetim, denetime etiket atama veya denetimleri gizleme ve gösterme gibi çeşitli görevleri gerçekleştirmek `Ribbon` için kullanabileceğiniz özellikler içerir.

 Bazı durumlarda, Şerit yüklenirken veya bir denetim dinamik menüye eklendikten sonra özellikler salt okunur olur. Daha fazla bilgi için [bkz. Salt okunur olan özellikleri ayarlama.](#SettingReadOnlyProperties)

 Aşağıdaki tabloda denetim özelliklerini kullanarak gerçekleştirebilirsiniz bazı görevler `Ribbon` açık almaktadır.

|Bu görev için:|Bunu yap:|
|--------------------|--------------|
|Denetimi gizleme veya gösterme.|Visible özelliğini kullanın.|
|Denetimi etkinleştirme veya devre dışı bırakma.|Etkin özelliğini kullanın.|
|Denetimin boyutunu ayarlayın.|ControlSize özelliğini kullanın.|
|Denetimde görünen görüntüyü elde etmek.|Image özelliğini kullanın.|
|Denetimin etiketini değiştirme.|Label özelliğini kullanın.|
|Denetime kullanıcı tanımlı veriler ekleyin.|Tag özelliğini kullanın.|
|, , veya <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> içinde <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> öğeleri <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> al<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> Denetim.|Items özelliğini kullanın.|
|, veya <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> denetimine öğe <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> ekleyin.|Items özelliğini kullanın.|
|denetimine denetimler <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> ekleyin.|Items özelliğini kullanın.<br /><br /> Şerit, Office uygulamasına yüklendikten sonra içine denetimler eklemek için Şerit, Office uygulamasına <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> yüklenmeden önce **özelliğini true** Office gerekir. Bilgi için [bkz. Salt okunur olan özellikleri ayarlama.](#SettingReadOnlyProperties)|
|öğesinin seçili öğesini <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> al,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>veya <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|SelectedItem özelliğini kullanın. için <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> özelliğini <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> kullanın.|
|üzerinde grupları <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> al.|özelliğini <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> kullanın.|
|içinde görünen satır ve sütun sayısını <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> belirtin.|ve <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> özelliklerini <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> kullanın.|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Salt okunur olan özellikleri ayarlama
 Bazı özellikler yalnızca şerit yüklemeden önce ayarlanabilirsiniz. Bu özellikleri ayarlamak için üç yer vardır:

- Visual Studio **penceresinde.**

- Şerit sınıfının **oluşturucusnda.**

- Projenizin `CreateRibbonExtensibilityObject` , `ThisAddin` veya sınıfının `ThisWorkbook` `ThisDocument` yönteminde.

  Dinamik menüler bazı özel durumlar sağlar. Yeni denetimler oluşturabilir, özelliklerini ayarlayın ve ardından menüyü içeren şerit yüklendikten sonra bile çalışma zamanında bunları dinamik bir menüye ekleyebilirsiniz.

  Dinamik bir menüye ekley istediğiniz zaman denetimlerin özelliklerine sahip olabilir.

  Daha fazla bilgi için [bkz. Salt okunur olan özellikler.](#ReadOnlyProperties)

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Şeridin oluşturucusuzda özellikleri ayarlama
 Bir denetimin özelliklerini `Ribbon` Şerit sınıfının oluşturucusuzda **ayarlayabilirsiniz.** Bu kod, yöntemine yapılan çağrıdan sonra `InitializeComponent` görün gerekir. Aşağıdaki örnek, geçerli saat 17:00 Pasifik Saati (UTC-8) veya sonrası ise gruba yeni bir düğme ekler.

 Aşağıdaki kodu ekleyin.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb" id="Snippet1":::

 2008'den Visual Studio Visual C# projelerinde oluşturucu Şerit kod dosyasında görünür.

 Visual Basic projelerinde veya içinde oluşturduğunuz Visual C# projelerinde [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] oluşturucu Şerit Tasarımcısı kod dosyasında görünür. Bu dosya *YourRibbonItem olarak adlandırılmıştır.* Designer.cs veya *YourRibbonItem*. Designer.vb. bu dosyayı Visual Basic projelerinde görmek için, önce Çözüm Gezgini **tüm dosyaları göster** düğmesini tıklamalısınız.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>CreateRibbonExtensibilityObject yönteminde özellikleri ayarlama
 Bir denetimin özelliklerini,, `Ribbon` `CreateRibbonExtensibilityObject` veya projenizin içindeki yöntemini geçersiz kılarsınız şekilde ayarlayabilirsiniz `ThisAddin` `ThisWorkbook` `ThisDocument` . Yöntemi hakkında daha fazla bilgi için `CreateRibbonExtensibilityObject` bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

 aşağıdaki örnek, `CreateRibbonExtensibilityObject` `ThisWorkbook` bir Excel çalışma kitabı projesinin sınıfının yöntemi içindeki şerit özelliklerini ayarlar.

 Aşağıdaki kodu ekleyin.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs" id="Snippet2":::

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Salt okunabilir hale gelecek özellikler
 Aşağıdaki tabloda, yalnızca Şerit yüklenmeden önce ayarlanmaları gereken özellikler gösterilmektedir.

> [!NOTE]
> Dinamik menülerde denetimlerin özelliklerini istediğiniz zaman ayarlayabilirsiniz. Bu tablo bu durumda uygulanmaz.

|Özellik|Şerit denetim sınıfı|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlID**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**Iletişim başlatıcısı**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dinamik**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Genel**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Gruplar**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**Görüntü**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**Öğe boyutu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**'In**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Ad**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position** (Pozisyon)|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Satır**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Startfromkaralama**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Sekmeler**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Başlık**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Outlook ınspectors 'da görünen şeritler için özellikleri ayarlayın
 Bir Kullanıcı şeridin göründüğü bir Inspector açtığında şeridin yeni bir örneği oluşturulur. Ancak, yukarıdaki tabloda listelenen özellikleri yalnızca şeridin ilk örneği oluşturulmadan önce ayarlayabilirsiniz. ilk örnek oluşturulduktan sonra, ilk örnek, Outlook şeriti yüklemek için kullandığı XML dosyasını tanımladığından, bu özellikler salt okunurdur.

 Şerit 'in diğer örnekleri oluşturulduğunda bu özelliklerden herhangi birini farklı bir değere ayarlayan koşullu mantığa sahipseniz, bu kodun hiçbir etkisi olmayacaktır.

> [!NOTE]
> Outlook şeridine eklediğiniz her denetim için **ad** özelliğinin ayarlanmış olduğundan emin olun. çalışma zamanında bir Outlook şeridine bir denetim eklerseniz, bu özelliği kodunuzda ayarlamanız gerekir. tasarım zamanında bir Outlook şeridine bir denetim eklerseniz, Name özelliği otomatik olarak ayarlanır.

## <a name="ribbon-control-events"></a>Şerit denetim olayları
 Her denetim sınıfı bir veya daha fazla olay içerir. Aşağıdaki tabloda bu olaylar açıklanmaktadır.

|Olay|Açıklama|
|-----------|-----------------|
|Eski kimlik doğrulamasını engelleme hakkında daha fazla bilgi edinmek için|Bir denetime tıklandığında gerçekleşir.|
|TextChanged olayını|Bir düzenleme kutusu veya Birleşik giriş kutusunun metni değiştirildiğinde gerçekleşir.|
|Item' yükleme|Denetimin Items koleksiyonu Office tarafından istendiğinde gerçekleşir. Office, kod denetimin özelliklerini değiştirene veya yöntemi çağırana kadar öğeler koleksiyonunu önbelleğe alır <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> .|
|Görüntüleyip|Ya da ' de bir düğme <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> tıklandığında gerçekleşir.|
|SelectionChanged|Seçim bir <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> veya <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> değiştiğinde gerçekleşir.|
|DialogLauncherClick|Bir grubun sağ alt köşesindeki iletişim kutusu Başlatıcısı simgesine tıklandığında gerçekleşir.|

 Bu olaylara yönelik olay işleyicileri aşağıdaki iki parametreye sahiptir.

|Parametre|Açıklama|
|---------------|-----------------|
|*Gönderen*|<xref:System.Object>Olayı tetikleyen denetimi temsil eden bir.|
|*a*|Bir <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> içerir <xref:Microsoft.Office.Core.IRibbonControl> . Tarafından sağlanan şerit nesne modelinde kullanılamayan herhangi bir özelliğe erişmek için bu denetimi kullanın [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Outlook için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Nasıl yapılır: Şerit Tasarımcısından Şerit XML 'ine şerit aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
