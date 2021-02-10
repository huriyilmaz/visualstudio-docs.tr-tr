---
title: InfoPath çözümleri
description: Visual Studio 'Yu kullanarak Microsoft InfoPath 2013 ve InfoPath 2010 için VSTO eklentileri oluşturma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3feab4a4b66ed2d6cf96fbccc8aaf1fb7de3bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962372"
---
# <a name="infopath-solutions"></a>InfoPath çözümleri
  Visual Studio, Microsoft Office InfoPath 2013 ve InfoPath 2010 için VSTO eklentileri oluşturmak üzere kullanabileceğiniz proje şablonları sağlar. InfoPath, Office 2016 ' de kullanılamaz.

> [!NOTE]
> Office 2016 ' i yüklemiş olsanız bile InfoPath için VSTO eklentisi oluşturmaya devam edebilirsiniz. InfoPath 2013 veya Office 2013 ' i Office 2016 ile yan yana yüklemelisiniz.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 InfoPath için VSTO eklentileri diğer Microsoft Office uygulamaları için VSTO eklentilerine benzerdir. Bu tür çözümler, uygulama tarafından yüklenen bir derlemeden oluşur. Son kullanıcılar, hangi form veya form şablonunun açık olduğuna bakılmaksızın bu derlemenin işlevselliğine erişebilir. VSTO eklentileri hakkında daha fazla bilgi için bkz. VSTO eklentileri ve VSTO eklentilerinin [mimarisi](../vsto/architecture-of-vsto-add-ins.md) [programlamasına](../vsto/getting-started-programming-vsto-add-ins.md) başlama.

> [!NOTE]
> Visual Studio 2015, Visual Studio 'nun önceki sürümlerinde sağlanmış olan InfoPath form şablonu projelerini içermez. Visual Studio 2015 ' i Visual Studio 'nun önceki bir sürümünde oluşturulmuş bir InfoPath form şablonu projesi açmak veya düzenlemek için de kullanamazsınız. Ancak, Uygulamalar için Visual Studio Araçları kullanarak bir InfoPath form şablonu projesi açabilir ve düzenleyebilirsiniz. Daha fazla bilgi için bkz [. ınfopath 2010 ' de VSTO 2008 projeleriyle çalışma.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010)

## <a name="automate-infopath-by-using-an-add-in"></a>Eklentiyi kullanarak InfoPath 'i otomatikleştirme
 Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan Office VSTO eklentilerden InfoPath nesne modeline erişmek için, `Application` `ThisAddIn` projenizdeki sınıfının alanını kullanın. `Application`Alan, <xref:Microsoft.Office.Interop.InfoPath.Application> InfoPath 'in geçerli örneğini temsil eden bir nesne döndürür. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

 Bir VSTO eklentisinin InfoPath nesne modelini çağırdığınızda, InfoPath için birincil birlikte çalışma derlemesinde sunulan türleri kullanırsınız. Birincil birlikte çalışma derlemesi, VSTO eklentisi ve InfoPath 'teki COM nesne modelinde yönetilen kod arasında bir köprü görevi görür. InfoPath birincil birlikte çalışma derlemesindeki tüm türler <xref:Microsoft.Office.Interop.InfoPath> ad alanında tanımlanmıştır. InfoPath birincil birlikte çalışma derlemesi hakkında daha fazla bilgi için bkz. [Microsoft Office InfoPath Primary Interop Assembly](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly). Birincil birlikte çalışma derlemeleri hakkında genel bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>InfoPath 'in Kullanıcı arabirimini eklenti kullanarak özelleştirme
 InfoPath için VSTO eklentisi oluşturduğunuzda, birkaç farklı kullanıcı arabirimi özelleştirme seçeneğiniz vardır. Aşağıdaki tabloda bu seçeneklerin bazıları listelenmektedir.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|
|InfoPath 'teki Şerite özel sekmeler ekleyin.|[InfoPath için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-infopath.md)|

 InfoPath ve diğer Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Microsoft Office InfoPath birincil birlikte çalışma derlemesi hakkında](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office geliştirmede InfoPath 2010](/previous-versions/office/developer/office-2010/ff604966(v=office.14))