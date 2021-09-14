---
title: Office şablonlarına genel bakış
description: Microsoft Office geliştirici araçlarının farklı türlerde Visual Studio çözüm oluşturmak için proje şablonlarını nasıl Office öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2436ccd10cc6ce8eb670be5e6cc537e0193171b9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726107"
---
# <a name="office-project-templates-overview"></a>Office şablonlarına genel bakış
  Aşağıdaki Microsoft Office geliştirici araçları Visual Studio aşağıdaki türlerde çözüm oluşturmak için proje Office içerir:

- [Belge düzeyinde özelleştirmeler](#DocLevel)

- [VSTO Eklentiler](#AppLevel)

  Bu tür çözüm çözümlerinin ayrıntılı bir karşılaştırması Office için [bkz. Office çözüm geliştirmeye genel &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

  Office proje **şablonları, Visual C#** **ve** Project dil düğümlerinin **Office** yeni Visual Basic iletişim **kutusunda** kullanılabilir. Her şablon, derleme başvuruları ve hata ayıklama ayarları dahil olmak üzere, hedef uygulamaya uygun yapılandırmaya sahip bir proje oluşturur.

  Her proje, belirli bir çözüm türü üzerinde çalışmaya başlamanızı sağlayacak dosyaları ve kodu sunar. Her bir proje için üretilen kod, başlangıç ve kapatma olayı işleyicilerini içerir. Yüklendiğinde çözümünüzü başlatmak ve kaldırıldığında çözümünüzü temizlemek için, bu olay işleyicilerine kod ekleyebilirsiniz. Daha fazla bilgi için [bkz. Office ortamındaki Visual Studio projelerini ve](../vsto/office-projects-in-the-visual-studio-environment.md) Office [projelerinde olaylar.](../vsto/events-in-office-projects.md)

> [!NOTE]
> Office geliştirme araçları Visual Studio'nun belirli sürümlerinde yer alır. Daha fazla bilgi için, [bkz. Configure a computer to develop Office .](../vsto/configuring-a-computer-to-develop-office-solutions.md)

## <a name="document-level-customizations"></a><a name="DocLevel"></a> Belge düzeyinde özelleştirmeler
 Yeni **Office** iletişim kutusundaki  Project düğümü, Word ve Excel için belge düzeyinde özelleştirmeler oluşturmaya başlamanız için aşağıdaki proje Excel:

- **Word 2013 ve 2016 VSTO Belgesi**

- **Word 2013 ve 2016 VSTO Şablonu**

- **Excel 2013 ve 2016 VSTO Çalışma Kitabı**

- **Excel 2013 ve 2016 VSTO Şablonu**

- **Word 2010 VSTO Belgesi**

- **Word 2010 VSTO Şablonu**

- **Excel 2010 VSTO Çalışma Kitabı**

- **Excel 2010 VSTO Şablonu**

  Word Belgesi ve Excel Çalışma Kitabı proje şablonları, belirli bir belgeyi veya çalışma sayfasını temel alan bir çözüm oluşturmaya başlamanızı sağlayacak kodu sunar. Bu tür çözümlerde kodunuz sadece Word veya Excel'de ilişkili belge açıksa çalışır.

  Word Şablonu ve Excel Şablonu proje şablonları, Word Belgesi ve Excel Çalışma Kitabı proje şablonlarıyla aynı şekilde davranır. Bununla birlikte, Word Şablonu ve Excel Şablonu proje şablonları, kullanıcıların çözümünüzdeki özelleştirilmiş şablonun yeni yerel belge veya çalışma kitabı kopyalarını oluşturmasını kolaylaştırır. Çözümünüzdeki özellikler, kullanıcının şablondan oluşturduğu yeni belgeden kullanılabilir.

> [!NOTE]
> Yönetilen kod uzantılarına başvurulan sözcük şablonları, genel VSTO olarak kullanılamaz. Şablon Word'in Başlangıç dizininden yüklenirse derleme çağrılmaz. Daha fazla bilgi için [bkz. Genel şablonların ve Excel (.xla dosyaları) sınırlamaları.](#Limitations)

 Bu proje türleriyle çalışmaya başlama hakkında bilgi için aşağıdaki konulara bakın:

- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)

- [Sözcük çözümleri](../vsto/word-solutions.md)

- [Excel çözümleri](../vsto/excel-solutions.md)

- [Adım adım kılavuz: Word için ilk belge düzeyi özelleştirmenizi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

- [Adım adım kılavuz: Belge düzeyi için ilk belge düzeyi özelleştirmenizi Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)

## <a name="vsto-add-ins"></a><a name="AppLevel"></a>VSTO Eklentiler
 Yeni **Office/SharePoint** **iletişim** kutusundaki Project düğümü, VSTO Eklentilerini oluşturmaya başlamanıza VSTO sağlar.

- **Excel 2013 ve 2016 VSTO Eklenti**

- **InfoPath 2013 VSTO Eklenti**

- **Outlook 2013 ve 2016 VSTO Eklenti**

- **PowerPoint 2013 ve 2016 Eklenti**

- **Project 2013 ve 2016 Eklenti**

- **Visio 2013 ve 2016 Eklenti**

- **Word 2013 ve 2016 Eklenti**

- **Excel 2010 Eklenti**

- **InfoPath 2010 Eklenti**

- **Outlook 2010 Eklenti**

- **PowerPoint 2010 Eklenti**

- **Project 2010 Eklenti**

- **Visio 2010 Eklenti**

- **Word 2010 Eklenti**

  Bu proje şablonlarından birini temel alan bir proje oluşturduğunuzda, çözümünüzdeki kod ilişkili uygulama açıldığı zaman çalışır. Belge düzeyinde projelerin aksine, kodunuz tek bir belgeyle ilişkili değildir.

  Bu proje türleriyle çalışmaya başlama hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Kullanmaya başlayın programlama VSTO Eklentileri](../vsto/getting-started-programming-vsto-add-ins.md)

- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)

- [Adım adım kılavuz: VSTO için İlk Eklentinizi Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Adım adım kılavuz: VSTO için İlk Eklentinizi Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [adım adım kılavuz: VSTO için İlk Eklentinizi PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Adım adım kılavuz: VSTO için İlk Eklentinizi Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Kılavuz: Word için VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

## <a name="document-vs-template-solutions"></a>Belge ve şablon çözümleri
 Word belgesi veya Excel çalışma kitabı etrafında bir çözüm tasarladığınızda, bu belgeyi kullanıcılarınıza sunmanın en iyi yoluna karar vermelisiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bazı durumlarda her kullanıcıya belgenin bir kopyasını vermek isteyebilirsiniz. Bu durumda, çözümünüzü Excel veya Word belgesi projesi olarak oluşturun.

 Diğer durumlarda, bir şablonu sunucuda kullanıma açmak isteyebilirsiniz; böylelikle her kullanıcı şablonu açıp yerel kopyasını belge olarak kaydedebilir. Bu durumda, çözümünüzü Excel veya Word şablonu projesi olarak oluşturun.

## <a name="comparison"></a>Karşılaştırma
 Aşağıdaki tabloda belgeler ile şablonlar arasındaki farklar ana hatlarıyla açıklanmıştır.

|Belgeler|Şablonlar|
|---------------|---------------|
|Kullanıcılar, salt okunur olmadığı sürece belgeyi açıp değiştirebilir. Kaydedilen tüm değişiklikler özgün belgede tutulur.|Kullanıcılar yeni bir belge olarak yerel kopya oluşturmak üzere şablonu açabilir. Özel izinler verilmediği sürece özgün belgede değişiklik yapamazlar.|
|Açıldığında, belge olayı <xref:Microsoft.Office.Tools.Word.Document.Open> yükselter.|Şablon açıldığında olayı <xref:Microsoft.Office.Tools.Word.Document.New> oluşturur.|

## <a name="limitations-of-global-templates-and-excel-add-ins-xla-files"></a><a name="Limitations"></a>Genel şablonların ve Excel (.xla Dosyaları) sınırlamaları
 Belgeler, çalışma kitapları ve şablonlar, genel şablonlar veya Excel VSTO (.xla dosyaları) olarak düzgün çalışmayabilir.

## <a name="word-templates"></a>Sözcük şablonları
 Bir Microsoft Office Word şablonunun yönetilen kod uzantıları varsa, şablonun bir genel şablon olarak iliştirilmesi veya Word'ün başlangıç dizininden yüklenmesi durumunda proje derlemesi çağrılmaz. Ayrıca belge, bir Office çözümünün parçası olan şablonun biçimini tanımaz.

## <a name="excel-add-ins-xla-files"></a>Excel Eklentiler (.xla Dosyaları)
 Bir Office *(.xla* dosyası) Excel VSTO proje yoktur. Bir çalışma kitabını .xla dosyası olarak kaydetmek mümkündür, ancak bu desteklenen bir işlem değildir ve önerilmez. Yönetilen kod uzantılarına sahip bir çalışma kitabını **Microsoft Office Excel Add-In ( \* .xla)** dosyası olarak kaydederek başka bir çalışma kitabına uygulamak için Eklentiler iletişim kutusundan bu çalışma kitabını kullanabilirsiniz.  Bazı durumlarda kodunuz, VSTO Eklenti uygulandıktan sonra hedef çalışma kitabında çalıştır ancak Office böyle bir kullanım desteklenmiyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Kullanmaya başlayın için belge düzeyinde özelleştirmeler programlama Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Kullanmaya başlayın word için belge düzeyinde özelleştirmeler programlama](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Kullanmaya başlayın programlama VSTO Eklentileri](../vsto/getting-started-programming-vsto-add-ins.md)
