---
title: Office çözümlerinde WPF denetimlerini kullanma
description: Visual Studio 'da Kullanıcı arabirimleri tasarlamak için Windows Presentation Foundation (WPF) denetimlerini nasıl kullanabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 7bc720e6218e4cbb76b14f356d190b738e31ede3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921901"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Office çözümlerinde WPF denetimlerini kullanma

Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan çözümler, Windows Forms denetimleriyle doğrudan çalışmak üzere tasarlansa da, çözümlerinizde WPF denetimlerini de kullanabilirsiniz. Windows Presentation Foundation (WPF), kullanıcı arabirimlerinin tasarlanmasıyla ilgili Windows Forms bir alternatiftir. WPF, Kullanıcı arabirimi, medya ve belge eklemek için yeni teknikler sağlamak üzere Extensible Application Markup Language (XAML) adlı bir biçimlendirme dili kullanır. Daha fazla bilgi için bkz. [WPF genel bakış](/dotnet/framework/wpf/introduction-to-wpf).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Bir Office çözümünde Windows Forms denetimleri barındırasağlayan herhangi bir UI öğesi WPF denetimlerini de barındırabilir. Bunlar aşağıdaki öğeleri içerir:

- Belge düzeyi özelleştirmelerde belgeler ve çalışma sayfaları.

- Belge düzeyi özelleştirmelerde Eylemler bölmeleri.

- VSTO Eklentilerindeki özel görev bölmeleri.

- Outlook için VSTO Eklentilerindeki form bölgeleri.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Tasarım zamanında Office projelerine WPF denetimleri ekleme

Office çözümlerinde doğrudan UI öğelerine WPF denetimleri ekleyemezsiniz. Bunun yerine projenize bir **Kullanıcı denetimi (WPF)** öğesi ekleyin ve bunu WPF denetimleri için tasarım yüzeyi olarak kullanın. Daha sonra, WPF Kullanıcı denetimini projenizdeki bir kullanıcı arabirimi öğesine ekleyin.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Bir eylemler bölmesine, özel görev bölmesine veya form bölgesine WPF denetimleri eklemek için

1. Özel görev bölmesi, Eylemler bölmesi veya form bölgesi eklemek istediğiniz bir projeyi açın.

2. Projenize bir **Kullanıcı denetimi (WPF)** öğesi ekleyin.

3. **Araç kutusundan** WPF Kullanıcı denetimi TASARıM yüzeyine WPF denetimleri ekleyin.

     Varsayılan olarak, WPF Kullanıcı denetimi Tasarımcısı açık olduğunda, **araç kutusu** yalnızca WPF denetimleri içerir.

4. Projeyi derleyin.

5. Projenize bir eylemler bölmesi, form bölgesi veya özel görev bölmesi ekleyin:

    - Form bölgeleri için projeye bir **Outlook form bölgesi** öğesi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Eylemler bölmeleri için projeye bir **Eylemler bölmesi denetimi** veya **Kullanıcı denetim** öğesi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - Özel görev bölmeleri için, projeye bir **Kullanıcı denetim** öğesi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. **Araç kutusunun** *ProjectName* **WPF Kullanıcı denetimleri** sekmesinden, Eylemler bölmesi, form BÖLGESI veya özel görev bölmesi için WPF Kullanıcı denetimini tasarımcıya sürükleyin.

     Visual Studio otomatik olarak <xref:System.Windows.Forms.Integration.ElementHost> , Kullanıcı arabirimi ÖĞESINDE WPF Kullanıcı denetimini barındıran bir nesne oluşturur.

7. Projeyi yeniden derleyin.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Belge düzeyi projedeki bir belgeye veya çalışma sayfasına WPF denetimleri eklemek için

1. Word veya Excel için belge düzeyi projesi açın.

2. Projenize bir **Kullanıcı denetimi (WPF)** öğesi ekleyin.

3. **Araç kutusundan** WPF Kullanıcı denetimi TASARıM yüzeyine WPF denetimleri ekleyin.

4. Projeyi derleyin.

5. Projeye bir **Kullanıcı denetim** öğesi (bir Windows Forms Kullanıcı denetimi) ekleyin.

6. Windows Forms Kullanıcı denetimi için tasarımcıyı açın.

7. **Araç kutusunun** *ProjectName* **WPF Kullanıcı denetimleri** sekmesinden, WPF Kullanıcı denetimini tasarımcıya sürükleyin.

     Visual Studio otomatik olarak <xref:System.Windows.Forms.Integration.ElementHost> Windows Forms Kullanıcı DENETIMINDEKI WPF Kullanıcı denetimini barındıran bir nesne oluşturur.

8. Program aracılığıyla Windows Forms Kullanıcı denetimini belgeye veya çalışma kitabına ekleyen kodu yazın. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Windows Forms Kullanıcı denetimini tasarımcıda belgeye veya çalışma sayfasına sürükleyemezsiniz.

9. Projeyi yeniden derleyin.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>ElementHost sınıfını kullanarak WPF denetimleri barındırma

Visual Studio, Office çözümlerinizde Windows Forms denetimleri kullanmanıza yardımcı olan özellikler sağlar, ancak WPF denetimleri için benzer özellikler sağlamaz. Örneğin, denetimleri **araç kutusundan** sürükleyerek veya çalışma zamanında yardımcı yöntemler kullanarak belgelere ve çalışma sayfalarına Windows Forms denetimleri ekleyebilirsiniz. Ancak, bu araçlar WPF denetimleri için kullanılamaz.

WPF denetimleri, <xref:System.Windows.Forms.Integration.ElementHost> bir Windows Forms denetimi veya formu Ile WPF denetimleri arasında bir tümleştirme katmanı olarak sınıfını kullanır. Çözümünüze tasarım zamanında WPF denetimleri eklediğinizde, Visual Studio sizin için otomatik olarak bir <xref:System.Windows.Forms.Integration.ElementHost> nesne oluşturur.

## <a name="wpf-resources"></a>WPF kaynakları

Windows Forms denetimleri ve formlarında WPF denetimlerini barındırmak için mimari ve tasarım sorunları hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Windows Forms ve WPF birlikte çalışabilirlik giriş mimarisi](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Windows Forms ve WPF özellik eşlemesi](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [WPF ve Windows Forms birlikte çalışma](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Windows Forms denetimleri ve eşdeğer WPF denetimleri](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Tasarım zamanında Visual Studio 'daki Windows Forms denetimlerine ve formlara WPF denetimleri ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [İzlenecek yol: tasarım zamanında Windows Forms yeni WPF içeriği oluşturma](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [İzlenecek yol: tasarım zamanında Windows Forms WPF içeriğini düzenleme](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [İzlenecek yol: biçim WPF içeriği](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Ayrıca bkz.

- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Özel görev bölmeleri](../vsto/custom-task-panes.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
