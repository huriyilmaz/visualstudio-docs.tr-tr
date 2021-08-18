---
title: Windows Belgelerde form Office genel bakış
description: Formlar Windows, kullanıcıların veri girmek veya işlemek için etkileşimde buluna nesneler olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 34de9b336138ca85e96be835ba71fc86a4797810
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135565"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Windows Belgelerde form Office genel bakış
  Windows Form denetimleri, kullanıcıların veri girmek veya işlemek için etkileşimde buluna nesneleridir. Microsoft Office Excel ve Microsoft Office Word için belge düzeyi projelerde, Windows Forms denetimlerini projenizin tasarım zamanında belgeye veya çalışma kitabına ekleyebilir veya bu denetimleri çalışma zamanında programlı olarak ekleyebilirsiniz. Bu denetimleri program aracılığıyla çalışma zamanında herhangi bir açık belgeye veya çalışma sayfasına, VSTO veya Word için Excel ekleyebilirsiniz.

 Daha fazla bilgi için, [bkz. How to: Add Windows Forms controls to Office .](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="use-windows-forms-controls"></a>Windows Forms denetimlerini kullanma

Belgelere ve Windows bölmeleri, özel görev bölmeleri ve özelleştirilebilir kullanıcı arabirimi (UI) öğelerine form denetimleri Windows Forms. Windows Form denetimleri genellikle belgelerde bu diğer kullanıcı arabirimi öğeleriyle aynı davranışa sahiptir, ancak bazı farklar vardır. Bilgi için, [bkz. Windows Forms denetimlerinin belgelerde Office.](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)

Bir belgeye form Windows veya başka bir kullanıcı arabirimi öğesi ekleme kararı çeşitli faktörlere bağlıdır. Çözüm arabirimini tasarlarken, aşağıdaki tabloda açıklandığı gibi Windows Forms denetimlerinin kullanımlarını göz önünde bulundurabilirsiniz.

Bir belgede.
- Denetimleri %100 oranında görüntülemek istediğiniz zaman.

- Düzenleme yüzeyinin kilitli olduğu form tabanlı belgeler gibi kullanıcıların doğrudan belgeye veri girmelerini istediğiniz zaman.

- Denetimlerin belgede yer alan verilerle aynı şekilde görüntülenmelerini istediğiniz zaman. Örneğin, bir liste nesnesinin her satırına düğme ekliyorsanız, bunların her liste öğesiyle aynı sırada yer almak istemesi gerekir.

Eylemler bölmesinde veya özel görev bölmesinde.
- Kullanıcıya bağlamsal bilgiler sağlamak istediğiniz zaman.

- Sorgu denetimleri ve verileri değil, yalnızca sonuçların belgede görünmesini istediğiniz zaman.

- Denetimlerin belgeyle yazdırılmış olduğundan emin olmak istediğiniz zaman.

- Denetimlerin belgenin görünümüne müdahale etmey olduğundan emin olmak istediğiniz zaman.

Bir Windows.
- Kullanıcı arabiriminin boyutunu kontrol etmek istediğiniz zaman.

- Kullanıcıların denetimleri gizlemesini veya silmesini engellemek istediğiniz zaman.

- Kullanıcıdan giriş almak ve giriş alınana kadar kullanıcının belgede herhangi bir şey yapmalarını engellemek istediğiniz zaman.

## <a name="add-windows-forms-controls-programmatically"></a>Form Windows program aracılığıyla ekleme
 Word belgelerine Windows form denetimleri ekleyebilir ve çalışma Excel çalışma sayfalarına ekleyebilirsiniz. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Formlar denetimleri için en yaygın Windows yöntemleri sağlar. Bu yardımcı yöntemler, Office belgenize hızla denetimler eklemenize ve Windows Forms denetim işlevselliğine ve bu denetimlerin Office işlevlerine erişmenize olanak sağlar.

 Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="use-windows-forms-controls-in-document-level-projects"></a>Belge Windows projelerinde Formlar denetimlerini kullanma
 Belgelerde Windows Forms denetimlerini kullanmanın bazı yönleri, belge düzeyi projelere özeldir ve bu da belge tasarımcısını kullanarak belgenizin kullanıcı arabirimini Visual Studio sağlar.

### <a name="create-custom-user-controls"></a>Özel kullanıcı denetimleri oluşturma
 Projenize bir kullanıcı denetimi ekleyebilir ve ardından Araç Kutusuna **ekleyin.** Daha sonra, belgenize bir Windows Forms denetimi eklemek için olduğu gibi kullanıcı Windows doğrudan belgenize sürükleyebilirsiniz. Kullanıcı denetimleri 7.000.

- Korumalı bir kullanıcı **denetimi** oluşturma. Denetimi belgenize sürüklerken, Visual Studio genişletip belgede kullanımını desteklemek için kullanıcı denetiminden türetilen bir sarmalayıcı sınıfı oluşturulur. Kullanıcı denetimi korumalı **ise,** Visual Studio sarmalayıcı sınıfını oluşturamaz.

- Kullanıcı denetimleri özniteliğinin <xref:System.Runtime.InteropServices.ComVisibleAttribute> true olarak ayarlanmış olması **gerekir.** Office projesinde oluşturulan kullanıcı denetimleri bu özniteliği **varsayılan** olarak true olarak ayarlar, ancak dış projelerin parçası olan kullanıcı denetimleri bu özniteliği true olarak **ayarlamaz.**

- Belgeye bir kullanıcı denetimi ekledikten sonra sınıfını projeden yeniden adlandırmayın <xref:System.Windows.Forms.UserControl> veya silmeyin. Kullanıcı denetimi adını değiştirmek için önce belgeden silmeniz ve ardından ad değiştirildikten sonra yeniden eklemeniz gerekir.

### <a name="arrange-controls-at-design-time"></a>Tasarım zamanında denetimleri düzenleme
 Word ve Excel belgelerinize tasarım zamanında birden çok denetim eklersiniz, Microsoft Office **Word** ve Microsoft Office Excel araç çubuklarını kullanarak seçilen denetimlerin **Visual Studio.** Bu araç çubukları yalnızca tasarımcıda bir belge veya çalışma sayfası açık olduğunda kullanılabilir.

 Tasarımcıda birden çok denetim seçerek denetimleri düzenlemek için bu araç çubuklarında aşağıdaki düğmeleri kullanabilirsiniz:

- **Sola Hizala**

- **Merkezleri Hizala**

- **Hakları Hizala**

- **Üstleri Hizala**

- **Ortaları Hizala**

- **Altları Hizala**

- **Yatay Aralığı Eşit Yapma**

- **Dikey Aralığı Eşit Yapma**

> [!NOTE]
> Word projelerinde bu düğmeler yalnızca seçilen denetimler metinle aynı satırda yer alamasa etkinleştirilir. Varsayılan olarak, tasarım zamanında belgeye ekley istediğiniz denetimler metinle aynı sıradadır.

### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Yükleme sırasında eski verilerin çalışma Excel görünmesini engelleme
 Tasarım zamanında Windows form denetimleri eklerken, kullanıcı belgeyi kapatıyorsa denetimler belgede kalır. Tasarım zamanında eklenen denetimlere statik *denetimler de denir.*

 Statik Excel içeren bir çalışma kitabı açıldığında, çalışma kitabı özelleştirme kodu çalıştırana ve gerçek denetimi yükinceye kadar denetimin bit eşlemi ActiveX denetiminde görüntüler. Excel bit eşlemi oluşturur ve çalışma kitabı her kaydedilebilirken çalışma kitabında depolar. Bit eşlem, denetimin görüntüde olduğu veriler de dahil olmak üzere çalışma kitabının son kayded zamanı gibi görünen denetimi gösterir. Windows Forms denetimlerini ve bit eşlemleri içeren ActiveX daha fazla bilgi için bkz. Windows Forms denetimlerinin [Office.](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)

 Belirli koşullarda kod yüklenmez ve örneğin kullanıcı çalışma kitabını tasarım modunda açtığında yalnızca bit eşlem görüntülenir. Ayrıca, kullanıcı çalışma kitabını yüklü olan bir bilgisayarda açarsa, özelleştirme denetimleri yüklemek için çalıştıramaz ve bu nedenle yalnızca denetimin [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bit eşlemi görünür olur. Kişisel bilgilerinizin yanlışlıkla açığa çıkarılamaması için çalışma kitabını kaydetmeden ve başka bir kullanıcıya göndermeden önce her zaman çalışma kitaplarının denetimlerinden kişisel bilgileri kaldırmanız gerekir.

### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Denetim boyutunu çalışma sayfasındaki hücre boyutuyla Excel eşleşme
 Üst hücrenin boyutu değiştirilirken denetimi otomatik olarak yeniden boyutlandırılmak için ayarlayın. Daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma.](../vsto/how-to-resize-controls-within-worksheet-cells.md)

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Tüm çalışma sayfaları tarafından paylaşılan bileşenleri ekleme
 Gibi tüm çalışma sayfaları arasında paylaşmak istediğiniz bileşenleri çalışma sayfaları yerine Çalışma Kitabı <xref:System.Data.DataSet> Tasarımcısı'nda ekleyebilirsiniz. Bileşen, bileşen tepsisinde görünür.

### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Bir çalışma sayfasına denetim ekleme Excel formülü
 Denetim çubuğundan bir denetim Excel Formül Çubuğunda **=EMBED("WinForms.Control.Host","")** **ifadesinin yer alır.** Bu metin gereklidir ve silinmemelidir.

### <a name="layout-style-of-controls-on-a-word-document"></a>Word belgesinde denetimlerin düzen stili
 Visual Studio tasarımcısını kullanarak belge düzeyi projesinde Word belgesine denetim eklerken, denetim metinle satıra eklenir. Denetimin düzen stilini değiştirmek için denetime sağ tıklayın ve ardından Biçim **Denetimi'ne tıklayın.** Nesneyi Biçimlendir iletişim kutusunun **Düzen** sayfasında bir **sarmalama** stili seçin.

 Çalışma zamanında word belgesine denetim eklerken, sınıfının farklı yöntem aşırı yüklemelerini kullanarak yeni denetimin düzen `Add` \<*control class*> stilini <xref:Microsoft.Office.Tools.Word.ControlCollection> belirtebilirsiniz:

- Denetimi metinle satıra eklemek için, denetimin konumunu belirten <xref:Microsoft.Office.Interop.Word.Range> bir kabul eden bir aşırı yükleme kullanın.

- Denetimi kayan şekil olarak eklemek için denetimin sol ve üst koordinatlarını kabul eden bir aşırı yükleme kullanın.

  Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

  Visual Studio tasarımcısında bir Word şablonu açarsanız, Visual Studio normal görünümde açıldığından şablonda satır içi olmayan **denetimler görünür** durumda olmayacaktır. Denetimleri görüntülemek için görünümü Yazdırma Düzeni **olarak değiştirebilirsiniz.**

### <a name="controls-outside-the-main-document-body"></a>Ana belge gövdesinin dışındaki denetimler
 Windows Form denetimleri bir üst bilgi veya alt bilgi içinde veya alt belge içinde desteklenmiyor.

### <a name="add-components-at-design-time"></a>Tasarım zamanında bileşen ekleme
 Bazı denetimler veya bileşenler belgede görünmez ve bunun yerine bir bileşen tepsisinde görüntülenir. Visual Studio belge penceresi için bir bileşen tepsisi sağlar. Bileşen tepsisi ekranda yalnızca belgede bileşenler varsa görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/index)
- [Office Windows Form denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Nasıl kullanılır: Windows Form denetimleri Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Nasıl olur: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Nasıl olur: Yazdırma sırasında çalışma sayfaları denetimlerini gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Adım adım kılavuz: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Adım adım kılavuz: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)
- [Adım adım kılavuz: Düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Adım adım kılavuz: Düğme kullanarak belge içinde metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)
- [Office Windows Form denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Adım adım kılavuz: Radyo düğmelerini kullanarak belgede bir grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)
- [Adım adım kılavuz: Radyo düğmelerini kullanarak çalışma sayfasındaki grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
