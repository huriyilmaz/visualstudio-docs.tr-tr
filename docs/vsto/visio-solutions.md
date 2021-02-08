---
title: Visio çözümleri
description: Visio 'Yu otomatikleştirebilmek, Visio özelliklerini genişletmek veya Visio Kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini nasıl kullanabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 9d888a27a8443b6500093a70416414bec453e77e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838050"
---
# <a name="visio-solutions"></a>Visio çözümleri
  Visual Studio, Microsoft Office Visio için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Visio 'Yu otomatikleştirmek, Visio özelliklerini genişletmek veya Visio Kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini kullanabilirsiniz.

 VSTO eklentileri hakkında daha fazla bilgi için bkz. VSTO eklentileri ve VSTO eklentilerinin [mimarisi](../vsto/architecture-of-vsto-add-ins.md) [programlamasına](../vsto/getting-started-programming-vsto-add-ins.md) başlama. Microsoft Office ile programlama konusunda yeni başladıysanız, bkz. [Visual Studio 'Da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Uygulama hedefi:** Bu konudaki bilgiler, Visio 2010 için VSTO eklentisi projelerine yöneliktir. Daha fazla bilgi edinmek için bkz. [Office Uygulaması ve Proje Türüne Göre Kullanılabilen Özellikler](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Visio nesne modelini kullanarak Visio 'Yu otomatikleştirme
 Visio nesne modeli, kurumsal grafikler, akış çizelgeleri, proje zaman çizelgeleri, ağ diyagramları, ofis alanları ve daha fazlası için diyagramlar oluşturmak üzere Visio 'Yu otomatikleştirmek için kullanabileceğiniz birçok sınıfı kullanıma sunar. API, ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:

- Diyagramda şekiller ve metin oluşturun ve konumlandırın.

- İş mantığı ve kullanıcı girişine göre şekil davranışını yönetin.

- Kaydırma ve yakınlaştırma gibi denetim diyagramı görselleştirmesi.

- Uygulama kullanıcı arabirimini özelleştirin.

- Dış verileri Visio 'ya aktarın, şekillere bağlayın ve bir sayfada grafik olarak görüntüleyin.

  Visio [belgeleriyle](../vsto/working-with-visio-documents.md) çalışma ve Visio [şekilleriyle](../vsto/working-with-visio-shapes.md)çalışma içindeki belgeler ve şekillerle çalışmak için Visio nesne modelini kullanmaya yönelik adım adım yordamları ve kod örneklerini görüntüleyebilirsiniz.

  Visio nesne modeline bir VSTO eklentisi 'nden erişmek için, `Application` `ThisAddIn` projenizdeki sınıfının alanını kullanın. `Application`Alan, `Microsoft.Office.Interop.Visio.Application` geçerli Visio örneğini temsil eden bir nesne döndürür. Daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

  Visio nesne modeline çağırdığınızda, Visio için birincil birlikte çalışma derlemesinde (PIA) sunulan türleri kullanırsınız. PIA, VSTO eklentisi ve Visio 'daki COM nesne modelinde yönetilen kod arasında bir köprü görevi görür. Visio PIA içindeki tüm türler `Microsoft.Office.Interop.Visio` ad alanında tanımlanmıştır. Birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz. [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) ve [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Visio nesne modeline genel bakış
 Visio nesne modeline [genel bakış](../vsto/visio-object-model-overview.md), Visio nesne modeli başvurusu ve SDK 'ların bağlantılarını içeren Visio nesne modeline genel bakış bulabilirsiniz.

## <a name="customize-the-user-interface-of-visio"></a>Visio Kullanıcı arabirimini özelleştirme
 Visio Kullanıcı arabiriminde aşağıdaki özelleştirme seçenekleri bulunur.

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Şeridi özelleştirin.|[Şerite Genel Bakış](../vsto/ribbon-overview.md)|

 Visio 'nun Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için, bkz. [Visio. UIObject](/office/vba/api/Visio.UIObject) sınıfı için VBA başvuru belgeleri.

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerini Programlamaya Başlama](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
- [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Visio nesne modeline genel bakış](../vsto/visio-object-model-overview.md)
- [Office geliştirmede Visio 2010](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
