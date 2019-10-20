---
title: Sınıf Tasarımcısı C++ görsel numaralandırmalar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651660"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Sınıf Tasarımcısında Visual C++ Numaralandırmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı `enum` C++ ve kapsamlı `enum class` türlerini destekler. Aşağıda bir örnek verilmiştir:

```
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

```

 Bir C++ sınıf diyagramındaki sabit listesi şekli bir yapı şekli gibi görünür ve bu şekilde çalışıyor, etiket **enum** veya **enum sınıfını**okuduğu, mavi yerine pembe ve sol ve üst kenar boşluklarında renkli bir kenarlığa sahip olur. Hem numaralandırma şekilleri hem de yapı şekillerinin kare köşeleri vardır.

 @No__t_0 türünü kullanma hakkında daha fazla bilgi için bkz. [numaralandırmalar](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).

## <a name="see-also"></a>Ayrıca Bkz.
 [Görsel C++ kod (sınıf Tasarımcısı)](../ide/working-with-visual-cpp-code-class-designer.md) [Numaralandırmalarla](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) çalışma
