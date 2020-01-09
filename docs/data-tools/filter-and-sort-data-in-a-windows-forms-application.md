---
title: Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 596397cc22cf0f0134463256c0861127dcfb81e1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586620"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama

<xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini, istenen kayıtları döndüren bir dize ifadesi olarak ayarlayarak verileri filtreleyebilirsiniz.

<xref:System.Windows.Forms.BindingSource.Sort%2A> özelliğini, sıralamak istediğiniz sütun adına ayarlayarak verileri sıralarsınız; azalan düzende sıralamak için `DESC` ekleyin veya artan düzende sıralamak için `ASC` ekleyin.

> [!NOTE]
> Uygulamanız <xref:System.Windows.Forms.BindingSource> bileşenleri kullanmıyorsa, <xref:System.Data.DataView> nesneleri kullanarak verileri filtreleyebilir ve sıralayabilirsiniz. Daha fazla bilgi için bkz. [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri filtrelemek için

- <xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini döndürmek istediğiniz ifadeye ayarlayın. Örneğin, aşağıdaki kod, müşterileri "B" ile başlayan bir `CompanyName` döndürür:

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri sıralamak için

- <xref:System.Windows.Forms.BindingSource.Sort%2A> özelliğini, sıralamak istediğiniz sütuna ayarlayın. Örneğin, aşağıdaki kod müşterileri `CompanyName` sütununda azalan düzende sıralar:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
