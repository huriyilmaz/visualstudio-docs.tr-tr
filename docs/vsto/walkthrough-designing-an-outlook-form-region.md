---
title: 'izlenecek yol: Outlook form bölgesi tasarlama'
description: bir kişi öğesinin ınspector penceresinde yeni bir sayfa olarak görünen özel bir Microsoft Outlook form bölgesini nasıl tasarlayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a230d5998a71cf9830fec9731aa825a612c9cfb82d779f796c6c108385e33462
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267409"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>izlenecek yol: Outlook form bölgesi tasarlama
  özel form bölgeleri, standart veya özel Microsoft Office Outlook formlarını genişletir. Bu kılavuzda, bir kişi öğesinin Inspector penceresinde yeni bir sayfa olarak görünen özel bir form bölgesi tasarlayacaksınız. bu form bölgesi, adres bilgilerini Windows canlı yerel arama Web sitesine göndererek, iletişim için listelenen her bir adresin haritasını görüntüler. form bölgeleri hakkında daha fazla bilgi için bkz. [Create Outlook form region](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- yeni bir Outlook VSTO eklenti projesi oluşturma.

- VSTO eklentisi projesine form bölgesi ekleme.

- Form bölgesinin yerleşimini tasarlama.

- Form bölgesinin davranışını özelleştirme.

- Outlook form bölgesini test etme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] veya daha yeni.

  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantısı") bu konunun video sürümü için bkz. [video nasıl yapılır: Outlook form bölgesi tasarlama](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>yeni bir Outlook VSTO eklenti projesi oluşturma
 ilk olarak temel bir VSTO eklentisi projesi oluşturun.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>yeni bir Outlook VSTO eklenti projesi oluşturmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **mapıtaddın** adlı bir Outlook VSTO eklenti projesi oluşturun.

2. **yeni Project** iletişim kutusunda **çözüm için dizin oluştur**' u seçin.

3. Projeyi herhangi bir dizine kaydedin.

     daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO eklenti projesine form bölgesi ekleme
 bir Outlook VSTO eklenti çözümü, bir veya daha fazla Outlook form bölgesi öğesi içerebilir. **yeni Outlook form bölgesi** sihirbazı 'nı kullanarak projenize bir form bölgesi öğesi ekleyin.

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO eklenti projesine form bölgesi eklemek için

1. **Çözüm Gezgini**, **MapItAddIn** projesini seçin.

2. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

3. **yeni öğe ekle** iletişim kutusunda, **Outlook Form bölgesi**' ni seçin, dosyayı **mapıt** olarak adlandırın ve **ekle**' ye tıklayın.

     **Newoutlook form bölgesi** Sihirbazı başlar.

4. **Form bölgesini nasıl oluşturmak Istediğinizi seçin** sayfasında **Yeni bir form bölgesi Tasarla**' ya tıklayın ve ardından **İleri**' ye tıklayın.

5. Oluşturmak istediğiniz **form bölgesinin türünü seçin** sayfasında, **ayrı**' ı tıklatın ve ardından **İleri**' yi tıklatın.

     *ayrı* bir form bölgesi Outlook forma yeni bir sayfa ekler. form bölgesi türleri hakkında daha fazla bilgi için bkz. [Create Outlook form](../vsto/creating-outlook-form-regions.md)region.

6. **Açıklayıcı metin sağlayın ve görüntüleme tercihlerini seçin** sayfasında, **ad** kutusuna **map** yazın.

     Bu ad, kişi öğesi açık olduğunda Inspector penceresinin şeridinde görüntülenir.

7. Yazma modunda olan **Inspectors** ve **okuma modundaki** **denetçiler**' i seçin ve ardından İleri ' ye tıklayın.

8. **Bu form bölgesini görüntüleyecek ileti sınıflarını belirleyin** sayfasında, **posta Iletisini** temizleyin, **iletişim**' i seçin ve ardından **son**' a tıklayın.

     Bir *mapit. cs* veya *mapit. vb* dosyası projenize eklenir.

## <a name="design-the-layout-of-the-form-region"></a>Form bölgesinin yerleşimini tasarlama
 Form *bölgesi tasarımcısını* kullanarak form bölgelerini görsel olarak geliştirin. Yönetilen denetimleri form bölgesi tasarımcı yüzeyine sürükleyebilirsiniz. Denetim düzeni ve görünümünü ayarlamak için tasarımcı ve **Özellikler** penceresini kullanın.

### <a name="to-design-the-layout-of-the-form-region"></a>Form bölgesinin yerleşimini tasarlamak için

1. **Çözüm Gezgini**, **MapItAddIn** projesini genişletin ve ardından form bölgesi tasarımcısını açmak için *mapit. cs* veya *mapit. vb* öğesine çift tıklayın.

2. Tasarımcı öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Özellikler** penceresinde, **boyutu** **664, 469** olarak ayarlayın.

     Bu, form bölgesinin bir Haritayı görüntülemesi için yeterince büyük olacağını sağlar.

