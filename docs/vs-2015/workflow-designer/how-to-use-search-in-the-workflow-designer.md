---
title: 'Nasıl yapılır: İş Akışı Tasarımcısı arama kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84f74b4718a7f976b386197a79692256ab49caa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659130"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısı arama kullanma
Daha büyük, daha karmaşık iş akışları oluşturmayı kolaylaştırmak için arama İş Akışı Tasarımcısı öğeleri anahtar sözcüğe göre bulmak için kullanılabilir. Tasarımcının değiştirme 'yi desteklemediğine unutmayın. Arama, tasarımcıda aşağıdakileri bulur:

## <a name="quick-find"></a>Hızlı bul
 Hızlı bul, tasarımcıda aşağıdakileri bulur:

- @No__t_0 nesnelerinin özellikleri, <xref:System.Activities.Statements.FlowNode> nesneleri, <xref:System.Activities.Statements.State> nesneleri, geçişleri ve diğer özel akış denetimi öğeleri.

- Değişkenler

- Arguments

- İfadeler

#### <a name="using-quick-find"></a>Hızlı bulma kullanma

1. İş akışı Tasarımcısı açıkken, **CTRL + F**tuşlarına basın veya **Düzenle**, **Bul ve Değiştir**, **hızlı bul**' u seçin.

2. **Aranan metin kutusuna** arama terimini girin ve **Sonrakini Bul**' a tıklayın.

3. Arama terimi geçerli iş akışında yer alır. Aşağıdaki ekran görüntüsünde, tasarımcıda bulunan bir etkinlik görünen adı gösterilmektedir.

     ![İş Akışı Tasarımcısı arama sonucu](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Dosyalarda bul
 Dosyalarda bul ' u kullanmak, XAML dosyaları da dahil olmak üzere iş akışı dosyalarındaki dizeleri bulur.

#### <a name="using-find-in-files"></a>Dosyalarda bul kullanma

1. Visual Studio 'da, **CTRL + SHIFT + F**tuşlarına basın veya **Düzenle**, **Bul ve Değiştir**, **dosyalarda bul** ' u seçin

2. **Aranan metin kutusuna** arama öğesini girin ve **Tümünü Bul** ' a tıklayın.

3. Bulma sonucu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]**sonucu bul** görünümünde gösterilir. Bir sonuç öğesine çift tıklamak, iş akışı tasarımcısında eşleşmeyi içeren etkinliğe gidecektir.