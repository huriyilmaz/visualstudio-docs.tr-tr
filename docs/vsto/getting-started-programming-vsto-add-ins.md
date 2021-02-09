---
title: VSTO Eklentilerini Programlamaya Başlama
description: Microsoft Office uygulamalarını otomatikleştirebilmek, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini özelleştirmek için VSTO Eklentilerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d7e6f891f8485d4e08734e59a11db8018eaa07b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860643"
---
# <a name="get-started-programming-vsto-add-ins"></a>VSTO Eklentilerini Programlamaya Başlama
  Microsoft Office uygulamalarını otomatikleştirmek, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini kullanabilirsiniz. VSTO eklentilerinin, Visual Studio kullanarak oluşturabileceğiniz diğer Office çözümleri türleriyle nasıl Karşılaştırıldığı hakkında bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>VSTO eklenti projeleri oluşturma
 **Yeni proje** ILETIŞIM kutusundaki VSTO eklentisi proje şablonlarından bırını kullanarak VSTO eklenti projeleri oluşturun. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir. Visual Studio, Office 'teki çoğu uygulama için VSTO eklentisi proje şablonları sağlar.

 VSTO eklenti projesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md). Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>VSTO eklentisi projelerini geliştirme
 VSTO eklenti projesi oluşturduğunuzda, Visual Studio otomatik olarak bir *ThisAddIn. vb* (ın [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) veya *ThisAddIn.cs* (C#) kod dosyası oluşturur. Bu dosya `ThisAddIn` , VSTO eklentisi için temel sağlayan sınıfını içerir. VSTO eklentisi yüklendiğinde veya kaldırıldığında, ana bilgisayar uygulamasının nesne modeline erişmek ve uygulamanın özelliklerini genişletmek için bu sınıfın üyelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Nesne modellerini kullanarak uygulamaları otomatikleştirin
 Microsoft Office uygulamaların nesne modelleri, VSTO Eklentilerindeki programlama yapabilecekleri birçok türü kullanıma sunar. Uygulamayı otomatikleştirebilmek için bu türleri kullanabilirsiniz. Örneğin, Outlook 'ta program aracılığıyla bir e-posta iletisi oluşturabilir ve gönderebilirsiniz ya da bir belgeyi açabilir ve Word 'e içerik ekleyebilirsiniz. Kod içinde ana bilgisayar uygulamasının nesne modeline erişme hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

 Belirli Microsoft Office uygulamalarının nesne modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)

- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)

- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)

- [InfoPath çözümleri](../vsto/infopath-solutions.md)

- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)

- [Proje çözümleri](../vsto/project-solutions.md)

- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Uygulamaların kullanıcı arabirimini özelleştirme
 VSTO eklentisini kullanarak konak uygulamasının Kullanıcı arabirimini özelleştirmenin birkaç farklı yolu vardır:

- Excel ve Word için belgelere yönetilen denetimler ekleyebilirsiniz. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Uygulama destekliyorsa, şeridi özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

- Uygulama destekliyorsa, özel bir görev bölmesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

- Outlook için özel bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

- Tüm Microsoft Office uygulamalar için, VSTO eklentiinizdeki Windows Forms görüntüleyebilirsiniz.

  Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Sonraki adımlar
 VSTO eklentileri oluşturmayı öğrenmek için aşağıdaki izlenecek yollara bakın:

- [İzlenecek yol: Excel için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [İzlenecek yol: Outlook için ilk VSTO Add-In oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [İzlenecek yol: PowerPoint için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [İzlenecek yol: proje için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [İzlenecek yol: Word için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Bu izlenecek yollar, Visual Studio 'da Office geliştirme araçları ve VSTO eklentileri için programlama modeli sağlar.

  Office projelerindeki yaygın görevlerden bazıları boyunca size kılavuzluk eden konuların listesi için bkz. [Office programlamada ortak görevler](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
