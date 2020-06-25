---
title: Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c420896a883146cf60de414100fc41080220e36
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282390"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama

<xref:System.Windows.Forms.BindingSource.Filter%2A>Özelliği, istenen kayıtları döndüren bir dize ifadesine ayarlayarak filtreleyebilirsiniz.

Özelliği, sıralamak istediğiniz sütun adına ayarlayarak verileri sıralayın <xref:System.Windows.Forms.BindingSource.Sort%2A> ; azalan düzende sıralamak için ekleme `DESC` yapın veya `ASC` artan düzende sıralamak için ekleyebilirsiniz.

> [!NOTE]
> Uygulamanız <xref:System.Windows.Forms.BindingSource> bileşenleri kullanmıyorsa, nesneleri kullanarak verileri filtreleyebilir ve sıralayabilirsiniz <xref:System.Data.DataView> . Daha fazla bilgi için bkz. [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri filtrelemek için

- <xref:System.Windows.Forms.BindingSource.Filter%2A>Özelliğini döndürmek istediğiniz ifadeye ayarlayın. Örneğin, aşağıdaki kod, `CompanyName` "B" ile başlayan müşterileri döndürür:

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri sıralamak için

- Özelliğini, <xref:System.Windows.Forms.BindingSource.Sort%2A> sıralamak istediğiniz sütuna ayarlayın. Örneğin, aşağıdaki kod, `CompanyName` sütunundaki müşterileri azalan sırada sıralar:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
