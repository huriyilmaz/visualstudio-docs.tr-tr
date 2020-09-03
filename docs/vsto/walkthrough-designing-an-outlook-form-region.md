---
title: 'İzlenecek yol: Outlook form bölgesi tasarlama'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01cfe55964a1d61c2ad200c9538ced9ff0aa5599
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985464"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>İzlenecek yol: Outlook form bölgesi tasarlama
  Özel form bölgeleri, standart veya özel Microsoft Office Outlook formlarını genişletir. Bu kılavuzda, bir kişi öğesinin Inspector penceresinde yeni bir sayfa olarak görünen özel bir form bölgesi tasarlayacaksınız. Bu form bölgesi, adres bilgilerini Windows Live Yerel arama Web sitesine göndererek, iletişim için listelenen her bir adresin haritasını görüntüler. Form bölgeleri hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Yeni bir Outlook VSTO eklentisi projesi oluşturma.

- VSTO eklentisi projesine form bölgesi ekleme.

- Form bölgesinin yerleşimini tasarlama.

- Form bölgesinin davranışını özelleştirme.

- Outlook form bölgesini test etme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] veya daha yeni.

  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantısı") Bu konunun video sürümü için bkz. [video nasıl yapılır: Outlook form bölgesi tasarlama](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklentisi projesi oluşturma
 Önce temel bir VSTO eklenti projesi oluşturun.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklentisi projesi oluşturmak için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **MapItAddIn**ADLı bir Outlook VSTO eklentisi projesi oluşturun.

2. **Yeni proje** iletişim kutusunda, **çözüm için dizin oluştur**' u seçin.

3. Projeyi herhangi bir dizine kaydedin.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO eklentisi projesine form bölgesi ekleme
 Outlook VSTO eklentisi çözümü, bir veya daha fazla Outlook form bölgesi öğesi içerebilir. **Yeni Outlook form bölgesi** Sihirbazı 'nı kullanarak projenize bir form bölgesi öğesi ekleyin.

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO eklentisi projesine form bölgesi eklemek için

1. **Çözüm Gezgini**, **MapItAddIn** projesini seçin.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** Iletişim kutusunda **Outlook form bölgesi**' ni seçin, dosyayı **MapIt**olarak adlandırın ve **Ekle**' ye tıklayın.

     **Newoutlook form bölgesi** Sihirbazı başlar.

4. **Form bölgesini nasıl oluşturmak Istediğinizi seçin** sayfasında **Yeni bir form bölgesi Tasarla**' ya tıklayın ve ardından **İleri**' ye tıklayın.

5. Oluşturmak istediğiniz **form bölgesinin türünü seçin** sayfasında, **ayrı**' ı tıklatın ve ardından **İleri**' yi tıklatın.

     *Ayrı* bir form bölgesi Outlook formuna yeni bir sayfa ekler. Form bölgesi türleri hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

6. **Açıklayıcı metin sağlayın ve görüntüleme tercihlerini seçin** sayfasında, **ad** kutusuna **map** yazın.

     Bu ad, kişi öğesi açık olduğunda Inspector penceresinin şeridinde görüntülenir.

7. Yazma modunda olan **Inspectors** ve **okuma modundaki** **denetçiler**' i seçin ve ardından İleri ' ye tıklayın.

8. **Bu form bölgesini görüntüleyecek ileti sınıflarını belirleyin** sayfasında, **posta Iletisini**temizleyin, **iletişim**' i seçin ve ardından **son**' a tıklayın.

     Projenize bir *MapIt.cs* veya *mapit. vb* dosyası eklenir.

## <a name="design-the-layout-of-the-form-region"></a>Form bölgesinin yerleşimini tasarlama
 Form *bölgesi tasarımcısını*kullanarak form bölgelerini görsel olarak geliştirin. Yönetilen denetimleri form bölgesi tasarımcı yüzeyine sürükleyebilirsiniz. Denetim düzeni ve görünümünü ayarlamak için tasarımcı ve **Özellikler** penceresini kullanın.

### <a name="to-design-the-layout-of-the-form-region"></a>Form bölgesinin yerleşimini tasarlamak için

1. **Çözüm Gezgini**, **MapItAddIn** projesini genişletin ve ardından form bölgesi tasarımcısını açmak Için *MapIt.cs* veya *mapit. vb* öğesine çift tıklayın.

2. Tasarımcı öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

3. **Özellikler** penceresinde, **boyutu** **664, 469**olarak ayarlayın.

     Bu, form bölgesinin bir Haritayı görüntülemesi için yeterince büyük olacağını sağlar.

