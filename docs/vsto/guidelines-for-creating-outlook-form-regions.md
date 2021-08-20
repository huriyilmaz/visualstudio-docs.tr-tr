---
title: Form bölgelerini Outlook yönergeleri
description: Form bölgelerinizi iyileştirmenize ve olası Outlook önlemenize yardımcı olacak form bölgeleri oluşturma yönergeleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e357126554169c54faa53fdd8810cf040851fc2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130487"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Form bölgelerini Outlook yönergeleri
  Aşağıdaki bilgiler form bölgelerinizi iyileştirmenize ve olası sorunlardan kaçınmanıza yardımcı olabilir:

- [Form bölgesi adlarını kullanın.](#UsingFormRegions)

- [Form bölgesi devralmayı devre dışı bırakma.](#DisablingInheritance)

- [Türleri ve ileti sınıfı adlarını anlama.](#ClassNames)

- [Okuma bölmesi için bitişik form bölgeleri tasarlar.](#ReadingPane)

- [En uygun simge boyutlarını kullanın.](#UsingOptimal)

  Form bölgeleri hakkında daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> Form bölgesi adlarını kullanma
 Form bölgelerini tanımlamak için kullanılan birkaç ad vardır. Bu adlar arasındaki farkı ve form bölgelerini nasıl etkilediğini anlamak önemlidir. Aşağıdaki tabloda her bir ad açık almaktadır.

|Form bölgesi adı|Açıklama|
|----------------------|-----------------|
|Form bölgesi öğe adı|Yeni Öğe Ekle iletişim **Outlook Form Bölgesi** öğesi için **belirttiğiniz** ad. Bu, dosyanın içinde görünen form bölgesi kod dosyasının **Çözüm Gezgini.**|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> Özellik|Bu adı Açıklayıcı metin **girin'de belirtir ve Yeni** Form Bölgesi sihirbazının **görüntüleme tercihleri Outlook seçersiniz.** Bu ad, Özellikler **penceresinde FormRegionName** özelliği **olarak** görünür.<br /><br /> Kullanıcı <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> arabiriminde (UI) form bölgelerini tanımlayan etiketi belirtmek Outlook özelliğini kullanın. Ayrı form bölgeleri için bu ad, bir öğenin Şerit'inde bir Outlook görünür.<br /><br /> Bitişik form bölgeleri için bu ad, form bölgesi üzerinde üst bilgi metni olarak görünür.|
|`Microsoft.Office.Tools.Outlook.FormRegionName` özniteliği|Projeye bir **Outlook Form** Bölgesi öğesi Visual Studio bu özelliği form bölgesi tam adı olarak ayarlar. Varsayılan tam ad, form VSTO bölge adına noktayla bağlı olan eklentinin adıdır( örneğin, `OutlookAddIn1.FormRegion1` ).<br /><br /> Bu tam ad, form bölgesi fabrika sınıfının en üstünde bir öznitelik olarak da görünür.<br /><br /> Form `Microsoft.Office.Tools.Outlook.FormRegionName` bölgelerini tüm veri kaynaklarında benzersiz olarak tanımlamak için özniteliğini Outlook VSTO kullanın. Form bölgesi öğesini yeniden kullanarak `Microsoft.Office.Tools.Outlook.FormRegionName` veya özelliğini değiştirerek özniteliğin değerini <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> değiştiremezsiniz. Bu adı değiştirmek için form bölgesi `Microsoft.Office.Tools.Outlook.FormRegionName` kod dosyasında özniteliğini değiştirmeniz gerekir.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> Form bölgesi devralmayı devre dışı bırakma
 Varsayılan olarak, özel bir ileti sınıfı temel ileti sınıfının tüm form bölgesi ilişkilendirmelerini devralınır. Örneğin, adlı bir ileti `IPM.Task.Contoso` sınıfı, 'den türetildi. `IPM.Task` Bu `IPM.Task.Contoso` nedenle, form bölgesi ilişkilendirmelerini `IPM.Task` devralr.

 Form bölgesi türetilen ileti sınıfları ile ilişkilendirilsin istemiyorsanız, form bölgesi özelliğini <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> true olarak **ayarlayın.** Örneğin, bir bitişik form bölgesi ile ilişkilendirmek ve özelliğini true olarak ayarlamak, form bölgesi yalnızca standart bir görev formunun `IPM.Task` <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> alt bölümüne eklenir.  Form bölgesi, standart bir görev formunun özelleştirilmiş sürümlerinin altına eklanmaz.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> Türleri ve ileti sınıfı adlarını anlama
 Bir öğenin Outlook adı, bir öğenin ileti sınıfı Outlook farklıdır. Örneğin, bir RSS öğesinin tür adı `Microsoft.Office.Interop.Outlook.PostItem` olur. Rss öğesinin ileti sınıfı adı: `IPM.Post.RSS` .

 Kodda bir öğenin türüne Outlook adını kullanın. Tür adlarının listesi için [bkz. Form bölgelerini bir form Outlook sınıfıyla ilişkilendirme.](../vsto/associating-a-form-region-with-an-outlook-message-class.md)

 Öğeyi form bölgesiyle ilişkilendirmek Outlook **Yeni** Outlook Form Bölgesi sihirbazında yer alan yeni öğe öğelerinin ileti sınıfı adını kullanın. Geçerli ileti sınıfı adlarının listesi için bkz. Form bölgelerini bir form [Outlook ile ilişkilendirme.](../vsto/associating-a-form-region-with-an-outlook-message-class.md)

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> Okuma Bölmesi için bitişik form bölgeleri tasarlama
 Öğeyi açmadan Outlook bir öğenin önizlemesini Outlook Okuma Bölmesi'ni kullanabilirsiniz. Okuma Bölmesi yalnızca okumak için tasarlanmıştır. Bu nedenle, metin kutusu gibi bitişik bir form bölgesi için ekley istediğiniz giriş denetimleri, Okuma Bölmesinde öğe ve form bölgesi açık olduğunda beklendiği gibi davranmayabilirsiniz.

 Örneğin, bitişik form bölgesi olan bir öğe Okuma Bölmesi'nde açıksa aşağıdaki durum mümkündür:

1. Form bölgesinde yer alan bir metin kutusunda metin seçin.

2. **Sil'e basın.**

3. Metin kutusunda metin yerine posta öğesinin tamamı silinir.

   Giriş denetimleri içeren bir bitişik form bölgesi tasarıyorsanız, düzgün çalışmalarını sağlamak için Okuma Bölmesi'nde denetimleri test edin. Beklendiği gibi davranan denetimleri devre dışı bırakan özel kod eklemeyi göz önünde bulundurabilirsiniz.

   Alternatif olarak, form bölgesi <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> özelliğini **False** olarak da ayarlayın. Bu şekilde form bölgesi Okuma Bölmesinde kullanılamaz.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> En uygun simge boyutlarını kullanma
 Özellikler penceresinin Simgeler özellik grubunda simge özelliklerini ayarerek form bölgesinden **hangi** simgelerin görüntülemelerini **istediğinize bakabilirsiniz.** En iyi görsel kalitesini elde etmek için aşağıdaki yönergeleri kullanın:

- Sayfa **simgesi için** Taşınabilir Ağ Grafikleri (PNG) dosyası kullanın.

- **Pencere** simgeleri 32 piksel ile 32 piksel olmalıdır.

- Diğer tüm simgeler 16 piksel ile 16 piksel olmalıdır.

  **Ayrı,** değiştirme veya tüm form bölgelerini değiştirme öğeleri için Bir Denetçinin Şeridinde Sayfa simgesi görünür.

  Pencere **simgesi** bildirim alanında ve Değiştirme veya tüm form bölgelerini değiştir seçeneğinin görüntüleniyor olduğu açık öğeler için **Alt** Sekme iletişim +  kutusunda görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Nasıl yapılanlar: Eklenti projesine Outlook bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Form bölgelerini bir form Outlook ile ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
