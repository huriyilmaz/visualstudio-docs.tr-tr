---
title: ListObject denetimi
description: ListObject denetimi, olayları ortaya çıkaran ve verilere bağlanabilen bir listesidir. Ayrıca, tasarım zamanında veya çalışma zamanında bir çalışma sayfasına ListObject denetimi ekleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e4193fd3aeeed1630ce6b35f27101f88293d495b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032543"
---
# <a name="listobject-control"></a>ListObject denetimi
  <xref:Microsoft.Office.Tools.Excel.ListObject>Denetim, olayları ortaya çıkaran ve verilere bağlanabilen bir listesidir. çalışma sayfasına bir liste eklediğinizde Visual Studio, <xref:Microsoft.Office.Tools.Excel.ListObject> Microsoft Office Excel nesne modelinde geçiş yapmak zorunda kalmadan doğrudan programlama yapabileceğiniz bir denetim oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Denetim oluşturma
 Belge düzeyi projelerinde, <xref:Microsoft.Office.Tools.Excel.ListObject> tasarım zamanında veya çalışma zamanında çalışma sayfasına denetimler ekleyebilirsiniz. VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfalarına yalnızca çalışma zamanında denetim ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md).

> [!NOTE]
> Varsayılan olarak, çalışma sayfası kapatıldığında dinamik olarak oluşturulan liste nesneleri çalışma sayfasında konak denetimleri olarak kalıcı olmaz. daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="bind-data-to-the-control"></a>Verileri denetime bağlama
 Bir <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim basit ve karmaşık veri bağlamayı destekler. <xref:Microsoft.Office.Tools.Excel.ListObject>Denetim, <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> tasarım zamanında ve çalışma zamanında yöntemi kullanılarak bir veri kaynağına bağlanabilir <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> .

> [!NOTE]
> , <xref:Microsoft.Office.Tools.Excel.ListObject> Verileri değiştiğinde olayları başlatan bir veri kaynağına bağlandığında otomatik olarak güncelleştirilir <xref:System.Data.DataTable> . <xref:Microsoft.Office.Tools.Excel.ListObject>Verileri değiştiğinde olayları yükseltmez bir veri kaynağına bağlarsanız, öğesini <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> güncelleştirmek için veya metodunu çağırmanız gerekir <xref:Microsoft.Office.Tools.Excel.ListObject> .

 bir <xref:Microsoft.Office.Tools.Excel.ListObject> yinelenen şema öğesini ilgili hücreyle eşleyerek çalışma sayfası hücresine bir eklediğinizde, Visual Studio otomatik olarak <xref:Microsoft.Office.Tools.Excel.ListObject> oluşturulan veri kümesiyle eşlenir. Ancak, <xref:Microsoft.Office.Tools.Excel.ListObject> otomatik olarak verilere bağlanmaz. <xref:Microsoft.Office.Tools.Excel.ListObject>Tasarım zamanında veya belge düzeyindeki bir projede çalışma zamanında veri kümesine bağlamak için gerekli adımları uygulayabilirsiniz. <xref:Microsoft.Office.Tools.Excel.ListObject>bir VSTO eklentisinde çalışma zamanında veri kümesine programlı bir şekilde bağlanabilirsiniz.

 Veriler öğesinden ayrı olduğundan, <xref:Microsoft.Office.Tools.Excel.ListObject> doğrudan aracılığıyla değil, bağlantılı veri kümesi aracılığıyla veri eklemeli ve çıkarmanız gerekir <xref:Microsoft.Office.Tools.Excel.ListObject> . Bağlantılı veri kümesindeki veriler herhangi bir mekanizmaya göre güncelleştirilirse, <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim otomatik olarak değişiklikleri yansıtır. daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

 Bir denetimi hızlı bir şekilde bir <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> veri kaynağına bağlayarak doldurabilirsiniz. Verileri veriye göre düzenlerseniz <xref:Microsoft.Office.Tools.Excel.ListObject> , değişiklikler otomatik olarak veri kaynağında de yapılır. ' <xref:Microsoft.Office.Tools.Excel.ListObject> I doldurup veri kaynağını değiştirmeden kullanıcının içindeki verileri değiştirmesini etkinleştirmek istiyorsanız, <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> veri kaynağından ayırmak için yöntemini kullanabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject> . Daha fazla bilgi için bkz. [nasıl yapılır: ListObject denetimlerini verilerle Doldur](../vsto/how-to-fill-listobject-controls-with-data.md).

> [!NOTE]
> Çakışan denetimlerde veri bağlama desteklenmiyor <xref:Microsoft.Office.Tools.Excel.ListObject> .

### <a name="improve-performance-in-listobject-controls"></a>ListObject denetimlerinde performansı geliştirme
 Bir XML dosyasını bir veri bağlama denetimine okumak, <xref:Microsoft.Office.Tools.Excel.ListObject> önce denetimi bağladığınızda daha yavaş olacak şekilde, sonra da <xref:System.Data.DataSet.ReadXml%2A> veri kümesini dolduracak şekilde daha yavaş olur. Performansı artırmak için, <xref:System.Data.DataSet.ReadXml%2A> denetimi paylaşmadan önce çağırın.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>Veri kaynağından ListObject denetimlerinin bağlantısını kesme
 Bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi verileri bir veri kaynağına bağlayarak doldurduktan sonra, liste nesnesindeki verilerde yapılan değişikliklerin veri kaynağını etkilememesi için bağlantısını kesebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ListObject denetimlerini verilerle Doldur](../vsto/how-to-fill-listobject-controls-with-data.md).

