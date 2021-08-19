---
title: İçerik denetimleri
description: İçerik denetimlerini ve içerik denetimlerinin belge ve şablon tasarlamanız için nasıl bir yol sağlay olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b6b086ece516a350963f03268064a526ed566dbc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130747"
---
# <a name="content-controls"></a>İçerik denetimleri
  İçerik denetimleri, şu özelliklere sahip belgeleri ve şablonları tasarlamanız için bir yol sağlar:

- Girişi form gibi denetlenen bir kullanıcı arabirimi (UI).

- Kullanıcıların belgenin veya şablonun korumalı bölümlerini düzenlemesini engelleyen kısıtlamalar. Daha fazla bilgi için [bkz. İçerik denetimlerini kullanarak belgelerin bölümlerini koruma.](#Protection)

- Veri kaynağına veri bağlama. Daha fazla bilgi için [bkz. verileri içerik denetimlerine bağlama.](#DataBinding)

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantısı") İlgili bir video gösterimi için bkz. Office sistemi [(3.0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12))için Visual Studio Araçları kullanarak Word 2007 içerik denetimlerine veri bağlama.

## <a name="overview-of-content-controls"></a>İçerik denetimlerine genel bakış
 İçerik denetimleri, hem kullanıcı girişi hem de yazdırma için iyileştirilmiş bir kullanıcı arabirimi sağlar. Bir belgeye içerik denetimi eklerken, denetim kullanıcıya yönergeler sağltıran bir kenarlık, başlık ve geçici metinle tanımlanır. Kenarlık ve denetimin başlığı belgenin yazdırılan sürümlerinde görünmez.

 Örneğin, kullanıcının belgenizin bir bölümüne tarih girmelerini istemiyorsanız, belgeye bir tarih seçici içerik denetimi ekleyebilirsiniz. Kullanıcılar denetime tıklansa standart tarih seçici kullanıcı arabirimi görüntülenir. Görüntülenen bölgesel takvimi ayarlamak ve tarih biçimini belirtmek için denetimin özelliklerini de belirtebilirsiniz. Kullanıcı bir tarih seçtikten sonra denetimin kullanıcı arabirimi gizlenir ve yalnızca kullanıcı belgeyi yazdırıyorsa tarih görüntülenir.

 İçerik denetimleri ayrıca şunları yapmaya yardımcı olur:

- Kullanıcıların bir belgenin bölümlerini düzenlemesini veya silmesini engelin. Bu, bir belge veya şablonda kullanıcıların okuyabilecek ancak düzenleyemez durumda olması gereken bilgileriniz varsa veya kullanıcıların içerik denetimlerini düzenleyemezken silmelerini istemiyorsanız yararlıdır.

- Bir belgenin veya şablonun parçalarını verilere bağlama. İçerik denetimlerini veritabanı alanlarına, içinde yönetilen nesnelere, belgede depolanan XML öğelerine ve [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] diğer veri kaynaklarına bekleyebilirsiniz.

  Belge düzeyindeki projelerde, tasarım zamanında veya çalışma zamanında belgenize içerik denetimleri ekleyebilirsiniz. Eklenti VSTO içinde, çalışma zamanında herhangi bir açık belgeye içerik denetimleri ekleyebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme.](../vsto/how-to-add-content-controls-to-word-documents.md)

> [!NOTE]
> İçerik denetimlerini yalnızca Open XML biçiminde kaydedilen belgelerde kullanabilirsiniz. Word 97-2003 belgesi ( veya ) biçiminde kaydedilen belgelerde *içerik.doc* kullanılamaz.

## <a name="types-of-content-controls"></a>İçerik denetimi türleri
 Belgelere ekleyebilirsiniz dokuz farklı içerik denetimi türü vardır. İçerik denetimlerinin çoğu ad alanına karşılık gelen bir <xref:Microsoft.Office.Tools.Word> türe sahiptir. Ayrıca, kullanılabilir içerik <xref:Microsoft.Office.Tools.Word.ContentControl> denetimlerini temsil eden genel bir kullanabilirsiniz. Kullanılabilir içerik denetimlerini nasıl kullanabileceğinizi gösteren bir kılavuz için bkz. [Kılavuz: İçerik denetimlerini kullanarak şablon oluşturma.](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)

### <a name="build-block-gallery"></a>Yapı bloğu galerisi
 Yapı taşı galerisi, kullanıcıların bir belgeye eklemek için belge *yapı taşları* listesinden seçimlerini sağlar. Belge yapı taşı, ortak bir cover sayfası, biçimlendirilmiş tablo veya üst bilgi gibi birden çok kez kullanılacak şekilde oluşturulmuş bir içeriktir. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> bakın. Yapı taşları hakkında daha fazla bilgi için [bkz. Word 2007'de geliştiricilere ilişkin yeni şeyler.](/previous-versions/office/developer/office-2007/bb266218(v=office.12))

### <a name="check-box"></a>Onay kutusu
 Onay kutusu, ikili durumu temsil eden bir kullanıcı arabirimi sağlar: seçili veya temiz.

 Diğer içerik denetimleri türlerinden farklı [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] olarak, onay kutusu içerik denetimlerini temsil eden belirli bir tür sağlamaz. Başka bir deyişle, tür `CheckBoxContentControl` yoktur. Ancak, yine de bir belgeye program aracılığıyla genel bir ekleyerek onay <xref:Microsoft.Office.Tools.Word.ContentControl> kutusu içerik denetimi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Word projelerinde onay kutusu içerik denetimleri.](#checkbox)

### <a name="combo-box"></a>Açılır kutu
 Birleşik giriş kutusu, kullanıcıların seçerek seçeliklerini gösteren bir öğe listesi görüntüler. Açılan listeden farklı olarak, birleşik giriş kutusu kullanıcıların kendi öğelerini eklemesini sağlar. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> bakın.

### <a name="date-picker"></a>Tarih seçici
 Tarih seçici, tarih seçmek için bir takvim kullanıcı arabirimi sağlar. Takvim, son kullanıcı denetimde açılan oka tıkladığında görünür. Bölgesel takvimleri ve farklı tarih biçimlerini kullanabilirsiniz. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> bakın.

### <a name="drop-down-list"></a>Açılan liste
 Açılan listede, kullanıcıların seçerek seçeliklerini gösteren bir öğe listesi görüntülenir. Açılır kutudan farklı olarak açılan liste kullanıcıların öğe eklemesine veya düzenlemesine izin vermez. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> bakın.

### <a name="group"></a>Grup
 Grup denetimi, kullanıcıların düzenleyemez veya silemez bir belgenin korumalı bir bölgesi tanımlar. Grup denetimi metin, tablo, grafik ve diğer içerik denetimleri gibi belge öğelerini içerebilir. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.GroupContentControl> bakın.

### <a name="picture"></a>Resim
 Resim denetimi bir görüntü görüntüler. Görüntüyü tasarım zamanında veya çalışma zamanında belirtebilirsiniz veya kullanıcılar belgeye eklemek istediğiniz görüntüyü seçmek için bu denetime tıklar. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.PictureContentControl> bakın.

### <a name="rich-text"></a>Zengin metin
 Zengin metin denetimi; tablolar, resimler veya diğer içerik denetimleri gibi metin veya diğer öğeleri içerir. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.RichTextContentControl> bakın.

### <a name="plain-text"></a>Düz metin
 Düz metin denetimi metin içerir. Düz metin denetimi tablolar, resimler veya diğer içerik denetimleri gibi başka öğeler içere değildir. Ayrıca, düz metin denetiminde yer alan tüm metinler aynı biçimlendirmeye sahip olur. Örneğin, düz metin denetiminde bulunan bir cümlenin tek bir sözcüğü italik hale getirildiyse, denetimin içindeki tüm metin italik olur. Daha fazla bilgi için türüne <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> bakın.

### <a name="generic-content-control"></a>Genel içerik denetimi
 Genel içerik denetimi, <xref:Microsoft.Office.Tools.Word.ContentControl> kullanılabilir içerik denetimi türlerinden herhangi birini temsil eden bir nesnedir. özelliğini kullanarak <xref:Microsoft.Office.Tools.Word.ContentControl> bir nesneyi farklı bir içerik denetimi türü gibi davranarak <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> değiştirebilirsiniz. Örneğin, düz metin denetimi temsil eden bir nesne oluşturursanız, çalışma zamanında bunu birleşik giriş kutusu gibi <xref:Microsoft.Office.Tools.Word.ContentControl> davranacak şekilde değiştirebilirsiniz.

 Nesneleri tasarım <xref:Microsoft.Office.Tools.Word.ContentControl> zamanında değil yalnızca çalışma zamanında oluşturabilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme.](../vsto/how-to-add-content-controls-to-word-documents.md)

## <a name="common-features-of-content-controls"></a>İçerik denetimlerinin ortak özellikleri
 Çoğu içerik denetimi, ortak görevleri gerçekleştirmek için kullanabileceğiniz bir üye kümesi paylaşır. Aşağıdaki tabloda, bu üyeleri kullanarak gerçekleştirebilirsiniz bazı görevler açıklanmış olur.

|Bu görev için:|Bunu yap:|
|--------------------|--------------|
|Denetimde görüntülenen metni almak veya ayarlamak.|Text **özelliğini** kullanın. **Not:**  ve <xref:Microsoft.Office.Tools.Word.PictureContentControl> <xref:Microsoft.Office.Tools.Word.ContentControl> türlerinin bu özelliği yok.|
|Kullanıcı denetimi düzenleyene, denetim bir veri kaynağından gelen verilerle doldurulana veya denetimin içeriği silinene kadar denetimde görüntülenen geçici metni al veya ayarla.|**PlaceholderText özelliğini** kullanın. **Not:**  Türün <xref:Microsoft.Office.Tools.Word.PictureContentControl> bu özelliği yok.|
|Kullanıcı tıkladığında içerik denetimi kenarlığında görüntülenen başlığı edinin veya ayarlayın.|Title **özelliğini** kullanın.|
|Kullanıcı denetimi düzenledikten sonra denetimi belgeden otomatik olarak kaldırın. (Denetimde yer alan metin belgede kalır.)|**Temporary özelliğini** kullanın.|
|Kullanıcı içerik denetimine tıkladığında veya imleç program aracılığıyla içerik denetimine taşındığında kod çalıştırın.|Denetimin <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> olayıyla başa çıkabilir.|
|Kullanıcı içerik denetimi dışına tıkladığında veya imleç program aracılığıyla içerik denetimi dışına taşındığında kod çalıştırın.|Denetimin <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> olayıyla başa çıkabilir.|
|İçerik denetimi belgeye eklendikten sonra, bir yeniden oluşturma veya geri alma işleminin sonucu olarak kodu çalıştırın.|Denetimin <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> olayıyla başa çıkabilir.|
|İçerik denetimi belgeden silinmeden hemen önce kodu çalıştırın.|Denetimin <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> olayıyla başa çıkabilir.|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> İçerik denetimlerini kullanarak belgelerin bölümlerini koruma
 Bir belgenin bir bölümünü korurken, kullanıcıların belgenin o bölümünde yer alan içeriği değiştirmesini veya silmesini önlersiniz. İçerik denetimlerini kullanarak bir belgenin bölümlerini korumanın birkaç yolu vardır.

 Korumak istediğiniz alan bir içerik denetimi içinde ise, kullanıcıların denetimi düzenlemesini veya silmesini engellemek için içerik denetimi özelliklerini kullanabilirsiniz:

- **LockContents özelliği,** kullanıcıların içeriği düzenlemesini önler.

- **LockContentControl** özelliği, kullanıcıların denetimi silmesine engel olur.

  Korumak istediğiniz alan bir içerik denetimi içinde yoksa veya içerik denetimleri ve diğer içerik türlerini içeren bir alanı korumak için tüm alanı bir içine <xref:Microsoft.Office.Tools.Word.GroupContentControl> koyabilirsiniz. Diğer içerik denetimlerini aksine, <xref:Microsoft.Office.Tools.Word.GroupContentControl> kullanıcıya görünür bir kullanıcı arabirimi sağlar. Tek amacı, kullanıcıların düzenleyemez olduğu bir bölge tanımlamaktır.

> [!NOTE]
> Ekli içerik <xref:Microsoft.Office.Tools.Word.GroupContentControl> denetimleri içeren bir oluşturabilirsiniz, ekli içerik denetimleri otomatik olarak korunmaz. Kullanıcıların içeriklerini düzenlemesini önlemek için her ekli denetimin **LockContents** özelliğini kullanabilirsiniz.

 Belgelerin bölümlerini korumak için içerik denetimlerini kullanma hakkında daha fazla bilgi için bkz. Nasıl kullanılır: İçerik denetimlerini [kullanarak belgelerin parçalarını koruma.](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> İçerik denetimlerine veri bağlama
 bir içerik denetimiyle veri kaynağına bağlanarak belgelerde verileri görüntüebilirsiniz. Veri kaynağı güncelleştirildiğinde, içerik denetimi değişiklikleri yansıtıyor. Ayrıca değişiklikleri veri kaynağına geri kaydedebilirsiniz.

 İçerik denetimleri aşağıdaki veri bağlama seçeneklerini sağlar:

- Windows Forms ile aynı veri bağlama modelini kullanarak içerik denetimlerini veritabanı alanlarına veya yönetilen nesnelere Windows.

- İçerik denetimlerini, belgeye eklenmiş XML parçaları (özel *XML parçaları* olarak da adlandırılmıştır) öğelerine bekleyebilirsiniz.

  Veri çözümlerinin veriye bağlanma Office genel bakış için bkz. Veri bağlama [çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="use-the-windows-forms-data-binding-model"></a>Windows Forms veri bağlama modelini kullanma
 Çoğu içerik denetimi, Formlar'ın kullandığı basit Windows modelini destekler. Basit veri bağlama, denetimin bir veri tablosu sütunundaki değer gibi tek bir veri öğesine bağlı olduğu anlamına gelir. Daha fazla bilgi için [bkz. Veri bağlama ve Windows Forms.](/dotnet/framework/winforms/data-binding-and-windows-forms)

 Belge düzeyindeki projelerde, içinde Veri Kaynakları penceresini kullanarak verileri içerik **denetimlerine** [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bekleyebilirsiniz. Belgelere veriye bağlı içerik denetimleri ekleme hakkında daha fazla bilgi için bkz. Nasıl [kullanılır:](../vsto/how-to-populate-documents-with-data-from-a-database.md) Belgeleri bir veritabanındaki verilerle doldurmak ve Nasıl kullanılır: Belgeleri nesnelerinden [verilerle doldurmak.](../vsto/how-to-populate-documents-with-data-from-objects.md)

 Aşağıdaki tabloda, Veri Kaynakları penceresindeki her bir veri türüne bağlanabilirsiniz içerik **denetimleri listele.**

|Veri türü|Varsayılan içerik denetimi|Bu veri türüne bağlanan diğer içerik denetimleri|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> Dizi|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Hiçbiri|

 Belge düzeyinde ve VSTO eklenti projelerinde, denetimin özelliğinin yöntemini kullanarak program aracılığıyla bir veri kaynağına içerik <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> denetimi bekleyebilirsiniz. Bunu yaparsanız Text dizesini **yönteminin** *propertyName* parametresine <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> iletirsiniz. **Text özelliği,** içerik denetimlerinin varsayılan veri bağlama özelliğidir.

 İçerik denetimleri, denetim değişikliklerinin veri kaynağına güncelleştirilen iki yollu veri bağlamayı da destekler. Daha fazla bilgi için, [bkz. How to: Update a data source with data from a host control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

> [!NOTE]
> İçerik denetimleri karmaşık veri bağlamayı desteklemez. Windows Forms veri modelini kullanarak bir veya öğesini bir veri kaynağına bağlarsanız, kullanıcılar denetime tıklayana kadar yalnızca <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> tek bir değer görebilir. Bu denetimleri kullanıcıların seçecekleri bir veri değerleri kümesine bağlamak için bu denetimleri özel bir XML parçasının öğelerine bebilirsiniz.

### <a name="bind-content-controls-to-custom-xml-parts"></a>İçerik denetimlerini özel XML bölümlerine bağlama
 Bazı içerik denetimlerini, belgeye eklenmiş olan özel XML bölümlerine bekleyebilirsiniz. Özel XML bölümleri hakkında daha fazla bilgi için bkz. [Özel XML parçalarına genel bakış.](../vsto/custom-xml-parts-overview.md)

 bir içerik denetimine özel XML parçasında bir öğe bağlamak için **denetimin XMLMapping** özelliğini kullanın. Aşağıdaki kod örneği, belgeye zaten eklenmiş olan özel bir XML bölümünde düğüm altındaki öğeye bir <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> `Price` `Product` bağlamayı gösterir.

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 İçerik denetimlerini özel XML bölümlerine bağlamayı daha ayrıntılı gösteren bir kılavuz için bkz. Kılavuz: İçerik denetimlerini özel [XML bölümlerine bağlama.](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

 İçerik denetiminizi özel bir XML parçasına bağ özel bir XML parçasına bağ her iki yolla veri bağlama otomatik olarak etkinleştirilir. Kullanıcı denetimde metin düzenlerse, ilgili XML öğeleri otomatik olarak güncelleştirilir. Benzer şekilde, özel XML parçalarında öğe değerleri değiştirilirse, XML öğelerine bağlı içerik denetimleri yeni verileri görüntüler.

 Aşağıdaki içerik denetimi türlerini özel XML bölümlerine bebilirsiniz:

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>İçerik denetimleri için veri bağlama olayları
 Tüm içerik denetimleri, veri kaynağı güncelleştirilmeden önce denetimde yer alan metnin belirli ölçütlere uygun olduğunu doğrulama gibi verilerle ilgili görevleri gerçekleştirmek için işlenilebilecek bir dizi olay sağlar. Aşağıdaki tabloda, veri bağlamayla ilgili içerik denetimi olayları listele devam ediyor.

|Görev|Olay|
|----------|-----------|
|Word'in özel bir XML parçasına bağlı bir içerik denetiminde metni otomatik olarak güncelleştirmeden hemen önce kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|Word,içeriği denetimine bağlı özel bir XML bölümünde verileri otomatik olarak güncelleştirmeden hemen önce kodu çalıştırın (diğer bir ifade, içerik denetiminde metin değiştikten sonra).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|Denetimin içeriğini özel ölçütlere göre doğrulamak için kendi kodunuzu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|Denetimin içeriği başarıyla doğrulandıktan sonra kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>İçerik denetimlerinin sınırlamaları
 İçerik denetimlerini Office, aşağıdaki sınırlamalara dikkat edin.

### <a name="behavior-differences-between-design-time-and-runtime"></a>Tasarım zamanı ile çalışma zamanı arasındaki davranış farklılıkları
 Word'Microsoft Office çalışma zamanında içerik denetimlerine uygulayan sınırlamaların çoğu tasarım zamanında uygulanmaz. içinde bir belge düzeyi çözümün kullanıcı arabirimini tasarlarken, içerik denetimlerini yalnızca çalışma zamanında desteklenen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yollarla değiştirerek emin olun.

 Tasarım zamanında içerik denetiminde denetimin çalışma zamanında desteklemeyecek şekilde değiştirirsiniz, tasarımcı desteklenmeyen değişiklikler hakkında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sizi uyarmaz. Ancak, projede hata ayıklasanız veya projeyi kaydedp yeniden açarsanız Word bir hata iletisi görüntüler ve belgeyi onarma izni ister. Belgeyi onararak Word desteklenmeyen tüm içeriği ve biçimlendirmeyi denetimden kaldırır.

 Örneğin Word, tasarım zamanında tabloya tablo eklemeyi <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> engellemez. Ancak, <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> nesneler çalışma zamanında tablo içereyene kadar, belge açıldığında Word bir hata iletisi görüntüler.

 Ayrıca içerik denetimlerinin davranışını tanımlayan birçok özelliğin tasarım zamanında hiçbir etkisi olmadığını unutmayın. Örneğin, tasarım zamanında bir içerik **denetimine ait LockContents** özelliğini **True** olarak ayarsanız, tasarımcıda denetimde metin düzenlemeye [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] devamabilirsiniz. Bu özellik, kullanıcıların denetimi yalnızca çalışma zamanında düzenlemesini önler.

### <a name="event-limitations"></a>Olay sınırlamaları
 İçerik denetimleri, kullanıcı denetimdeki metni veya diğer öğeleri değiştirirken ortaya çıkan bir olay sağlamaz. Örneğin, bir kullanıcı veya içinde farklı bir öğe seçerse hiçbir olay ortaya <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> çıkar. <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

 Bir kullanıcının içerik denetimi içeriğini ne zaman düzenley olduğunu belirlemek için, denetimi özel bir XML parçasına bağp ardından olayı <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> işebilirsiniz. Bu olay, kullanıcı özel bir XML parçasına bağlı bir denetimin içeriğini değiştirirse ortaya çıkar. bir içerik denetimine özel XML parçası bağlamayı gösteren bir kılavuz için bkz. Kılavuz: İçerik denetimlerini özel [XML bölümlerine bağlama.](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Word projelerinde onay kutusu içerik denetimleri
 Word 2010'da onay kutusunu temsil eden yeni bir içerik denetimi türü tanıtıldı. Ancak, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bu projelerde kullanabileceğiniz karşılık gelen bir CheckBoxContentControl Office sağlamaz. bir veya Word 2010 projesinde onay kutusu içerik denetimi oluşturmak için, nesnesini oluşturmak için yöntemini kullanın ve onay kutusu içerik denetimi belirtmek üzere değeri [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> <xref:Microsoft.Office.Tools.Word.ContentControl> <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> yöntemine iletir. Aşağıdaki kod örneğinde bunun nasıl gerçekleştir olduğu gösterildi.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb" id="Snippet800":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs" id="Snippet800":::

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Adım adım kılavuz: İçerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Veri Office verileri](../vsto/data-in-office-solutions.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
