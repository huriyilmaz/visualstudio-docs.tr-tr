---
title: Proje çözümleri
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84dfe7cf86df2139b06a320d1c6441665a08a1b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985633"
---
# <a name="project-solutions"></a>Proje çözümleri
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , Microsoft Office projesi için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Projeyi otomatikleştirmek, proje özelliklerini genişletmek veya proje Kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini kullanabilirsiniz.

 VSTO eklentileri hakkında daha fazla bilgi için bkz. VSTO eklentileri ve VSTO eklentilerinin [mimarisi](../vsto/architecture-of-vsto-add-ins.md) [programlamasına](../vsto/getting-started-programming-vsto-add-ins.md) başlama. Microsoft Office ile programlama konusunda yeni başladıysanız, bkz. [Visual Studio 'Da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Proje nesne modelini kullanarak projeyi otomatikleştirin
 Proje nesnesi modeli, projeyi otomatikleştirmek için kullanabileceğiniz birçok türü ortaya koyar. Bu türler, bir projedeki görevleri programlı bir şekilde oluşturma ve değiştirme gibi genel görevleri gerçekleştirmek için kod yazmanıza olanak tanır.

 Bir VSTO eklentisinin proje nesne modeline erişmek için, `Application` `ThisAddIn` projenizdeki sınıfının alanını kullanın. `Application`Alan, `Microsoft.Office.Interop.MsProject.Application` projenin geçerli örneğini temsil eden bir nesne döndürür. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

 Proje nesne modeli ' ne çağırdığınızda, proje için birincil birlikte çalışma derlemesinde sunulan türleri kullanırsınız. Birincil birlikte çalışma derlemesi, VSTO eklentisinin içindeki yönetilen kod ile projedeki COM nesne modelinde bir köprü görevi görür. Proje birincil birlikte çalışma derlemesindeki tüm türler `Microsoft.Office.Interop.MSProject` ad alanında tanımlanır. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Proje nesne modeli belgelerini kullanın
 Proje nesne modeli hakkında tüm bilgiler için, proje VBA nesne modeli başvurusuna başvurabilirsiniz. VBA nesne modeli başvurusu, proje nesne modelini Visual Basic for Applications (VBA) koduna açık olarak belgeler. Daha fazla bilgi için bkz. [proje nesne modeli başvurusu](/office/vba/api/project.object).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler, proje birincil birlikte çalışma derlemesindeki (PIA) türlere ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki takvim nesnesi, `Microsoft.Office.Interop.MSProject.Calendar` Proje PIA içindeki türe karşılık gelir. VBA nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, Visual Studio 'Yu kullanarak oluşturduğunuz bir proje VSTO eklentisi projesinde kullanmak istiyorsanız bu başvurudaki VBA kodunu Visual Basic veya Visual C# ' ye çevirmeniz gerekir.

> [!NOTE]
> Şu anda, proje birincil birlikte çalışma derlemesi için başvuru belgesi yoktur.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Proje birincil birlikte çalışma derlemesindeki altyapı türleri
 Projeyi PIA kullanan bir kod yazdığınızda, VBA başvurusunda açıklanmayan birçok tür fark edebilirsiniz. Bu ek türler, projenin COM tabanlı nesne modelindeki nesneleri yönetilen koda çevirmeye yardımcı olur, doğrudan kodunuzda kullanılmaya yönelik değildir.

 Daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/office-12/ms247299(v=office.12)).

## <a name="customize-the-user-interface-of-project"></a>Projenin Kullanıcı arabirimini özelleştirme
 Aşağıdaki yollarla proje Kullanıcı arabirimini özelleştirebilirsiniz.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Projedeki Şerite özel sekmeler ekleme|[Şerite genel bakış](../vsto/ribbon-overview.md)|

 Projenin ve diğer Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: proje için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office geliştirmede proje 2010 ve Project Server 2010](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
