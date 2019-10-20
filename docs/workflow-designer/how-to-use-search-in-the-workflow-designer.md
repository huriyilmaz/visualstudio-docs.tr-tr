---
title: 'Nasıl yapılır: İş Akışı Tasarımcısı arama kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 12bda4af085b8ab41d3e11841f24cd5dfd389738
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650306"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısı arama kullanma

Daha büyük, daha karmaşık iş akışları oluşturmayı kolaylaştırmak için, öğeleri anahtar sözcüğe göre bulmak için İş Akışı Tasarımcısı içinde arama yapabilirsiniz. Tasarımcının değiştirme 'yi desteklemediğine unutmayın.

## <a name="quick-find"></a>Hızlı bul

Hızlı bul, tasarımcıda aşağıdakileri bulur:

- @No__t_0 nesnelerinin özellikleri, <xref:System.Activities.Statements.FlowNode> nesneleri, <xref:System.Activities.Statements.State> nesneleri, geçişleri ve diğer özel akış denetimi öğeleri.

- Değişkenler

- Arguments

- İfadeler

### <a name="use-quick-find"></a>Hızlı bul kullanma

1. İş akışı Tasarımcısı açıkken, **CTRL + F**tuşlarına basın veya **Düzenle**  > **bul** ' u seçin  > **hızlı bul**' u seçin.

2. **Aranan metin kutusuna** arama terimini girin ve **Sonrakini Bul**' a tıklayın.

3. Arama terimi geçerli iş akışında bulunur. Aşağıdaki görüntüde, tasarımcıda bulunan bir etkinlik görünen adı gösterilmektedir:

   ![İş Akışı Tasarımcısı arama sonucu](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Dosyalarda bul

Dosyalarda bul, XAML dosyaları da dahil olmak üzere iş akışı dosyalarındaki dizeleri bulur.

### <a name="use-find-in-files"></a>Dosyalarda bul kullanma

1. Visual Studio 'da, **Ctrl** +**SHIFT** +**F**tuşlarına basın veya**dosya içinde bul** > **Bul ve  >  Değiştir** ' i seçin.

2. **Aranan metin kutusuna** arama öğesini girin ve **Tümünü Bul**' a tıklayın.

3. Bulma sonucu **bul sonucu** görünümünde gösterilir. Bir sonuç öğesine çift tıklamak, iş akışı tasarımcısında eşleşmeyi içeren etkinliğe gider.