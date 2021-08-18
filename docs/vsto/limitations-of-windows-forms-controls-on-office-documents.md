---
title: Belgelerde Windows Forms denetimlerinin Office sınırlamaları
description: Windows Forms Windows özellikleriyle ilgili sınırlamalar hakkında bilgi Microsoft Office öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8eddcb8273b1ff3c619de85c6f871d617d3c9a92
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082926"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Belgelerde Windows Forms denetimlerinin Office sınırlamaları

Microsoft Office Word belgelerine veya Microsoft Office Excel çalışma sayfalarına eklenen Windows Forms denetimleri ile Windows Forms denetimleri arasında bazı farklar Windows vardır. Örneğin, bir belgeye denetim eklerken , ve gibi <xref:Microsoft.Office.Tools.Word.Controls.Button> özellikler beklediğiniz gibi <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> <xref:System.Windows.Forms.Control.TabIndex> davranmaz.

Bu farkların çoğu, form formlarının Windows barındırma yolundan kaynaklandı. Bir Windows Forms denetimi bir belgeye ekleniyorsa, ActiveX Forms Windows barındıran bir Windows denetimi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ekler. Windows Forms denetimi doğrudan belgeye ekli değildir.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows Forms denetimlerinin yöntemleri ve özellikleriyle ilgili sınırlamalar

Windows Forms denetimlerinin Windows Formlarında olduğu gibi çalışmayan bir dizi yöntem ve özelliği vardır ve bu nedenle kullanılmamaları önerilir. Örneğin, ve gibi özellikleri ayarlama, belge yerine yalnızca kapsayıcı denetimi ActiveX <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> denetimin konumunu etkiler. Aşağıda Word ve Windows Forms denetimlerinin desteklenmeyen yöntemleri ve özelliklerinin bir listesi Excel:

- Denetimler için desteklenmeyen Excel:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Word denetimlerinin desteklenmeyen yöntemleri ve özellikleri:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Ayrıca, Word <xref:System.Windows.Forms.Control.Left> belgesinde <xref:System.Windows.Forms.Control.Top> metinle Windows form denetimlerinin veya özelliğini ayaramazsınız. Windows Form denetimleri aşağıdaki durumlarda metinle satır içinde eklenir:

- Program aracılığıyla Word belgesine denetim ekler ve konum için bir aralık belirten bir yöntem kullanırsınız.

- Tasarım zamanında Windows Word belgesine bir Form denetimi eklersiniz. Tasarımcıda denetimi değiştirerek bunu değiştirebilirsiniz.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Belgelerde Windows Forms denetim Office farklar

Windows Form denetimleri genellikle Office Form'Windows aynı davranışa sahiptir, ancak bazı farklar vardır. Aşağıdaki tabloda, belgelerde Windows Forms denetimleri için mevcut Office açıkmektedir.

