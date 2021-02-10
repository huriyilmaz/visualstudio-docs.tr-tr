---
title: Çalışma zamanında Şerite erişin
description: Şeriti göstermek, gizlemek ve değiştirmek için kod yazabilir ve kullanıcıların kodu özel bir görev bölmesinde, Eylemler bölmesinde veya Outlook form bölgesindeki denetimlerden çalıştırmasını sağlayabilirsiniz.
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
ms.workload:
- office
ms.openlocfilehash: 224396d7b4328164c55bc58c746909ada015e02f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965739"
---
# <a name="access-the-ribbon-at-run-time"></a>Çalışma zamanında Şerite erişin
  Şeriti göstermek, gizlemek ve değiştirmek için kod yazabilir ve kullanıcıların kodu özel bir görev bölmesinde, Eylemler bölmesinde veya Outlook form bölgesindeki denetimlerden çalıştırmasını sağlayabilirsiniz.

 Sınıfını kullanarak şerit 'e erişebilirsiniz `Globals` . Outlook projeleri için, belirli bir Outlook denetçisinde veya Outlook Explorer penceresinde görünen Şeritlere erişebilirsiniz.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Globals sınıfını kullanarak şeride erişin
 `Globals`Belge düzeyindeki bir projede veya VSTO eklenti projesindeki şerit 'e, projenin herhangi bir yerinden erişmek için sınıfını kullanabilirsiniz.

 Sınıfı hakkında daha fazla bilgi için `Globals` bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

 Aşağıdaki örnek, `Globals` adlı özel bir Şerite erişmek `Ribbon1` ve Şeritteki Birleşik giriş kutusunda görüntülenen metni ayarlamak için sınıfını kullanır `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Belirli bir Outlook Inspector penceresinde görünen Şerit koleksiyonuna erişin
 Outlook *Inspector*' da görünen bir Şerit koleksiyonuna erişebilirsiniz. Inspector, kullanıcılar e-posta iletileri oluşturma gibi belirli görevleri gerçekleştirirken Outlook 'ta açılan bir penceredir. Inspector penceresinin Şeritine erişmek için, `Ribbons` sınıfının özelliğini çağırın `Globals` ve <xref:Microsoft.Office.Interop.Outlook.Inspector> denetçisi temsil eden bir nesneyi geçirin.

 Aşağıdaki örnek, şu anda odağa sahip olan Inspector 'ın şerit koleksiyonunu alır. Bu örnek daha sonra adlı bir Şerite erişir `Ribbon1` ve Şeritteki Birleşik giriş kutusunda görüntülenen metni ayarlar `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Belirli bir Outlook Gezgini için görüntülenen Şerit koleksiyonuna erişin
 Outlook *Explorer*'Da görünen Şerit koleksiyonuna erişebilirsiniz. Gezgin bir Outlook örneği için ana uygulama kullanıcı arabirimi (UI) ' dir. Gezgin penceresinin Şeritine erişmek için, `Ribbons` sınıfının özelliğini çağırın `Globals` ve <xref:Microsoft.Office.Interop.Outlook.Explorer> Gezgini temsil eden bir nesneyi geçirin.

 Aşağıdaki örnek, şu anda odağa sahip olan gezgin 'in şerit koleksiyonunu alır. Bu örnek daha sonra adlı bir Şerite erişir `Ribbon1` ve Şeritteki Birleşik giriş kutusunda görüntülenen metni ayarlar `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [Şerit XML](../vsto/ribbon-xml.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Outlook için şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)
- [Çalışma zamanında form bölgesine erişme](../vsto/accessing-a-form-region-at-run-time.md)
