---
title: PowerPoint çözümleri
description: Microsoft Visual Studio'ler için yeni eklenti oluşturmak üzere VSTO proje şablonları sağladığını PowerPoint.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 97cec1fe5e1954ff04c56f40e3b0313aa35c2170
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025907"
---
# <a name="powerpoint-solutions"></a>PowerPoint çözümleri
  Visual Studio, VSTO için VSTO proje şablonları Microsoft Office PowerPoint. VSTO kullanıcı arabirimini (UI) PowerPoint, PowerPoint özelliklerini genişletmek veya PowerPoint özelliklerini özelleştirmek için PowerPoint kullanabilirsiniz.

 Eklentilerin nasıl VSTO daha fazla bilgi için [bkz. Kullanmaya başlayın](getting-started-programming-vsto-add-ins.md) programlama VSTO Eklentileri ve [VSTO Mimarisi.](architecture-of-vsto-add-ins.md) Programlamaya yeni Microsoft Office, [bkz. Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;. ](getting-started-office-development-in-visual-studio.md)

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>PowerPoint nesne modelini kullanarak PowerPoint otomatikleştirme
 Nesne PowerPoint modeli, veri türlerini otomatikleştirmek için kullanabileceğiniz birçok PowerPoint. Bu türler, yaygın görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:

- Program aracılığıyla sunu oluşturma ve biçimlendirme.

- Sunulara slayt ekleyin veya sunulardan slaytları kaldırın.

- Bir slayta şekil ekleme veya değiştirme.

  Bir PowerPoint eklentiden VSTO nesne modeline erişmek için `Application` projenizin `ThisAddIn` sınıfının alanını kullanın. alanı, `Application` [uygulamanın geçerli](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) örneğini temsil eden bir Application PowerPoint. Daha fazla bilgi için [bkz. Program VSTO Eklentileri](programming-vsto-add-ins.md).

  Nesne modeline çağrı PowerPoint, derleme için birincil birlikte çalışma derlemesinde sağlanan türleri PowerPoint. Birincil birlikte çalışma derlemesi, VSTO Eklentisinde yönetilen kodla PowerPoint. Birincil birlikte çalışma derlemesinde PowerPoint türler [Microsoft.Office. Birlikte çalış -abilir -lik. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) Ad alanı. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için [bkz. Office çözüm geliştirmeye](office-solutions-development-overview-vsto.md) genel bakış &#40;VSTO&#41;[ve Office derlemeleri.](office-primary-interop-assemblies.md)

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a>PowerPoint nesne modeli belgelerini kullanma
 PowerPoint nesne modeli hakkında tam bilgi için, PowerPoint birincil birlikte çalışma derlemesi (PIA) başvurusuna ve VBA nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 PiA PowerPoint belgelerinde, çalışma için birincil birlikte çalışma derlemesinde türleri PowerPoint. Bu belgeler şu konumdan kullanılabilir: [PowerPoint 2010 birincil birlikte çalışma derleme başvurusu.](office-primary-interop-assemblies.md)

 PowerPoint PIA'nın tasarımı hakkında daha fazla bilgi için bkz. PIA'daki sınıflar ve arabirimler arasındaki farklar ve PIA'daki olayların uygulanması, bkz. Office birincil birlikte çalışma derlemelerinde [sınıflara ve](/previous-versions/office/developer/office-2010/ff759900(v=office.14))arabirimlere genel bakış.

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, PowerPoint (VBA) koduna açık olduğu için Visual Basic for Applications modelini belgeler. Daha fazla bilgi için [bkz. PowerPoint 2010 nesne modeli başvurusu.](/office/vba/api/overview/PowerPoint/object-model)

 VBA nesne modeli başvurusunda yer alan tüm nesneler ve üyeler, birincil birlikte çalışma derlemesi (PIA) içindeki PowerPoint ve üyelere karşılık geldi. Örneğin, VBA nesne modeli başvurusunda Presentation nesnesi PIA'daki [Sunum](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) türüne PowerPoint verir. VBA nesne modeli başvurusu çoğu özellik, yöntem ve olay için kod örnekleri sağlar ancak bu başvuruda VBA kodunu Visual Basic veya Visual C# dili kullanarak oluşturacağını bir PowerPoint VSTO Eklenti projesinde kullanmak için çevirmeniz Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Uygulamanın kullanıcı arabirimini PowerPoint
 Kullanıcı arabirimini aşağıdaki PowerPoint değiştirebilirsiniz.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](custom-task-panes.md)|
|Şerit'e özel sekmeler ekleyin.|[Şerit'e genel bakış](ribbon-overview.md)|
|Şerit'te yerleşik bir sekmeye özel gruplar ekleyin.|[Nasıl yapılır: Yerleşik sekmeyi özelleştirme](how-to-customize-a-built-in-tab.md)|

 PowerPoint ve diğer Microsoft Office kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için [bkz. Office kullanıcı arabirimi özelleştirmesi.](office-ui-customization.md)

## <a name="see-also"></a>Ayrıca bkz.
- [adım adım kılavuz: VSTO için İlk Eklentinizi PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Kullanmaya başlayın programlama VSTO Eklentileri](getting-started-programming-vsto-add-ins.md)
- [Office çözümlerine genel bakış &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](architecture-of-vsto-add-ins.md)
- [Nasıl Office: Office projelerini Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO Eklentileri](programming-vsto-add-ins.md)
- [Kod yazma Office yazma](writing-code-in-office-solutions.md)
- [Office birlikte çalışma derlemelerini birleştirme](office-primary-interop-assemblies.md)
- [Office Kullanıcı arabirimi özelleştirmesi](office-ui-customization.md)
- [PowerPoint geliştirmede 2010 Office geliştirme](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
