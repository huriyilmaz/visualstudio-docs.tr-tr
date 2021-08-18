---
title: 'Nasıl kullanılır: Çok Office kullanıcı arabirimini hedefleme'
description: Çok dilli kullanıcı Visual Studio program aracılığıyla hedefleyebilirsiniz Microsoft Office nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c6d3c98f2b9675681aacbd84d9abd8f919eb69ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147940"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Nasıl kullanılır: Çok Office kullanıcı arabirimini hedefleme
  Çok Dilde Kullanıcı Arabirimi (MUI), son kullanıcıya kullanıcı arabiriminin (UI) dilini değiştirme olanağı veren bir Microsoft Office özelliğidir. Örneğin, İngilizce kullanıcı arabirimiyle çalışan bir son kullanıcı, kullanıcı arabiriminin dilini İspanyolca olarak değiştirebilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Uygulamanız birçok Office dili kullanan kişiler tarafından kullanılacaksa, kullanıcı arabirimi dizelerinin dilini, kullanıcının bilgisayarında Office tarafından kullanılan dille eş olacak şekilde otomatik olarak değiştirmek için kod kullanılmaktadır (kullanıcının doğru kaynakları yüklüyse).

## <a name="to-check-the-current-office-ui-setting"></a>Geçerli kullanıcı arabirimi ayarını Office için

1. Geçerli <xref:System.Threading.Thread.CurrentUICulture%2A> iş parçacığının özelliğini kullanın. Kullanıcı arabirimi dizelerinin dilini, kullanıcının bilgisayarında çalışan Office diliyle eş olacak şekilde ayarlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Birincil Office derlemeleri aracılığıyla uygulamaları hedefle](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Çözümlerde Office bağlama](../vsto/late-binding-in-office-solutions.md)
