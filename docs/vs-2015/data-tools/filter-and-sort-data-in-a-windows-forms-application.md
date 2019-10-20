---
title: Windows Forms uygulamasındaki verileri filtreleme ve sıralama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671644"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 özelliğini, istenen kayıtları döndüren bir dize ifadesi olarak ayarlayarak verileri filtreleyebilirsiniz.

 @No__t_0 özelliğini, sıralamak istediğiniz sütun adı olarak ayarlayarak verileri sıralarsınız; azalan düzende sıralamak için `DESC` ekleyin veya artan düzende sıralamak için `ASC` ekleyin.

> [!NOTE]
> Uygulamanız <xref:System.Windows.Forms.BindingSource> bileşenleri kullanmıyorsa, <xref:System.Data.DataView> nesneleri kullanarak verileri filtreleyebilir ve sıralayabilirsiniz. Daha fazla bilgi için bkz. [DataView](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri filtrelemek için

- @No__t_0 özelliğini döndürmek istediğiniz ifadeye ayarlayın. Örneğin, aşağıdaki kod, müşterileri "B" ile başlayan bir `CompanyName` döndürür:

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri sıralamak için

- @No__t_0 özelliğini, sıralamak istediğiniz sütuna ayarlayın. Örneğin, aşağıdaki kod müşterileri `CompanyName` sütununda azalan düzende sıralar:

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
