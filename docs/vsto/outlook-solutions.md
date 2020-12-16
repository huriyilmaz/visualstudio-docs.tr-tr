---
title: Outlook çözümleri
description: Outlook 'U otomatik hale getirmek, Outlook özelliklerini genişletmek veya Outlook Kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ded4652704a47252f0839aed151f0557ae5e6766
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527544"
---
# <a name="outlook-solutions"></a>Outlook çözümleri
  Visual Studio, Outlook Microsoft Office için VSTO eklentileri oluşturmak için kullanabileceğiniz proje şablonları sağlar. Outlook 'U otomatikleştirmek, Outlook özelliklerini genişletmek veya Outlook Kullanıcı arabirimini (UI) özelleştirmek için VSTO Eklentilerini kullanabilirsiniz. VSTO eklentileri hakkında daha fazla bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Outlook VSTO eklentisi projesi oluşturma
 **Yeni proje** Iletişim kutusundaki **Outlook eklentisi** proje şablonunu kullanarak Outlook projeleri oluşturun. Bu şablon gerekli derleme başvurularını ve proje dosyalarını içerir.

 VSTO eklenti projesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md). Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO eklentisi programlama modeli
 Outlook VSTO eklentisi projesi oluşturduğunuzda, Visual Studio çözümünüzün temeli olan adlı bir sınıf oluşturur `ThisAddIn` . Bu sınıf, kodunuzu yazmak için bir başlangıç noktası sağlar ve Outlook 'un nesne modelini VSTO eklentinize de sunar.

 `ThisAddIn`VSTO eklentilerinde kullanabileceğiniz sınıf ve diğer özellikler hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Outlook nesne modelini kullanarak Outlook 'U otomatikleştirme
 Outlook nesne modeli, Outlook 'U otomatikleştirmek için kullanabileceğiniz birçok türü kullanıma sunar. Bu türler ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:

- Program aracılığıyla e-posta iletileri oluşturma ve gönderme.

- Yeni Toplantı istekleri gönderin.

- Outlook klasörlerinde öğeleri arayın.

  Daha fazla bilgi için bkz. [Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Outlook uygulamasının Kullanıcı arabirimini özelleştirme

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Outlook denetçisinin Şeritine özel sekmeler ekleyin.|[Şerite genel bakış](../vsto/ribbon-overview.md)|
|Outlook Inspector 'daki yerleşik bir sekmeye özel gruplar ekleyin.|[Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)|
|Outlook denetçisinde görünen özel bir görev bölmesi ekleme|[Özel görev bölmeleri](../vsto/custom-task-panes.md).|
|Varolan Outlook formlarını genişleten veya değiştiren bir form bölgesi ekleyin.|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|

 Outlook ve diğer Microsoft Office uygulamalarının Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)|Outlook nesne modeli tarafından sağlanan nesnelere genel bakış sağlar.|
|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|Form bölgelerini tasarlamanıza, geliştirmenize ve hata ayıklamanıza daha kolay hale getirerek Visual Studio tarafından sunulan araçları açıklar.|
|[İzlenecek yol: Outlook için ilk VSTO Add-In oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Outlook Microsoft Office için bir VSTO eklentisi oluşturmayı gösterir.|
|[Office geliştirmede Outlook 2010](/previous-versions/office/developer/office-2010/ff458122(v=office.14))|MSDN Kitaplığı 'nın, Outlook çözümlerini geliştirme (Visual Studio kullanarak Office geliştirmeye özgü değil) hakkında makaleler ve başvuru belgeleri bulabileceğiniz alanı.|
