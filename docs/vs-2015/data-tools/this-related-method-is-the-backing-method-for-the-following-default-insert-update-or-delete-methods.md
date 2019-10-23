---
title: Bu ilgili yöntem, aşağıdaki varsayılan ekleme, güncelleştirme veya silme yöntemleri için yedekleme yöntemidir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84d27dc6f5081a36a237748c091429cfdabbe841
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667176"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Bu ilgili metot, aşağıdaki varsayılan ekleme, güncelleştirme ve silme metotları için yedek bir metottur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu ilgili yöntem, aşağıdaki varsayılan INSERT, Update veya Delete yöntemleri için yedekleme yöntemidir. Silinirse, bu yöntemler de silinir. Devam etmek istiyor musunuz?

 Seçili `DataContext` yöntemi şu anda O/R tasarımcısında olan varlık sınıflarından biri için INSERT, Update veya delete yöntemlerinden biri olarak kullanılıyor. Seçili yöntemi silmek, bu yöntemi kullanan varlık sınıfının bir güncelleştirme sırasında INSERT, Update veya Delete işlemini gerçekleştirmek için varsayılan çalışma zamanı davranışına geri dönmesi oluşmasına neden olur.

### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Seçili yöntemi silmek için, Entity sınıfının çalışma zamanı güncelleştirmelerini kullanmasına neden olur

- **Evet**'i tıklayın.

     Seçilen yöntem silinir ve güncelleştirme davranışını geçersiz kılmak için bu yöntemi kullanan sınıflar varsayılan LINQ to SQL çalışma zamanı davranışı kullanılarak döndürülür.

### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>İleti kutusunu kapatmak için, seçili yöntemi değiştirmeden bırakın

- **Hayır**'a tıklayın.

     İleti kutusu kapanır ve hiçbir değişiklik yapılmaz.

## <a name="see-also"></a>Ayrıca Bkz.
 [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) [How: [Visual Studio 'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md) güncelleştirme, ekleme ve silme (O/R Designer) ](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) LINQ to SQL araçları gerçekleştirmek için saklı yordamlar atama [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
