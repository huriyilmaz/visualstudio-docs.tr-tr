---
title: 'Nasıl yapılır: türler arasında devralma oluşturma (Sınıf Tasarımcısı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668102"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Nasıl yapılır: türler arasında devralma oluşturma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı kullanarak bir sınıf diyagramında iki tür arasında bir devralma ilişkisi oluşturmak için, temel türü türetilen tür veya türleriyle bağlayın. İki sınıf arasında, bir sınıf ile arabirim arasında veya iki arabirim arasında bir devralma ilişkisine sahip olabilirsiniz.

### <a name="to-create-an-inheritance-between-types"></a>Türler arasında devralma oluşturmak için

1. Çözüm Gezgini ' de projenizden bir sınıf diyagramı (. CD) dosyası açın.

     Bir sınıf diyagramınız yoksa, oluşturun. Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. **Araç kutusunda**, **Sınıf Tasarımcısı**altında **Devralma**' ı tıklatın.

3. Sınıf diyagramında, buradan başlayarak istediğiniz türler arasında bir devralma çizgisi çizin:

    - Taban sınıfına türetilmiş bir sınıf

    - Uygulanan arabirim için uygulama sınıfı

    - Genişletilmiş arabirime yönelik genişletme arabirimi

4. İsteğe bağlı olarak, genel bir türden türetilmiş bir türse, devralma satırına tıklayın. **Özellikler** penceresinde, **tür bağımsız değişkenleri** özelliğini genel tür için istediğiniz türle eşleşecek şekilde ayarlayın.

    > [!NOTE]
    > Bir üst soyut sınıf en az bir soyut üye içeriyorsa, tüm soyut Üyeler soyut olmayan devralma sınıfları olarak uygulanır.
    >
    >  Mevcut genel türleri görselleştirebilseniz de, yeni genel türler oluşturamazsınız. Ayrıca, varolan genel türler için tür parametrelerini değiştiremezsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Devralma](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea) [Devralma hakkında temel bilgiler](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5) : [Sınıf Tasarımcısı içindeki C++ ](../ide/visual-cpp-classes-in-class-designer.md) [türler (sınıf Tasarımcısı) görsel sınıfları arasında devralmayı görüntüleme](../ide/how-to-view-inheritance-between-types-class-designer.md)
