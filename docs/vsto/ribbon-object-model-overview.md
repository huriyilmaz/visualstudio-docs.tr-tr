---
title: Şerit nesne modeline genel bakış
description: Office için Visual Studio Araçları çalışma zamanının, çalışma zamanında şerit denetimlerinin özelliklerini almak ve ayarlamak için kullanabileceğiniz, türü kesin belirlenmiş bir nesne modeli nasıl kullanıma sunduğunu öğrenin.
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
ms.openlocfilehash: 8018eed6f621e81a7ee57ae2e4087ff30615cac1c29cbd6401413c12716f054e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226147"
---
# <a name="ribbon-object-model-overview"></a>Şerit nesne modeline genel bakış
  , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Çalışma zamanında Şerit denetimlerinin özelliklerini almak ve ayarlamak için kullanabileceğiniz, türü kesin belirlenmiş bir nesne modeli sunar. Örneğin, menü denetimlerini dinamik olarak doldurabilir veya bağlamsal olarak denetimlerini gösterebilir ve gizleyebilirsiniz. ayrıca şerit 'e sekmeler, gruplar ve denetimler ekleyebilirsiniz, ancak yalnızca şerit Office uygulama tarafından yüklenmeden önce. Bilgi için bkz. [Salt okunabilir olan özellikleri ayarlama](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Bu şerit nesne modeli, genellikle [Şerit sınıfından](#RibbonClass), [Şerit olaylarından](#RibbonEvents)ve [Şerit denetim sınıflarından](#RibbonControlClasses)oluşur.

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Şerit sınıfı
 projeye yeni bir **şerit (görsel tasarımcı)** öğesi eklediğinizde Visual Studio projenize bir **şerit** sınıfı ekler. **Şerit** sınıfı <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> sınıfından devralır.

 Bu sınıf, Şerit kod dosyası ve Şerit Tasarımcı kod dosyası arasında bölünen kısmi bir sınıf olarak görünür.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Şerit olayları
 **Şerit** sınıfı aşağıdaki üç olayı içerir:

|Olay|Açıklama|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Office uygulaması şerit özelleştirmesini yüklediğinde tetiklenir. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>Olay işleyicisi, Şerit kod dosyasına otomatik olarak eklenir. Şerit yüklendiğinde özel kod çalıştırmak için bu olay işleyicisini kullanın.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Şerit 'in yüklediğinde, Şerit özelleştirmesindeki görüntüleri önbelleğe almanıza olanak sağlar. Bu olay işleyicisindeki Şerit görüntülerini önbelleğe almak için kod yazarsanız küçük bir performans kazancı elde edebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Şerit örneği kapandığında tetiklenir.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Şerit denetimleri
 <xref:Microsoft.Office.Tools.Ribbon>ad alanı, **araç kutusunun** **Office şerit denetimleri** grubunda gördüğünüz her denetim için bir tür içerir.

 Aşağıdaki tabloda her bir denetimin türü gösterilmektedir `Ribbon` . Her denetimin açıklaması için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

