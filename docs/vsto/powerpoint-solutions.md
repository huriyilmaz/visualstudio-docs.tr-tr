---
title: PowerPoint çözümleri
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c41b2942b53c97222abf7308b6706a7cdc734df1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985663"
---
# <a name="powerpoint-solutions"></a>PowerPoint çözümleri
  Visual Studio, Microsoft Office PowerPoint için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. PowerPoint 'i otomatikleştirebilmek, PowerPoint özelliklerini genişletmek veya PowerPoint Kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini kullanabilirsiniz.

 VSTO eklentileri hakkında daha fazla bilgi için bkz. VSTO eklentileri ve VSTO eklentilerinin [mimarisi](architecture-of-vsto-add-ins.md) [programlamasına](getting-started-programming-vsto-add-ins.md) başlama. Microsoft Office ile programlama konusunda yeni başladıysanız, bkz. [Visual Studio 'Da Office geliştirme &#40;kullanmaya başlama&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>PowerPoint nesne modelini kullanarak PowerPoint 'i otomatikleştirin
 PowerPoint nesne modeli, PowerPoint 'i otomatikleştirmek için kullanabileceğiniz birçok türü kullanıma sunar. Bu türler ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:

- Program aracılığıyla sunular oluşturun ve biçimlendirin.

- Sunumlardan slaytlar ekleyin veya kaldırın.

- Slaytlara şekil ekleme veya şekilleri değiştirme.

  Bir VSTO eklentisinin PowerPoint nesne modeline erişmek için, `Application` `ThisAddIn` projenizdeki sınıfının alanını kullanın. `Application`Alan, PowerPoint 'in geçerli örneğini temsil eden bir [uygulama](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) nesnesi döndürür. Daha fazla bilgi için bkz. [Program VSTO eklentileri](programming-vsto-add-ins.md).

  PowerPoint nesne modeli ' ne çağırdığınızda, PowerPoint için birincil birlikte çalışma derlemesinde sunulan türleri kullanırsınız. Birincil birlikte çalışma derlemesi, VSTO eklentisinin yönetilen kodu ile PowerPoint 'teki COM nesne modelinde bir köprü görevi görür. PowerPoint birincil birlikte çalışma derlemesindeki tüm türler, [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) ad alanında tanımlanmıştır. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemeleri](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> PowerPoint nesne modeli belgelerini kullanma
 PowerPoint nesne modeli hakkında tüm bilgiler için, PowerPoint birincil birlikte çalışma derlemesi (PIA) başvurusuna ve VBA nesne modeli başvurusuna başvurabilirsiniz.

### <a name="primary-interop-assembly-reference"></a>Birincil birlikte çalışma derleme başvurusu
 PowerPoint PIA başvuru belgeleri, PowerPoint için birincil birlikte çalışma derlemesindeki türleri açıklar. Bu belge şu konumdan edinilebilir: [PowerPoint 2010 birincil birlikte çalışma derleme başvurusu](office-primary-interop-assemblies.md).

 PIA içindeki sınıflar ve arabirimler arasındaki farklar ve PIA 'teki olayların nasıl uygulandığı gibi, PowerPoint PIA tasarımı hakkında daha fazla bilgi için bkz. [Office birincil birlikte çalışma derlemelerindeki sınıflara ve arabirimlere genel bakış](/previous-versions/office/developer/office-2010/ff759900(v=office.14)).

### <a name="vba-object-model-reference"></a>VBA nesne modeli başvurusu
 VBA nesne modeli başvurusu, Visual Basic for Applications (VBA) koduna açık olduğu için PowerPoint nesne modelini belgeler. Daha fazla bilgi için bkz. [PowerPoint 2010 nesne modeli başvurusu](/office/vba/api/overview/PowerPoint/object-model).

 VBA nesne modeli başvurusundaki tüm nesneler ve Üyeler, PowerPoint birincil birlikte çalışma derlemesindeki (PIA) türlere ve üyelere karşılık gelir. Örneğin, VBA nesne modeli başvurusundaki sunum nesnesi, PowerPoint PIA içindeki [sunum](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) türüne karşılık gelir. VBA nesne modeli başvurusu birçok özellik, yöntem ve olay için kod örnekleri sağlasa da, Visual Studio 'Yu kullanarak oluşturduğunuz bir PowerPoint VSTO eklentisi projesinde kullanmak istiyorsanız bu başvurudaki VBA kodunu Visual Basic veya Visual C# ' ye çevirmeniz gerekir.

## <a name="customize-the-user-interface-of-powerpoint"></a>PowerPoint 'in Kullanıcı arabirimini özelleştirme
 PowerPoint Kullanıcı arabirimini aşağıdaki yollarla değiştirebilirsiniz.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Özel bir görev bölmesi oluşturun.|[Özel görev bölmeleri](custom-task-panes.md)|
|Şerite özel sekmeler ekleyin.|[Şerite genel bakış](ribbon-overview.md)|
|Şeritteki yerleşik bir sekmeye özel gruplar ekleyin.|[Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](how-to-customize-a-built-in-tab.md)|

 PowerPoint ve diğer Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](office-ui-customization.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: PowerPoint için ilk VSTO eklentisini oluşturma](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [VSTO Eklentilerini Programlamaya Başlama](getting-started-programming-vsto-add-ins.md)
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](architecture-of-vsto-add-ins.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO eklentileri](programming-vsto-add-ins.md)
- [Office çözümlerinde kod yazma](writing-code-in-office-solutions.md)
- [Office birincil birlikte çalışma derlemeleri](office-primary-interop-assemblies.md)
- [Office UI özelleştirmesi](office-ui-customization.md)
- [Office geliştirme 'da PowerPoint 2010](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
