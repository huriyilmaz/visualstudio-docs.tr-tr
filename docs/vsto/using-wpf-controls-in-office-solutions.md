---
title: WpF denetimlerini Office kullanma
description: Windows Presentation Foundation 'de kullanıcı arabirimleri tasarlamak için Windows Presentation Foundation (WPF) denetimlerini nasıl Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6f6acecd2d6554da0efbcb0b31d61d3f51511180
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114979"
---
# <a name="use-wpf-controls-in-office-solutions"></a>WpF denetimlerini Office kullanma

Visual Studio'daki Office geliştirme araçları kullanılarak oluşturulan çözümler Windows Forms denetimleriyle çalışacak şekilde tasarlanmış olsa da, çözümleriniz içinde WPF denetimlerini de kullanabilirsiniz. Windows Presentation Foundation (WPF), kullanıcı arabirimleri tasarlamaya Windows Forms'a alternatiftir. WPF kullanıcı arabirimi, medya ve Extensible Application Markup Language eklemeye yeni teknikler sağlamak için Extensible Application Markup Language (XAML) adlı bir işaretleme dili kullanır. Daha fazla bilgi için bkz. [WPF'ye genel bakış.](/dotnet/framework/wpf/introduction-to-wpf)

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Bir Office çözümünde Windows Forms denetimlerini barındıran herhangi bir kullanıcı arabirimi öğesi de WPF denetimlerini barındırabilirsiniz. Bunlar aşağıdaki öğeleri içerir:

- Belge düzeyi özelleştirmelerde belgeler ve çalışma sayfaları.

- Belge düzeyi özelleştirmelerde Eylemler bölmeleri.

- Eklentilerde özel VSTO bölmeleri.

- VSTO için eklentilerde bölgeleri Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Tasarım zamanında projelerini Office WPF denetimleri ekleme

WPF denetimlerini doğrudan kullanıcı arabirimi öğelerine ek olarak Office ekamazsiniz. Bunun yerine, **projenize bir Kullanıcı Denetimi (WPF)** öğesi ekleyin ve WPF denetimleri için tasarım yüzeyi olarak kullanın. Ardından, WPF kullanıcı denetimi projenizin kullanıcı arabirimi öğesine ekleyin.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Eylemler bölmesine, özel görev bölmesine veya form bölgenize WPF denetimleri eklemek için

1. Özel görev bölmesi, eylemler bölmesi veya form bölgesi eklemek istediğiniz bir projeyi açın.

2. Projenize **bir Kullanıcı Denetimi (WPF)** öğesi ekleyin.

3. Araç **Kutusundan,** WPF kullanıcı denetimi tasarım yüzeyine WPF denetimleri ekleyin.

     Varsayılan olarak, WPF kullanıcı denetimi tasarımcısı açık olduğunda, **Araç Kutusu yalnızca** WPF denetimlerini içerir.

4. Projeyi derleyin.

5. Projenize eylemler bölmesi, form bölgesi veya özel görev bölmesi ekleyin:

    - Form bölgeleri için projeye **Outlook Form Bölgesi** öğesi ekleyin. Daha fazla bilgi [için, bkz. How to: Add-in projesinde Outlook bölge ekleme.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

    - Eylemler bölmeleri için projeye **bir Eylem Bölmesi Denetimi** veya **Kullanıcı** Denetimi öğesi ekleyin. Daha fazla bilgi için [bkz. Nasıl kullanılır: Word belgelerine](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)veya çalışma kitaplarını Excel bölmesi ekleme.

    - Özel görev bölmeleri için projeye **bir Kullanıcı Denetimi** öğesi ekleyin. Daha fazla bilgi [için, bkz. How to: Add a custom task pane to an application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. Araç Kutusunun *ProjectName* **WPF Kullanıcı** Denetimleri sekmesinden, WPF kullanıcı denetimlerini eylemler bölmesi, form bölgesi veya özel görev bölmesi için tasarımcıya sürükleyin. 

     Visual Studio, KULLANıCı arabirimi <xref:System.Windows.Forms.Integration.ElementHost> öğesinde WPF kullanıcı denetimi barındıran bir nesneyi otomatik olarak oluşturur.

7. Projeyi yeniden oluşturma.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Belge düzeyi projesinde bir belgeye veya çalışma sayfasına WPF denetimleri eklemek için

1. Word veya Excel için belge düzeyinde bir Excel.

2. Projenize **bir Kullanıcı Denetimi (WPF)** öğesi ekleyin.

3. Araç **Kutusundan,** WPF kullanıcı denetimi tasarım yüzeyine WPF denetimleri ekleyin.

4. Projeyi derleyin.

5. Projeye **bir Kullanıcı** Denetimi öğesi (Windows Forms kullanıcı denetimi) ekleyin.

6. Windows Forms kullanıcı denetimi için tasarımcıyı açın.

7. Araç Kutusunun *ProjectName* **WPF Kullanıcı** Denetimleri sekmesinden, WPF kullanıcı denetimlerini tasarımcıya sürükleyin. 

     Visual Studio, Windows Forms kullanıcı denetiminde WPF kullanıcı denetimi barındıran <xref:System.Windows.Forms.Integration.ElementHost> bir nesneyi otomatik olarak oluşturur.

8. Windows Forms kullanıcı Windows belgeye veya çalışma kitabına program aracılığıyla ekleyen kod yazın. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

    > [!NOTE]
    > Windows Forms kullanıcı denetimlerini tasarımcıda belgeye veya çalışma sayfasına sürükleyebilirsiniz.

9. Projeyi yeniden oluşturma.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>ElementHost sınıfını kullanarak WPF denetimlerini barındırma

Visual Studio, Windows Forms denetimlerini Office özellikleri sağlar, ancak WPF denetimleri için benzer özellikler sağlamaz. Örneğin, araç kutusundan Windows veya yardımcı yöntemleri kullanarak çalışma zamanında denetimleri sürükleyerek tasarım zamanında belgelere ve çalışma sayfalarına form formları denetimleri ekleyebilirsiniz. Ancak, bu araçlar WPF denetimleri için kullanılamaz.

WPF denetimleri, sınıfını bir Windows Forms denetimi veya formu ile WPF denetimleri <xref:System.Windows.Forms.Integration.ElementHost> arasında tümleştirme katmanı olarak kullanır. Tasarım zamanında çözümünüze WPF denetimleri eklerken, Visual Studio otomatik olarak bir <xref:System.Windows.Forms.Integration.ElementHost> nesne oluşturur.

## <a name="wpf-resources"></a>WPF kaynakları

WPF denetimlerini Windows Forms denetim ve formlarında barındırmaya ilişkin mimari ve tasarım sorunları hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Windows Formlar ve WPF birlikte çalışabilirlik giriş mimarisi](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Windows Formlar ve WPF özellik eşlemesi](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [WPF ve Windows Forms birlikte çalışabilirliği](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Windows Form denetimleri ve eşdeğer WPF denetimleri](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

WpF denetimlerini tasarım zamanında Windows Formlar denetimlerine ve formlarına Visual Studio daha fazla bilgi için aşağıdaki konulara bakın:

- [Adım adım kılavuz: Windows Forms'ta tasarım zamanında yeni WPF içeriği oluşturma](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Adım adım kılavuz: WPF içeriğini tasarım Windows formlarında düzenleme](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Adım adım kılavuz: WPF içeriği stili](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Ayrıca bkz.

- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Form Outlook bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Nasıl kullanılır: Word belgelerine veya çalışma kitaplarını Excel bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Nasıl ekleyebilirsiniz: Uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Nasıl yapılanlar: Eklenti projesine Outlook bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
