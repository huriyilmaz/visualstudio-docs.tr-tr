---
title: Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama
description: Windows Forms uygulamasındaki verileri filtreleme ve sıralama. Filter özelliğini, istenen kayıtları döndüren bir dize ifadesi olarak ayarlayın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 045da0ade1ce60e2a8d21c24238c8e2b061e8612
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215831"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama

<xref:System.Windows.Forms.BindingSource.Filter%2A>Özelliği, istenen kayıtları döndüren bir dize ifadesine ayarlayarak filtreleyebilirsiniz.

Özelliği, sıralamak istediğiniz sütun adına ayarlayarak verileri sıralayın <xref:System.Windows.Forms.BindingSource.Sort%2A> ; azalan düzende sıralamak için ekleme `DESC` yapın veya `ASC` artan düzende sıralamak için ekleyebilirsiniz.

> [!NOTE]
> Uygulamanız <xref:System.Windows.Forms.BindingSource> bileşenleri kullanmıyorsa, nesneleri kullanarak verileri filtreleyebilir ve sıralayabilirsiniz <xref:System.Data.DataView> . Daha fazla bilgi için bkz. [DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri filtrelemek için

- <xref:System.Windows.Forms.BindingSource.Filter%2A>Özelliğini döndürmek istediğiniz ifadeye ayarlayın. Örneğin, aşağıdaki kod, `CompanyName` "B" ile başlayan müşterileri döndürür:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource bileşeni kullanarak verileri sıralamak için

- Özelliğini, <xref:System.Windows.Forms.BindingSource.Sort%2A> sıralamak istediğiniz sütuna ayarlayın. Örneğin, aşağıdaki kod, `CompanyName` sütunundaki müşterileri azalan sırada sıralar:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
