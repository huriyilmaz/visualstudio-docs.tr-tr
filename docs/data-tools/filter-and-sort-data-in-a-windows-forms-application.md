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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 68adaf6df9f97bee94e7cb393fa01ee133444c80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648466"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama

@No__t_0 özelliğini, istenen kayıtları döndüren bir dize ifadesi olarak ayarlayarak verileri filtreleyebilirsiniz.

@No__t_0 özelliğini, sıralamak istediğiniz sütun adına ayarlayarak verileri sıralarsınız; azalan düzende sıralamak için `DESC` ekleyin veya artan düzende sıralamak için `ASC` ekleyin.

> [!NOTE]
> Uygulamanız <xref:System.Windows.Forms.BindingSource> bileşenleri kullanmıyorsa, <xref:System.Data.DataView> nesneleri kullanarak verileri filtreleyebilir ve sıralayabilirsiniz. Daha fazla bilgi için bkz. [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri filtrelemek için

- @No__t_0 özelliğini döndürmek istediğiniz ifadeye ayarlayın. Örneğin, aşağıdaki kod, müşterileri "B" ile başlayan bir `CompanyName` döndürür:

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri sıralamak için

- @No__t_0 özelliğini, sıralamak istediğiniz sütuna ayarlayın. Örneğin, aşağıdaki kod müşterileri `CompanyName` sütununda azalan düzende sıralar:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)