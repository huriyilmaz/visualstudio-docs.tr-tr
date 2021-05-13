---
title: Kullanmaya başlayın VSTO Eklentilerini programlama
description: Uygulamalarınızı otomatikleştirmek, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini özelleştirmek Microsoft Office VSTO Eklentilerini nasıl kullanabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848298"
---
# <a name="get-started-programming-vsto-add-ins"></a>Kullanmaya başlayın VSTO Eklentilerini programlama
> [!IMPORTANT]
> VSTO, [.NET Framework.](https://docs.microsoft.com/dotnet/framework/get-started/overview) COM eklentileri de .NET Framework. Office Eklentileri,.NET Core ve [.NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five)ile oluşturulamaz. Bu, .NET'in en son sürümleridir. Bunun nedeni.NET Core/.NET 5+ ile aynı işlemde .NET Framework birlikte çalışamaz ve eklenti yük hatalarına yol açabilir. Office için VSTO .NET Framework COM eklentilerini yazmak üzere .NET Framework kullanmaya devam edebilirsiniz. Microsoft, VSTO veya COM eklenti platformunu .NET Core veya .NET 5+ kullanmak üzere güncelleştirmez. Office Web Eklentileri'nin sunucu tarafını oluşturmak için .NET Core ve .NET 5+ ASP.NET Core'dan [faydalanabilirsiniz.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  Uygulamalarınızı otomatikleştirmek, uygulamanın Microsoft Office genişletmek ve uygulamanın kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini kullanabilirsiniz. VSTO Eklentileri'nin Visual Studio kullanarak oluştura diğer Office çözümü türleriyle karşılaştırması hakkında bilgi için bkz. [VSTO ](../vsto/office-solutions-development-overview-vsto.md)&#40;için Office çözümleri&#41;.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>VSTO Eklenti projeleri oluşturma
 Yeni Proje iletişim kutusundaki VSTO Eklenti proje şablonlarından birini kullanarak VSTO **Eklenti projeleri** oluşturun. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir. Visual Studio Office'te çoğu uygulama için VSTO Eklenti proje şablonları sağlar.

 VSTO Eklenti projesi oluşturma hakkında daha fazla bilgi için bkz. Nasıl 2019'da [Office Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md) Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>VSTO Eklenti projeleri geliştirme
 VsTO Eklenti projesi oluşturursanız, Visual Studio bir *ThisAddIn.vb (içinde)* veya [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (C#) kod dosyası oluşturur. Bu dosya `ThisAddIn` , VSTO eklentisi için temel sağlayan sınıfını içerir. VSTO eklentisi yüklendiğinde veya kaldırıldığında, ana bilgisayar uygulamasının nesne modeline erişmek ve uygulamanın özelliklerini genişletmek için bu sınıfın üyelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

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

- Uygulama destekliyorsa Şeridi özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

- Uygulama destekliyorsa özel bir görev bölmesi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)

- Outlook için özel bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Outlook form bölgeleri oluşturma.](../vsto/creating-outlook-form-regions.md)

- Tüm Microsoft Office, VSTO Windows Forms'sinde görüntüleniyor.

  Uygulama kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi Microsoft Office office kullanıcı arabirimi [özelleştirme.](../vsto/office-ui-customization.md)

## <a name="next-steps"></a>Sonraki adımlar
 VSTO Eklentilerini oluşturma hakkında bilgi edinmek için aşağıdaki adım adım kılavuzlara bakın:

- [Adım adım kılavuz: Excel için ilk VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Adım adım kılavuz: Outlook için ilk VSTO Add-In oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Adım adım kılavuz: PowerPoint için ilk VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Adım adım kılavuz: Proje için ilk VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Adım adım kılavuz: Word için ilk VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Bu kılavuzlarda, Visual Studio'daki Office geliştirme araçları ve VSTO Eklentileri için programlama modeli tanıtmaktadır.

  Office projelerinde yaygın görevlerden bazıları için size yol gösterir konuların listesi için bkz. [Office programlamada ortak görevler.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Visual Studio: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office çözümlerini kullanarak kod yazma](../vsto/writing-code-in-office-solutions.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [VSTO Eklentilerini Programla](../vsto/programming-vsto-add-ins.md)
