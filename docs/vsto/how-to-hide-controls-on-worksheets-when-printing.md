---
title: 'Nasıl olur: Yazdırma sırasında çalışma sayfaları denetimlerini gizleme'
description: Windows Forms denetimlerini içeren bir çalışma Microsoft Office Excel yazdırırken denetimleri gizleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 621a33d8808b167bc17dd76b265ee0990bb11686
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100042"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Nasıl olur: Yazdırma sırasında çalışma sayfaları denetimlerini gizleme
  Formlar denetimlerini Microsoft Office Excel bir belgeyi Windows, denetimler yazdırılan çalışma sayfasında görünür. Çalışma sayfasını yazdırırken denetimleri gizleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> gibi veri görüntüleme denetimlerini gizlersanız, denetimde yer alan <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> veriler yazdırılan çalışma sayfasında görünmez.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Çalışma sayfası yazdırılırken denetimleri gizlemek için

1. Visual Studio'da Excel proje oluşturun veya açın ve **Sayfa1'in** tasarımcıda görünür olduğunu doğrulayın. Proje oluşturma hakkında daha fazla bilgi için [bkz. Nasıl Office: Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

2. Araç **Kutusunun Ortak** Denetimler **sekmesinden,** bir denetimi <xref:Microsoft.Office.Tools.Excel.Controls.Button> üzerinde bir hücreye `Sheet1` sürükleyin.

3. Özellikler **penceresinde** özelliğini <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> False olarak **ayarlayın.**

## <a name="see-also"></a>Ayrıca bkz.
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Nasıl Windows: Windows Form denetimleri ekleme Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Nasıl olur: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
