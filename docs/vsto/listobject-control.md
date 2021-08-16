---
title: ListObject denetimi
description: ListObject denetimi, olayları ortaya çıkaran ve verilere bağlanan bir listedir. Ayrıca, çalışma sayfasına tasarım zamanında veya çalışma zamanında ListObject denetimleri ekleyebilirsiniz.
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
ms.openlocfilehash: 555cb96deb97b08068ca1b9634ee1770d0f340f021e3e9e29f09ec8150a09eaf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408155"
---
# <a name="listobject-control"></a>ListObject denetimi
  Denetim, <xref:Microsoft.Office.Tools.Excel.ListObject> olayları ortaya çıkaran ve verilere bağlanan bir listedir. Bir çalışma sayfasına liste eklerken, Visual Studio nesne modeli arasında geçiş yapmak zorunda kalmadan <xref:Microsoft.Office.Tools.Excel.ListObject> doğrudan programlayabilirsiniz Microsoft Office Excel oluşturur.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Denetimi oluşturma
 Belge düzeyindeki projelerde, çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.ListObject> tasarım zamanında veya çalışma zamanında denetimler ekleyebilirsiniz. Eklenti VSTO çalışma sayfalarına yalnızca çalışma <xref:Microsoft.Office.Tools.Excel.ListObject> zamanında denetim ekleyebilirsiniz. Daha fazla bilgi için, [bkz. How to: Add ListObject controls to worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).

> [!NOTE]
> Varsayılan olarak, çalışma sayfası kapatıldığında dinamik olarak oluşturulan liste nesneleri konak denetimleri olarak çalışma sayfasında kalıcı olmaz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="bind-data-to-the-control"></a>Denetime veri bağlama
 Denetim <xref:Microsoft.Office.Tools.Excel.ListObject> basit ve karmaşık veri bağlamayı destekler. Denetim, <xref:Microsoft.Office.Tools.Excel.ListObject> tasarım zamanında ve özellikleri veya çalışma zamanında yöntemi kullanılarak bir veri <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> <xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A> <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> kaynağına bağlı olabilir.

> [!NOTE]
> , gibi bir veri kaynağına bağlı olduğunda otomatik olarak güncelleştirilir ve veri <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Data.DataTable> değiştiklerde olaylar oluşturulur. veri değişikliği olduğunda olayları yükseltmez bir veri <xref:Microsoft.Office.Tools.Excel.ListObject> kaynağına bağlarsanız, güncelleştirmek için <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> veya <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> yöntemini çağırmanız <xref:Microsoft.Office.Tools.Excel.ListObject> gerekir.

 Bir çalışma sayfası hücresine yinelenen bir şema öğesini bu hücreye eşleerek bir eklerken, Visual Studio otomatik olarak oluşturulan <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> veri kümesine eşlenir. Ancak, <xref:Microsoft.Office.Tools.Excel.ListObject> verilerine otomatik olarak bağlı değildir. tasarım zamanında veya belge düzeyi projesinde çalışma zamanında veri kümesine bağlama <xref:Microsoft.Office.Tools.Excel.ListObject> adımlarını atabilirsiniz. çalışma zamanında veri kümesine program <xref:Microsoft.Office.Tools.Excel.ListObject> aracılığıyla bir eklentide VSTO babilirsiniz.

 Veriler 'den ayrı olduğundan, doğrudan aracılığıyla değil, bağlı veri kümesi aracılığıyla veri ekli ve <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> kaldırabilirsiniz. Bağlı veri kümesinde yer alan veriler herhangi bir mekanizma aracılığıyla <xref:Microsoft.Office.Tools.Excel.ListObject> güncelleştirilirse denetim değişiklikleri otomatik olarak yansıtacaktır. Daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

 Bir denetimi bir veri <xref:Microsoft.Office.Tools.Excel.ListObject> kaynağına bağarak <xref:Microsoft.Office.Tools.Excel.ListObject> hızlı bir şekilde doldurabilirsiniz. Verileri veriye bağlı olarak <xref:Microsoft.Office.Tools.Excel.ListObject> düzenlersiniz, değişiklikler veri kaynağında da otomatik olarak yapılır. doldurmak ve ardından kullanıcının veri kaynağını değiştirmeden 'de verileri değiştirmesini sağlamak için yöntemini kullanarak veri kaynağından <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> <xref:Microsoft.Office.Tools.Excel.ListObject> ayırabilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: ListObject denetimlerini verilerle doldurma.](../vsto/how-to-fill-listobject-controls-with-data.md)

> [!NOTE]
> Çakışan denetimlerde veri bağlama <xref:Microsoft.Office.Tools.Excel.ListObject> desteklenmiyor.

### <a name="improve-performance-in-listobject-controls"></a>ListObject denetimlerde performansı geliştirme
 Bir XML dosyasını veriye bağlı denetime okuma, önce denetimi bağlamanız ve ardından veri kümesini doldurmak için çağrınız gerekirse <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Data.DataSet.ReadXml%2A> daha yavaş olabilir. Performansı artırmak için denetimi <xref:System.Data.DataSet.ReadXml%2A> bağlamadan önce çağrısında bulundurabilirsiniz.

### <a name="disconnect-listobject-controls-from-the-data-source"></a>ListObject denetimlerinin veri kaynağıyla bağlantısını kesme
 Bir denetimi veri kaynağına bağarak verilerle doldururken, liste nesnesinde yapılan değişikliklerin veri kaynağını etkilemesi için denetimin bağlantısını <xref:Microsoft.Office.Tools.Excel.ListObject> kesebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: ListObject denetimlerini verilerle doldurma.](../vsto/how-to-fill-listobject-controls-with-data.md)

