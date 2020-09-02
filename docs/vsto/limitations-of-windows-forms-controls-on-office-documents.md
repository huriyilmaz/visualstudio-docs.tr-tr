---
title: Office belgelerindeki Windows Forms denetimlerinin sınırlamaları
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81a7da585f49b2a2d1f7df4df11d0c78b7a35d69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71251924"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office belgelerindeki Windows Forms denetimlerinin sınırlamaları

Microsoft Office Word belgelerine veya Microsoft Office Excel çalışma sayfalarına eklenen Windows Forms denetimleri ve Windows Forms eklenen Windows Forms denetimleri arasında bazı farklılıklar vardır. Örneğin, belgeye bir denetim eklediğinizde,,, <xref:Microsoft.Office.Tools.Word.Controls.Button> ve gibi özellikler, <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> beklendiğinde, ve gibi <xref:System.Windows.Forms.Control.TabIndex> davranmaz.

Bu farklılıkların birçoğu, Windows Forms denetimlerinin belgelerde barındırıldığı yönteme neden olmuştur. Bir belgeye Windows Forms denetimi eklendiğinde, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] daha sonra belgedeki Windows Forms denetimini barındıran ActiveX denetimini gömer. Windows Forms denetimi doğrudan belgeye katıştırılmamış.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows Forms denetimlerinin yöntemlerinin ve özelliklerinin sınırlamaları

Bir Windows form üzerinde olduğu gibi bir belgede aynı şekilde çalışmayan Windows Forms denetimlerinin çeşitli yöntemleri ve özellikleri vardır ve bu nedenle kullanılmamalıdır. Örneğin, ve gibi özelliklerinin ayarlanması <xref:System.Windows.Forms.Control.Dock> <xref:System.Windows.Forms.Control.Anchor> , yalnızca denetimin konumunu belge yerine kapsayıcı ActiveX denetimine göre etkiler. Aşağıda Word ve Excel için Windows Forms denetimlerinin desteklenmeyen yöntemlerinin ve özelliklerinin bir listesi verilmiştir:

- Excel denetimlerinin desteklenmeyen özellikleri:

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

Ayrıca, <xref:System.Windows.Forms.Control.Left> <xref:System.Windows.Forms.Control.Top> bir Word belgesindeki metin ile satırdaki Windows Forms denetimlerinin veya özelliğini ayarlayamazsınız. Windows Forms denetimleri, aşağıdaki durumlarda metinle birlikte çizgiye eklenir:

- Programlı olarak bir Word belgesine denetim ekler ve konum için bir Aralık belirten bir yöntem kullanırsınız.

- Tasarım zamanında Word belgesine bir Windows Forms denetimi eklersiniz. Tasarımcıda denetimi değiştirerek bunu değiştirebilirsiniz.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office belgelerindeki Windows Forms denetimlerindeki farklılıklar

Windows Forms denetimleri, bir Office belgesi üzerinde genellikle aynı davranışa sahiptir, ancak bazı farklılıklar vardır. Aşağıdaki tabloda Office belgelerindeki Windows Forms denetimleri için mevcut olan farklar açıklanmaktadır.

