---
title: Çalışma zamanında Şerit'e erişme
description: Şerit'i göstermek, gizlemek ve değiştirmek için kod yazabilir ve kullanıcıların kodu özel bir görev bölmesinde, eylemler bölmesinde veya form bölgesinde denetimlerden Outlook etkinleştirebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 3636afa4eea04feaa8aaa58a00c8d1af6ffaf4a28e80e90c4a9ac4d5643a72e7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424638"
---
# <a name="access-the-ribbon-at-run-time"></a>Çalışma zamanında Şerit'e erişme
  Şerit'i göstermek, gizlemek ve değiştirmek için kod yazabilir ve kullanıcıların kodu özel bir görev bölmesinde, eylemler bölmesinde veya form bölgesinde denetimlerden Outlook etkinleştirebilirsiniz.

 Sınıfını kullanarak Şerit'e `Globals` erişin. Daha Outlook için, belirli bir Denetçi penceresinde görünen Şeritlere veya Outlook Gezgini penceresinde Outlook erişebilirsiniz.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Globals sınıfını kullanarak Şerit'e erişme
 Sınıfını kullanarak belge düzeyi projesinde Şerit'e erişebilirsiniz veya VSTO herhangi bir yerden Eklenti `Globals` projesini kullanabilirsiniz.

 sınıfı hakkında daha fazla `Globals` bilgi için [bkz. Office projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

 Aşağıdaki örnek, adlı özel bir Şerit'e erişmek ve Şerit'in birleşik giriş kutusunda görüntülenen metni olarak ayarlamak `Globals` `Ribbon1` için sınıfını `Hello World` kullanır.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet4":::

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Belirli bir Denetçi penceresinde görünen Şeritler koleksiyonuna Outlook erişme
 Outlook Inspectors içinde görünen şeritler koleksiyonuna *erişin.* Denetçi, kullanıcılar e-posta Outlook gibi belirli görevleri gerçekleştirecekleri zaman verilerde açılan bir penceredir. Denetçi penceresinin Şeridine erişmek için sınıfının `Ribbons` özelliğini çağırın `Globals` ve Denetçi'yi temsil <xref:Microsoft.Office.Interop.Outlook.Inspector> eden bir nesnesi girin.

 Aşağıdaki örnek, şu anda odaklanan Denetçinin Şerit koleksiyonunu alır. Bu örnek daha sonra adlı bir Şerit'e `Ribbon1` erişerek Şerit'in birleşik giriş kutusunda görünen metni olarak `Hello World` ayarlar.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet5":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet5":::

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Gezgin'de belirli bir şerit için görünen şeritler koleksiyonuna Outlook erişin
 Outlook Explorer'da görünen şeritler koleksiyonuna *erişebilirsiniz.* Gezgin, bir örnek için ana uygulama kullanıcı arabirimidir (UI) Outlook. Gezgin penceresinin Şeridine erişmek için sınıfının `Ribbons` özelliğini `Globals` çağırın ve Gezgin'i temsil <xref:Microsoft.Office.Interop.Outlook.Explorer> eden bir nesnesine geçişin.

 Aşağıdaki örnek, şu anda odaklanan Gezgin'in Şerit koleksiyonunu alır. Bu örnek daha sonra adlı bir Şerit'e `Ribbon1` erişerek Şerit'in birleşik giriş kutusunda görünen metni olarak `Hello World` ayarlar.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Ayrıca bkz.
- [Şerit'e genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
- [Adım adım kılavuz: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Adım adım kılavuz: Çalışma zamanında şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Şerit'i Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md)
