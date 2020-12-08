---
title: İçerik denetimleri
description: İçerik denetimleri ve içerik denetimlerinin belge ve şablon tasarlamak için bir yol nasıl sağladığını öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a34211c7fb1fa001719219b7d08baab65340bde5
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848046"
---
# <a name="content-controls"></a>İçerik denetimleri
  İçerik denetimleri, bu özelliklere sahip belge ve şablonlar tasarlamak için bir yol sağlar:

- Form gibi denetimli girişi olan bir kullanıcı arabirimi (UI).

- Kullanıcıların belge veya şablonun korunan bölümlerini düzenlemesini engelleyen kısıtlamalar. Daha fazla bilgi için bkz. [içerik denetimlerini kullanarak belgelerin parçalarını koruma](#Protection).

- Veri kaynağına veri bağlama. Daha fazla bilgi için bkz. [içerik denetimlerine veri bağlama](#DataBinding).

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantısı") İlgili video gösterimi için bkz. [Office sistemi için Visual Studio araçları kullanarak verileri Word 2007 içerik denetimlerine bağlama (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="overview-of-content-controls"></a>İçerik denetimlerine genel bakış
 İçerik denetimleri hem Kullanıcı girişi hem de yazdırma için iyileştirilmiş bir kullanıcı arabirimi sağlar. Belgeye bir içerik denetimi eklediğinizde, denetim bir kenarlık, başlık ve kullanıcıya yönergeler sağlayabilen geçici bir metinle tanımlanır. Denetimin kenarlığı ve başlığı belgenin yazdırılmış sürümlerinde görünmez.

 Örneğin, kullanıcının belgenizin bir bölümüne Tarih girmesini istiyorsanız belgeye bir tarih seçici içerik denetimi ekleyebilirsiniz. Kullanıcılar denetime tıkladığınızda, standart tarih seçici Kullanıcı arabirimi görüntülenir. Ayrıca, görüntülenen bölgesel takvimi ayarlamak ve tarih biçimini belirtmek için denetimin özelliklerini de ayarlayabilirsiniz. Kullanıcı bir tarih seçtikten sonra, denetimin kullanıcı arabirimi gizlenir ve yalnızca Kullanıcı belgeyi yazdırırsa tarih görüntülenir.

 İçerik denetimleri de şunları yapmanıza yardımcı olur:

- Kullanıcıların bir belgenin parçalarını düzenlemesini veya silmesini engelleyin. Bu, bir belge veya şablonda, kullanıcıların okuyabilmesini ancak düzenleyemeyeceğini, ancak kullanıcıların içerik denetimlerini düzenleyebilmesini ancak silmesine izin vermek istiyorsanız yararlıdır.

- Bir belgenin veya şablonun parçalarını verilere bağlayın. İçerik denetimlerini veritabanı alanları, içindeki yönetilen nesneler, [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] belgede depolanan xml öğeleri ve diğer veri kaynakları için bağlayabilirsiniz.

  Belge düzeyi projelerinde, tasarım zamanında veya çalışma zamanında belgenize içerik denetimleri ekleyebilirsiniz. VSTO eklenti projelerinde, çalışma zamanında herhangi bir açık belgeye içerik denetimleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).

> [!NOTE]
> İçerik denetimlerini yalnızca Open XML biçiminde kaydedilmiş belgelerde kullanabilirsiniz. Word 97-2003 Document (*. doc*) biçiminde kaydedilmiş belgelerde içerik denetimlerini kullanamazsınız.

## <a name="types-of-content-controls"></a>İçerik denetimi türleri
 Belgelere ekleyebileceğiniz dokuz farklı türde içerik denetimi vardır. İçerik denetimlerinin çoğunun ad alanında karşılık gelen bir türü vardır <xref:Microsoft.Office.Tools.Word> . Ayrıca <xref:Microsoft.Office.Tools.Word.ContentControl> , kullanılabilir içerik denetimlerinden herhangi birini temsil eden genel ' i de kullanabilirsiniz. Kullanılabilir içerik denetimlerinin her birinin nasıl kullanılacağını gösteren bir anlatım için bkz. [Izlenecek yol: içerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

### <a name="build-block-gallery"></a>Derleme bloğu Galerisi
 Yapı taşı Galerisi, kullanıcıların bir belgeye eklemek üzere *belge yapı taşları* listesinden seçim yapmasına olanak sağlar. Belge yapı taşı, ortak kapak sayfası, biçimlendirilen tablo veya üst bilgi gibi birden çok kez kullanılmak üzere oluşturulmuş bir içerik parçasıdır. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> .. Blok oluşturma hakkında daha fazla bilgi için bkz. [Word 2007 ' de geliştiriciler için](/previous-versions/office/developer/office-2007/bb266218(v=office.12))yenilikler.

### <a name="check-box"></a>Onay kutusu
 Bir onay kutusu, bir ikili durumu temsil eden bir kullanıcı arabirimi sağlar: seçili veya temizlenmiş.

 Diğer içerik denetimi türlerinin aksine, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bir onay kutusu içerik denetimini temsil eden belirli bir tür sağlamaz. Diğer bir deyişle, hiçbir tür yoktur `CheckBoxContentControl` . Bununla birlikte, bir belgeye programlı bir şekilde genel ekleyerek bir onay kutusu içerik denetimi de oluşturabilirsiniz <xref:Microsoft.Office.Tools.Word.ContentControl> . Daha fazla bilgi için bkz. [Word projelerinde içerik denetimleri onay kutusu](#checkbox).

### <a name="combo-box"></a>Açılır kutu
 Açılan kutu, kullanıcıların seçebileceğiniz öğelerin bir listesini görüntüler. Açılan listenin aksine, açılan kutu, kullanıcıların kendi öğelerini eklemesini sağlar. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ..

### <a name="date-picker"></a>Tarih seçici
 Tarih Seçici, bir tarih seçmek için bir Takvim Kullanıcı arabirimi sağlar. Takvim, Son Kullanıcı denetimdeki açılan oka tıkladığında görüntülenir. Bölgesel takvimleri ve farklı tarih biçimlerini kullanabilirsiniz. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> ..

### <a name="drop-down-list"></a>Açılan liste
 Açılır liste, kullanıcıların seçebileceğiniz öğelerin bir listesini görüntüler. Birleşik giriş kutusunun aksine, açılan liste kullanıcıların öğeleri eklemesine veya düzenlemesine izin vermez. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ..

### <a name="group"></a>Grup
 Bir grup denetimi, kullanıcıların düzenleyeve silememe veya silmesine yönelik bir belgenin korumalı bölgesini tanımlar. Bir grup denetimi metin, tablolar, grafikler ve diğer içerik denetimleri gibi herhangi bir belge öğesi içerebilir. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.GroupContentControl> ..

### <a name="picture"></a>Resim
 Resim denetimi bir resim görüntüler. Görüntüyü tasarım zamanında veya çalışma zamanında belirtebilir veya kullanıcılar bu denetime tıklayarak belgeye eklenecek bir görüntü seçebilirsiniz. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.PictureContentControl> ..

### <a name="rich-text"></a>Zengin metin
 Zengin metin denetimi, tablolar, resimler veya diğer içerik denetimleri gibi metin veya diğer öğeleri içerir. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ..

### <a name="plain-text"></a>Düz metin
 Düz metin denetimi metin içerir. Düz metin denetimi tablolar, resimler veya diğer içerik denetimleri gibi diğer öğeleri içeremez. Ayrıca, düz metin denetimindeki metnin hepsi aynı biçimlendirmeye sahiptir. Örneğin, bir tümcenin düz metin denetimindeki bir sözcüğünü italik yaparsanız, denetimin içindeki tüm metin italik olur. Daha fazla bilgi için bkz <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> ..

### <a name="generic-content-control"></a>Genel içerik denetimi
 Genel içerik denetimi, <xref:Microsoft.Office.Tools.Word.ContentControl> kullanılabilir içerik denetimi türlerinden herhangi birini temsil eden bir nesnedir. Özelliğini kullanarak, bir <xref:Microsoft.Office.Tools.Word.ContentControl> nesneyi farklı türde bir içerik denetimi gibi davranacak şekilde değiştirebilirsiniz <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> . Örneğin, bir <xref:Microsoft.Office.Tools.Word.ContentControl> düz metin denetimini temsil eden bir nesne oluşturursanız, çalışma zamanında onu bir açılan kutu gibi davranması için değiştirebilirsiniz.

 <xref:Microsoft.Office.Tools.Word.ContentControl>Tasarım zamanında değil, yalnızca çalışma zamanında nesne oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).

## <a name="common-features-of-content-controls"></a>İçerik denetimlerinin ortak özellikleri
 Çoğu içerik denetimi, ortak görevleri gerçekleştirmek için kullanabileceğiniz bir üye kümesini paylaşır. Aşağıdaki tabloda, bu üyeleri kullanarak gerçekleştirebileceğiniz görevlerden bazıları açıklanmaktadır.

|Bu görev için:|Bunu yapın:|
|--------------------|--------------|
|Denetimde görüntülenen metni alır veya ayarlar.|**Text** özelliğini kullanın. **Note:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> Ve <xref:Microsoft.Office.Tools.Word.ContentControl> türlerinde bu özellik yoktur.|
|Kullanıcı denetimi düzenleene kadar denetimde görüntülenen geçici metni alır veya ayarlar, denetim bir veri kaynağından alınan verilerle doldurulmuştur veya denetimin içeriği silinir.|**PlaceholderText** özelliğini kullanın. **Note:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> Tür bu özelliğe sahip değil.|
|Kullanıcı üzerini tıklattığında içerik denetiminin kenarlığında görüntülenen başlığı alır veya ayarlar.|**Title** özelliğini kullanın.|
|Kullanıcı denetimi düzenledikten sonra denetimi belgeden otomatik olarak kaldırın. (Denetimdeki metin belge içinde kalır.)|**Geçici** özelliğini kullanın.|
|Kullanıcı içerik denetimine tıkladığında veya imleç içerik denetimine programlı olarak taşındığında kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>Denetimin olayını işleyin.|
|Kullanıcı içerik denetiminin dışına tıkladığında veya imleç içerik denetiminin dışına bir program aracılığıyla taşındığında kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>Denetimin olayını işleyin.|
|Yineleme veya geri alma işleminin sonucu olarak belgeye içerik denetimi eklendikten sonra kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>Denetimin olayını işleyin.|
|İçerik denetimi belgeden silinmeden hemen önce kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>Denetimin olayını işleyin.|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> İçerik denetimlerini kullanarak belge bölümlerini koruma
 Belgenin bir bölümünü koruduğunuzda, kullanıcıların belgenin o bölümündeki içeriği değiştirmesini veya silmesini engelleyebilirsiniz. İçerik denetimlerini kullanarak bir belgenin parçalarını koruyabileceğiniz çeşitli yollar vardır.

 Korumak istediğiniz alan bir içerik denetimi içindeyse, kullanıcıların denetimi düzenlemesini ve silmesini engellemek için içerik denetiminin özelliklerini kullanabilirsiniz:

- **LockContents** özelliği kullanıcıların içeriği düzenlemesini engeller.

- **LockContentControl** özelliği kullanıcıların denetimi silmesini engeller.

  Korumak istediğiniz alan bir içerik denetimi içinde değilse veya içerik denetimleri ve diğer içerik türlerini içeren bir alanı korumak istiyorsanız, tüm alanı ' a yerleştirebilirsiniz <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Diğer içerik denetimlerinden farklı olarak,, <xref:Microsoft.Office.Tools.Word.GroupContentControl> Kullanıcı tarafından görülemeyen bir kullanıcı arabirimi sağlar. Tek amacı, kullanıcıların düzenleyene bir bölge tanımlamaktır.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.GroupContentControl>Katıştırılmış içerik denetimleri içeren bir oluşturursanız, katıştırılmış içerik denetimleri otomatik olarak korunmaz. Kullanıcıların içeriklerini düzenlemesini engellemek için, her bir katıştırılmış denetimin **LockContents** özelliğini kullanmanız gerekir.

 Belge parçalarını korumak için içerik denetimlerini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> İçerik denetimlerine veri bağlama
 Bir içerik denetimini bir veri kaynağına bağlayarak belgelerde verileri görüntüleyebilirsiniz. Veri kaynağı güncelleştirildiği zaman, içerik denetimi değişiklikleri yansıtır. Değişiklikleri veri kaynağına geri de kaydedebilirsiniz.

 İçerik denetimleri, aşağıdaki veri bağlama seçeneklerini sağlar:

- Windows Forms ile aynı veri bağlama modelini kullanarak, içerik denetimlerini veritabanı alanlarına veya yönetilen nesnelere bağlayabilirsiniz.

- İçerik denetimlerini, XML parçaları ( *özel XML parçaları* olarak da adlandırılır) halinde belgeye katıştırılmış öğelere bağlayabilirsiniz.

  Office çözümlerinde verilere konak denetimlerini bağlamaya genel bakış için bkz. [Office çözümlerinde verileri denetimlere](../vsto/binding-data-to-controls-in-office-solutions.md)bağlama.

### <a name="use-the-windows-forms-data-binding-model"></a>Windows Forms veri bağlama modelini kullanma
 Çoğu içerik denetimi, Windows Forms kullandığı basit veri bağlama modelini destekler. Basit veri bağlama, bir denetimin veri tablosu sütunundaki bir değer gibi tek bir veri öğesine bağlandığı anlamına gelir. Daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Belge düzeyi projelerinde, içindeki **veri kaynakları** penceresini kullanarak içerik denetimlerine veri bağlayabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Belgelere veriye dayalı içerik denetimleri ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md) ve [nasıl yapılır: belgeleri nesnelerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md).

 Aşağıdaki tabloda, **veri kaynakları** penceresinde her bir veri türüne bağlayabileceğiniz içerik denetimleri listelenmektedir.

|Veri türü|Varsayılan içerik denetimi|Bu veri türüne bağlanabilen diğer içerik denetimleri|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> dizide|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Hiçbiri|

 Belge düzeyi ve VSTO eklenti projelerinde, <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> denetimin özelliğinin yöntemini kullanarak bir içerik denetimini bir veri kaynağına programlı bir şekilde bağlayabilirsiniz <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . Bunu yaparsanız, dize **metnini** yönteminin *PropertyName* parametresine geçirin <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> . **Text** özelliği, içerik denetimlerinin varsayılan veri bağlama özelliğidir.

 İçerik denetimleri Ayrıca, denetimdeki değişikliklerin veri kaynağına güncelleştirildiği iki yönlü veri bağlamayı destekler. Daha fazla bilgi için bkz. [nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

> [!NOTE]
> İçerik denetimleri karmaşık veri bağlamayı desteklemez. Bir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> veri kaynağını Windows Forms veri modelini kullanarak bağlarsanız, kullanıcılar denetime tıkladıklarında yalnızca tek bir değer görür. Bu denetimleri kullanıcıların aralarından seçim yapabileceğiniz bir veri kümesine bağlamak istiyorsanız, bu denetimleri özel bir XML bölümünde bulunan öğelere bağlayabilirsiniz.

### <a name="bind-content-controls-to-custom-xml-parts"></a>İçerik denetimlerini özel XML bölümlerine bağlama
 Bazı içerik denetimlerini belgeye katıştırılmış özel XML bölümleri öğelerine bağlayabilirsiniz. Özel XML bölümleri hakkında daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).

 Bir içerik denetimini özel bir XML bölümünde bir öğeye bağlamak için denetimin **XmlMapping** özelliğini kullanın. Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> `Price` `Product` belgeye zaten eklenmiş olan özel bir XML bölümünde, düğümü altındaki öğesine nasıl bağlanacağını göstermektedir.

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 İçerik denetimlerini özel XML bölümlerine nasıl bağlayabileceğinizi gösteren bir anlatım için bkz. [Izlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

 Bir içerik denetimini özel bir XML bölümüne bağladığınızda, iki yönlü veri bağlama otomatik olarak etkinleştirilir. Kullanıcı denetimdeki metni düzenlerse, karşılık gelen XML öğeleri otomatik olarak güncelleştirilir. Benzer şekilde, özel XML bölümlerinin öğe değerleri değiştirilirse, XML öğelerine bağlanan içerik denetimleri yeni verileri görüntüler.

 Aşağıdaki içerik denetimi türlerini özel XML bölümlerine bağlayabilirsiniz:

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>İçerik denetimleri için veri bağlama olayları
 Tüm içerik denetimleri, veri kaynağı güncelleştirildikten önce bir denetimdeki metnin belirli ölçütlere uygun olduğunu doğrulamak gibi verilerle ilgili görevleri gerçekleştirmek için işleyebilmeniz gereken bir olay kümesi sağlar. Aşağıdaki tabloda, veri bağlamasıyla ilgili içerik denetimi olayları listelenmektedir.

|Görev|Olay|
|----------|-----------|
|Word, özel bir XML bölümüne bağlanan içerik denetimindeki metni otomatik olarak güncelleştirmeden hemen önce kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|Word, bir içerik denetimine (içerik denetimindeki metin değiştirildikten sonra) bağlanan özel bir XML parçasındaki verileri otomatik olarak güncelleştirmeden hemen önce kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|Özel ölçütlere göre denetimin içeriğini doğrulamak için kendi kodunuzu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|Denetim içeriği başarıyla doğrulandıktan sonra kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>İçerik denetimlerinin sınırlamaları
 Office projelerinizde içerik denetimlerini kullandığınızda, aşağıdaki sınırlamalara dikkat edin.

### <a name="behavior-differences-between-design-time-and-runtime"></a>Tasarım zamanı ve çalışma zamanı arasındaki davranış farklılıkları
 Word 'Ün Microsoft Office, çalışma zamanında içerik denetimlerine hangi sınırlamaların birçoğu, tasarım zamanında zorlanmaz. İçinde belge düzeyi çözümünün Kullanıcı arabirimini tasarlarken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , içerik denetimlerini yalnızca çalışma zamanında desteklenen şekillerde değiştirdiğinizden emin olun.

 Tasarım zamanında bir içerik denetimini denetimin çalışma zamanında desteklemediği bir şekilde değiştirirseniz, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcı desteklenmeyen değişiklikler konusunda sizi uyarmaz. Ancak, projeyi hata ayıkladığınızda veya çalıştırdığınızda ya da projeyi kaydedip yeniden açarsanız, Word bir hata iletisi görüntüler ve belgeyi onarmak için izin ister. Belgeyi onardığınızda, Word desteklenmeyen tüm içerik ve biçimlendirmeyi denetimden kaldırır.

 Örneğin, Word tasarım zamanına bir tablo eklemenizi engellemez <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> . Ancak, <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> nesneler çalışma zamanında tablo içeremediğinden, belge açıldığında Word bir hata mesajı görüntüler.

 Ayrıca, içerik denetimlerinin davranışını tanımlayan birçok özellik tasarım zamanında hiçbir etkiye sahip değildir. Örneğin, tasarım zamanında bir içerik denetiminin **LockContents** özelliğini **true** olarak ayarlarsanız, tasarımcıda denetimdeki metni yine de düzenleyebilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bu özellik yalnızca kullanıcıların çalışma zamanında denetimi düzenlemesini engeller.

### <a name="event-limitations"></a>Olay sınırlamaları
 İçerik denetimleri, Kullanıcı denetimdeki metni veya diğer öğeleri değiştirdiğinde oluşan bir olay sağlamaz. Örneğin, bir kullanıcı veya içinde farklı bir öğe seçtiğinde oluşturulan hiçbir olay yoktur <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> .

 Bir kullanıcının bir içerik denetiminin içeriğini ne zaman düzenlediğini öğrenmek için, denetimi özel bir XML bölümüne bağlayabilir ve sonra <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> olayı işleyebilirsiniz. Bu olay, Kullanıcı özel bir XML bölümüne bağlanan bir denetimin içeriğini değiştirdiğinde tetiklenir. Bir içerik denetimini özel bir XML bölümüne bağlamayı gösteren bir anlatım için bkz. [Izlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Word projelerindeki içerik denetimleri onay kutusu
 Word 2010, bir onay kutusunu temsil eden yeni bir içerik denetimi türü sunmuştur. Ancak, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office projelerinde kullanabilmeniz için karşılık gelen bir CheckBoxContentControl türü sağlamaz. Bir veya Word 2010 projesinde onay kutusu içerik denetimi oluşturmak için, [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> yöntemini kullanarak bir <xref:Microsoft.Office.Tools.Word.ContentControl> nesne oluşturun ve bir <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> onay kutusu içerik denetimi belirtmek için değeri yöntemine geçirin. Aşağıdaki kod örneği bunun nasıl yapılacağını göstermektedir.

 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [İzlenecek yol: içerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
