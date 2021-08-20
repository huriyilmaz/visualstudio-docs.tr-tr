---
title: "İzlenecek yol: Outlook ' de tasarlanan form bölgesini Içeri aktarma"
description: Microsoft Outlook 'de form bölgesi tasarlamayı öğrenin ve ardından yeni form bölgesi sihirbazı 'nı kullanarak form bölgesini bir Outlook VSTO eklentisi projesine içeri aktarın.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6182f28e8f18689caf38ca581bf84df26cfe0ce3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068510"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>İzlenecek yol: Outlook ' de tasarlanan form bölgesini Içeri aktarma
  bu izlenecek yol, Microsoft Office Outlook bir form bölgesinin nasıl tasarlanacağını ve sonra **yeni form bölgesi** sihirbazı 'nı kullanarak form bölgesini bir Outlook VSTO eklentisi projesine aktarmayı gösterir. Outlook form bölgesini tasarlamak Outlook verilerine bağlanan form bölgesine yerel Outlook denetimleri eklemenizi olanaklı kılar. Form bölgesini içeri aktardıktan sonra her bir denetimin olaylarını işleyebilirsiniz.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Outlook 'de form bölgesi tasarımcısını kullanarak form bölgesi tasarlama.

- form bölgesini Outlook VSTO eklenti projesine aktarma.

