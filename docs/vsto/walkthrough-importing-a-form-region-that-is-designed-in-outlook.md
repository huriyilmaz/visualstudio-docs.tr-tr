---
title: "İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma"
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a0de1a25a5309e99193b7be8bce2819808665b8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584982"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma
  Bu izlenecek yol, Outlook Microsoft Office bir form bölgesinin nasıl tasarlanacağını ve **Yeni form bölgesi** Sihirbazı 'nı kullanarak form bölgesini BIR Outlook VSTO eklentisi projesine aktarmayı gösterir. Form bölgesini Outlook 'ta tasarlamak, Outlook verilerine bağlanan form bölgesine yerel Outlook denetimleri eklemenize olanak tanır. Form bölgesini içeri aktardıktan sonra her bir denetimin olaylarını işleyebilirsiniz.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Outlook 'ta form bölgesi tasarımcısını kullanarak form bölgesi tasarlama.

- Form bölgesini Outlook VSTO eklenti projesine aktarma.

- Form bölgesindeki denetimlerin olaylarını işleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] veya [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Outlook 'ta form bölgesi tasarımcısını kullanarak form bölgesi tasarlama
 Bu adımda Outlook 'ta bir form bölgesi tasarlayacaksınız. Daha sonra formu içine aktarabilmeniz için form bölgesini kolay bulunacak bir konuma kaydedin [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Bu örnek form bölgesi, normal görev formunun tamamen yerini alır. Ana görev gerçekleştirilmeden önce tamamlanması gereken tüm görevlerin ilerlemesini izlemek için bir yol sağlar (önkoşul görevleri). Form bölgesi, önkoşul görevlerinin bir listesini görüntüler ve listedeki her görevin tamamlanma durumunu gösterir. Kullanıcılar listeye görev ekleyebilir ve bunları kaldırabilir. Ayrıca, her görevin tamamlanma durumunu yenileyebilirler.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Outlook 'ta form bölgesi tasarımcısını kullanarak form bölgesi tasarlamak için

1. Outlook Microsoft Office başlatın.

2. Outlook 'ta, **Geliştirici** sekmesinde **Form Tasarla**' ya tıklayın. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. **Tasarım formu** kutusunda **görev**' i ve sonra **Aç**' ı tıklatın.

4. Outlook 'ta, **Geliştirici** sekmesinde, **Tasarım** grubunda, **Yeni form bölgesi**' ne tıklayın.

     Yeni bir form bölgesi açılır. **Alan Seçicisi** görünmezse, **Araçlar** grubunda **alan Seçicisi** ' ne tıklayın.

5. **Konu** alanını ve **Tamamlanma yüzdesi** alanını **alan seçicinden** form bölgesine sürükleyin.

6. **Araç**kutusunu açmak için **Araçlar** grubunda **Denetim araç kutusu** ' na tıklayın.

7. **Araç kutusundan** bir etiketi form bölgesine sürükleyin. Etiketi **konunun** altına ve **Tamamlanma yüzdesi** alanlarının altına yerleştirin.

8. Etikete sağ tıklayın ve ardından **Gelişmiş Özellikler**' e tıklayın.

9. **Özellikler** penceresinde, **başlık** özelliğini bu görev olarak ayarlayın, **aşağıdaki görevlere bağlıdır**, **Width** özelliğini **200**olarak ayarlayın ve **Uygula**' ya tıklayın.

10. **Araç kutusu** ' ndan form bölgesine bir ListBox denetimi sürükleyin. Liste kutusunun bu görevin altına konumu **aşağıdaki görevler etiketine bağlıdır** .

11. Yeni eklediğiniz liste kutusunu seçin.

12. **Özellikler** penceresinde, **genişliği** **300**olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

13. **Araç kutusundan** bir etiketi form bölgesine sürükleyin. Etiketi liste kutusunun altına konumlandırın.

14. Yeni eklediğiniz etiketi seçin.

15. **Özellikler** penceresinde, **başlık** özelliğini, **Bağımlı görevler listesine eklenecek bir görevi seçmek**için ayarlayın, **Width** özelliğini **200**olarak ayarlayın ve **Uygula**' ya tıklayın.

16. **Araç kutusu** ' ndan form bölgesine bir ComboBox denetimi sürükleyin. **Bağımlı görevler etiketi listesine eklemek için bir görev seçin ' in** altındaki açılan kutuyu konumlandırın.

17. Yeni eklediğiniz Birleşik giriş kutusunu seçin.

18. **Özellikler** penceresinde, **Width** özelliğini **300**olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

19. **Araç kutusundan** bir CommandButton denetimini form bölgesine sürükleyin. Açılan kutunun yanındaki komut düğmesini konumlandırın.

20. Yeni eklediğiniz komut düğmesini seçin.

21. **Özellikler** penceresinde, **adı** **AddDependentTask**olarak ayarlayın, alt **yazı başlığını** **bağımlı görev eklemek**için ayarlayın, **genişliği** **100**olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

22. **Alan Seçicisi**' nde **Yeni**' ye tıklayın.

23. **Yeni alan** Iletişim kutusunda **ad** alanına **HiddenField** yazın ve ardından **Tamam**' a tıklayın.

24. **Alan seçicinden** **HiddenField** alanını form bölgesine sürükleyin.

25. **Özellikler** penceresinde, **Visible** ' ı **0-false**olarak ayarlayın ve ardından **Uygula**' ya tıklayın.

26. Outlook 'ta, **Geliştirici** sekmesinde, **Tasarım** grubunda **Kaydet** düğmesine tıklayın ve ardından **form bölgesini farklı kaydet**' e tıklayın.

     Form bölgesini **TaskFormRegion** olarak adlandırın ve bilgisayarınızdaki yerel bir dizine kaydedin.

     Outlook, form bölgesini bir Outlook form depolama (*. ofs*) dosyası olarak kaydeder. Form bölgesi *TaskFormRegion. ofs*adıyla kaydedilir.

27. Outlook 'tan çıkın.

## <a name="create-a-new-outlook-add-in-project"></a>Yeni bir Outlook eklentisi projesi oluşturma
 Bu adımda, bir Outlook VSTO eklentisi projesi oluşturacaksınız. Bu kılavuzda daha sonra, form bölgesini projeye aktaracaksınız.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklentisi projesi oluşturmak için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **taskaddin**ADLı bir Outlook VSTO eklentisi projesi oluşturun.

2. **Yeni proje** iletişim kutusunda, **çözüm için dizin oluştur**' u seçin.

3. Projeyi varsayılan proje dizinine kaydedin.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Form bölgesini içeri aktarma
 Outlook 'ta tasarladığınız form bölgesini Outlook VSTO eklenti projesinde **Yeni Outlook form bölgesi** Sihirbazı ' nı kullanarak içeri aktarabilirsiniz.

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Form bölgesini Outlook VSTO eklenti projesine aktarmak için

1. **Çözüm Gezgini**, **taskaddin** projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.

2. **Şablonlar** bölmesinde **Outlook form bölgesi**' ni seçin, dosyayı **TaskFormRegion**olarak adlandırın ve **Ekle**' ye tıklayın.

     **Newoutlook form bölgesi** Sihirbazı başlar.

3. **Form bölgesini nasıl oluşturmak Istediğinizi seçin** sayfasında, **Outlook form depolama (. ofs) dosyasını içeri aktar**' a tıklayın ve sonra da **Araştır**' a tıklayın.

4. **Mevcut Outlook form bölgesi dosya konumu** iletişim kutusunda, *TaskFormRegion. ofs*'un konumuna gidin, **TaskFormRegion. ofs**' ı seçin, **Aç**' a tıklayın ve ardından **İleri**' ye tıklayın.

5. Oluşturmak istediğiniz **form bölgesinin türünü seçin** sayfasında, **Tümünü Değiştir**' e tıklayın ve ardından **İleri**' ye tıklayın.

     *Replace-All* form bölgesi tüm Outlook formunun yerini alır. Form bölgesi türleri hakkında daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

6. **Açıklayıcı metin girin ve görüntüleme tercihlerini seçin** sayfasında **İleri**' ye tıklayın.

7. **Bu form bölgesini görüntüleyecek ileti sınıflarını tanımla** sayfasında, **hangi özel ileti sınıflarında bu form bölgesini görüntüleyecek** ? alanına **IPM yazın. Task. TaskFormRegion**ve ardından **son**' a tıklayın.

     Projenize bir *TaskFormRegion.cs* veya *TaskFormRegion. vb* dosyası eklenir.

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Form bölgesindeki denetimlerin olaylarını işleme
 Artık projede form bölgesine sahip olduğunuza `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` göre, Outlook 'ta form bölgesine eklediğiniz düğmenin olayını işleyen bir kod ekleyebilirsiniz.

 Ayrıca, form <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> bölgesi göründüğünde form bölgesindeki denetimleri güncelleştiren olaya kod ekleyin.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Form bölgesindeki denetimlerin olaylarını işlemek için

1. **Çözüm Gezgini**, *TaskFormRegion.cs* veya *TaskFormRegion. vb*öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

    Kod düzenleyicisinde *TaskFormRegion.cs* veya *TaskFormRegion. vb* açılır.

2. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. Bu kod, form bölgesindeki Birleşik giriş kutusunu Outlook Tasks klasöründeki her görevin konu satırıyla doldurur.

    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]

3. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - `Microsoft.Office.Interop.Outlook.TaskItem` `FindTaskBySubjectName` Yardımcı yöntemini çağırarak ve istenen görevin konusunu geçirerek Görevler klasörünü bulur. `FindTaskBySubjectName`Sonraki adımda yardımcı yöntemi ekleyeceksiniz.

   - `Microsoft.Office.Interop.Outlook.TaskItem.Subject` `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` Bağımlı görev liste kutusuna ve değerlerini ekler.

   - Görev konusunu form bölgesindeki gizli alana ekler. Gizli alan bu değerleri Outlook öğesinin bir parçası olarak depolar.

     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]

4. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. Bu kod, `FindTaskBySubjectName` önceki adımda açıklanan yardımcı yöntemi sağlar.

    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]

5. Aşağıdaki kodu `TaskFormRegion` sınıfına ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Form bölgesindeki liste kutusunu, her bağımlı görevin geçerli tamamlanma durumuyla yeniler.

   - Her bağımlı görevin konusunu almak için gizli metin alanını ayrıştırır. Ardından, her biri `Microsoft.Office.Interop.Outlook.TaskItem` *Tasks* `FindTaskBySubjectName` yardımcı yöntemini çağırarak ve her görevin konusunu geçirerek görevler klasöründeki her birini bulur.

   - `Microsoft.Office.Interop.Outlook.TaskItem.Subject` `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` Bağımlı görev liste kutusuna ve değerlerini ekler.

     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]

