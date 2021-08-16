---
title: InfoPath çözümleri
description: Microsoft InfoPath 2013 Visual Studio InfoPath 2010 için VSTO eklentileri oluşturmak üzere Visual Studio'yi nasıl kullanabileceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: aafd260434a80d84c192c4c84b5435de4f847310a1e87cddf90f20359e8b4b93
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394152"
---
# <a name="infopath-solutions"></a>InfoPath çözümleri
  Visual Studio InfoPath 2013 VSTO InfoPath 2010 için Microsoft Office oluşturmak üzere kullanabileceğiniz proje şablonları sağlar. InfoPath, 2016'Office kullanılamaz.

> [!NOTE]
> 2016'VSTO yüklemiş olsa bile InfoPath için bir Office oluşturabilirsiniz. InfoPath 2013'ü veya Office 2013'ü Office 2016'ya yükleyin.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 VSTO InfoPath eklentileri, diğer VSTO uygulamaları için ek eklentilere Microsoft Office benzer. Bu tür çözümler, uygulama tarafından yüklenen bir derlemeden oluşur. Hangi form veya form şablonunun açık olduğu fark etmez, son kullanıcılar bu derlemenin işlevselliğine erişime sahip olabilir. Eklentilerin nasıl VSTO daha fazla bilgi için [bkz. Kullanmaya başlayın](../vsto/getting-started-programming-vsto-add-ins.md) programlama VSTO Eklentileri ve [VSTO Mimarisi.](../vsto/architecture-of-vsto-add-ins.md)

> [!NOTE]
> Visual Studio 2015, önceki sürümlerde sağlanan InfoPath form şablonu projelerini Visual Studio. Ayrıca, Visual Studio 2015'i, önceki bir sürümde oluşturulmuş bir InfoPath form şablonu projesini açmak veya düzenlemek için Visual Studio. Ancak, bir InfoPath form şablonu projesini açmak ve düzenlemek için Uygulamalar için Visual Studio Araçları. Daha fazla bilgi için [bkz. InfoPath 2010'da VSTO 2008 projeleriyle çalışma.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010).

## <a name="automate-infopath-by-using-an-add-in"></a>Eklenti kullanarak InfoPath'i otomatikleştirme
 Visual Studio'de Office geliştirme araçları kullanılarak oluşturulan bir Office VSTO Eklentiden InfoPath nesne modeline erişmek için projenizin sınıfının `Application` `ThisAddIn` alanını kullanın. alanı, `Application` <xref:Microsoft.Office.Interop.InfoPath.Application> geçerli InfoPath örneğini temsil eden bir nesnesi döndürür. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

 Bir eklentiden InfoPath nesne modeline VSTO, InfoPath için birincil birlikte çalışma derlemesinde sağlanan türleri kullanırız. Birincil birlikte çalışma derlemesi, VSTO Eklentisinde yönetilen kod ile InfoPath'te COM nesne modeli arasında bir köprü olarak hareket eder. InfoPath birincil birlikte çalışma derlemesi içindeki tüm türler ad alanında <xref:Microsoft.Office.Interop.InfoPath> tanımlanır. InfoPath birincil birlikte çalışma derlemesi hakkında daha fazla bilgi için [bkz. Microsoft Office InfoPath birincil birlikte çalışma derlemesi hakkında.](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly) Genel olarak birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için [bkz. Office](../vsto/office-solutions-development-overview-vsto.md) çözüm geliştirmeye genel bakış &#40;VSTO&#41;[ve Office derlemeleri.](../vsto/office-primary-interop-assemblies.md)

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Eklenti kullanarak InfoPath kullanıcı arabirimini özelleştirme
 InfoPath için VSTO bir eklenti oluşturma, birkaç farklı kullanıcı arabirimi özelleştirme seçeneğine sahip olur. Aşağıdaki tabloda bu seçeneklerden bazıları liste bulunmaktadır.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](../vsto/custom-task-panes.md)|
|InfoPath'te Şerit'e özel sekmeler ekleyin.|[InfoPath için Şerit Özelleştirme](../vsto/customizing-a-ribbon-for-infopath.md)|

 InfoPath ve diğer uygulama kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi Microsoft Office bkz. [Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

## <a name="see-also"></a>Ayrıca bkz.
- [InfoPath Microsoft Office derlemesi hakkında](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Kullanmaya başlayın programlama VSTO Eklentileri](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office çözümlerine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
- [Office birlikte çalışma derlemelerini birleştirme](../vsto/office-primary-interop-assemblies.md)
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Geliştirme aşamasında InfoPath 2010 Office geliştirme](/previous-versions/office/developer/office-2010/ff604966(v=office.14))