4. **Görünüm** menüsünde **araç kutusu**' na tıklayın.

5. **Araç kutusunun** **ortak denetimler** sekmesinden form bölgesine bir **WebBrowser** ekleyin.

     **WebBrowser** , iletişim için listelenen her bir adresin haritasını görüntüler.

## <a name="customize-the-behavior-of-the-form-region"></a>Form bölgesinin davranışını özelleştirme
 Form bölgesinin çalışma zamanında davranış şeklini özelleştirmek için form bölgesine olay işleyicilerine kod ekleyin. bu form bölgesi için kod, bir Outlook öğesinin özelliklerini inceler ve Map ıt form bölgesinin görüntülenip görüntülenmeyeceğini belirler. form bölgesini görüntülüyorsa, kod canlı yerel arama Windows gider ve Outlook kişi öğesinde listelenen her adresin haritasını yükler.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Form bölgesinin davranışını özelleştirmek için

1. **Çözüm Gezgini**, *mapit. cs* veya *mapit. vb* öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

    *Mapit. cs* veya *mapit. vb* , kod düzenleyicisinde açılır.

2. **Form bölgesi fabrikası** kod bölgesini genişletin.

    Adlı form bölgesi fabrikası sınıfı `MapItFactory` sunulur.

3. Olay işleyicisine aşağıdaki kodu ekleyin `MapItFactory_FormRegionInitializing` . Bu olay işleyicisi, Kullanıcı bir kişi öğesi açtığında çağrılır. Aşağıdaki kod, kişi öğesinin bir adres içerip içermediğini belirler. Kişi öğesi bir adres içermiyorsa, bu kod <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> sınıfın özelliğini **true** olarak ayarlar ve form bölgesi görüntülenmez. aksi takdirde, VSTO eklentisi <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> olayı oluşturur ve form bölgesini görüntüler.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::

4. Olay işleyicisine aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> . Bu kod aşağıdaki görevleri gerçekleştirir:

   - Kişi öğesindeki her adresi birleştirir ve bir URL dizesi oluşturur.

   - <xref:System.Windows.Forms.WebBrowser.Navigate%2A>Nesnesinin yöntemini çağırır <xref:System.Windows.Forms.WebBrowser> ve URL dizesini parametre olarak geçirir.

     Yerel arama Web sitesi Map It form bölgesinde görünür ve her adresi karalama panelinde sunar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet2":::

## <a name="test-the-outlook-form-region"></a>Outlook form bölgesini Test etme
 projeyi çalıştırdığınızda, Visual Studio Outlook açılır. Map It form bölgesini görüntülemek için bir kişi öğesi açın. Map It form bölgesi, adresi içeren herhangi bir kişi öğesi formunda bir sayfa olarak görünür.

### <a name="to-test-the-map-it-form-region"></a>Map It form bölgesini test etmek için

1. Projeyi çalıştırmak için **F5** tuşuna basın.

     Outlook açılır.

2. Outlook **giriş** sekmesinde, **yeni öğeler**' e ve ardından **iletişim**' e tıklayın.

3. Kişi formunda, iletişim adı olarak **Ann beeyazın** ve ardından aşağıdaki üç adresi belirtin.

    |Adres Türü|Adres|
    |------------------|-------------|
    |**İş**|**4567 Main St. Buffalo, NY**|
    |**Giriş Ekranı**|**1234 Kuzey St. Buffalo, NY**|
    |**Diğer**|**3456 Main St. Seattle, WA**|

4. Kişi öğesini kaydedin ve kapatın.

5. **Ann beeto** kişi öğesini yeniden açın.

    Outlook, bu, kişiler için adres defterini açarak **bul** grubunda yapılabilir ya da Ann bee, **arama insanları** içine olmalıdır.

6. Öğenin şerit 'inin **göster** grubunda, Map It form bölgesini açmak Için **Haritayı eşle** ' ye tıklayın.

     Map It form bölgesi görünür ve yerel arama Web sitesini görüntüler. **İş**, **giriş** ve **diğer** adresler karalama panelinde görüntülenir. Karalama panelinde, eşlemek istediğiniz bir adres seçin.

## <a name="next-steps"></a>Sonraki adımlar
 Bir uygulamanın kullanıcı arabirimini özelleştirme hakkında daha fazla Outlook şu konulardan öğrenebilirsiniz:

- Bir öğenin şeridini özelleştirme hakkında bilgi Outlook için [bkz.](../vsto/customizing-a-ribbon-for-outlook.md)Outlook.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Form bölgelerini Outlook yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Adım adım kılavuz: Veri kaynağında tasarlanmış bir form Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Nasıl yapılanlar: Eklenti projesine Outlook bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Form bölgelerini bir form Outlook ile ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Form bölgelerinde Outlook eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
- [Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
