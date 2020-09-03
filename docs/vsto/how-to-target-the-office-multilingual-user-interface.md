---
title: 'Nasıl yapılır: Office çok dilli kullanıcı arabirimini hedefleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5217f2d6cf67eced00c0c84b9bacda94573c5a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537507"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Nasıl yapılır: Office çok dilli kullanıcı arabirimini hedefleme
  Çok dilli kullanıcı arabirimi (MUI), son kullanıcıya Kullanıcı arabirimi (UI) dilini değiştirme yeteneği veren bir Microsoft Office özelliğidir. Örneğin, Ingilizce Kullanıcı arabirimiyle çalışan bir son kullanıcı, Kullanıcı arabiriminin dilini Ispanyolca olarak değiştirebilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Uygulamanız Office 'in birçok dilini kullanan kişiler tarafından kullanılacaksa, Kullanıcı bilgisayar Dizelerinizin dilini otomatik olarak değiştirmek için kod ekleyebilirsiniz (Kullanıcı doğru kaynakların yüklü olması halinde varsa).

## <a name="to-check-the-current-office-ui-setting"></a>Geçerli Office Kullanıcı arabirimi ayarını denetlemek için

1. <xref:System.Threading.Thread.CurrentUICulture%2A>Geçerli iş parçacığının özelliğini kullanın. Kullanıcı ARABIRIMI Dizelerinizin dilini, kullanıcının bilgisayarında çalışmakta olan Office sürümü tarafından kullanılan dille eşleşecek şekilde ayarlayın.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: birincil birlikte çalışma Derlemeleriyle Office uygulamalarını hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Office çözümlerinde geç bağlama](../vsto/late-binding-in-office-solutions.md)
