---
title: Office UI özelleştirmesi
description: Visual Studio Office geliştirici araçlarını kullanarak Microsoft Office uygulamalarının kullanıcı arabirimini (uı) nasıl özelleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0b3f49a6e1ff74eda4561b4fc0283ca9196f8040
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155635"
---
# <a name="office-ui-customization"></a>Office UI özelleştirmesi
  Microsoft Office uygulamalarının kullanıcı arabirimini (uı), Visual Studio Office geliştirici araçlarını kullanarak özelleştirebilirsiniz. Bu konuda, aşağıdaki bölümlerde özelleştirebileceğiniz Kullanıcı arabirimi özellikleri açıklanmaktadır:

- [UI özelliklerinin karşılaştırması](#Comparison)

- [Eylemler bölmeleri ve özel görev bölmeleri](#Actions)

- [Özel şerit kullanıcı arabirimi](#Ribbon)

- [Backstage görünümü](#Backstage)

- [Outlook form bölgeleri](#FormRegion)

- [Belgelerdeki denetimler](#Controls)

- [Kısayol Menüleri](#Shortcut)

## <a name="comparison-of-ui-features"></a><a name="Comparison"></a> UI özelliklerinin karşılaştırması
 aşağıdaki tabloda, Microsoft Office projelerinde özelleştirebileceğiniz ana uı özellikleri karşılaştırılmaktadır.

|Özellik|Desteklenen proje türleri|desteklenen Microsoft Office uygulamalar|
|-------------|-----------------------------|---------------------------------------------|
|Eylemler bölmesi|Belge düzeyinde özelleştirmeler|Excel<br /><br /> Word|
|Özel görev bölmeleri|VSTO Eklentiler|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|Özel şerit kullanıcı arabirimi|Belge düzeyinde özelleştirmeler<br /><br /> VSTO Eklentiler|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Backstage görünümü|Belge düzeyinde özelleştirmeler<br /><br /> VSTO Eklentiler|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Outlook form bölgeleri|VSTO Eklentiler|Outlook|
|Belgelerdeki denetimler|Belge düzeyinde özelleştirmeler<br /><br /> VSTO Eklentiler|Excel<br /><br /> Word|
|Kısayol Menüleri|Belge düzeyinde özelleştirmeler<br /><br /> VSTO Eklentiler|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="actions-panes-and-custom-task-panes"></a><a name="Actions"></a> Eylemler bölmeleri ve özel görev bölmeleri
 görev bölmeleri, genellikle bir Microsoft Office uygulamasındaki bir pencerenin bir tarafına yerleştirilen kullanıcı arabirimi panolardır. neredeyse tüm Microsoft Office uygulamalar yerleşik görev bölmelerini içerir. Word 'deki Yardım görev bölmesi bir görev bölmesi örneğidir.

 Visual Studio Office geliştirme araçları, görev bölmelerini özelleştirmek için iki farklı yol sağlar:

- Belge düzeyi özelleştirmesinde bir eylemler bölmesi ekleyebilirsiniz. Varsayılan olarak, Eylemler bölmesi uygulamanın sağ tarafında, belgenin sağında görüntülenir. Ancak, Eylemler bölmesi belgenin sol, üst veya alt kısmına da gösterilebilir.

- VSTO bir eklentiye özel bir görev bölmesi ekleyebilirsiniz. Kullanıcılar özel görev bölmelerini uygulama penceresinin farklı taraflarına sabitleyebilir veya özel görev bölmelerini penceredeki herhangi bir konuma sürükleyebilir.

  Eylemler bölmeleri ve özel görev bölmeleri, kullanıcılara veri girişi gibi görevler konusunda yardımcı olmak için çeşitli denetimler barındırarak işlevsellik sağlar. Bir şerit grubuyla karşılaştırıldığında, Eylemler bölmeleri ve özel görev bölmeleri metin ve denetimleri içermesi için çok daha büyük bir alan sağlar.

  Eylemler bölmeleri hakkında daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md). Özel görev bölmeleri hakkında daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="custom-ribbon-ui"></a><a name="Ribbon"></a> Özel şerit kullanıcı arabirimi
 Office ' deki uygulamalara eklediğiniz işlevleri göstermek için şerit kullanıcı arabirimini özelleştirebilirsiniz. Şerit, daha kolay bulabilmeniz için ilgili komutları (denetimler biçiminde) düzenlemenin bir yoludur. Kullanıcılarınıza, çözümünüzde sağladığınız işlevlere erişim sağlamak için kendi şerit sekmelerinizi ve gruplarınızı oluşturabilirsiniz. Microsoft Office sisteminin önceki sürümlerindeki menüler ve araç çubukları kullanılarak erişilen özelliklerin çoğuna artık şerit kullanılarak erişilebilir.

 Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

## <a name="backstage-view"></a><a name="Backstage"></a> Backstage görünümü
 Office uygulamalarda **dosya** sekmesine tıkladığınızda Backstage görünümü açılır. Backstage görünümü, dosya düzeyi görevleri ve eylemleri birleştiren bir kullanıcı arabirimi sağlar ve 2007 Microsoft Office sistemindeki Microsoft Office düğmesinden sağlanan benzer işlevselliği değiştirir. Backstage görünümü XML kullanılarak tamamen genişletilebilir.

 Visual Studio, Backstage görünümünü özelleştirmek için bir tasarımcı veya apı sağlamaz. ancak, Office projenize bir **şerit (XML)** öğesi eklerseniz, Backstage görünümünü özelleştirmek için şerit xml dosyasına XML ekleyebilirsiniz. **Şerit (XML)** öğeleri hakkında daha fazla bilgi için bkz. [Ribbon XML](../vsto/ribbon-xml.md).

 Backstage görünümünü özelleştirme hakkında daha fazla bilgi için bkz. [geliştiriciler için Office 2010 backstage görünümüne giriş](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) ve [geliştiriciler için Office 2010 backstage görünümünü özelleştirme](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

## <a name="outlook-form-regions"></a><a name="FormRegion"></a>Outlook form bölgeleri
 standart Microsoft Office Outlook formlarına özel işlevsellik eklemek için form bölgelerini kullanın. Varolan bir formu ek alanlarla veya denetimlerle genişleten form bölgeleri oluşturabilirsiniz. Visual Studio ' de Office geliştirme araçlarını kullanarak yeni bir form bölgesi oluşturursanız, form bölgesindeki yalnızca Windows Forms denetimleri kullanabilirsiniz. Outlook ' de tasarlanan bir form bölgesini içeri aktarırsanız, yalnızca yerel Outlook denetimleri kullanabilirsiniz.

 Outlook Kullanıcı arabiriminin farklı alanları kaplayan form bölgeleri oluşturabilirsiniz. Örneğin, bitişik form bölgeleri formun ilk sayfasının alt kısmında görüntülenir ve her bitişik form bölgesi daraltılabilir olur. Ayrıca, tam bir ek form sayfası olarak görüntülenen ve var olan herhangi bir standart form veya özel form üzerinde görünebilen ayrı bir form bölgesi de ekleyebilirsiniz.

 daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

## <a name="controls-on-documents"></a><a name="Controls"></a> Belgeler üzerinde denetimler
 Word belgelerine ve çalışma sayfalarına çeşitli denetimler Excel ekleyebilirsiniz. Örneğin, kullanıcının tarihleri standart biçimde gire bir belgeye tarih seçici denetimi eklemek veya bir veritabanına veri göndermek için çalışma sayfasına bir düğme koymak istiyor olabilirsiniz.

 Excel veya Word için belge düzeyi projeler geliştirirken, tasarım zamanında projenizin belge veya çalışma kitabına denetim eklemek için Visual Studio tasarımcısını kullanabilir veya çalışma zamanında program aracılığıyla denetimler ekleyebilirsiniz. Excel veya Word VSTO eklenti projeleri geliştirirken, çalışma zamanında herhangi bir açık belgeye veya çalışma kitabına programlı olarak denetimler ekleyebilirsiniz.

 Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel](../vsto/host-items-and-host-controls-overview.md) [bakış Windows belgelerine genel Office form denetimleri.](../vsto/windows-forms-controls-on-office-documents-overview.md)

## <a name="shortcut-menus"></a><a name="Shortcut"></a> Kısayol Menüleri
 Bir belgeye veya uygulama penceresine sağ tıklarken kısayol menüsü görüntülenir. Kullanıcı bir belgeye, çalışma kitabına veya konak denetimine sağ tıkladığında gibi bir olay gerçekleştikten sonra görünecek bir kısayol menüsü ayarlayın. Kısayol menüsüne bir dizi farklı menü komutu veya denetim ekleyebilirsiniz. XML kullanarak kısayol menüleri oluşturun. Office projenize Şerit **(XML)** öğesi eklersiniz, kısayol menüleri oluşturmak için Şerit XML dosyasına XML eklersiniz. Kısayol menüleri oluşturmak için XML kullanma hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Kısayol menülerine komut ekleme.](../vsto/how-to-add-commands-to-shortcut-menus.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Windows belgelere genel bakış Office form denetimleri](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [WpF denetimlerini Office kullanma](../vsto/using-wpf-controls-in-office-solutions.md)
- [Nasıllı: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [Nasıl kullanılır: Eklenti kullanıcı arabirimi hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Adım adım kılavuz: Bir form kullanarak Windows toplama](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
