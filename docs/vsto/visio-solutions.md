---
title: Visio çözümleri
description: Visio otomatik hale getirmek, Visio özelliklerini genişletmek veya Visio kullanıcı arabirimini (uı) özelleştirmek için VSTO eklentilerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 14f3c77d35f0c2fea648897e091ac454dda5156b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046223"
---
# <a name="visio-solutions"></a>Visio çözümleri
  Visual Studio, Microsoft Office Visio için VSTO eklentileri oluşturmak üzere kullanabileceğiniz proje şablonları sağlar. Visio otomatikleştirmek, Visio özelliklerini genişletmek veya Visio kullanıcı arabirimini (uı) özelleştirmek için VSTO eklentileri kullanabilirsiniz.

 VSTO eklentileri hakkında daha fazla bilgi için bkz. VSTO eklentilerin [VSTO eklentileri ve mimarisini kullanmaya başlama](../vsto/getting-started-programming-vsto-add-ins.md) . [](../vsto/architecture-of-vsto-add-ins.md) Microsoft Office ile programlama konusunda yeni başladıysanız, bkz. [Office &#40;Visual Studio&#41;geliştirme ](../vsto/getting-started-office-development-in-visual-studio.md).

 **Uygulama hedefi:** bu konudaki bilgiler, Visio 2010 VSTO eklenti projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Visio nesne modelini kullanarak Visio otomatikleştirin
 Visio nesne modeli, kurumsal grafikler, akış çizelgeleri, proje zaman çizelgeleri, ağ diyagramları, ofis alanları ve daha fazlası için diyagramlar oluşturmak üzere Visio otomatik hale getirmek için kullanabileceğiniz birçok sınıfı kullanıma sunar. API, ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:

- Diyagramda şekiller ve metin oluşturun ve konumlandırın.

- İş mantığı ve kullanıcı girişine göre şekil davranışını yönetin.

- Kaydırma ve yakınlaştırma gibi denetim diyagramı görselleştirmesi.

- Uygulama kullanıcı arabirimini özelleştirin.

- dış verileri Visio içeri aktarın, şekillere bağlayın ve bir sayfada grafik olarak görüntüleyin.

  Visio nesne modelini kullanmaya yönelik adım adım yordamları ve kod örneklerini, [Visio belgelerle](../vsto/working-with-visio-documents.md) çalışma ve [Visio şekilleriyle](../vsto/working-with-visio-shapes.md)çalışma içindeki belgeler ve şekillerle çalışmak için görüntüleyebilirsiniz.

  VSTO bir eklentinin Visio nesne modeline erişmek için, `Application` `ThisAddIn` projenizdeki sınıfının alanını kullanın. `Application`Alan, `Microsoft.Office.Interop.Visio.Application` Visio geçerli örneğini temsil eden bir nesne döndürür. daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

  Visio nesne modeline çağırdığınızda, Visio için birincil birlikte çalışma derlemesinde (pıa) sunulan türleri kullanırsınız. pıa, Visio VSTO eklentisi ve COM nesne modelinde yönetilen kod arasında bir köprü görevi görür. Visio pıa içindeki tüm türler `Microsoft.Office.Interop.Visio` ad alanında tanımlanmıştır. birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Visio nesne modeline genel bakış
 Visio nesne modeline genel bakış bulabilirsiniz. bu, Visio nesne modeli başvurusunun ve sdk 'ların bağlantılarını içeren [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md).

## <a name="customize-the-user-interface-of-visio"></a>Visio Kullanıcı arabirimini özelleştirme
 Visio kullanıcı arabiriminde aşağıdaki özelleştirme seçenekleri bulunur.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Şeridi özelleştirin.|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|

 Visio kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için, Visio VBA başvuru belgelerine bakın [. UIObject](/office/vba/api/Visio.UIObject) sınıfı.

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO eklentileriyle çalışmaya başlama](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [birincil birlikte çalışma derlemelerini Office](../vsto/office-primary-interop-assemblies.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Office geliştirmede 2010 Visio](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