|İşlev|Fark|
|-------------------|----------------|
|Denetim sekmesi sırası|Bir çalışma sayfası veya Word belgesine Excel denetimler arasında sekmeler açamazsınız.|
|Denetim gruplama|Bir belgeye <xref:System.Windows.Forms.GroupBox> başka denetimler içeren bir denetim Office kullanılamaz. Belgeye doğrudan birden çok radyo düğmesi eklerken, radyo düğmeleri birbirini dışlar. Radyo düğmelerini birbirini dışlar hale yapmak için kod yazabilirsiniz; ancak, tercih edilen yaklaşım radyo düğmelerini bir kullanıcı denetimine eklemek ve ardından kullanıcı denetimi belgeye eklemektir. Daha fazla bilgi için, geliştirme örnekleri ve izlenecek yollar Excel Word Denetimleri [Örneği veya Office Denetimler Örneği'ne bakın.](../vsto/office-development-samples-and-walkthroughs.md)|
|Denetim türü|Windows Belgelerde kullanılan form denetimleri, tarafından sağlanan ve denetimlere çalışma sayfası veya Word belgesine özgü [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ek işlevler Excel bir sınıfta sarmalanmıştır. Örneğin, bir çalışma  sayfasında düğme denetimi Excel nesnesine başvururken veya tür değiştirme yerine türünü <xref:Microsoft.Office.Tools.Excel.Controls.Button> <xref:System.Windows.Forms.Button> belirttiğinizden emin olun.|
|Denetim konumu ve boyutu|Denetimin boyutu ve konumu, kapsayıcının ve denetimin parçası olan ActiveX belirlenir. Denetim ActiveX, bir Windows Forms denetimine eşdeğer özelliklerden farklı değerler alır. Bir denetimin `Top` `Left` , , veya özelliklerini `Height` `Width` ayarlarken, piksel yerine nokta cinsinden ölçülür.|
|Word belgelerde denetim konumu|Akış tabanlı bir düzende denetimler eklersiniz, içerik değiştiklerine göre denetimlerin içerikle birlikte akacaklarını unutmayın. Denetimi Araç Kutusundan sürüklerken bir paragrafa sabitleyesiniz çünkü denetim metinle satır içinde Word belgesine eklenir.  Denetimi eklemek için başka bir yöntem kullanırsanız (denetime çift tıklama gibi) denetim, resim eklemek için ayar istediğiniz Word seçeneğine göre eklenir.<br /><br /> Metinle satır `Left` `Top` içi olan bir denetimin veya özelliğini ayaramazsiniz.<br /><br /> Denetimleri bir üst bilgiye, alt bilgiye veya alt belgeye yer açamazsınız.|
|Olayları denetleme|Denetim seçildiğinde, olayları aşağıdaki sırayla yükselter:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Denetimin seçimi kaldırıldığında, olaylar aşağıdaki sırayla neden olur:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Ölçeklendirmeyi denetleme|Bir belgenin yakınlaştırma ayarını %100 dışında bir şey olarak değiştirseniz de denetimler, belgeyle birlikte ölçeklendirildi gibi görünse de devre dışı bırakılır. Örneğin, belgeniz %130 yakınlaştırmada olduğunda bir düğmeye tıklarsanız, yakınlaştırma %100 olarak ayarlanana kadar denetimin devre dışı bırakılmıştır iletisiyle karşılaşırsınız. Yakınlaştırmayı %100 olarak değiştir değiştirecek olurken denetimler düzgün şekilde işlev gösterir.|
|Özellik değerlerini denetleme|Windows Form'Windows denetimlerin özellikleri tamsayı değerine ayarlanmış olsa da, Word belgesinde denetimler için tek bir değere ayarlanır. Bu Excel, denetimlerin özellik değerleri çift olarak ayarlanır. Çalışma `Height` `Width` sayfasındaki denetimin ve özelliği çalışma sayfasının veya ekranın boyutunu aşarsa değer kesilir.|
|Yeniden boyutlandırmayı denetleme|Sekiz boyutlandırma tutamaçlarından birini kullanarak belge üzerinde bir denetimi yeniden boyutlandırırsanız, denetim  yeniden seçilene kadar yeni denetim boyutları Özellikler penceresine yansıtılmaz.|
|Denetim davranışı|Çalışma sayfası Excel çalışma sayfası penceresi bölünüyorsa tahmin edilemez şekilde davranabilirsiniz. Örneğin, çalışma <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> sayfasındaki bir'e erişim yalnızca windows'un birsinde kullanılabilir.|
|Denetim adlandırması|Denetimleri ad olarak kullanmak için ayrılmış sözcükler kullanılamaz. Örneğin, bir çalışma sayfasına bir ekler ve adı Sistem olarak <xref:Microsoft.Office.Tools.Excel.Controls.Button> **değiştirirsiniz,** projeyi derleme sırasında hatalar oluşur.|
|Program aracılığıyla denetim ekleme|Çalışma zamanında belgenize denetim eklemek için denetimin oluşturucusu kullanma. Bunun yerine, tarafından sağlanan yardımcı yöntemleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanın. Örneğin, çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> düğme eklemek için yöntemini kullanın. Bu yardımcı yöntemler tarafından desteklenen bir denetim eklemek için yöntemini `AddControl` kullanabilirsiniz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)|
|Denetimleri kopyalama|Windows Forms Windows kopyalayıp çalışma zamanında bir belgeye yapıştırırsanız, boş ActiveX kapsayıcı denetimi belgeye yapıştırır. Windows Forms denetimi yeni konumda görünmez ve özgün denetimin arkasındaki kod kapsayıcı denetimine ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Belge düzeyi projelerde sınırlamalar

Belgelerde Formlar Windows kullanmanın bazı sınırlamaları belge düzeyindeki projelere özeldir.

### <a name="control-support-at-design-time"></a>Tasarım zamanında denetim desteği

Belirli Windows Formlar denetimleri, Excel  çalışma sayfası veya Word belgesi tasarımcıda açık olduğunda Araç Kutusundan Visual Studio kaldırılır. Bunun nedeni teknik sınırlamaların veya işlevselliğin Word veya Excel. Excel ve Word projeleri, Windows odağı olduğunda Araç Kutusunda görünen tüm Windows  Forms denetimlerini ve diğer bileşenleri destekler ve bir çalışma sayfasına veya belgeye üçüncü taraf denetimleri de ekleyebilirsiniz.

> [!NOTE]
> Bir belge korunmaktayken **tüm denetimler** Araç Kutusundan kaldırılır. Belge koruması hakkında bilgi için [bkz. Belge düzeyi çözümlerde belge koruması.](../vsto/document-protection-in-document-level-solutions.md)

> [!NOTE]
> Üçüncü taraf denetimlerin bir <xref:System.Runtime.InteropServices.ComVisibleAttribute> çözümde kullanılası **için** özniteliği true olarak Office gerekir.

Aşağıdaki denetimler ve bileşenler Araç Kutusunda **kullanılamaz:**

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Eski veri ActiveX desteği

ActiveX denetimlerini Office içeren var olan bir Word belgesi veya Excel çalışma kitabını kullanan bir belge düzeyi ActiveX projesi oluşturmanız, ActiveX işlevlerini kaybetmez; bununla birlikte, belgelerinize yeni ActiveX denetimler eklemek için destek Visual Studio. Örneğin Word belgenizin Denetim araç kutusunda  Visual Basic for Applications (VBA) makrosu çalıştıran bir düğmesi varsa, belge bir Office projesinde kullanıldıktan sonra makroyu çalıştırmaya devam eder. Ancak, bu denetimleri ve VBA ActiveX kaldırmanız ve bunları Formlar denetimleri ve yönetilen kod Windows ile değiştirmeniz önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl Windows: Windows Form denetimleri ekleme Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
