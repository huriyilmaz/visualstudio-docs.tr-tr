---
title: Özellik silinemiyor
description: Özellik silinemiyor. bu Visual Studio Nesne İlişkisel Tasarımcısı (O/R Designer) iletisiyle ilgili bilgileri görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 307e0f7bf52ed7e95536a13b4b292fda90ef4be1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631130"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>\<property name> özelliği silinemiyor

\<property name>Ve arasında devralmanın **ayrıştırıcı özelliği** olarak ayarlandığı için özellik silinemiyor \<class name>\<class name>

Seçilen özellik, hata iletisinde belirtilen sınıflar arasındaki devralma için **ayrıştırıcı özelliği** olarak ayarlanır. Veri sınıfları arasında devralma yapılandırmasına katılımları halinde Özellikler silinemez.

İstenen özelliğin başarıyla silinmesini sağlamak için, **ayrıştırıcı özelliğini** veri sınıfının farklı bir özelliğine ayarlayın.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. **O/R tasarımcısında**, hata iletisinde belirtilen veri sınıflarını bağlayan devralma satırını seçin.

2. **Ayrıştırıcı** özelliğini farklı bir özelliğe ayarlayın.

3. Özelliği silmeyi yeniden deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)