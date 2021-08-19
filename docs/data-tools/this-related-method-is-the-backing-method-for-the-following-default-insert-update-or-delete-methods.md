---
title: Backing yöntemi silinedi
description: Bu ilgili metot, aşağıdaki varsayılan ekleme, güncelleştirme ve silme metotları için yedek bir metottur
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8dcf07340584a3103a854dae3ffa7787cabee448
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129915"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Bu ilgili metot, aşağıdaki varsayılan ekleme, güncelleştirme ve silme metotları için yedek bir metottur

Bu ilgili yöntem, aşağıdaki varsayılan , veya yöntemleri `Insert` `Update` için backing `Delete` yöntemidir. Silinirse, bu yöntemler de silinir. Devam etmek istiyor musunuz?

Seçilen `DataContext` yöntem şu anda `Insert` `Update` `Delete` **O/R Tasarımcısı'nda** varlık sınıflarından biri için , veya yöntemlerinden biri olarak kullanılır. Seçilen yöntemin silinmesi, bu yöntemi kullanan varlık sınıfının bir güncelleştirme sırasında ekleme, güncelleştirme veya silme gerçekleştirmeye yönelik varsayılan çalışma zamanı davranışına dönmesine neden olur.

## <a name="selected-method-options"></a>Seçilen yöntem seçenekleri

- Seçilen yöntemi silmek ve varlık sınıfının çalışma zamanı güncelleştirmelerini kullanmasına neden olmak için Evet'e **tıklayın.**

   Seçilen yöntem silinir ve güncelleştirme davranışını geçersiz kılma için bu yöntemi kullanan tüm sınıflar varsayılan çalışma zamanı davranışı LINQ to SQL geri döner.

- İleti kutusunu kapatmak için, seçili yöntemi değiştirmeden bırakın, Hayır'a **tıklayın.**

   İleti kutusu kapanır ve hiçbir değişiklik olmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)