- Form bölgesindeki denetimlerin olaylarını işleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] veya [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Outlook 'de form bölgesi tasarımcısını kullanarak form bölgesi tasarlama
 Bu adımda Outlook bir form bölgesi tasarlayacaksınız. Daha sonra formu içine aktarabilmeniz için form bölgesini kolay bulunacak bir konuma kaydedin [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Bu örnek form bölgesi, normal görev formunun tamamen yerini alır. Ana görev gerçekleştirilmeden önce tamamlanması gereken tüm görevlerin ilerlemesini izlemek için bir yol sağlar (önkoşul görevleri). Form bölgesi, önkoşul görevlerinin bir listesini görüntüler ve listedeki her görevin tamamlanma durumunu gösterir. Kullanıcılar listeye görev ekleyebilir ve bunları kaldırabilir. Ayrıca, her görevin tamamlanma durumunu yenileyebilirler.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Outlook 'de form bölgesi tasarımcısını kullanarak form bölgesi tasarlamak için

1. Microsoft Office Outlook başlatın.

2. Outlook, **geliştirici** sekmesinde **Form tasarla**' ya tıklayın. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. **Tasarım formu** kutusunda **görev**' i ve sonra **Aç**' ı tıklatın.

4. Outlook, **geliştirici** sekmesinde, **tasarım** grubunda, **yeni Form bölgesi**' ne tıklayın.

     Yeni bir form bölgesi açılır. **Alan Seçicisi** görünmezse, **Araçlar** grubunda **alan Seçicisi** ' ne tıklayın.

5. **Konu** alanını ve **Tamamlanma yüzdesi** alanını **alan seçicinden** form bölgesine sürükleyin.

6. **Araç** kutusunu açmak için **Araçlar** grubunda **Denetim araç kutusu** ' na tıklayın.

7. **Araç kutusundan** bir etiketi form bölgesine sürükleyin. Etiketi **konunun** altına ve **Tamamlanma yüzdesi** alanlarının altına yerleştirin.

8. Etikete sağ tıklayın ve ardından **Gelişmiş Özellikler**' e tıklayın.

9. **Özellikler** penceresinde, **başlık** özelliğini bu görev olarak ayarlayın, **aşağıdaki görevlere bağlıdır**, **Width** özelliğini **200** olarak ayarlayın ve **Uygula**' ya tıklayın.

10. **Araç kutusu** ' ndan form bölgesine bir ListBox denetimi sürükleyin. Liste kutusunun bu görevin altına konumu **aşağıdaki görevler etiketine bağlıdır** .

11. Yeni eklediğiniz liste kutusunu seçin.

12. **Özellikler** penceresinde, **genişliği** **300** olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

13. **Araç kutusundan** bir etiketi form bölgesine sürükleyin. Etiketi liste kutusunun altına konumlandırın.

14. Yeni eklediğiniz etiketi seçin.

15. **Özellikler** penceresinde, **başlık** özelliğini, **Bağımlı görevler listesine eklenecek bir görevi seçmek** için ayarlayın, **Width** özelliğini **200** olarak ayarlayın ve **Uygula**' ya tıklayın.

16. **Araç kutusu** ' ndan form bölgesine bir ComboBox denetimi sürükleyin. **Bağımlı görevler etiketi listesine eklemek için bir görev seçin ' in** altındaki açılan kutuyu konumlandırın.

17. Yeni eklediğiniz Birleşik giriş kutusunu seçin.

18. **Özellikler** penceresinde, **Width** özelliğini **300** olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

19. **Araç kutusundan** bir CommandButton denetimini form bölgesine sürükleyin. Açılan kutunun yanındaki komut düğmesini konumlandırın.

20. Yeni eklediğiniz komut düğmesini seçin.

21. **Özellikler** penceresinde, **adı** **AddDependentTask** olarak ayarlayın, alt **yazı başlığını** **bağımlı görev eklemek** için ayarlayın, **genişliği** **100** olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

22. **Alan Seçicisi**' nde **Yeni**' ye tıklayın.

23. **Yeni alan** Iletişim kutusunda **ad** alanına **HiddenField** yazın ve ardından **Tamam**' a tıklayın.

24. **Alan seçicinden** **HiddenField** alanını form bölgesine sürükleyin.

25. **Özellikler** penceresinde, **Visible** ' ı **0-false** olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

26. Outlook, **geliştirici** sekmesinde, **tasarım** grubunda, **kaydet** düğmesine tıklayın ve ardından **Form bölgesini farklı kaydet**' e tıklayın.

     Form bölgesini **TaskFormRegion** olarak adlandırın ve bilgisayarınızdaki yerel bir dizine kaydedin.

     Outlook form bölgesini Outlook form Depolama (*. ofs*) dosyası olarak kaydeder. Form bölgesi *TaskFormRegion. ofs* adıyla kaydedilir.

27. Çıkış Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>yeni bir Outlook eklentisi projesi oluşturma
 bu adımda, bir Outlook VSTO eklenti projesi oluşturacaksınız. Bu kılavuzda daha sonra, form bölgesini projeye aktaracaksınız.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>yeni bir Outlook VSTO eklenti projesi oluşturmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **taskaddin** adlı bir Outlook VSTO eklenti projesi oluşturun.

2. **yeni Project** iletişim kutusunda **çözüm için dizin oluştur**' u seçin.

3. Projeyi varsayılan proje dizinine kaydedin.

     daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Form bölgesini içeri aktarma
 **yeni Outlook form bölgesi** sihirbazı 'nı kullanarak, Outlook 'de tasarladığınız form bölgesini Outlook VSTO eklenti projesine aktarabilirsiniz.

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>form bölgesini Outlook VSTO eklenti projesine aktarmak için

1. **Çözüm Gezgini**, **taskaddin** projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.

2. **şablonlar** bölmesinde **Outlook Form bölgesi**' ni seçin, dosyayı **TaskFormRegion** olarak adlandırın ve **ekle**' ye tıklayın.

     **Newoutlook form bölgesi** Sihirbazı başlar.

3. **form bölgesini nasıl oluşturmak istediğinizi seçin** sayfasında, **Outlook form Depolama (. ofs) dosyasını içeri aktar**' a tıklayın ve sonra da **araştır**' a tıklayın.

4. **mevcut Outlook Form bölgesi dosya konumu** iletişim kutusunda, *taskformregion. ofs*'un konumuna gidin, **taskformregion. ofs**' ı seçin, **aç**' a tıklayın ve ardından **ileri**' ye tıklayın.

5. Oluşturmak istediğiniz **form bölgesinin türünü seçin** sayfasında, **Tümünü Değiştir**' e tıklayın ve ardından **İleri**' ye tıklayın.

     *replace-all* form bölgesi tüm Outlook formunu değiştirir. form bölgesi türleri hakkında daha fazla bilgi için bkz. [Create Outlook form](../vsto/creating-outlook-form-regions.md)region.

6. **Açıklayıcı metin girin ve görüntüleme tercihlerini seçin** sayfasında **İleri**' ye tıklayın.

7. **Bu form bölgesini görüntüleyecek ileti sınıflarını tanımla** sayfasında, **hangi özel ileti sınıflarında bu form bölgesini görüntüleyecek** ? alanına **IPM yazın. Task. TaskFormRegion** ve ardından **son**' a tıklayın.

     Projenize bir *TaskFormRegion. cs* veya *TaskFormRegion. vb* dosyası eklenir.

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Form bölgesindeki denetimlerin olaylarını işleme
 Artık projede form bölgesine sahip olduğunuza `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` göre, Outlook form bölgesine eklediğiniz düğmenin olayını işleyen kodu ekleyebilirsiniz.

 Ayrıca, form <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> bölgesi göründüğünde form bölgesindeki denetimleri güncelleştiren olaya kod ekleyin.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Form bölgesindeki denetimlerin olaylarını işlemek için

1. **Çözüm Gezgini**, *TaskFormRegion. cs* veya *TaskFormRegion. vb* öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

    Kod düzenleyicisinde *TaskFormRegion. cs* veya *TaskFormRegion. vb* açılır.

2. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. bu kod, form bölgesindeki birleşik giriş kutusunu, Outlook Tasks klasöründeki her görevin konu satırıyla doldurur.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet1":::

3. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - `Microsoft.Office.Interop.Outlook.TaskItem` `FindTaskBySubjectName` Yardımcı yöntemini çağırarak ve istenen görevin konusunu geçirerek Görevler klasörünü bulur. `FindTaskBySubjectName`Sonraki adımda yardımcı yöntemi ekleyeceksiniz.

   - `Microsoft.Office.Interop.Outlook.TaskItem.Subject` `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` Bağımlı görev liste kutusuna ve değerlerini ekler.

   - Görev konusunu form bölgesindeki gizli alana ekler. gizli alan bu değerleri Outlook öğenin bir parçası olarak depolar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet2":::

4. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. Bu kod, önceki adımda `FindTaskBySubjectName` açıklanan yardımcı yöntemi sağlar.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet3":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet3":::

5. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Form bölgesinde liste kutusunu her bağımlı görevin geçerli tamamlanma durumuyla yeniler.

   - Her bağımlı görevin konusunu almak için gizli metin alanını ayrıştırıyor. Ardından yardımcı yöntemini çağırarak ve her görevin konusunu geçerek Görevler `Microsoft.Office.Interop.Outlook.TaskItem`  `FindTaskBySubjectName` klasöründeki her birini yerini saptar.

   - bağımlı `Microsoft.Office.Interop.Outlook.TaskItem.Subject` görev `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` listesi kutusuna ve değerlerini ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet4":::

6. Olay `TaskFormRegion_FormRegionShowing` işleyicisini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Form bölgesi göründüğünde, form bölgesinde birleşik giriş kutusunu görev konularıyla doldurun.

   - Form `RefreshTaskListBox` bölgesi göründüğünde yardımcı yöntemini çağıran. Bu, öğe daha önce açıldığında liste kutusuna eklenen bağımlı görevleri görüntüler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet5":::

## <a name="test-the-outlook-form-region"></a>Form Outlook test etmek
 Form bölgelerini test etmek için, form bölgesinde önkoşul görevleri listesine görevler ekleyin. Bir önkoşul görevinin tamamlanma durumunu güncelleştirin ve ardından görevin güncelleştirilmiş tamamlanma durumunu önkoşul görev listesinde görüntüleniyor.

### <a name="to-test-the-form-region"></a>Form bölgelerini test etmek için

1. Projeyi **çalıştırmak için F5** tuşuna basın.

     Outlook başlar.

2. Bu Outlook, Giriş **sekmesinde Yeni** Öğeler'e **ve ardından** Görev'e **tıklayın.**

3. Görev formunda, Konu **alanına** Bağımlı **Görev** yazın.

4. Şeridin **Görev** sekmesinde, Eylemler grubunda **Kaydet'e** ve Kapat'& **tıklayın.**

5. Bu Outlook, Giriş **sekmesinde** Yeni Öğeler'e, Diğer **Öğeler'e** ve ardından Form **Seç'e tıklayın.**

6. Form Seç **iletişim kutusunda** **TaskFormRegion 'a ve** ardından Aç'a **tıklayın.**

     **TaskFormRegion** form bölgesi görüntülenir. Bu form, görev formunun tamamının yerini almaktadır. Bağımlı **görevler listesine eklemek için bir görev seçin** birleşik giriş kutusu Görevler klasöründeki diğer görevlerle doldurulur.

7. Görev formunda, Konu **alanına** Birincil Görev **yazın.**

8. Bağımlı görevler **listesine eklemek istediğiniz görevi** seçin birleşik kutusunda Bağımlı Görev'i seçin ve Bağımlı Görev **Ekle'ye tıklayın.** 

     **%0 Tamamlandı -- Bağımlı Görev** Bu **görev, aşağıdaki görevler liste kutusuna** bağlıdır. Bu, düğmenin olaylarını `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` başarıyla işleyenin olduğunu gösterir.

9. Birincil Görev öğesini **kaydedin ve** kapatın.

10. Bağımlı Görev öğesini Outlook.

11. Bağımlı Görev formunda Tamamlama **%** alanını **%50 olarak değiştirebilirsiniz.**

12. Bağımlı **Görev Şeridi'nin** Görev sekmesinde, Eylemler grubunda Kaydet'e ve Kapat'& **tıklayın.** 

13. Birincil Görev **öğesini Outlook.**

     **%50 Tamamlandı -- Bağımlı** Görev artık Bu **görev, aşağıdaki görevler liste kutusuna bağlıdır.**

## <a name="next-steps"></a>Sonraki adımlar
 Bir uygulamanın kullanıcı arabirimini özelleştirme hakkında daha fazla Outlook şu konulardan öğrenebilirsiniz:

- Yönetilen denetimleri görsel tasarımcıya sürükleyerek form bölgesi görünümünü tasarlama hakkında daha fazla bilgi edinmek için bkz. Adım adım: Form [bölgesinde Outlook tasarlama.](../vsto/walkthrough-designing-an-outlook-form-region.md)

- Bir öğenin Şeridini özelleştirme hakkında bilgi Outlook için [bkz.](../vsto/customizing-a-ribbon-for-outlook.md)Outlook.

- Uygulamanıza özel görev bölmesi ekleme hakkında daha fazla bilgi Outlook [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Form bölgelerini Outlook yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Adım adım kılavuz: Form Outlook tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Nasıl yapılanlar: Eklenti projesine Outlook bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Form bölgelerini bir form Outlook ile ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Form bölgelerinde Outlook eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
- [Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
