---
title: 'Adım adım kılavuz: Form Outlook tasarlama'
description: Bir kişi öğesinin Denetçi penceresinde Outlook sayfa olarak görünen özel bir Microsoft Outlook form bölgesi tasarlamayı öğrenin.
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
ms.openlocfilehash: 2ae0560f34e7cd303aeee3e9f7d8a82d23d68e14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147550"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Adım adım kılavuz: Form Outlook tasarlama
  Özel form bölgeleri standart veya özel formların Microsoft Office Outlook genişletmektedir. Bu kılavuzda, bir kişi öğesinin Denetçi penceresinde yeni sayfa olarak görünen özel bir form bölgesi tasarlayabilirsiniz. Bu form bölgesi, adres bilgilerini Canlı Yerel Arama Web sitesine göndererek kişi için listelenen her Windows bir harita görüntüler. Form bölgeleri hakkında bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Yeni bir Outlook VSTO projesi oluşturma.

- VSTO Add-in projesine form bölgesi ekleme.

- Form bölgesi düzenini tasarlama.

- Form bölgesi davranışını özelleştirme.

- Form Outlook test etme.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] veya daha yeni bir sürüm.

  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantısı") Bu konu başlığında video sürümü için bkz. Video ile ilgili nasıl Outlook [tasarımı.](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90))

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO Eklenti projesi oluşturma
 İlk olarak Eklenti VSTO temel bir uygulama oluşturun.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Yeni bir eklenti Outlook VSTO oluşturmak için

1. içinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **MapItAddIn** Outlook VSTO bir Eklenti projesi oluşturun.

2. Yeni uygulama **Project** kutusunda Çözüm için dizin **oluştur'a tıklayın.**

3. Projeyi herhangi bir dizine kaydedin.

     Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO Add-in projesine form bölgesi ekleme
 Bir Outlook VSTO eklenti çözümü, form bölgesi öğeleri için bir Outlook veya daha fazla örnek içerebilir. Yeni Form Bölgesi sihirbazını kullanarak projenize **bir form Outlook öğesi** ekleyin.

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Outlook VSTO Add-in projesine form bölgesi eklemek için

1. Bu **Çözüm Gezgini** **MapItAddIn projesini** seçin.

2. Yeni **Project** Ekle'ye **tıklayın.**

3. Yeni Öğe **Ekle iletişim kutusunda** Form Bölgesi'Outlook **seçin,** **dosyaya MapIt** adını ve ardından Ekle'ye **tıklayın.**

     **NewOutlook Form Bölgesi** sihirbazı başlatılır.

4. Form **bölgesi oluşturmak istediğiniz şekli seçin sayfasında** Yeni bir form bölgesi tasarla'ya ve ardından Sonraki'ye **tıklayın.**

5. Oluşturmak **istediğiniz form bölgesi türünü seçin sayfasında, Ayır'a** ve **ardından** Sonraki'ye **tıklayın.**

     Ayrı *bir* form bölgesi, bir form için yeni Outlook ekler. Form bölgesi türleri hakkında daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

6. Açıklayıcı **metin girin ve görüntüleme tercihlerinizi seçin** sayfasında Ad **kutusuna Bunu Eşle** **yazın.**

     Bu ad, kişi öğesi açıkken Denetçi penceresinin Şeridinde görünür.

7. Oluşturma **modundaki Denetçiler'i ve okuma** **modundaki Denetçiler'i seçin ve** ardından Sonraki 'ye **tıklayın.**

8. Bu **form bölgesi görüntüecek ileti sınıflarını** tanımla sayfasında Posta İletisi'nin temizlerini **silin,** İletişim'i **seçin** ve ardından Son'a **tıklayın.**

     Projenize *bir MapIt.cs* *veya MapIt.vb* dosyası eklenir.

## <a name="design-the-layout-of-the-form-region"></a>Form bölgesi düzenini tasarlama
 Form bölgesi tasarımcısını kullanarak form *bölgelerini görsel olarak geliştirin.* Yönetilen denetimleri form bölgesi tasarımcı yüzeyine sürükleyebilirsiniz. Tasarımcıyı ve Özellikler **penceresini kullanarak** denetim düzenini ve görünümünü ayarlayın.

### <a name="to-design-the-layout-of-the-form-region"></a>Form bölgesi düzenini tasarlamak için

1. Bu **Çözüm Gezgini** **MapItAddIn** projesini genişletin ve Ardından *MapIt.cs veya MapIt.vb'ye* çift tıklar *ve* Form Bölgesi Tasarımcısını açın.

2. Tasarımcıya sağ tıklayın ve ardından Özellikler'e **tıklayın.**

3. Özellikler penceresinde **Boyut'un** **664, 469 olarak ayarlayın.** 

     Bu, form bölgesi bir haritayı görüntülemek için yeterince büyük olacak şekilde sağlar.

