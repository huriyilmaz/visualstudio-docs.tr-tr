---
title: Office UI özelleştirmesi
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 257f87aedf5d4337e81fb6f251cc8df07f4e577c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88041070"
---
# <a name="office-ui-customization"></a>Office UI özelleştirmesi
  Visual Studio 'da Office geliştirici araçlarını kullanarak Microsoft Office uygulamalarının Kullanıcı arabirimini (UI) özelleştirebilirsiniz. Bu konuda, aşağıdaki bölümlerde özelleştirebileceğiniz Kullanıcı arabirimi özellikleri açıklanmaktadır:

- [UI özelliklerinin karşılaştırması](#Comparison)

- [Eylemler bölmeleri ve özel görev bölmeleri](#Actions)

- [Özel şerit kullanıcı arabirimi](#Ribbon)

- [Backstage görünümü](#Backstage)

- [Outlook form bölgeleri](#FormRegion)

- [Belgelerdeki denetimler](#Controls)

- [Kısayol Menüleri](#Shortcut)

## <a name="comparison-of-ui-features"></a><a name="Comparison"></a> UI özelliklerinin karşılaştırması
 Aşağıdaki tabloda, Microsoft Office projelerinde özelleştirebileceğiniz ana UI özellikleri karşılaştırılmaktadır.

|Öne çıkan özelliği|Desteklenen proje türleri|Desteklenen Microsoft Office uygulamalar|
|-------------|-----------------------------|---------------------------------------------|
|Eylemler bölmesi|Belge düzeyinde özelleştirmeler|Excel<br /><br /> Word|
|Özel görev bölmeleri|VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|Özel şerit kullanıcı arabirimi|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Backstage görünümü|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Outlook form bölgeleri|VSTO eklentileri|Outlook|
|Belgelerdeki denetimler|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> Word|
|Kısayol Menüleri|Belge düzeyinde özelleştirmeler<br /><br /> VSTO eklentileri|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="actions-panes-and-custom-task-panes"></a><a name="Actions"></a> Eylemler bölmeleri ve özel görev bölmeleri
 Görev bölmeleri, genellikle bir Microsoft Office uygulamasındaki bir pencerenin bir tarafına yerleştirilen Kullanıcı arabirimi panolardır. Neredeyse tüm Microsoft Office uygulamalar yerleşik görev bölmelerini içerir. Word 'deki Yardım görev bölmesi bir görev bölmesi örneğidir.

 Visual Studio 'da Office geliştirme araçları, görev bölmelerini özelleştirmek için iki farklı yol sağlar:

- Belge düzeyi özelleştirmesinde bir eylemler bölmesi ekleyebilirsiniz. Varsayılan olarak, Eylemler bölmesi uygulamanın sağ tarafında, belgenin sağında görüntülenir. Ancak, Eylemler bölmesi belgenin sol, üst veya alt kısmına da gösterilebilir.

- Bir VSTO eklentisinin özel görev bölmesini ekleyebilirsiniz. Kullanıcılar özel görev bölmelerini uygulama penceresinin farklı taraflarına sabitleyebilir veya özel görev bölmelerini penceredeki herhangi bir konuma sürükleyebilir.

  Eylemler bölmeleri ve özel görev bölmeleri, kullanıcılara veri girişi gibi görevler konusunda yardımcı olmak için çeşitli denetimler barındırarak işlevsellik sağlar. Bir şerit grubuyla karşılaştırıldığında, Eylemler bölmeleri ve özel görev bölmeleri metin ve denetimleri içermesi için çok daha büyük bir alan sağlar.

  Eylemler bölmeleri hakkında daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md). Özel görev bölmeleri hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="custom-ribbon-ui"></a><a name="Ribbon"></a> Özel şerit kullanıcı arabirimi
 Office 'teki uygulamalara eklediğiniz işlevleri göstermek için şerit kullanıcı arabirimini özelleştirebilirsiniz. Şerit, daha kolay bulabilmeniz için ilgili komutları (denetimler biçiminde) düzenlemenin bir yoludur. Kullanıcılarınıza, çözümünüzde sağladığınız işlevlere erişim sağlamak için kendi şerit sekmelerinizi ve gruplarınızı oluşturabilirsiniz. Microsoft Office sisteminin önceki sürümlerindeki menüler ve araç çubukları kullanılarak erişilen özelliklerin çoğuna artık şerit kullanılarak erişilebilir.

 Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

## <a name="backstage-view"></a><a name="Backstage"></a> Backstage görünümü
 Office uygulamalarında **Dosya** sekmesine tıkladığınızda Backstage görünümü açılır. Backstage görünümü, dosya düzeyi görevleri ve eylemleri birleştiren bir kullanıcı arabirimi sağlar ve 2007 Microsoft Office sistemindeki Microsoft Office düğmesinden sağlanan benzer işlevselliği değiştirir. Backstage görünümü XML kullanılarak tamamen genişletilebilir.

 Visual Studio, Backstage görünümünü özelleştirmek için bir tasarımcı veya API sağlamaz. Ancak, Office projenize bir **Şerit (XML)** öğesi eklerseniz, Backstage görünümünü özelleştirmek IÇIN Şerit XML dosyasına XML ekleyebilirsiniz. **Şerit (XML)** öğeleri hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md).

 Backstage görünümünü özelleştirme hakkında daha fazla bilgi için bkz. [geliştiriciler Için office 2010 Backstage görünümüne giriş](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) ve [geliştiriciler Için Office 2010 Backstage görünümünü özelleştirme](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

## <a name="outlook-form-regions"></a><a name="FormRegion"></a> Outlook form bölgeleri
 Standart Microsoft Office Outlook formlarına özel işlevsellik eklemek için form bölgelerini kullanın. Varolan bir formu ek alanlarla veya denetimlerle genişleten form bölgeleri oluşturabilirsiniz. Visual Studio 'da Office geliştirme araçları 'nı kullanarak yeni bir form bölgesi oluşturursanız, form bölgesindeki yalnızca Windows Forms denetimleri kullanabilirsiniz. Outlook 'ta tasarlanan bir form bölgesini içeri aktarırsanız, yalnızca yerel Outlook denetimleri kullanabilirsiniz.

 Outlook Kullanıcı arabirimindeki farklı alanları kaplayan form bölgeleri oluşturabilirsiniz. Örneğin, bitişik form bölgeleri formun ilk sayfasının alt kısmında görüntülenir ve her bitişik form bölgesi daraltılabilir olur. Ayrıca, tam bir ek form sayfası olarak görüntülenen ve var olan herhangi bir standart form veya özel form üzerinde görünebilen ayrı bir form bölgesi de ekleyebilirsiniz.

 Daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

## <a name="controls-on-documents"></a><a name="Controls"></a> Belgelerdeki denetimler
 Word belgelerine ve Excel çalışma sayfalarına çeşitli denetimler ekleyebilirsiniz. Örneğin, kullanıcının Tarihleri standart bir biçimde girebilmesi veya bir veritabanına veri göndermek üzere çalışma sayfasına düğme koymak için bir belgeye tarih seçici denetimi eklemek isteyebilirsiniz.

 Excel veya Word için belge düzeyi projeleri geliştirirken, tasarım zamanında projenizdeki belgeye veya çalışma kitabına denetim eklemek için Visual Studio tasarımcısını kullanabilir veya çalışma zamanında programlı bir şekilde denetim ekleyebilirsiniz. Excel veya Word için VSTO eklentisi projeleri geliştirirken, çalışma zamanında herhangi bir açık belge veya çalışma kitabına program aracılığıyla denetim ekleyebilirsiniz.

 Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) ve [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md).

## <a name="shortcut-menus"></a><a name="Shortcut"></a> Kısayol Menüleri
 Bir belgeye veya bir uygulama penceresine sağ tıkladığınızda bir kısayol menüsü görüntülenir. Bir kullanıcının bir belgeyi, çalışma kitabını veya konak denetimini sağ tıkladığı gibi bir olay gerçekleştikten sonra görüntülenecek kısayol menüsünü ayarlayabilirsiniz. Bir kısayol menüsüne birçok farklı menü komutu veya denetimi ekleyebilirsiniz. XML kullanarak kısayol menüleri oluşturun. Office projenize bir **Şerit (XML)** öğesi eklerseniz, kısayol menüleri oluşturmak IÇIN Şerit XML dosyasına XML ekleyebilirsiniz. Kısayol menüleri oluşturmak için XML kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Kısayol menülerine komut ekleme](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Office çözümlerinde WPF denetimlerini kullanma](../vsto/using-wpf-controls-in-office-solutions.md)
- [Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
- [İzlenecek yol: Windows formu kullanarak veri toplama](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
