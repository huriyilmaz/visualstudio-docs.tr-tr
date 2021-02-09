---
title: Office proje şablonlarına genel bakış
description: Visual Studio 'daki Microsoft Office Geliştirici araçlarının farklı türlerde Office çözümleri oluşturmak için proje şablonları nasıl dahil edileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], about project templates
- Excel Workbook project template
- Word Template project template
- Excel [Office development in Visual Studio], project templates
- Project [Office development in Visual Studio], project templates
- project templates [Office development in Visual Studio]
- project templates, Word
- InfoPath [Office development in Visual Studio], project templates
- Excel Template project template
- project templates, 2007 Microsoft Office system
- project templates, Excel
- PowerPoint [Office development in Visual Studio], project templates
- Word [Office development in Visual Studio], Word project templates
- Office projects [Office development in Visual Studio], templates
- Excel projects in Visual Studio
- Word Document project template
- Visio [Office development in Visual Studio], project templates
- Word projects in Visual Studio
- Outlook [Office development in Visual Studio], project templates
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af01bf165c823ce34957e4a9eba38ef90c5344a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892040"
---
# <a name="office-project-templates-overview"></a>Office proje şablonlarına genel bakış
  Visual Studio 'daki Microsoft Office geliştirici araçları, aşağıdaki türlerde Office çözümlerini oluşturmaya yönelik proje şablonları içerir:

- [Belge düzeyinde özelleştirmeler](#DocLevel)

- [VSTO eklentileri](#AppLevel)

  Bu tür Office çözümlerinin ayrıntılı bir karşılaştırması için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

  Office proje şablonları, **Yeni proje** iletişim kutusunda, **Visual C#** ve **Visual Basic** dil düğümlerinin **Office** düğümü altında bulunur. Her şablon, derleme başvuruları ve hata ayıklama ayarları dahil olmak üzere, hedef uygulamaya uygun yapılandırmaya sahip bir proje oluşturur.

  Her proje, belirli bir çözüm türü üzerinde çalışmaya başlamanızı sağlayacak dosyaları ve kodu sunar. Her bir proje için üretilen kod, başlangıç ve kapatma olayı işleyicilerini içerir. Yüklendiğinde çözümünüzü başlatmak ve kaldırıldığında çözümünüzü temizlemek için, bu olay işleyicilerine kod ekleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md) ve [Office Projelerindeki Olaylar](../vsto/events-in-office-projects.md).

> [!NOTE]
> Office geliştirme araçları Visual Studio'nun belirli sürümlerinde yer alır. Daha fazla bilgi için bkz. [Office çözümleri geliştirmek için bir bilgisayarı yapılandırma](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="document-level-customizations"></a><a name="DocLevel"></a> Belge düzeyi özelleştirmeleri
 **Yeni proje** Iletişim kutusundaki **Office** düğümü, Word ve Excel için belge düzeyi özelleştirmeleri oluşturmaya başlamanızı sağlamak üzere aşağıdaki proje şablonlarını sağlar:

- **Word 2013 ve 2016 VSTO belgesi**

- **Word 2013 ve 2016 VSTO şablonu**

- **Excel 2013 ve 2016 VSTO çalışma kitabı**

- **Excel 2013 ve 2016 VSTO şablonu**

- **Word 2010 VSTO belgesi**

- **Word 2010 VSTO şablonu**

- **Excel 2010 VSTO çalışma kitabı**

- **Excel 2010 VSTO şablonu**

  Word Belgesi ve Excel Çalışma Kitabı proje şablonları, belirli bir belgeyi veya çalışma sayfasını temel alan bir çözüm oluşturmaya başlamanızı sağlayacak kodu sunar. Bu tür çözümlerde kodunuz sadece Word veya Excel'de ilişkili belge açıksa çalışır.

  Word Şablonu ve Excel Şablonu proje şablonları, Word Belgesi ve Excel Çalışma Kitabı proje şablonlarıyla aynı şekilde davranır. Bununla birlikte, Word Şablonu ve Excel Şablonu proje şablonları, kullanıcıların çözümünüzdeki özelleştirilmiş şablonun yeni yerel belge veya çalışma kitabı kopyalarını oluşturmasını kolaylaştırır. Çözümünüzdeki özellikler, kullanıcının şablondan oluşturduğu yeni belgeden kullanılabilir.

> [!NOTE]
> Yönetilen kod uzantılarına başvuran Word şablonları genel VSTO eklentileri olarak kullanılamaz. Şablon Word Başlangıç dizininden yüklenirse derleme çağrılmaz. Daha fazla bilgi için bkz. [Genel şablonlar ve Excel eklentilerinin (. xla dosyaları) sınırlamaları](#Limitations).

 Bu proje türleriyle çalışmaya başlama hakkında bilgi için aşağıdaki konulara bakın:

- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)

- [Word çözümleri](../vsto/word-solutions.md)

- [Excel çözümleri](../vsto/excel-solutions.md)

- [İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="vsto-add-ins"></a><a name="AppLevel"></a> VSTO eklentileri
 **Yeni proje** Iletişim kutusundaki **Office/SHAREPOINT** düğümü, VSTO eklentileri oluşturmaya başlamanızı sağlamak için aşağıdaki proje şablonlarını sağlar.

- **Excel 2013 ve 2016 VSTO eklentisi**

- **InfoPath 2013 VSTO eklentisi**

- **Outlook 2013 ve 2016 VSTO eklentisi**

- **PowerPoint 2013 ve 2016 eklentisi**

- **Proje 2013 ve 2016 eklentisi**

- **Visio 2013 ve 2016 eklentisi**

- **Word 2013 ve 2016 eklentisi**

- **Excel 2010 eklentisi**

- **InfoPath 2010 eklentisi**

- **Outlook 2010 eklentisi**

- **PowerPoint 2010 eklentisi**

- **Proje 2010 eklentisi**

- **Visio 2010 eklentisi**

- **Word 2010 eklentisi**

  Bu proje şablonlarından birini temel alan bir proje oluşturduğunuzda, çözümünüzdeki kod ilişkili uygulama açıldığı zaman çalışır. Belge düzeyinde projelerin aksine, kodunuz tek bir belgeyle ilişkili değildir.

  Bu proje türleriyle çalışmaya başlama hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md)

- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)

