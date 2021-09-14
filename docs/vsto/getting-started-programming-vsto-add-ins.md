---
title: Kullanmaya başlayın programlama VSTO Eklentileri
description: Microsoft Office uygulamalarını otomatikleştirmek, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini özelleştirmek için VSTO Eklentilerini nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: e36c290ed4411ffb4bc0a5dd994a8f14a9fc3ab1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725607"
---
# <a name="get-started-programming-vsto-add-ins"></a>Kullanmaya başlayın programlama VSTO Eklentileri
> [!IMPORTANT]
> VSTO, [.NET Framework.](/dotnet/framework/get-started/overview) COM eklentileri de aşağıdaki .NET Framework. Office Eklentiler, .NET Core ve [.NET 5+](/dotnet/core/dotnet-five)ile oluşturulamaz. Bu, .NET'in en son sürümleridir. Bunun nedeni.NET Core/.NET 5+ ile aynı işlemde .NET Framework birlikte çalışamaz ve eklenti yük hatalarına yol açabilir. .NET Framework için VSTO com eklentilerini yazmak üzere Office. Microsoft, .NET Core VSTO .NET 5+ kullanmak için VSTO com eklenti platformunu güncelleştirmez. Web Eklentileri'nin sunucu tarafını oluşturmak için .NET Core ASP.NET Core .NET 5+ Office [faydalanabilirsiniz.](/office/dev/add-ins/overview/office-add-ins)

  VSTO uygulamaları otomatikleştirmek, Microsoft Office özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini kullanabilirsiniz. VSTO kullanarak Office çözüm türleriyle karşılaştırması hakkında bilgi için bkz. Visual Studio Office çözüm [geliştirmeye genel bakış &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>VSTO Eklenti projeleri oluşturma
 Yeni VSTO iletişim kutusundaki VSTO Eklenti proje şablonlarından birini kullanarak eklenti **projelerini Project** oluşturun. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir. Visual Studio, VSTO çoğu uygulama için bir eklenti proje şablonu Office.

 VSTO Eklenti projesi oluşturma hakkında daha fazla bilgi için, bkz. Nasıl Office [projelerini Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md) Proje şablonları hakkında daha fazla bilgi için bkz. [Office şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>Eklenti VSTO geliştirme
 VSTO Eklenti projesi oluşturursanız, Visual Studio bir *ThisAddIn.vb (içinde)* veya [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (C#) kod dosyasını otomatik olarak oluşturur. Bu dosya, `ThisAddIn` eklentinizin temelini sağlayan sınıfını VSTO içerir. VSTO Eklenti yüklendiğinde veya kaldırılmış olduğunda, konak uygulamanın nesne modeline erişmek ve uygulamanın özelliklerini genişletmek için kod çalıştırmak için bu sınıfın üyelerini kullanabilirsiniz. Daha fazla bilgi için [bkz. Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Nesne modellerini kullanarak uygulamaları otomatikleştirme
 Uygulama modellerinin nesne Microsoft Office, bir eklentide programlayabilirsiniz birçok VSTO sunar. Uygulamayı otomatikleştirmek için bu türleri kullanabilirsiniz. Örneğin, program aracılığıyla bir e-posta iletisi oluşturabilir ve Outlook veya bir belge açıp Word'de içerik ekleyebilirsiniz. Kodda konak uygulamanın nesne modeline erişme hakkında daha fazla bilgi için bkz. [Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

 Belirli bir uygulamanın nesne modelleri hakkında daha fazla Microsoft Office aşağıdaki konulara bakın:

- [Excel modeline genel bakış](../vsto/excel-object-model-overview.md)

- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)

- [Outlook modeline genel bakış](../vsto/outlook-object-model-overview.md)

- [InfoPath çözümleri](../vsto/infopath-solutions.md)

- [PowerPoint çözümleri](../vsto/powerpoint-solutions.md)

- [Project çözümleri](../vsto/project-solutions.md)

- [Visio modeline genel bakış](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Uygulamaların kullanıcı arabirimini özelleştirme
 Konak uygulamanın kullanıcı arabirimini özel bir eklenti kullanarak özelleştirmenin birkaç farklı VSTO vardır:

- Word Excel için belgelere yönetilen denetimler ebilirsiniz. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

- Uygulama destekliyorsa Şeridi özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

- Uygulama destekliyorsa özel bir görev bölmesi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)

- Daha Outlook için özel bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

- Tüm Microsoft Office uygulamalar için, Windows Forms'VSTO görüntüleniyor.

  Uygulama kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi Microsoft Office bkz. [Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

## <a name="next-steps"></a>Sonraki adımlar
 Eklenti oluşturma hakkında VSTO için aşağıdaki adım adım kılavuzlara bakın:

- [Adım adım kılavuz: VSTO için İlk Eklentinizi Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Adım adım kılavuz: VSTO Add-In için ilk çalışma Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Adım adım kılavuz: VSTO için İlk Eklentinizi PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Adım adım kılavuz: VSTO için İlk Eklentinizi Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Kılavuz: Word için VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Bu kılavuzlarda, Office'daki Visual Studio geliştirme araçları ve VSTO programlama modeli tanıtmaktadır.

  Office projelerinde sık kullanılan görevlerden bazıları hakkında size yol Office için [bkz. programlamada ortak Office.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