### <a name="restore-column-and-row-order"></a>Sütun ve satır sırasını geri yükleme
 <xref:Microsoft.Office.Tools.Excel.ListObject>tasarım zamanında bir belgeye eklenen bir denetime veri bağladığınızda Visual Studio, çalışma kitabı kaydedildiği zaman sütun ve satır sırasını izler. Bir kullanıcı çalışma <xref:Microsoft.Office.Tools.Excel.ListObject> zamanında sütunları veya satırları taşısa, çalışma kitabının bir sonraki açılışında yeni sıra korunur ve <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim veri kaynağına yeniden bağlanır.

 <xref:Microsoft.Office.Tools.Excel.ListObject>' I özgün sütununa ve satır sırasına geri yüklemek istiyorsanız, <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> yöntemini çağırabilirsiniz. Bu yöntem, belirtilen sütun ve satır sırasıyla ilgili özel belge özelliklerini kaldırır <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown>Öğesinin sütun ve satır sırasını korumak istemiyorsanız, çalışma kitabının olayından bu yöntemi çağırın <xref:Microsoft.Office.Tools.Excel.ListObject> .

## <a name="format"></a>Biçimlendir
 Bir denetime uygulanabilen biçimlendirme <xref:Microsoft.Office.Interop.Excel.ListObject> , bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetime uygulanabilir. Buna kenarlık, yazı tipi, sayı biçimi ve stil dahildir. Son kullanıcılar, verileri bir veri ile bağlantılı olarak yeniden düzenleyebilir <xref:Microsoft.Office.Tools.Excel.ListObject> ve bu değişiklikler belge ile birlikte kalıcı hale getirilir, ancak <xref:Microsoft.Office.Tools.Excel.ListObject> belgeye tasarım zamanında eklenmiş olur. Belge bir dahaki sefer açıldığında, liste nesnesi aynı veri kaynağına bağlanır, ancak sütun sırası kullanıcıların değişikliklerini yansıtır.

## <a name="add-and-remove-columns-at-run-time"></a>Çalışma zamanında sütun ekleme ve kaldırma
 Çalışma zamanında veriye dayalı bir denetimde sütunları el ile ekleyemez veya kaldıramazsınız <xref:Microsoft.Office.Tools.Excel.ListObject> . Son Kullanıcı bir sütunu silmeye çalışırsa, hemen geri yüklenir ve eklenen sütunlar kaldırılır. Bu nedenle, kullanıcılara, verilere bağlı olan bir üzerinde bu işlemleri gerçekleştiremediğini açıklayan bir kod yazmak önemlidir <xref:Microsoft.Office.Tools.Excel.ListObject> . Visual Studio, <xref:Microsoft.Office.Tools.Excel.ListObject> veri bağlamasıyla ilgili çeşitli olaylar sağlar. Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> kullanıcıyı silmeye çalıştıkları verilerin silinemediğini ve geri yüklendiğini uyarmak için olayını kullanabilirsiniz.

## <a name="add-and-remove-rows-at-run-time"></a>Çalışma zamanında satır ekleme ve kaldırma
 Veri <xref:Microsoft.Office.Tools.Excel.ListObject> kaynağı yeni satırların eklenmesine izin verdiğinden ve salt okunmadığından, veri kaynağı denetimine satırları el ile ekleyebilir ve kaldırabilirsiniz. Verileri doğrulamak için gibi olaylara karşı kod yazabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> . Daha fazla bilgi için bkz. [nasıl yapılır: ListObject denetimine yeni bir satır eklendiğinde verileri doğrulama](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md).

 Bazen liste nesnesinin veri kaynağıyla ilişkisi rutin hatalara neden olur. Örneğin, içinde görünmesini istediğiniz sütunları eşleyebilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject> . bu nedenle, null değerleri kabul edemeyecek bir alan gibi kısıtlamalar bulunan sütunları atlarsanız, her satır oluşturulduğunda hatalar oluşur. Olay için bir olay işleyicisine eksik değerler eklemek için kod yazabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> .

## <a name="rename-listobject-controls-in-excel"></a>Excel ListObject denetimlerini yeniden adlandırma
 Excel, kullanıcıların **tasarım** sekmesini kullanarak çalışma zamanında Excel tablolarının adını değiştirmesine olanak sağlar. Ancak, <xref:Microsoft.Office.Tools.Excel.ListObject> denetim bu özelliği desteklemez. bir kullanıcı öğesine karşılık gelen bir Excel tablosunu yeniden adlandırmaya çalışırsa <xref:Microsoft.Office.Tools.Excel.ListObject> , çalışma kitabı kaydedildiğinde Excel tablosunun adı otomatik olarak özgün ada döndürülür.

## <a name="events"></a>Ekinlikler
 Denetim için aşağıdaki olaylar mevcuttur <xref:Microsoft.Office.Tools.Excel.ListObject> :

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Change>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>

- <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>

- <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>

- <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>

## <a name="see-also"></a>Ayrıca bkz.
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
- [Nasıl yapılır: ListObject denetimine yeni bir satır eklendiğinde verileri doğrulama](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Nasıl yapılır: ListObject sütunlarını verilerle eşleme](../vsto/how-to-map-listobject-columns-to-data.md)
- [Nasıl yapılır: ListObject denetimlerini verilerle Doldur](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