|Denetim adı|Sınıf adı|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Düğme**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Listenin**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Galeri**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Grup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Etiketle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menü**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Ayırıcı**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Sekme**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 Ad alanı, ad <xref:Microsoft.Office.Tools.Ribbon> alanındaki denetim sınıflarının adlarıyla ad çarpışmasını önlemek için bu türler için "Ribbon" önekini kullanır <xref:System.Windows.Forms> .

 Şerit Tasarımcısına bir denetim eklediğinizde, Şerit Tasarımcısı bu denetimin sınıfını Şerit Tasarımcı kod dosyasında bir alan olarak bildirir.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Şerit denetimlerinin özelliklerini kullanan ortak görevler
 Her `Ribbon` Denetim, bir denetime etiket atama ya da denetimleri gizleme veya gösterme gibi çeşitli görevleri gerçekleştirmek için kullanabileceğiniz özellikleri içerir.

 Bazı durumlarda, şerit yüklendikten sonra veya bir denetim dinamik menüye eklendikten sonra Özellikler salt okunurdur. Daha fazla bilgi için bkz. [Salt okunabilir olan özellikleri ayarlama](#SettingReadOnlyProperties).

 Aşağıdaki tabloda, denetim özelliklerini kullanarak gerçekleştirebileceğiniz görevlerden bazıları açıklanmaktadır `Ribbon` .

|Bu görev için:|Bunu yapın:|
|--------------------|--------------|
|Bir denetimi gizleyin veya gösterin.|Visible özelliğini kullanın.|
|Bir denetimi etkinleştirin veya devre dışı bırakın.|Enabled özelliğini kullanın.|
|Bir denetimin boyutunu ayarlayın.|ControlSize özelliğini kullanın.|
|Denetimde görüntülenen görüntüyü alın.|Image özelliğini kullanın.|
|Bir denetimin etiketini değiştirin.|Label özelliğini kullanın.|
|Bir denetime kullanıcı tanımlı veriler ekleyin.|Tag özelliğini kullanın.|
|Öğeleri,,, veya içinde alın <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> denetimle.|Items özelliğini kullanın.|
|Bir <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> , <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> veya denetimine öğe ekleyin <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Items özelliğini kullanın.|
|Bir öğesine denetimler ekleyin <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> .|Items özelliğini kullanın.<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>şerit Office uygulamasına yüklendikten sonra öğesine denetim eklemek için, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> şerit Office uygulamasına yüklenmeden önce özelliği **true** olarak ayarlamanız gerekir. Bilgi için bkz. [Salt okunabilir olan özellikleri ayarlama](#SettingReadOnlyProperties).|
|Seçili öğe <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, veya <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Selectedidıtem özelliğini kullanın. Bir için <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> özelliğini kullanın.|
|Grupları bir üzerinde alın <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Özelliğini kullanın <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> .|
|İçinde görünen satır ve sütun sayısını belirtin <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A>Ve özelliklerini kullanın <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> .|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Salt okuma yapılacak özellikleri ayarlama
 Bazı özellikler yalnızca Şerit yüklenmeden önce ayarlanabilir. Bu özellikleri ayarlamak için üç yer vardır:

- Visual Studio **özellikler** penceresinde.

- **Şerit** sınıfının oluşturucusunda.

- `CreateRibbonExtensibilityObject` `ThisAddin` , `ThisWorkbook` , Veya `ThisDocument` projenizin sınıfında.

  Dinamik menüler bazı özel durumlar sağlar. Menüyü içeren şerit yüklendikten sonra bile, yeni denetimler oluşturabilir, özelliklerini ayarlayabilir ve ardından onları çalışma zamanında dinamik bir menüye ekleyebilirsiniz.

  Dinamik menüye eklediğiniz denetimlerin özellikleri herhangi bir zamanda ayarlanabilir.

  Daha fazla bilgi için, bkz. [Salt okunabilir hale gelecek özellikler](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Şeridin oluşturucusunda Özellikleri ayarla
 `Ribbon` **Şerit** sınıfının oluşturucusunda bir denetimin özelliklerini ayarlayabilirsiniz. Bu kod, yönteme çağrıdan sonra görünmelidir `InitializeComponent` . Aşağıdaki örnek, geçerli saat 17:00 Pasifik saati (UTC-8) veya daha sonraki bir gruba yeni bir düğme ekler.

 Aşağıdaki kodu ekleyin.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb" id="Snippet1":::

 Visual Studio 2008 ' den yükselttiğiniz Visual C# projelerinde, oluşturucu şerit kod dosyasında görünür.

 Visual Basic projelerinde veya içinde oluşturduğunuz Visual C# projelerinde, [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] oluşturucu şerit tasarımcı kod dosyasında görünür. Bu dosya *YourRibbonItem* olarak adlandırılmıştır. Tasarımcı. cs veya *YourRibbonItem*. Designer. vb. Bu dosyayı projelerde Visual Basic için önce dosyanın tüm dosyalarını **göster** düğmesine tıklamanız Çözüm Gezgini.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>CreateRibbonExtensibilityObject yönteminde özellikleri ayarlama
 Bir denetimin özelliklerini, `Ribbon` projenizin , veya sınıfındaki yöntemini `CreateRibbonExtensibilityObject` geçersiz `ThisAddin` `ThisWorkbook` `ThisDocument` kılarak ayarlayabilirsiniz. yöntemi hakkında daha fazla bilgi `CreateRibbonExtensibilityObject` için bkz. [Şerit'e Genel Bakış.](../vsto/ribbon-overview.md)

 Aşağıdaki örnek, bir çalışma kitabı `CreateRibbonExtensibilityObject` projesinin sınıfının `ThisWorkbook` yönteminde Şerit Excel ayarlar.

 Aşağıdaki kodu ekleyin.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs" id="Snippet2":::

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Salt okunur hale dönüşen özellikler
 Aşağıdaki tabloda yalnızca şerit yüklemeden önce ayarlanacak özellikler yer alır.

> [!NOTE]
> Denetimlerin özelliklerini dinamik menülerde herhangi bir zamanda ayarlayabilirsiniz. Bu tablo bu durumda geçerli değildir.

|Özellik|Şerit denetim sınıfı|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Buttontype**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Columncount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Controlıd**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dinamik**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Genel**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Gruplar**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ımagename**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Maxlength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Ad**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position** (Pozisyon)|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Rowcount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Sekmeler**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Başlık**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Denetçilerde görünen şeritlerin Outlook ayarlama
 Bir kullanıcı şeridin göründüğü bir Denetçiyi her açtığında şeridin yeni bir örneği oluşturulur. Ancak, yukarıdaki tabloda listelenen özellikleri yalnızca şeridin ilk örneği oluşturulmadan önce ayarlayın. İlk örnek oluşturulduktan sonra bu özellikler salt okunur hale geldi çünkü ilk örnek şeridi yüklemek için Outlook XML dosyasını tanımlar.

 Şeridin diğer örnekleri oluşturulduğunda bu özelliklerden herhangi birini farklı bir değere ayaran koşullu mantığınız varsa, bu kodun hiçbir etkisi olmaz.

> [!NOTE]
> Name özelliğinin **Bir** Şerit'e ekley istediğiniz her denetim için Outlook emin olur. Çalışma zamanında bir Outlook Şerit'e denetim eklersiniz, kodunda bu özelliği ayarlayabilirsiniz. Tasarım zamanında Bir Outlook Şerit'e denetim eklersiniz, Name özelliği otomatik olarak ayarlanır.

## <a name="ribbon-control-events"></a>Şerit denetimi olayları
 Her denetim sınıfı bir veya daha fazla olay içerir. Aşağıdaki tabloda bu olaylar açık almaktadır.

|Olay|Açıklama|
|-----------|-----------------|
|Eski kimlik doğrulamasını engelleme hakkında daha fazla bilgi edinmek için|Bir denetime tık olduğunda gerçekleşir.|
|TextChanged|Bir düzenleme kutusunun veya birleşik giriş kutusunun metni değiştir geldiğinde gerçekleşir.|
|ItemsLoading|Denetimin Items koleksiyonu, denetim tarafından Office. Office, kodunuz denetimin özelliklerini değiştirmeden veya yöntemini çağırana kadar Items koleksiyonunu önbelleğe <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> alıyor.|
|Buttonclick|veya içinde bir düğmeye <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> tıkıldığında <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> gerçekleşir.|
|Selectionchanged|veya içinde seçim değişirse <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> gerçekleşir.|
|DialogLauncherClick|Bir grubun sağ alt köşesindeki iletişim kutusu başlatıcı simgesine tıklarsanız gerçekleşir.|

 Bu olaylar için olay işleyicileri aşağıdaki iki parametreye sahip olur.

|Parametre|Açıklama|
|---------------|-----------------|
|*Gönderen*|Olayı <xref:System.Object> yükselten denetimi temsil eden bir.|
|*E*|içeren <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> bir <xref:Microsoft.Office.Core.IRibbonControl> . tarafından sağlanan Şerit nesne modelinde mevcut olan herhangi bir özel nesneye erişmek için bu denetimi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanın.|

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında şerite erişme](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Nasıl Kullanmaya başlayın: şeridi özelleştirme](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Adım adım kılavuz: Çalışma zamanında şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Bir şeridi Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl yapılır: Yerleşik sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl olur: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Nasıl kullanılır: Şerit Tasarımcısı'nda şeritten Şerit XML'sini dışarı aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl kullanılır: Eklenti kullanıcı arabirimi hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
