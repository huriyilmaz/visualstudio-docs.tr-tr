---
title: Kullanmaya başlayın programlama VSTO Eklentileri
description: VSTO uygulamalarını otomatik Microsoft Office, uygulamanın özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini özelleştirmek için VSTO'leri nasıl kullanabileceğinizi öğrenin.
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
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980949"
---
# <a name="get-started-programming-vsto-add-ins"></a>Kullanmaya başlayın programlama VSTO Eklentileri
> [!IMPORTANT]
> VSTO, [.NET Framework.](/dotnet/framework/get-started/overview) COM eklentileri de .NET Framework. Office Eklentiler, .NET Core ve [.NET 5+](/dotnet/core/dotnet-five)ile oluşturulamaz. Bu, .NET'in en son sürümleridir. Bunun nedeni. .NET Core/.NET 5+ ile aynı .NET Framework birlikte çalışamaz ve eklenti yük hatalarına yol açabilir. .NET Framework için VSTO com eklentilerini yazmak üzere Office. Microsoft, .NET Core VSTO .NET 5+ kullanmak için VSTO com eklenti platformunu güncelleştirmez. Web Eklentileri'nin sunucu tarafını oluşturmak için .NET Core ve .NET 5+ ASP.NET Core da dahil [olmak üzere Office kullanabilirsiniz.](/office/dev/add-ins/overview/office-add-ins)

  VSTO uygulamalarını otomatikleştirmek, Microsoft Office özelliklerini genişletmek ve uygulamanın kullanıcı arabirimini (UI) özelleştirmek için VSTO eklentilerini kullanabilirsiniz. VSTO kullanarak Office çözüm türleriyle karşılaştırıldığında nasıl Visual Studio hakkında bilgi için bkz. Office çözüm [geliştirmeye genel &#40;VSTO&#41;. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Eklenti VSTO oluşturma
 Yeni VSTO iletişim kutusundaki VSTO Eklenti proje şablonlarından birini kullanarak Eklenti **projelerini Project** oluşturun. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir. Visual Studio, VSTO çoğu uygulama için eklenti proje şablonları Office.

 VSTO Eklenti projesi oluşturma hakkında daha fazla bilgi için [bkz.](../vsto/how-to-create-office-projects-in-visual-studio.md)Nasıl Office: Visual Studio. Proje şablonları hakkında daha fazla bilgi için bkz. [Office şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>Eklenti VSTO geliştirme
 VSTO Eklenti projesi oluşturursanız, Visual Studio bir *ThisAddIn.vb (içinde)* veya [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (C#) kod dosyasını otomatik olarak oluşturur. Bu dosya, `ThisAddIn` eklentinizin temelini sağlayan sınıfını VSTO içerir. VSTO Eklentisi yüklendiğinde veya kaldırılmış olduğunda, konak uygulamanın nesne modeline erişmek ve uygulamanın özelliklerini genişletmek için kod çalıştırmak için bu sınıfın üyelerini kullanabilirsiniz. Daha fazla bilgi için [bkz. Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Nesne modellerini kullanarak uygulamaları otomatikleştirme
 Microsoft Office uygulamalarının nesne modelleri, bir eklentide programlayabilirsiniz birçok VSTO sunar. Uygulamayı otomatikleştirmek için bu türleri kullanabilirsiniz. Örneğin, program aracılığıyla bir e-posta iletisi oluşturabilir ve Outlook veya bir belge açıp Word'de içerik ekleyebilirsiniz. Kodda konak uygulamanın nesne modeline erişme hakkında daha fazla bilgi için bkz. [Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

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

- Excel ve Word için belgelere yönetilen denetimler ebilirsiniz. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

- Uygulama destekliyorsa Şeridi özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Şerit'e genel bakış.](../vsto/ribbon-overview.md)

- Uygulama destekliyorsa özel bir görev bölmesi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Özel görev bölmeleri.](../vsto/custom-task-panes.md)

- Daha Outlook için özel bir form bölgesi oluşturabilirsiniz. Daha fazla bilgi için [bkz. Form Outlook oluşturma.](../vsto/creating-outlook-form-regions.md)

- Tüm Microsoft Office uygulamaları için, Windows Formlar'VSTO görüntüleniyor.

  Uygulama kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi Microsoft Office bkz. [Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

## <a name="next-steps"></a>Sonraki adımlar
 Eklenti oluşturma hakkında VSTO için aşağıdaki adım adım kılavuzlara bakın:

- [Adım adım kılavuz: VSTO için ilk Eklentinizi Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Adım adım kılavuz: VSTO Add-In için ilk çalışma Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Adım adım kılavuz: VSTO için İlk Eklentinizi PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [adım adım kılavuz: VSTO için İlk Eklentinizi Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Kılavuz: Word için VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Bu kılavuzlarda, Office'daki Visual Studio geliştirme araçlarına ve VSTO programlama modeline yer vemektedir.

  Projelerde yaygın olarak kullanılan görevlerden bazıları hakkında size yol Office bir konu listesi için bkz. [Programlamada Office görevler.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Office: Visual Studio'da Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
