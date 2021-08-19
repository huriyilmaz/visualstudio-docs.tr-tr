---
title: Outlook çözümleri
description: Outlook otomatik hale getirmek, Outlook özelliklerini genişletmek veya Outlook kullanıcı arabirimini (uı) özelleştirmek için VSTO eklentilerini nasıl kullanabileceğinizi öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3ae690d5ef3aeaba6d587970f7dff1ddc34e4be7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147862"
---
# <a name="outlook-solutions"></a>Outlook çözümleri
  Visual Studio, Microsoft Office Outlook için VSTO eklentileri oluşturmak üzere kullanabileceğiniz proje şablonları sağlar. Outlook otomatikleştirmek, Outlook özelliklerini genişletmek veya Outlook kullanıcı arabirimini (uı) özelleştirmek için VSTO eklentileri kullanabilirsiniz. VSTO eklentileri hakkında daha fazla bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>bir Outlook VSTO eklentisi oluşturun Project
 **yeni Project** iletişim kutusunda **Outlook eklentisi** proje şablonunu kullanarak Outlook projeleri oluşturun. Bu şablon gerekli derleme başvurularını ve proje dosyalarını içerir.

 VSTO eklenti projesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projeleri oluşturma Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO eklenti programlama modeli
 bir Outlook VSTO eklenti projesi oluşturduğunuzda Visual Studio, çözümünüzün temeli olan adlı bir sınıf oluşturur `ThisAddIn` . bu sınıf, kodunuzu yazmak için bir başlangıç noktası sağlar ve ayrıca VSTO eklentinize Outlook nesne modelini gösterir.

 `ThisAddIn`bir VSTO eklentisi içinde kullanabileceğiniz sınıf ve diğer özellikler hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Outlook nesne modelini kullanarak Outlook otomatikleştirin
 Outlook nesne modeli, Outlook otomatik hale getirmek için kullanabileceğiniz birçok türü kullanıma sunar. Bu türler ortak görevleri gerçekleştirmek için kod yazmanıza olanak sağlar:

- Program aracılığıyla e-posta iletileri oluşturma ve gönderme.

- Yeni Toplantı istekleri gönderin.

- Outlook klasörlerdeki öğeleri arayın.

  daha fazla bilgi için bkz. [nesne modeline genel bakış Outlook](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Outlook uygulamasının kullanıcı arabirimini özelleştirme

|Görev|Daha fazla bilgi edinmek için|
|----------|--------------------------|
|Outlook denetçisinin şeritine özel sekmeler ekleyin.|[Şerite genel bakış](../vsto/ribbon-overview.md)|
|Outlook denetçisindeki yerleşik bir sekmeye özel gruplar ekleyin.|[Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)|
|Outlook denetçisinde görüntülenen özel bir görev bölmesi ekleme|[Özel görev bölmeleri](../vsto/custom-task-panes.md).|
|varolan Outlook formlarını genişleten veya değiştiren bir form bölgesi ekleyin.|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|

 Outlook ve diğer Microsoft Office uygulamalarının kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi için bkz. [Office uı özelleştirmesi](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Outlook nesne modeline genel bakış](../vsto/outlook-object-model-overview.md)|Outlook nesne modeli tarafından sağlanan nesnelere genel bir bakış sağlar.|
|[Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)|form bölgelerini tasarlamanıza, geliştirmenize ve hata ayıklamanıza daha kolay hale getirerek Visual Studio tarafından sunulan araçları açıklar.|
|[izlenecek yol: Outlook için ilk VSTO Add-In oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Microsoft Office Outlook için VSTO eklentisinin nasıl oluşturulacağını gösterir.|
|[Office geliştirmede 2010 Outlook](/previous-versions/office/developer/office-2010/ff458122(v=office.14))|MSDN kitaplığı 'nın, Outlook çözümleri geliştirme (Visual Studio kullanarak Office geliştirmeye özgü değil) hakkında makaleler ve başvuru belgeleri bulabileceğiniz alanı.|
