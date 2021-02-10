---
title: Office belgelerindeki Windows Forms denetimlerine genel bakış
description: Windows Forms denetimlerinin, kullanıcıların verileri girmek veya işlemek üzere etkileşime girebileceği nesneler olduğunu öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: b2d221cdc3e66205ef9bf3d816b6f226be69ff51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937179"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Office belgelerindeki Windows Forms denetimlerine genel bakış
  Windows Forms denetimleri, kullanıcıların verileri girmek veya işlemek için etkileşime girebileceği nesnelerdir. Excel ve Microsoft Office Word 'Ün Microsoft Office belge düzeyi projelerinde, tasarım zamanında projenizdeki belge veya çalışma kitabına Windows Forms denetimleri ekleyebilir veya çalışma zamanında bu denetimleri program aracılığıyla ekleyebilirsiniz. Excel veya Word için VSTO eklentisinde çalışma zamanında bu denetimleri herhangi bir açık belgeye veya çalışma sayfasına programlı olarak ekleyebilirsiniz.

 Daha fazla bilgi için bkz. [nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="use-windows-forms-controls"></a>Windows Forms denetimleri kullanma

Belgelere ve Eylemler bölmeleri, özel görev bölmeleri ve Windows Forms dahil özelleştirilebilir kullanıcı arabirimi (UI) öğelerine Windows Forms denetimleri ekleyebilirsiniz. Windows Forms denetimler genellikle bu diğer kullanıcı arabirimi öğelerindeki gibi belgelerde aynı davranışa sahiptir ancak bazı farklılıklar vardır. Bilgi için bkz. [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

Bir belgeye ya da başka bir kullanıcı arabirimi öğesine Windows Forms denetimleri ekleme kararı, çeşitli etkenlere bağlıdır. Çözümünüzün Kullanıcı arabirimini tasarlarken, aşağıdaki tabloda açıklandığı gibi Windows Forms denetimlerinin kullanımını göz önünde bulundurun.

Bir belge üzerinde.
- Denetimlerin %100 ' i görüntülemeyi istediğiniz zaman.

- Kullanıcıların doğrudan belgeye veri girmesini istediğinizde, örneğin, düzen yüzeyinin kilitli olduğu form tabanlı belgelerde.

- Denetimlerin belgedeki verilerle satır içinde görüntülenmesini istediğinizde. Örneğin, bir liste nesnesinin her satırına düğme ekliyorsanız, bunların her bir liste öğesiyle aynı hizaya olmasını istersiniz.

Eylemler bölmesinde veya özel bir görev bölmesinde.
- Kullanıcıya bağlamsal bilgiler sağlamak istediğinizde.

- Yalnızca sonuçların belgede görünmesini istediğinizde, sorgu denetimleri ve verileri değildir.

- Denetimlerin belgeyle yazdırılmadığından emin olmak istediğinizde.

- Denetimlerin belge görünümünü etkilememesini sağlamak istediğinizde.

Bir Windows formunda.
- Kullanıcı arabiriminin boyutunu denetlemek istediğinizde.

- Kullanıcıların denetimleri gizlemesini veya silmelerini engellemek istediğinizde.

- Kullanıcıdan giriş almak istediğinizde ve giriş alınana kadar kullanıcının belgede herhangi bir şey yapmasını önleyin.

## <a name="add-windows-forms-controls-programmatically"></a>Program aracılığıyla Windows Forms denetimleri ekleme
 Çalışma zamanında Word belgelerine ve Excel çalışma sayfalarına Windows Forms denetimleri ekleyebilirsiniz. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]En yaygın Windows Forms denetimlerini eklemek için yardımcı yöntemler sağlar. Bu yardımcı yöntemler, Office belgenize hızlı bir şekilde denetim eklemenizi ve bu denetimlerin birleştirilmiş Windows Forms denetim işlevlerine ve Office ile ilgili işlevselliğine erişmenizi sağlar.

 Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="use-windows-forms-controls-in-document-level-projects"></a>Belge düzeyi projelerinde Windows Forms denetimleri kullanma
 Belgeler üzerinde Windows Forms denetimleri kullanmanın bazı yönleri belge düzeyindeki projelere özgüdür, bu da Visual Studio tasarımcısını kullanarak belgenizin Kullanıcı arabirimini tasarlamanıza olanak tanır.

### <a name="create-custom-user-controls"></a>Özel Kullanıcı denetimleri oluşturma
 Projenize bir kullanıcı denetimi ekleyip **araç kutusuna** ekleyebilirsiniz. Daha sonra, belgenize Windows Forms denetimi ekleyeceğiniz şekilde belgenize Kullanıcı denetimini doğrudan sürükleyebilirsiniz. Kullanıcı denetimleri oluştururken göz önünde bulundurmanız gereken bazı şeyler vardır:

- **Korumalı** Kullanıcı denetimi oluşturmayın. Denetimi belgenize sürüklediğinizde, Visual Studio genişletmek ve belge üzerinde kullanımını desteklemek için Kullanıcı denetiminden türetilmiş bir sarmalayıcı sınıfı oluşturur. Kullanıcı denetimi **mühürlü** ise, Visual Studio sarmalayıcı sınıfı üretemiyor.

- Kullanıcı denetimlerinde <xref:System.Runtime.InteropServices.ComVisibleAttribute> özniteliği **true** olarak ayarlanmalıdır. Bir Office projesi içinde oluşturulan kullanıcı denetimleri, bu özniteliği varsayılan olarak **true** olarak ayarlanmıştır, ancak dış projelerin parçası olan Kullanıcı denetimleri bu özniteliği **true** olarak ayarlanmamış olabilir.

- Belgeye bir kullanıcı denetimi ekledikten sonra, sınıfı projeden yeniden adlandırmayın veya silmeyin <xref:System.Windows.Forms.UserControl> . Bir kullanıcı denetiminin adını değiştirmeniz gerekiyorsa, önce onu belgeden silmeniz ve ardından ad değiştirildikten sonra yeniden eklemeniz gerekir.

### <a name="arrange-controls-at-design-time"></a>Tasarım zamanında denetimleri düzenleme
 Tasarım zamanında Word ve Excel belgelerinize birden çok denetim eklerseniz, Visual Studio 'da **Microsoft Office Word** ve **Microsoft Office Excel** araç çubuklarını kullanarak tüm seçili denetimlerin hizalamasını hızlı bir şekilde ayarlayabilirsiniz. Bu araç çubukları yalnızca Tasarımcıda bir belge veya çalışma sayfası açık olduğunda kullanılabilir.

 Tasarımcıda birden çok denetim seçtiğinizde, denetimleri düzenlemek için bu araç çubuklarında aşağıdaki düğmeleri kullanabilirsiniz:

- **Solları Hizala**

- **Merkeze Hizala**

- **Hakları Hizala**

- **Üste Hizala**

- **Ortaları Hizala**

- **Botları Hizala**

- **Yatay aralığı eşit yap**

- **Dikey aralığı eşit yap**

> [!NOTE]
> Word projelerinde, bu düğmeler yalnızca seçili denetimler metin ile satır içinde değilse etkinleştirilir. Varsayılan olarak, tasarım zamanında belgeye eklediğiniz denetimler metinle birlikte görüntülenir.

### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Yükleme sırasında Excel çalışma kitaplarında eski verilerin görünmesini engelleyin
 Tasarım zamanında belgelere veya çalışma sayfalarına Windows Forms denetimleri eklediğinizde, Kullanıcı belgeyi kapattığında denetimler belgede kalır. Tasarım zamanında eklenen denetimlere de *Statik denetimler* denir.

 Statik denetimleri içeren bir Excel çalışma kitabı açıldığında, özelleştirme kodu çalıştırılıncaya ve gerçek denetim yükleninceye kadar çalışma kitabı ActiveX denetimindeki denetimin bir bit eşlemini görüntüler. Excel bu bit eşlemi oluşturur ve çalışma kitabı kaydedildiği zaman çalışma kitabında depolar. Bit eşlem, denetimin görüntülendiği tüm veriler de dahil olmak üzere, çalışma kitabının en son kaydedildiği zamanı göründüğü şekliyle görüntülenir. Windows Forms denetimleri ve bit eşlemler içeren ActiveX denetimi hakkında daha fazla bilgi için bkz. [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

 Belirli koşullarda, kod yüklenmez ve yalnızca Kullanıcı çalışma kitabını tasarım modunda açtığında olduğu gibi yalnızca bit eşlem görüntülenir. Ayrıca, Kullanıcı çalışma kitabını yüklü olmayan bir bilgisayarda açarsa [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , özelleştirme, denetimleri yüklemek için çalıştırılamaz ve bu nedenle yalnızca denetimin bit eşlemi görünür olur. Çalışma kitabını kaydetmeden ve kişisel bilgilerinizin yanlışlıkla açıklanmamasını sağlamak üzere başka bir kullanıcıya göndermeden önce, çalışma kitaplarında bulunan denetimlerden kişisel bilgileri her zaman kaldırmanız gerekir.

### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Excel çalışma sayfasındaki denetim boyutunu hücre boyutuyla Eşleştir
 Üst hücrenin boyutu değiştirildiğinde denetimi otomatik olarak yeniden boyutlandırılacak şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Tüm çalışma sayfaları tarafından paylaşılan bileşenleri ekleme
 Çalışma sayfaları yerine tüm çalışma sayfaları arasında paylaştırmak istediğiniz bileşenleri <xref:System.Data.DataSet> (örneğin, çalışma sayfası tasarımcısına) ekleyebilirsiniz. Bileşen, bileşen tepsisinde görünür.

### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Excel çalışma sayfasına denetim ekleme formülü
 Excel 'de bir denetim seçtiğinizde, **Formül çubuğuna** **= embed ("WinForms. Control. Host", "")** görürsünüz. Bu metin gereklidir ve silinmemelidir.

### <a name="layout-style-of-controls-on-a-word-document"></a>Word belgesindeki denetimlerin düzen stili
 Visual Studio tasarımcısını kullanarak belge düzeyindeki bir projede Word belgesine bir denetim eklediğinizde, denetim metinle satıra eklenir. Denetimin düzen stilini değiştirmek için denetime sağ tıklayın ve sonra **Biçim denetimi**' ne tıklayın. **Nesne biçimlendirme** Iletişim kutusunun **Düzen** sayfasında bir kaydırma stili seçin.

 Çalışma zamanında Word belgesine bir denetim eklediğinizde, `Add` \<*control class*> sınıfının farklı yöntem yüklerini kullanarak yeni denetimin düzen stilini belirtebilirsiniz <xref:Microsoft.Office.Tools.Word.ControlCollection> :

- Denetimi metin ile satıra eklemek için, denetimin konumunu belirten bir aşırı yükleme kullanın <xref:Microsoft.Office.Interop.Word.Range> .

- Denetimi kayan bir şekil olarak eklemek için, denetimin sol ve üst koordinatlarını kabul eden bir aşırı yükleme kullanın.

  Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Visual Studio tasarımcısında bir Word şablonu açarsanız, Visual Studio şablonu **normal** görünümde açtığından, şablonda satır içi olmayan denetimler görünmeyebilir. Denetimleri görüntülemek için görünümü **yazdırma düzeni** olarak değiştirin.

### <a name="controls-outside-the-main-document-body"></a>Ana belge gövdesinin dışındaki denetimler
 Windows Forms denetimleri bir üst bilgi veya alt bilgi içinde veya bir alt belge içinde desteklenmez.

### <a name="add-components-at-design-time"></a>Tasarım zamanında bileşen ekleme
 Belirli denetimler veya bileşenler belgede görünmez ve bunun yerine bileşen tepsisinde görüntülenir. Visual Studio, her belge penceresi için bir bileşen tepsisi sağlar. Bileşen tepsisi, yalnızca belge üzerinde bileşenler mevcutsa ekranda görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/index)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Nasıl yapılır: yazdırırken çalışma sayfalarında denetimleri gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [İzlenecek yol: CheckBox denetimlerini kullanarak çalışma sayfası biçimlendirmesini değiştirme](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [İzlenecek yol: CheckBox denetimlerini kullanarak belge biçimlendirmesini değiştirme](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)
- [İzlenecek yol: düğme kullanarak çalışma sayfasındaki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [İzlenecek yol: düğme kullanarak bir belgedeki metin kutusunda metin görüntüleme](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)
- [Office belgelerindeki Windows Forms denetimlerinin sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [İzlenecek yol: radyo düğmelerini kullanarak bir belgedeki grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)
- [İzlenecek yol: radyo düğmelerini kullanarak çalışma sayfasındaki bir grafiği güncelleştirme](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