4. **Görünüm** menüsünde **araç kutusu**' na tıklayın.

5. **Araç kutusunun** **ortak denetimler** sekmesinden form bölgesine bir **WebBrowser** ekleyin.

     **WebBrowser** , iletişim için listelenen her bir adresin haritasını görüntüler.

## <a name="customize-the-behavior-of-the-form-region"></a>Form bölgesinin davranışını özelleştirme
 Form bölgesinin çalışma zamanında davranış şeklini özelleştirmek için form bölgesine olay işleyicilerine kod ekleyin. Bu form bölgesi için, kod bir Outlook öğesinin özelliklerini inceler ve Map It form bölgesinin görüntülenip görüntülenmeyeceğini belirler. Form bölgesini görüntülüyorsa, kod Windows Live Yerel arama 'ya gider ve Outlook kişi öğesinde listelenen her adresin haritasını yükler.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Form bölgesinin davranışını özelleştirmek için

1. **Çözüm Gezgini**, *MapIt.cs* veya *mapit. vb*öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

    *MapIt.cs* veya *mapit. vb* , kod düzenleyicisinde açılır.

2. **Form bölgesi fabrikası** kod bölgesini genişletin.

    Adlı form bölgesi fabrikası sınıfı `MapItFactory` sunulur.

3. Olay işleyicisine aşağıdaki kodu ekleyin `MapItFactory_FormRegionInitializing` . Bu olay işleyicisi, Kullanıcı bir kişi öğesi açtığında çağrılır. Aşağıdaki kod, kişi öğesinin bir adres içerip içermediğini belirler. Kişi öğesi bir adres içermiyorsa, bu kod <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> sınıfın özelliğini **true** olarak ayarlar ve form bölgesi görüntülenmez. Aksi halde, VSTO eklentisi <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> olayı oluşturur ve form bölgesini görüntüler.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Olay işleyicisine aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> . Bu kod aşağıdaki görevleri gerçekleştirir:

   - Kişi öğesindeki her adresi birleştirir ve bir URL dizesi oluşturur.

   - <xref:System.Windows.Forms.WebBrowser.Navigate%2A>Nesnesinin yöntemini çağırır <xref:System.Windows.Forms.WebBrowser> ve URL dizesini parametre olarak geçirir.

     Yerel arama Web sitesi Map It form bölgesinde görünür ve her adresi karalama panelinde sunar.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Outlook form bölgesini test etme
 Projeyi çalıştırdığınızda, Visual Studio Outlook 'U açar. Map It form bölgesini görüntülemek için bir kişi öğesi açın. Map It form bölgesi, adresi içeren herhangi bir kişi öğesi formunda bir sayfa olarak görünür.

### <a name="to-test-the-map-it-form-region"></a>Map It form bölgesini test etmek için

1. Projeyi çalıştırmak için **F5** tuşuna basın.

     Outlook açılır.

2. Outlook 'ta **giriş** sekmesinde **yeni öğeler**' e ve ardından **iletişim**' e tıklayın.

3. Kişi formunda, iletişim adı olarak **Ann beeyazın** ve ardından aşağıdaki üç adresi belirtin.

    |Adres Türü|Adres|
    |------------------|-------------|
    |**İş**|**4567 Main St. Buffalo, NY**|
    |**Giriş**|**1234 Kuzey St. Buffalo, NY**|
    |**Diğer**|**3456 Main St. Seattle, WA**|

4. Kişi öğesini kaydedin ve kapatın.

5. **Ann beeto** kişi öğesini yeniden açın.

    Outlook 'ta, bu, kişiler için adres defterini açarak **bul** grubunda yapılabilir veya Ann Bee, **arama kişilere**da girebilir.

6. Öğenin şerit 'inin **göster** grubunda, Map It form bölgesini açmak Için **Haritayı eşle** ' ye tıklayın.

     Map It form bölgesi görünür ve yerel arama Web sitesini görüntüler. **İş**, **giriş**ve **diğer** adresler karalama panelinde görüntülenir. Karalama panelinde, eşlemek istediğiniz bir adres seçin.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan bir Outlook uygulamasının Kullanıcı arabirimini nasıl özelleştireceğiniz hakkında daha fazla bilgi edinebilirsiniz:

- Outlook öğesinin şeritlerini nasıl özelleştireceğiniz hakkında bilgi edinmek için bkz. [Outlook için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
- [Nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