### <a name="restore-column-and-row-order"></a>Sütunu ve satır sıralamayı geri yükleme
 Tasarım zamanında belgeye eklenmiş olan bir denetime veri bağ Visual Studio çalışma kitabı kaydedilen her durumda sütunu ve satır <xref:Microsoft.Office.Tools.Excel.ListObject> sıralamayı takip ediyor olur. Bir kullanıcı çalışma zamanı sırasında sütunları veya satırları taşırsa, çalışma kitabı bir sonraki açıldığında ve denetim veri kaynağına yeniden bağlanıp yeni <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> sıra korunur.

 özgün sütununa ve <xref:Microsoft.Office.Tools.Excel.ListObject> satır sırasına geri yüklemek için yöntemini <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> çağırebilirsiniz. Bu yöntem, belirtilen sütun ve satır sırasıyla ilgili özel belge özelliklerini <xref:Microsoft.Office.Tools.Excel.ListObject> kaldırır. sütununu ve <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> satır sıralamasını korumak istemiyorsanız Çalışma Kitabı olayından bu yöntemi <xref:Microsoft.Office.Tools.Excel.ListObject> çağırabilirsiniz.

## <a name="format"></a>Biçimlendir
 bir denetimine uygulanan <xref:Microsoft.Office.Interop.Excel.ListObject> biçimlendirme bir denetime <xref:Microsoft.Office.Tools.Excel.ListObject> uygulanabilir. Buna kenarlıklar, yazı tipleri, sayı biçimi ve stiller dahildir. Son kullanıcılar veriye bağlı bir içinde sütunları yeniden düzenleyebilir ve tasarım zamanında belgeye eklenmiş olması şartıyla bu değişiklikler <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> belgeyle birlikte kalıcı olur. Belge bir sonraki açıldığında liste nesnesi aynı veri kaynağına bağlı olur ancak sütun sırası kullanıcıların değişikliklerini yansıtacak.

## <a name="add-and-remove-columns-at-run-time"></a>Çalışma zamanında sütun ekleme ve kaldırma
 Çalışma zamanında veriye bağlı denetimde sütunları el ile <xref:Microsoft.Office.Tools.Excel.ListObject> ekamaz veya kaldıramazsınız. Son kullanıcı bir sütunu silebilirse hemen geri yüklenir ve eklenen tüm sütunlar kaldırılır. Bu nedenle, kullanıcılara verilere bağlı bir üzerinde bu eylemleri neden gerçekleştire olduklarını açıklamak <xref:Microsoft.Office.Tools.Excel.ListObject> için kod yazmak önemlidir. Visual Studio bağlama ile ilgili çeşitli <xref:Microsoft.Office.Tools.Excel.ListObject> olaylar sağlar. Örneğin, silme girişiminde bulunduğu verilerin silinene ve geri yüklendiklerini kullanıcıları uyarmak <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> için olayı kullanabilirsiniz.

## <a name="add-and-remove-rows-at-run-time"></a>Çalışma zamanında satır ekleme ve kaldırma
 Veri kaynağı yeni satırlar eklemeye izin verir ve salt okunur değildir şartıyla, veriye bağlı bir denetimde satırları el ile <xref:Microsoft.Office.Tools.Excel.ListObject> ekleyebilir ve kaldırabilirsiniz. Verileri doğrulamak için gibi olaylara karşı <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> kod yazabilirsiniz. Daha fazla bilgi için [bkz. ListObject denetimine yeni bir satır eklendiği zaman verileri doğrulama.](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)

 Bazen liste nesnesinin veri kaynağıyla ilişkisi rutin hatalara neden olur. Örneğin, içinde görünmesini istediğiniz sütunları eşlersiniz; bu nedenle, null değerleri kabul etmeyen bir alan gibi kısıtlamaları olan sütunları atlarsanız, satır her oluşturulduğunda hatalar <xref:Microsoft.Office.Tools.Excel.ListObject> ortaya çıkar. Olay için bir olay işleyicisinde eksik değerleri eklemek için kod <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> yazabilirsiniz.

## <a name="rename-listobject-controls-in-excel"></a>Excel'da ListObject denetimlerini yeniden adlandırma
 Excel tasarım sekmesini kullanarak kullanıcıların çalışma zamanında Excel tabloların adını **değiştirmesini** sağlar. Ancak denetim <xref:Microsoft.Office.Tools.Excel.ListObject> bu özelliği desteklemez. Bir kullanıcı, bir Excel tabloyu yeniden adlandırmaya çalışırsa, çalışma kitabı Excel otomatik olarak özgün adına <xref:Microsoft.Office.Tools.Excel.ListObject> geri döner.

## <a name="events"></a>Ekinlikler
 Denetim için aşağıdaki olaylar <xref:Microsoft.Office.Tools.Excel.ListObject> kullanılabilir:

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
- [Genişletilmiş Excel kullanarak otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl olur: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
- [Nasıl kullanılır: ListObject denetimine yeni bir satır eklendiği zaman verileri doğrulama](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Nasıl kullanılır: ListObject sütunlarını veriyle eşleme](../vsto/how-to-map-listobject-columns-to-data.md)
- [Nasıl kullanılır: ListObject denetimlerini verilerle doldurma](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl kullanılır: Çalışma sayfalarını bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