4. Görünüm menüsünde **Araç** **Kutusu'na tıklayın.**

5. Araç **Kutusunun Ortak** Denetimler **sekmesinden,** form **bölgesi için bir WebBrowser** ekleyin.

     **WebBrowser** kişi için listelenen her adresin bir haritasını görüntüler.

## <a name="customize-the-behavior-of-the-form-region"></a>Form bölgesi davranışını özelleştirme
 Form bölgesi olay işleyicileri için bir form bölgesi çalışma zamanında nasıl davranacağını özelleştirmek için kod ekleyin. Bu form bölgesi için kod, bir Outlook öğesinin özelliklerini inceler ve Map It form bölgelerinin görüntülendiğinden belirler. Form bölgesi görüntülenmiyorsa, kod Canlı Windows Arama'ya gidin ve ilgili kişi öğesinde listelenen her adresin Outlook yükler.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Form bölgesi davranışını özelleştirmek için

1. Bu **Çözüm Gezgini** *MapIt.cs veya MapIt.vb'ye* sağ *tıklayın* ve ardından Kodu **Görüntüle'ye tıklayın.**

    *MapIt.cs* veya *MapIt.vb,* Kod Düzenleyicisi'nde açılır.

2. Form Bölgesi **Fabrika kod** bölgesini genişletin.

    adlı form bölgesi fabrika `MapItFactory` sınıfı açığa çıkar.

3. Olay işleyiciye aşağıdaki `MapItFactory_FormRegionInitializing` kodu ekleyin. Kullanıcı bir kişi öğesi açtığında bu olay işleyicisi çağrılır. Aşağıdaki kod, kişi öğesinin bir adres içerdiğini belirler. Kişi öğesi bir adres içeriyorsa, bu kod sınıfın özelliğini true olarak <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> ayarlar ve form bölgesi <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> görüntülenmez.  Aksi takdirde VSTO eklenti olayı ve <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> form bölgelerini görüntüler.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::

4. Olay işleyiciye aşağıdaki <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> kodu ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Kişi öğesinde her adresi bir oluşturur ve bir URL dizesi oluşturur.

   - nesnesinin <xref:System.Windows.Forms.WebBrowser.Navigate%2A> yöntemini <xref:System.Windows.Forms.WebBrowser> çağırarak URL dizesini parametre olarak iletir.

     Yerel Arama Web sitesi Harita Bu form bölgesinde görünür ve her adresi karalama paneli içinde gösterir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet2":::

## <a name="test-the-outlook-form-region"></a>Form Outlook test
 Projeyi çalıştırarak Visual Studio Outlook. Eşle form bölgelerini görüntülemek için bir kişi öğesi açın. Harita Bu form bölgesi, adres içeren herhangi bir kişi öğesi şeklinde bir sayfa olarak görünür.

### <a name="to-test-the-map-it-form-region"></a>Harita Oluşturma form bölgelerini test etmek için

1. Projeyi **çalıştırmak için F5** tuşuna basın.

     Outlook açılır.

2. Bu Outlook, Giriş **sekmesinde Yeni** Öğeler'e **ve ardından** kişi'ye **tıklayın.**

3. Kişi formuna kişi adı **olarak Ann Be belirli** bir ad yazın ve ardından aşağıdaki üç adresi belirtin.

    |Adres Türü|Adres|
    |------------------|-------------|
    |**İş**|**4567 Main St. Ny, NY**|
    |**Giriş Ekranı**|**1234 North St. Ny, NY**|
    |**Diğer**|**3456 Main St. Seattle, WA**|

4. Kişi öğesini kaydedin ve kapatın.

5. **Ann Betab kişi öğesini** yeniden açın.

    Bu Outlook, Kişiler için Adres Defteri  açarak veya Kişi Ara'ya Ann Belop yazarak Bul **grubunda yapılabilir.**

6. Öğenin **Şeridinin** Göster grubunda Eşle'ye **tıklayın ve** Harita Bu form bölgesini açın.

     Harita Bu form bölgesi görüntülenir ve Yerel Arama Web sitesi görüntülenir. **İş,** **Giriş** ve Diğer **adresler,** karalama panelinin içinde görünür. Karalama panelinin eşlemek istediğiniz adresini seçin.

## <a name="next-steps"></a>Sonraki adımlar
 Bir uygulamanın kullanıcı arabirimini özelleştirme hakkında daha fazla Outlook şu konulardan öğrenebilirsiniz:

- Bir öğenin şeridini özelleştirme hakkında bilgi edinmek Outlook için bkz. Bir şeridi [Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Form bölgelerini Outlook yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Adım adım kılavuz: Veri kaynağında tasarlanmış bir form Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Nasıl yapılanlar: Eklenti projesine Outlook bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Form bölgelerini bir form Outlook ile ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Form bölgelerinde Outlook eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
- [Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