|İşlev|Fark|
|-------------------|----------------|
|Denetim sekmesi sırası|Excel çalışma sayfasına veya Word belgesine yerleştirilmiş denetimlerde sekmeye geçiş yapılamaz.|
|Denetim gruplandırma|Bir <xref:System.Windows.Forms.GroupBox> Office belgesinde diğer denetimleri içeren bir denetim kullanamazsınız. Birden çok radyo düğmesini doğrudan belgeye eklediğinizde radyo düğmeleri birbirini dışlar. Radyo düğmelerini birbirini dışlamalı hale getirmek için kod yazabilirsiniz; Ancak, tercih edilen yaklaşım, radyo düğmelerini bir kullanıcı denetimine eklemek ve ardından belgeye Kullanıcı denetimini eklemektir. Daha fazla bilgi için bkz. [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)'da örnek veya Excel denetimleri örneği.|
|Denetim türü|Belgelerde kullanılan Windows Forms denetimleri, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] denetimleri Excel çalışma sayfasına veya Word belgesine özgü ek işlevselliği sağlayan tarafından sağlanmış bir sınıfa sarmalanır. Örneğin, bir Excel çalışma sayfasında **düğme** <xref:Microsoft.Office.Tools.Excel.Controls.Button> denetiksahipseniz, <xref:System.Windows.Forms.Button> nesneyi başvuru veya atama sırasında değil, türü belirttiğinizden emin olun.|
|Denetim konumu ve boyutu|Denetimin boyutu ve konumu, kapsayıcı ActiveX denetiminin parçası olan özelliklere göre belirlenir. ActiveX denetim özellikleri, Windows Forms denetiminin denk özelliklerinden farklı değerler alır. `Top` `Left` Bir denetimin,, veya özelliklerini ayarladığınızda, `Height` `Width` piksel yerine punto olarak ölçülür.|
|Word belgelerindeki denetim konumu|Akış tabanlı bir düzene denetimler eklerseniz, denetimlerin içerik değiştikçe içerik ile akacağını aklınızda bulundurun. Denetim **araç** çubuğundan sürüklediğiniz sırada bir paragrafa bağlayamazsınız. Bu denetim, metin içeren satır içindeki Word belgesine eklenir. Denetimi eklemek için başka bir yöntem kullanıyorsanız (denetime çift tıklanması gibi), Denetim resim ekleme için ayarladığınız sözcük seçeneğine göre eklenir.<br /><br /> `Left` `Top` Metin ile satır içi bir denetimin veya özelliğini ayarlayamazsınız.<br /><br /> Bir üst bilgi veya altbilgiye veya bir alt belge içine denetim yerleştirebilirsiniz.|
|Denetim olayları|Denetim seçildiğinde, olayları aşağıdaki sırayla başlatır:<br /><br /> 1.  `Enter`<br />iki.  `GotFocus`<br /><br /> Denetim seçimi kaldırıldığında olayları aşağıdaki sırayla başlatır:<br /><br /> 1.  `Leave`<br />iki.  `Validating`<br />03.  `Validated`<br />4.  `LostFocus`|
|Denetim ölçeklendirme|Bir belgenin yakınlaştırma ayarını %100 dışında bir şekilde değiştirdiğinizde, denetimler belge ile ölçeklendirilmesine rağmen devre dışı bırakılır. Örneğin, belgeniz %130 yakınlaştırmadan bir düğmeye tıkladığınızda, yakınlaştırma %100 olarak ayarlanana kadar denetimin devre dışı bırakıldığını belirten bir ileti gösterilir. Yakınlaştırmayı %100 olarak değiştirdiğinizde denetimler doğru şekilde çalışır.|
|Denetim özelliği değerleri|Bir Windows formundaki denetimlerin özellikleri bir tamsayı değerine ayarlanmış olsa da, bir Word belgesindeki denetimler için tek bir olarak ayarlanır. Excel 'de denetimlerin özellik değerleri Double olarak ayarlanır. `Height` `Width` Çalışma sayfasındaki bir denetimin ve özelliği çalışma sayfasının veya ekranın boyutunu aşarsa, değer kesilir.|
|Yeniden boyutlandırma denetimi|Belgedeki bir denetimi sekiz boyutlandırma tutamaçlarından birini kullanarak yeniden boyutlandırırsanız, yeni denetim boyutları denetim yeniden seçilene kadar **Özellikler** penceresinde yansıtılmaz.|
|Denetim davranışı|Excel çalışma sayfasındaki denetimler, çalışma sayfası penceresi bölündüğünde tahmin edilemeyecek şekilde çalışmayabilir. Örneğin, çalışma sayfasındaki bir öğesine erişim <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> yalnızca pencerelerin birinde kullanılabilir olabilir.|
|Denetim adlandırması|Denetimleri adlandırmak için ayrılmış sözcükler kullanamazsınız. Örneğin, bir çalışma sayfasına bir ekler <xref:Microsoft.Office.Tools.Excel.Controls.Button> ve adı **sistem**olarak değiştirirseniz, projeyi oluşturduğunuzda hatalar oluşur.|
|Programlı olarak denetim ekleme|Çalışma zamanında belgenize denetim eklemek için denetimin oluşturucusunu kullanmayın. Bunun yerine, tarafından sağlanmış olan yardımcı yöntemlerini kullanın [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Örneğin, <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> bir çalışma sayfasına düğme eklemek için yöntemini kullanın. Bu yardımcı yöntemler tarafından desteklenmeyen bir denetim eklemek istiyorsanız, `AddControl` yöntemini kullanabilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Denetimleri kopyalama|Bir Windows Forms denetimini kopyalayıp çalışma zamanında bir belgeye yapıştırırsanız, boş bir kapsayıcı ActiveX denetimi belgeye yapıştırılır. Windows Forms denetimi yeni konumda görünmez ve özgün denetimin arkasındaki kod kapsayıcı ActiveX denetimine kopyalanmaz.|

## <a name="limitations-in-document-level-projects"></a>Belge düzeyi projelerindeki sınırlamalar

Belgeler üzerinde Windows Forms denetimleri kullanmanın bazı sınırlamaları belge düzeyi projelere özgüdür.

### <a name="control-support-at-design-time"></a>Tasarım zamanında denetim desteği

Visual Studio tasarımcısında bir Excel çalışma sayfası veya Word belgesi açıldığında bazı Windows Forms denetimleri **araç** çubuğundan kaldırılır. Bunun nedeni teknik sınırlamalardan veya işlevin Word veya Excel 'de zaten kullanılabilir olmasından kaynaklanır. Excel ve Word projeleri, belge odağa sahip olduğunda **araç kutusunda** görünen tüm Windows Forms denetimlerini ve diğer bileşenleri destekler ve ayrıca bir çalışma sayfasına veya belgeye üçüncü taraf denetimleri de ekleyebilirsiniz.

> [!NOTE]
> Bir Belge korunduğunda **araç** çubuğundan tüm denetimler kaldırılır. Belge koruma hakkında daha fazla bilgi için bkz. belge [düzeyi çözümlerinde belge koruma](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Üçüncü taraf denetimleri, <xref:System.Runtime.InteropServices.ComVisibleAttribute> bir Office çözümünde kullanılabilmesi için özniteliği **true** olarak ayarlanmış olmalıdır.

Aşağıdaki denetimler ve bileşenler **araç kutusunda**kullanılamaz:

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

### <a name="support-for-legacy-activex-controls"></a>Eski ActiveX denetimleri için destek

ActiveX denetimleri içeren mevcut bir Word belgesi veya Excel çalışma kitabı kullanan belge düzeyi Office projesi oluşturursanız, ActiveX denetimlerinin işlevselliği kaybolmaz; Ancak, Visual Studio içinden belgelerinize yeni ActiveX denetimleri ekleme desteği yoktur. Örneğin, Word belgeniz bir Visual Basic for Applications (VBA) makrosunu çalıştıran **Denetim** araç kutusundan bir düğmeye sahipse, belge bir Office projesinde kullanıldıktan sonra makroyu çalıştırmaya devam edecektir. Ancak, ActiveX denetimlerini ve VBA makrolarını kaldırmanız ve bunları Windows Forms denetimleri ve yönetilen kodla değiştirmeniz önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
