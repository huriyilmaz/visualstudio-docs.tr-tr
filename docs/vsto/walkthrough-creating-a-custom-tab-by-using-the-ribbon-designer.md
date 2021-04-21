---
title: 'İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma'
description: Özel bir sekme oluşturma ve ardından Şerit Tasarımcısını kullanarak bu sekmeye denetim ekleme ve bunları yerleştirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3886e20d45834f98f36b8d7e48f3b11c9ef7d5dd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824828"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma
  Şerit Tasarımcısını kullanarak özel bir sekme oluşturup bu sekmeye denetim ekleyip konumlandırabilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- [Eylemler bölmesi oluşturun](#BKMK_CreateActionsPanes).

- [Özel bir sekme oluşturun](#BKMK_CreateCustomTab).

- [Özel sekmedeki düğmeleri kullanarak Eylemler bölmesini gizleyin ve gösterin](#BKMK_HideShowActionsPane).

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-an-excel-workbook-project"></a>Excel çalışma kitabı projesi oluşturma
 Şerit Tasarımcısını kullanma adımları tüm Office uygulamaları için neredeyse aynıdır. Bu örnekte bir Excel çalışma kitabı kullanılmıştır.

### <a name="to-create-an-excel-workbook-project"></a>Excel çalışma kitabı projesi oluşturmak için

- **MyExcelRibbon** adlı bir Excel çalışma kitabı projesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni çalışma kitabını açar ve **Çözüm Gezgini** **MyExcelRibbon** projesini ekler.

## <a name="create-actions-panes"></a><a name="BKMK_CreateActionsPanes"></a> Eylem bölmeleri oluşturma
 Projeye iki özel eylem bölmesi ekleyin. Daha sonra bu eylemler bölmelerini gösteren ve özel sekmeye gizleyecek düğmeler ekleyeceksiniz.

### <a name="to-create-actions-panes"></a>Eylemler bölmesi oluşturmak için

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **ActionsPaneControl**' u ve ardından **Ekle**' yi seçin.

     **ActionsPaneControl1. cs** veya **ActionsPaneControl1. vb** dosyası tasarımcıda açılır.

3. **Araç kutusunun** **ortak denetimler** sekmesinden tasarımcı yüzeyine bir etiket ekleyin.

4. **Özellikler** penceresinde Label1 öğesinin **Text** özelliğini **Eylemler bölmesi 1** olarak ayarlayın.

5. İkinci bir eylemler bölmesi ve etiketi oluşturmak için 1 ile 5 arasındaki adımları yineleyin. İkinci etiketin **Text** özelliğini **Eylemler bölmesi 2** olarak ayarlayın.

## <a name="create-a-custom-tab"></a><a name="BKMK_CreateCustomTab"></a> Özel sekme oluşturma
 Office uygulaması tasarım yönergelerinden biri, kullanıcıların her zaman Office uygulaması kullanıcı arabirimi denetimine sahip olması gerekir. Bu özelliği eylemler bölmesine eklemek için, Şeritteki özel bir sekmeden her bir eylem bölmesini gösteren ve gizleyen düğmeler ekleyebilirsiniz. Özel bir sekme oluşturmak için projeye bir **Şerit (görsel Tasarımcı)** öğesi ekleyin. Tasarımcı denetimleri eklemenize ve konumlandıramanıza, denetim özelliklerini ayarlamanıza ve denetim olaylarını işleymenize yardımcı olur.

### <a name="to-create-a-custom-tab"></a>Özel sekme oluşturmak için

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin.

3. Yeni şeridin adını **MyRibbon** olarak değiştirin ve **Ekle**' yi seçin.

     **MyRibbon. cs** veya **MyRibbon. vb** dosyası Şerit Tasarımcısı 'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit Tasarımcısında Varsayılan sekmesini seçin.

5. **Özellikler** penceresinde **ControlID** özelliğini genişletin ve **ControlIdType** özelliğini **Custom** olarak ayarlayın.

6. **Label** özelliğini **özel sekme** olarak ayarlayın.

7. Şerit tasarımcısında **grup1** öğesini seçin.

8. **Özellikler** penceresinde **etiketi** **Eylemler Bölmesi Yöneticisi** olarak ayarlayın.

9. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden, **grup1** üzerine bir düğme sürükleyin.

10. **Button1**' i seçin.

11. **Özellikler** penceresinde **etiketi** , **Eylemler bölmesi 1**' i gösterecek şekilde ayarlayın.

12. **Grup1** öğesine ikinci bir düğme ekleyin ve **başlık** özelliğini **Eylemler bölmesi 2**' yi gösterecek şekilde ayarlayın.

13. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden, **grup1** üzerine bir **ToggleButton** denetimi sürükleyin.

14. **Etiket** özelliğini **Eylemler bölmesini gizle** olarak ayarlayın.

## <a name="hide-and-show-actions-panes-by-using-buttons-on-the-custom-tab"></a><a name="BKMK_HideShowActionsPane"></a> Özel sekmedeki düğmeleri kullanarak Eylemler bölmesini gizleme ve gösterme
 Son adım kullanıcıya yanıt veren kodu eklemektir. <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>İki düğmenin olayları ve iki durumlu düğmenin olayı için olay işleyicileri ekleyin <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> . Eylemler bölmelerini gizlemeyi ve göstermeyi etkinleştirmek için bu olay işleyicilerine kod ekleyin.

### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Özel sekmedeki düğmeleri kullanarak Eylemler bölmesini gizleme ve gösterme

1. **Çözüm Gezgini**, *MyRibbon. cs* veya *MyRibbon. vb* kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

2. Aşağıdaki kodu sınıfının üst kısmına ekleyin `MyRibbon` . Bu kod iki eylem bölmesi nesnesi oluşturur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet1":::

3. `MyRibbon_Load` yöntemini aşağıdaki kodla değiştirin. Bu kod, Eylemler bölmesi nesnelerini <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> koleksiyona ekler ve nesneleri görünümden gizler. Visual C# kodu ayrıca çeşitli şerit denetim olaylarına temsilciler ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet2":::

4. Aşağıdaki üç olay işleyicisi yöntemini `MyRibbon` sınıfına ekleyin. Bu yöntemler <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> iki düğmenin olaylarını ve iki <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> durumlu düğmenin olayını işler. Button1 ve Button2 için olay işleyicileri alternatif eylemler bölmelerini gösterir. ToggleButton1 için olay işleyicisi, etkin Eylemler bölmesini gösterir ve gizler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb" id="Snippet3":::

## <a name="test-the-custom-tab"></a>Özel sekmeyi test etme
 Projeyi çalıştırdığınızda Excel başlar ve şeritte **özel sekme** sekmesi görüntülenir. Eylemler bölmelerini göstermek ve gizlemek için **özel Sekmesimde** bulunan düğmeleri seçin.

### <a name="to-test-the-custom-tab"></a>Özel sekmeyi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. **Özel sekme** sekmesini seçin.

3. **Özel Eylemler Bölmesi Yöneticisi** grubunda, **Eylemler bölmesi 1**' i göster ' i seçin.

     Eylemler bölmesi görünür ve **Eylemler bölmesi 1** etiketini görüntüler.

4. **Eylemler bölmesini göster 2**' yi seçin.

     Eylemler bölmesi görüntülenir ve **Eylemler bölmesi 2** etiketini görüntüler.

5. **Eylemler bölmesini gizle**' yi seçin.

     Eylemler bölmeleri artık görünmez.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan Office Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi edinebilirsiniz:

- Herhangi bir belge düzeyi özelleştirmesine bağlam tabanlı kullanıcı arabirimi ekleyin. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

- Bir standart veya özel Microsoft Office Outlook formunu genişletin. Daha fazla bilgi için bkz. [Izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Outlook için şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
