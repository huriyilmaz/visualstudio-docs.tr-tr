---
title: Office belgelerinde dinamik denetimleri kalıcı hale getirme
description: Kullanıcı kapalı bir belgeyi yeniden açtığında kalıcı dinamik denetimleri yeniden oluşturmak için çözümünüze nasıl kod ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0cb0f808dae82b696ee9d766f394a91d25c50cd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046249"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Office belgelerinde dinamik denetimleri kalıcı hale getirme

Çalışma zamanında eklenen denetimler belge veya çalışma kitabı kaydedilip kapatıldığında kalıcı olmaz. tam davranış konak denetimleri ve Windows Forms denetimleri için farklıdır. Her iki durumda da, Kullanıcı belgeyi yeniden açtığında denetimleri yeniden oluşturmak için çözümünüze kod ekleyebilirsiniz.

Çalışma zamanında belgelere eklediğiniz denetimlere *Dinamik denetimler* denir. dinamik denetimler hakkında daha fazla bilgi için bkz. [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Belgedeki konak denetimlerini kalıcı yap

Bir belge kaydedilip kapatıldığında, tüm dinamik konak denetimleri belgeden kaldırılır. yalnızca temeldeki yerel Office nesneleri geride kalır. Örneğin, bir <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> konak denetimi bir olur <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> . yerel Office nesneleri konak denetim olaylarına bağlı değildir ve konak denetiminin veri bağlama işlevselliğine sahip değildir.

aşağıdaki tabloda her konak denetimi türü için bir belgede kalan yerel Office nesnesi listelenmektedir.

|Konak denetim türü|yerel Office nesne türü|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Belgeler açıldığında dinamik ana bilgisayar denetimlerini yeniden oluştur

Bir Kullanıcı belgeyi her açtığında, var olan yerel denetimlerin yerine dinamik ana bilgisayar denetimlerini yeniden oluşturabilirsiniz. Bir belge açıldığında, kullanıcıların beklediği deneyime benzediğinde, bu şekilde konak denetimleri oluşturma.

Word için bir konak denetimini veya <xref:Microsoft.Office.Tools.Excel.NamedRange> Excel için bir veya konak denetimini yeniden oluşturmak için bir <xref:Microsoft.Office.Tools.Excel.ListObject> `Add` \<*control class*> <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> veya nesnesinin yöntemini kullanın <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> . yerel Office nesnesi için parametresi olan bir yöntemi kullanın.

Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> belge açıldığında var olan bir yerel kümeden bir konak denetimi oluşturmak istiyorsanız, <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> yöntemini kullanın ve mevcut ' ı geçirin <xref:Microsoft.Office.Interop.Excel.ListObject> . Aşağıdaki kod örneği, Excel için belge düzeyi bir projede bunu gösterir. Kod, <xref:Microsoft.Office.Tools.Excel.ListObject> sınıfında varolan bir adı temel alan dinamik bir dinamik oluşturur <xref:Microsoft.Office.Interop.Excel.ListObject> `MyListObject` `Sheet1` .

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs" id="Snippet6":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb" id="Snippet6":::

### <a name="re-create-chart"></a>Grafiği yeniden oluştur

Bir konak denetimini yeniden oluşturmak için <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> önce yerel ' i silmeniz <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> ve ardından yöntemini kullanarak yeniden oluşturmanız gerekir <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> . `Add` \<*control class*> Varolan bir temel oluşturmaya göre yeni bir oluşturma işlemi yapmanızı sağlayan bir yöntem yoktur <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> .

Önce yerel ' i silmeyin, <xref:Microsoft.Office.Interop.Excel.Chart> yeniden oluşturduğunuzda ikinci ve yinelenen bir grafik oluşturacaksınız <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> .

## <a name="persist-windows-forms-controls-in-documents"></a>belgelerde Windows Forms denetimleri sürdür

bir belge kaydedilip sonra kapatıldığında, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dinamik olarak oluşturulan Windows Forms denetimleri belgeden otomatik olarak kaldırır. ancak, davranış belge düzeyi ve VSTO eklentisi projeleri için farklıdır.

belge düzeyi özelleştirmelerde, denetimler ve temel alınan ActiveX sarmalayıcılar (belge üzerinde denetimleri barındırmak için kullanılır) belge bir dahaki sefer açıldığında kaldırılır. Denetimlerin orada olduğunu belirten bir belirti yoktur.

VSTO eklentilerde denetimler kaldırılır, ancak ActiveX sarmalayıcılar belgede kalır. kullanıcının belgeyi bir sonraki açılışında ActiveX sarmalayıcılar görünür. Excel, ActiveX sarmalayıcılar, denetimin görüntülerini belgenin kaydedildiği son zamanda göründüğü şekilde görüntüler. Word 'de, kullanıcı onlara tıklamadığı müddetçe ActiveX sarmalayıcılar görünmez ve bu durumda denetimlerin kenarlığını temsil eden noktalı bir çizgi görüntüler. ActiveX sarmalayıcıları kaldırabilmeniz için çeşitli yollar vardır. daha fazla bilgi için bkz. [eklentideki ActiveX sarmalayıcıları kaldırma](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>belgeler açıldığında Windows Forms denetimleri yeniden oluştur

kullanıcı belgeyi yeniden açtığında silinen Windows Forms denetimlerini yeniden oluşturabilirsiniz. Bunu yapmak için çözümünüzün aşağıdaki görevleri gerçekleştirmesi gerekir:

1. Belge kaydedildiğinde veya kapatıldığında denetimlerin boyut, konum ve durumuyla ilgili bilgileri depolayın. Belge düzeyi özelleştirmesinde verileri belgedeki veri önbelleğine kaydedebilirsiniz. VSTO bir eklentiye, verileri belgedeki özel bir XML parçasına kaydedebilirsiniz.

2. Belge açıldığında oluşturulan bir olayda denetimleri yeniden oluşturun. Belge düzeyi projelerinde bunu `Sheet` *n* `_Startup` veya `ThisDocument_Startup` olay işleyicilerinde yapabilirsiniz. VSTO eklenti projelerinde, veya olayları için olay işleyicilerinde bunu yapabilirsiniz <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

### <a name="remove-activex-wrappers-in-an-add-in"></a><a name="removingActiveX"></a>eklentideki ActiveX sarmalayıcıları kaldırma

bir VSTO eklentisi kullanarak belgelere dinamik Windows Forms denetimleri eklediğinizde, bir sonraki sefer açıldığında denetimlerin ActiveX sarmalayıcılarını belgede görüntülenmesini engelleyebilirsiniz.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>belge açıldığında ActiveX sarmalayıcıları kaldır

tüm ActiveX sarmalayıcıları kaldırmak için, `GetVstoObject` <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Excel.Workbook> yeni açılan belgeyi temsil eden veya için bir konak öğesi oluşturmak üzere yöntemini çağırın. örneğin, bir Word belgesinden tüm ActiveX sarmalayıcıları kaldırmak için, `GetVstoObject` <xref:Microsoft.Office.Interop.Word.Document> olayı için olay işleyicisine geçirilen nesne için bir konak öğesi oluşturmak üzere yöntemini çağırabilirsiniz <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

bu yordam, belgenin yalnızca VSTO eklentisinin yüklü olduğu bilgisayarlarda açılacağını bildiğiniz durumlarda faydalıdır. belge, VSTO eklentisi yüklü olmayan diğer kullanıcılara geçirilmemişse, bunun yerine belgeyi kapatmadan önce denetimleri kaldırmayı göz önünde bulundurun.

Aşağıdaki kod örneği, belge açıldığında yönteminin nasıl çağrılacağını gösterir `GetVstoObject` .

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet11":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet11":::

yöntemi, `GetVstoObject` birincil olarak çalışma zamanında yeni bir konak öğesi oluşturmak için kullanılsa da, bu yöntem, belirli bir belge için ilk çağrılışında belgedeki tüm ActiveX sarmalayıcıları da temizler. yönteminin nasıl kullanılacağı hakkında daha fazla bilgi için `GetVstoObject` bkz. [çalışma zamanında VSTO eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

VSTO eklentisi belge açıldığında dinamik denetimler oluşturursa, VSTO eklentisi, `GetVstoObject` denetimleri oluşturma işleminin parçası olarak yöntemi zaten çağırır. `GetVstoObject`bu senaryodaki ActiveX sarmalayıcıları kaldırmak için yönteme ayrı bir çağrı eklemeniz gerekmez.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Belge kapatılmadan önce dinamik denetimleri kaldırın

VSTO eklentisi, belge kapatılmadan önce her dinamik denetimi belgeden açıkça kaldırabilir. bu yordam, VSTO eklentisi yüklü olmayan diğer kullanıcılara geçirilebilecek belgeler için yararlıdır.

aşağıdaki kod örneği, belge kapatıldığında bir Word belgesinden tüm Windows Forms denetimlerinin nasıl kaldırılacağını gösterir.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet10":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet10":::

## <a name="see-also"></a>Ayrıca bkz.

- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
