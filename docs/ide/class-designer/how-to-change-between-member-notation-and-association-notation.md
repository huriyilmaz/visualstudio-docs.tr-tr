---
title: Üye ve & değişikliği
description: Sınıf diyagramının üye notasyonundan ilişkilendirme Sınıf Tasarımcısı ilişki ilişkisine (veya tam tersi) arasındaki ilişki ilişkisini nasıl temsil ettiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3b97ff04abdbed42b9adb1a5fd2b41d4feca9931
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124223"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Nasıl Sınıf Tasarımcısı'de üye notasyonu ve ilişkilendirme Sınıf Tasarımcısı

Bu **Sınıf Tasarımcısı,** sınıf diyagramının üye notasyonundan ilişkilendirmeye iki tür arasındaki ilişkiyi temsil ettiği ilişkiyi (veya tam tersi) değiştirebilirsiniz. İlişki çizgileri olarak görüntülenen üyeler genellikle türlerin nasıl ilişkili olduğunu yararlı bir görselleştirme sağlar.

> [!NOTE]
> İlişki ilişkileri bir üye özelliği veya alanı olarak temsil olabilir. Üye notasyonu ilişkilendirme notasyonuna değiştirmek için, bir türün başka bir türün üyesi olması gerekir. İlişkileme notlarını üye notasyonuyla değiştirmek için iki türün bir ilişkilendirme çizgisiyle bağlı olması gerekir. Daha fazla bilgi için, [bkz. How to: Create associations between types](how-to-create-associations-between-types.md). Projeniz birden çok sınıf diyagramı içeriyorsa, diyagramda ilişki ilişkilerinin görüntülediği şekilde yaptığınız değişiklikler yalnızca bu diyagramı etkiler. Başka bir diyagramın ilişki ilişkilerini görüntüleme yolunu değiştirmek için bu diyagramı açın veya görüntüp bu adımları gerçekleştirin.

## <a name="to-change-member-notation-to-association-notation"></a>Üye notalarını ilişkilendirme ile değiştirmek için

1. Çözüm Gezgini proje düğümünden sınıf diyagramı (.cd) dosyasını açın.

2. Sınıf diyagramının tür şeklinde, ilişkilendirmeyi temsil eden üye özelliğine veya alanına sağ tıklayın ve İlişkili olarak **göster'i seçin.**

    > [!TIP]
    > Tür şeklinde hiçbir özellik veya alan görünmüyorsa, şekil bölmeleri daraltılmış olabilir. Tür şeklini genişletmek için bölme adına çift tıklayın veya tür şekline sağ tıklayın ve Genişlet'i **seçin.**

    Üye, tür şeklindeki bölmeden kaybolur ve iki türü bağlamak için bir ilişkilendirme çizgisi görünür. İlişki satırı, özelliğin veya alanın adıyla etiketlenmiş.

## <a name="to-change-association-notation-to-member-notation"></a>İlişkileme notlarını üye notasyonuyla değiştirmek için

Sınıf diyagramında ilişkilendirme satırına sağ tıklayın ve Uygun şekilde Özellik Olarak **Göster** veya Alan **Olarak Göster'i** seçin. İlişki çizgisi kaybolur ve özelliği diyagramda tür şeklinin içindeki uygun bölmede görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl: Türler Arasında Devralma Oluşturma](how-to-create-inheritance-between-types.md)
- [Nasıl: Türler Arasında Devralmayı Görüntüleme](how-to-view-inheritance-between-types.md)
- [Türleri ve İlişkileri Görüntüleme](designing-and-viewing-classes-and-types.md)
- [Nasıl: Koleksiyon İlişkisi Görselleştirme](how-to-visualize-a-collection-association.md)