- [İzlenecek yol: Excel için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [İzlenecek yol: Outlook için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [İzlenecek yol: PowerPoint için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [İzlenecek yol: proje için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [İzlenecek yol: Word için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Belge ve şablon çözümleri karşılaştırması
 Word belgesi veya Excel çalışma kitabı etrafında bir çözüm tasarladığınızda, bu belgeyi kullanıcılarınıza sunmanın en iyi yoluna karar vermelisiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bazı durumlarda her kullanıcıya belgenin bir kopyasını vermek isteyebilirsiniz. Bu durumda, çözümünüzü Excel veya Word belgesi projesi olarak oluşturun.

 Diğer durumlarda, bir şablonu sunucuda kullanıma açmak isteyebilirsiniz; böylelikle her kullanıcı şablonu açıp yerel kopyasını belge olarak kaydedebilir. Bu durumda, çözümünüzü Excel veya Word şablonu projesi olarak oluşturun.

## <a name="comparison"></a>Karşılaştırma
 Aşağıdaki tabloda belgeler ile şablonlar arasındaki farklar ana hatlarıyla açıklanmıştır.

|Belgeler|Şablonlar|
|---------------|---------------|
|Kullanıcılar, salt okunur olmadığı sürece belgeyi açıp değiştirebilir. Kaydedilen tüm değişiklikler özgün belgede tutulur.|Kullanıcılar yeni bir belge olarak yerel kopya oluşturmak üzere şablonu açabilir. Özel izinler verilmediği sürece özgün belgede değişiklik yapamazlar.|
|Açıldığında, belge <xref:Microsoft.Office.Tools.Word.Document.Open> olayını oluşturur.|Açıldığında, şablon <xref:Microsoft.Office.Tools.Word.Document.New> olayını oluşturur.|

## <a name="limitations-of-global-templates-and-excel-add-ins-xla-files"></a><a name="Limitations"></a> Genel şablonlar ve Excel eklentilerinin (. xla dosyaları) sınırlamaları
 Belgeler, çalışma kitapları ve şablonlar, genel şablonlar veya Excel VSTO eklentileri (. xla dosyaları) olarak doğru çalışmayabilir.

## <a name="word-templates"></a>Word şablonları
 Bir Microsoft Office Word şablonunun yönetilen kod uzantıları varsa, şablonun bir genel şablon olarak iliştirilmesi veya Word'ün başlangıç dizininden yüklenmesi durumunda proje derlemesi çağrılmaz. Ayrıca belge, bir Office çözümünün parçası olan şablonun biçimini tanımaz.

## <a name="excel-add-ins-xla-files"></a>Excel eklentileri (. xla dosyaları)
 Excel VSTO eklentisi (*. xla* dosyası) oluşturmaya yönelik bir Office projesi yok. Bir çalışma kitabını .xla dosyası olarak kaydetmek mümkündür, ancak bu desteklenen bir işlem değildir ve önerilmez. Yönetilen kod uzantılarına sahip bir çalışma kitabını **Microsoft Office Excel Add-In ( \* . xla)** dosyası olarak kaydederseniz, başka bir çalışma kitabına uygulamak için **Eklentiler** iletişim kutusunda bunu seçebilirsiniz. Bazı durumlarda, VSTO eklentisi uygulandıktan sonra kodunuz hedef çalışma kitabında çalışır, ancak bu tür Office çözümünün kullanılması desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Excel için belge düzeyi özelleştirmelerini Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Word için belge düzeyi özelleştirmeleri Programlamaya Başlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md)
