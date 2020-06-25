---
title: Özellik silinemiyor
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 91fce94babf443c974a49885263b8e7eb77d9eaa
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281351"
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

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)