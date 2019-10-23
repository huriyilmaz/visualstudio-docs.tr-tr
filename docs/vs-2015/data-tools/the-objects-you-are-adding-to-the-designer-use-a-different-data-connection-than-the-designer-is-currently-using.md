---
title: Tasarımcıya eklemekte olduğunuz nesneler, tasarımcının Şu anda kullandığı farklı bir veri bağlantısı kullanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672298"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Tasarımcıya eklemekte olduğunuz nesneler, tasarımcının kullanmakta olduğundan farklı bir veri bağlantısı kullanıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tasarımcıya eklemekte olduğunuz nesneler, tasarımcının kullanmakta olduğundan farklı bir veri bağlantısı kullanır. Tasarımcı tarafından kullanılan bağlantıyı değiştirmek istiyor musunuz?

 @No__t_0 öğeler eklediğinizde ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), tüm öğeler paylaşılan bir veri bağlantısı kullanır. (Tasarım yüzeyi, yüzeyde tüm nesneler için tek bir bağlantı kullanan <xref:System.Data.Linq.DataContext> temsil eder.) Tasarımcıya, tasarımcı tarafından kullanılmakta olan veri bağlantısından farklı bir veri bağlantısı kullanan bir nesne eklerseniz, bu ileti görünür. Bu hatayı çözmek için var olan bağlantıyı korumayı seçebilirsiniz. Bu seçimi yaparsanız, seçilen nesne eklenmez. Alternatif olarak, nesneyi eklemeyi ve yeni bağlantıya <xref:System.Data.Linq.DataContext> bağlantıyı sıfırlamayı seçebilirsiniz.

> [!NOTE]
> **Evet**' e tıklarsanız, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tüm varlık sınıfları yeni bağlantıyla eşlenir.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Mevcut bağlantıyı seçilen nesne tarafından kullanılan bağlantıyla değiştirmek için

- **Evet**'i tıklayın.

     Seçilen nesne [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] eklenir ve DataContext. Connection yeni bağlantı olarak ayarlanır.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Mevcut bağlantıyı kullanmaya devam etmek ve seçili nesneyi eklemeyi iptal etmek için

- **Hayır**'a tıklayın.

     Eylem iptal edildi. DataContext. Connection mevcut bağlantı olarak ayarlanmış durumda kalır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)