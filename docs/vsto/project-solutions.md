---
title: Project çözümleri
description: VSTO özelliklerini otomatik Project, Project genişletmek veya Project arabirimini (UI) özelleştirmek için nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6d03ff38fbbf4084c8dd60738b2d5340d53638a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115050"
---
# <a name="project-solutions"></a>Project çözümleri
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], VSTO'ler için VSTO proje şablonları Microsoft Office Project. VSTO özelliklerini otomatikleştirmek, Project genişletmek Project kullanıcı arabirimini (UI) özelleştirmek için Project eklentilerini kullanabilirsiniz.

 Eklentilerin nasıl VSTO daha fazla bilgi için [bkz. Kullanmaya başlayın eklentilerinin VSTO](../vsto/getting-started-programming-vsto-add-ins.md) programlama ve [VSTO Mimarisi.](../vsto/architecture-of-vsto-add-ins.md) Programlamaya yeni Microsoft Office, [bkz. Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;. ](../vsto/getting-started-office-development-in-visual-studio.md)

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Proje nesne modelini kullanarak projeyi otomatikleştirme
 Nesne Project modeli, veri türlerini otomatikleştirmek için kullanabileceğiniz birçok Project. Bu türler, bir projede program aracılığıyla görev oluşturma ve değiştirme gibi yaygın görevleri gerçekleştirmek için kod yazmanız için olanak sağlar.

 Eklentiden Project nesne modeline erişmek VSTO `Application` projenizin `ThisAddIn` sınıfının alanını kullanın. alanı, `Application` geçerli örneği temsil eden bir nesne döndürür `Microsoft.Office.Interop.MsProject.Application` Project. Daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

 Bir nesne modeline Project, derleme için birincil birlikte çalışma derlemesinde sağlanan türleri Project. Birincil birlikte çalışma derlemesi, VSTO Eklentisinde yönetilen kod ile Project com nesne modeli arasında bir köprü olarak Project. Birincil birlikte çalışma Project derlemesinde tüm türler ad alanında `Microsoft.Office.Interop.MSProject` tanımlanır. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için [bkz. Office çözüm geliştirmeye](../vsto/office-solutions-development-overview-vsto.md) genel bakış &#40;VSTO&#41;[ve Office derlemeleri.](../vsto/office-primary-interop-assemblies.md)

## <a name="use-the-project-object-model-documentation"></a>Proje nesne modeli belgelerini kullanma
 Nesne modeliyle ilgili Project için VBA nesne modeli başvurusu Project başvurabilirsiniz. VBA nesne modeli başvurusu, Project (VBA) koduna açık olduğu için Visual Basic for Applications modelini belgeler. Daha fazla bilgi için [bkz. Project modeli başvurusu.](/office/vba/api/project.object)

 VBA nesne modeli başvurusunda yer alan tüm nesneler ve üyeler, birincil birlikte çalışma derlemesi (PIA) içindeki Project ve üyelere karşılık geldi. Örneğin, VBA nesne modeli başvurusunda Takvim nesnesi, PIA'nın Project `Microsoft.Office.Interop.MSProject.Calendar` karşılık gel. VBA nesne modeli başvurusu çoğu özellik, yöntem ve olay için kod örnekleri sağlar, ancak bu başvuruda VBA kodunu Visual Basic veya Visual C# diliyle oluşturmak istediğiniz bir Project VSTO Eklenti projesinde kullanmak istediğiniz VBA kodunu Visual Studio.

> [!NOTE]
> Şu anda, birincil birlikte çalışma derlemesi için Project belgeleri yoktur.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Proje birincil birlikte çalışma derlemesinde altyapı türleri
 PiA'nın Project kod yazarken VBA başvurusunda açıklanmaz birçok tür olduğunu farkebilirsiniz. Bu ek türler, Project com tabanlı nesne modelinde nesneleri yönetilen koda çevirmeye yardımcı olur. Bunlar doğrudan kodunda kullanılmaya yönelik değildir.

 Daha fazla bilgi için [bkz. Birincil birlikte çalışma derlemeleri için Office arabirimlere genel bakış.](/previous-versions/office/office-12/ms247299(v=office.12))

## <a name="customize-the-user-interface-of-project"></a>Projenin kullanıcı arabirimini özelleştirme
 Kullanıcı arabirimini Project şekilde özelleştirebilirsiniz.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Project'da Şerit'e özel sekmeler ekleme|[Şerit'e genel bakış](../vsto/ribbon-overview.md)|

 Project ve diğer Microsoft Office kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için [bkz. Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kılavuz: Proje için VSTO Eklentinizi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Kullanmaya başlayın programlama VSTO Eklentileri](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office çözümlerine genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
- [Office birlikte çalışma derlemelerini birleştirme](../vsto/office-primary-interop-assemblies.md)
- [Office Kullanıcı arabirimi özelleştirmesi](../vsto/office-ui-customization.md)
- [Project 2010 ve Project Server 2010 Office geliştirme](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