6. `TaskFormRegion_FormRegionShowing`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Form bölgesi göründüğünde form bölgesindeki Birleşik giriş kutusunu görev konularıyla doldurur.

   - `RefreshTaskListBox`Form bölgesi göründüğünde yardımcı yöntemini çağırır. Bu, öğe daha önce açıldığında liste kutusuna eklenen bağımlı görevleri görüntüler.

     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]

## <a name="test-the-outlook-form-region"></a>Outlook form bölgesini test etme
 Form bölgesini test etmek için form bölgesindeki önkoşul görevleri listesine görevler ekleyin. Bir önkoşul görevinin tamamlanma durumunu güncelleştirin ve sonra önkoşul görev listesinde görevin güncelleştirilmiş tamamlanma durumunu görüntüleyin.

### <a name="to-test-the-form-region"></a>Form bölgesini test etmek için

1. Projeyi çalıştırmak için **F5** tuşuna basın.

     Outlook başlatılır.

2. Outlook 'ta **giriş** sekmesinde, **yeni öğeler**' i ve ardından **görev**' i tıklatın.

3. Görev formunda, **Konu** alanına **bağımlı görev** yazın.

4. Şeridin **görev** sekmesinde, **Eylemler** grubunda, **Kaydet & kapat**' a tıklayın.

5. Outlook 'ta, **giriş** sekmesinde, **yeni öğeler**' i tıklatın, **daha fazla öğe**' yi ve ardından **Form Seç**' i tıklatın.

6. **Form Seç** Iletişim kutusunda **TaskFormRegion**' ye ve sonra **Aç**' a tıklayın.

     **TaskFormRegion** form bölgesi belirir. Bu form tüm görev formunu değiştirir. **Bağımlı görevler listesine eklemek için bir görev seçin** Birleşik giriş kutusu, görevler klasöründeki diğer görevlerle doldurulur.

7. Görev formunda, **Konu** alanına **birincil görev**yazın.

8. **Bağımlı görevler listesine eklemek için bir görev seçin** Birleşik giriş kutusunda **bağımlı görev**' i seçin ve ardından **bağımlı görev ekle**' ye tıklayın.

     **%0 tam--bu görevde bağımlı görev** görünür **ve aşağıdaki görevler** liste kutusuna bağlıdır. Bu, düğmenin olayını başarıyla işlebileceğinizi gösterir `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` .

9. **Birincil görev** öğesini kaydedin ve kapatın.

10. Outlook 'ta bağımlı görev öğesini yeniden açın.

11. Bağımlı görev formunda, **Tamamlanma yüzdesi** alanını% **50**olarak değiştirin.

12. Bağımlı görev şeridinin **görev** sekmesinde, **Eylemler** grubunda, **Kaydet & kapat**' a tıklayın.

13. Outlook 'taki **birincil görev** öğesini yeniden açın.

     **%50 tam--bu görevde bağımlı görev** görüntülenir ve **aşağıdaki görevler** liste kutusuna bağlıdır.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan bir Outlook uygulamasının Kullanıcı arabirimini nasıl özelleştireceğiniz hakkında daha fazla bilgi edinebilirsiniz:

- Yönetilen denetimleri bir görsel tasarımcıya sürükleyerek form bölgesinin görünümünü tasarlama hakkında daha fazla bilgi edinmek için bkz. [Izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Outlook öğesinin şeritlerini nasıl özelleştireceğiniz hakkında bilgi edinmek için bkz. [Outlook için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md).

- Outlook 'a özel bir görev bölmesi ekleme hakkında daha fazla bilgi edinmek için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
- [Nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
