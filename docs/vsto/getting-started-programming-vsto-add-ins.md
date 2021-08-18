---
title: VSTO eklentileriyle çalışmaya başlama
description: Microsoft Office uygulamaları otomatikleştirebilmek, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini özelleştirmek için VSTO eklentilerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 65ccd3385ca33e098eb5cec073ea56fd742e4d65
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130526"
---
# <a name="get-started-programming-vsto-add-ins"></a>VSTO eklentileriyle çalışmaya başlama
> [!IMPORTANT]
> VSTO [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview)bağlıdır. COM eklentileri de .NET Framework yazılabilir. Office Eklentiler .net [Core ve .NET 5 +](https://docs.microsoft.com/dotnet/core/dotnet-five)ile birlikte oluşturulamaz ve en son .net sürümleridir. bunun nedeni, .net Core/. NET 5 + ' ın aynı işlemde .NET Framework birlikte çalışamadığı ve eklenti yükleme hatalarına neden olabilir. Office için VSTO ve COM eklentilerini yazmak üzere .NET Framework kullanmaya devam edebilirsiniz. Microsoft, .net Core veya .net 5 + kullanacak şekilde VSTO veya COM eklentisi platformunu güncelleştirmemelidir. [Office Web](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)eklentilerinin sunucu tarafını oluşturmak için ASP.NET Core dahil .net Core ve .net 5 + avantajlarından faydalanabilirsiniz.

  Microsoft Office uygulamalarını otomatikleştirmek, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini (uı) özelleştirmek için VSTO eklentileri kullanabilirsiniz. VSTO eklentilerin Visual Studio kullanarak oluşturabileceğiniz diğer Office çözümleri ile nasıl karşılaştırılacağı hakkında bilgi için bkz. [Office solutions development overview ](../vsto/office-solutions-development-overview-vsto.md)&#40;VSTO&#41;.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>VSTO eklentisi projeleri oluşturma
 **yeni Project** iletişim kutusunda VSTO eklentisi proje şablonlarından birini kullanarak VSTO eklenti projeleri oluşturun. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir. Visual Studio, Office çoğu uygulama için VSTO eklenti proje şablonları sağlar.

 VSTO eklenti projesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projeleri oluşturma Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>VSTO eklentisi projeleri geliştirme
 VSTO bir eklenti projesi oluşturduğunuzda, Visual Studio otomatik olarak bir *thisaddın. vb* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) veya *thisaddın. cs* (C#) kod dosyası oluşturur. bu dosya `ThisAddIn` , VSTO eklentisi için temel sağlayan sınıfını içerir. VSTO eklentisi yüklendiğinde veya kaldırıldığında, ana bilgisayar uygulamasının nesne modeline erişmek ve uygulamanın özelliklerini genişletmek için bu sınıfın üyelerini kullanabilirsiniz. daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Nesne modellerini kullanarak uygulamaları otomatikleştirin
 Microsoft Office uygulamaların nesne modelleri, VSTO eklentilerindeki programlama yapabilecekleri birçok türü kullanıma sunar. Uygulamayı otomatikleştirebilmek için bu türleri kullanabilirsiniz. örneğin, Outlook bir e-posta iletisi oluşturup gönderebilir veya bir belgeyi açıp Word 'e içerik ekleyebilirsiniz. kod içinde ana bilgisayar uygulamasının nesne modeline erişme hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

 belirli Microsoft Office uygulamalarının nesne modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)

- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)

- [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)

- [InfoPath çözümleri](../vsto/infopath-solutions.md)

- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)

- [Project çözümleri](../vsto/project-solutions.md)

- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Uygulamaların kullanıcı arabirimini özelleştirme
 VSTO eklentisi kullanarak konak uygulamasının kullanıcı arabirimini özelleştirmenin birkaç farklı yolu vardır:

- Excel ve Word için belgelere yönetilen denetimler ekleyebilirsiniz. daha fazla bilgi için bkz. [çalışma zamanında VSTO eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Uygulama destekliyorsa, şeridi özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Şerit 'e genel bakış](../vsto/ribbon-overview.md).

- Uygulama destekliyorsa, özel bir görev bölmesi oluşturabilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

- Outlook için özel bir form bölgesi oluşturabilirsiniz. daha fazla bilgi için bkz. [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md).

- tüm Microsoft Office uygulamalar için, VSTO eklentiinizdeki Windows Forms görüntüleyebilirsiniz.

  Microsoft Office uygulamalarının kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için, bkz. [Office uı özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Sonraki adımlar
 VSTO eklentileri oluşturmayı öğrenmek için aşağıdaki izlenecek yollara bakın:

- [izlenecek yol: Excel için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [izlenecek yol: Outlook için ilk VSTO Add-In oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [izlenecek yol: PowerPoint için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [izlenecek yol: Project için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [izlenecek yol: Word için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  bu izlenecek yollar, Visual Studio ve VSTO eklentileri için programlama modelinde Office geliştirme araçları sağlar.

  Office projelerindeki yaygın görevlerden bazıları boyunca size kılavuzluk eden konuların listesi için, bkz. [Office programlamada ortak görevler](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
