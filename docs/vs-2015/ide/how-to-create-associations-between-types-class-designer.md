---
title: 'Nasıl yapılır: türler arasında Ilişkilendirme oluşturma (Sınıf Tasarımcısı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb46d3bf7096d0a7e14ce3926514d946d7536e2d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668111"
---
# <a name="how-to-create-associations-between-types-class-designer"></a>Nasıl yapılır: türler arasında Ilişkilendirme oluşturma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı'nda ilişkilendirme çizgileri, bir diyagramdaki sınıfların nasıl ilişkili olduğunu gösterir. İlişkilendirme çizgisi, projenizdeki başka bir sınıfın özellik veya alan türü olan bir sınıfı temsil eder. İlişkilendirme çizgileri genellikle, projenizdeki sınıflar arasında en önemli ilişkileri göstermek için kullanılır.

 Tüm alanları ve özellikleri ilişkilendirmeler halinde görüntüleyebilirsiniz; bununla birlikte diyagramda vurgulamak istediğiniz unsura bağlı olarak yalnızca önemli üyeleri ilişkilendirme olarak göstermek daha anlamlı olur. (Daha az önemli üyeleri normal üye olarak gösterebilir veya bütünüyle gizleyebilirsiniz.)

> [!NOTE]
> Sınıf Tasarımcısı yalnızca tek yönlü ilişkilendirmeleri destekler.

### <a name="to-define-an-association-line-in-the-class-diagram"></a>Sınıf Diyagramı'nda bir ilişkilendirme çizgisi tanımlamak için

1. Araç kutusunda, Sınıf Tasarımcısı altında **ilişkilendirme**' yi seçin.

2. İlişkilendirme ile bağlamak istediğiniz iki şekil arasına bir çizgi çizin.

     İlk sınıfta yeni bir özellik oluşturulur. Bu özellik varsayılan ada sahip bir ilişkilendirme çizgisi görüntüler (şekildeki bir bölme içinde özellik olarak değil). Türü ise, ilişkilendirme çizgisinin işaret ettiği şekildir.

### <a name="to-change-the-name-of-an-association"></a>İlişkilendirmenin adını değiştirmek için

- Diyagram yüzeyinde ilişkilendirme çizgisinin etiketine tıklayın ve etiketi düzenleyin.

  \- veya-

1. İlişkilendirme olarak gösterilen özelliği içeren şekle tıklayın.

     Şekil odağı alır ve üyeleri Sınıf Ayrıntıları penceresinde ve Özellikler penceresinde görüntülenir.

2. Sınıf Ayrıntıları penceresinde ya da Özellikler penceresinde bu özelliğe ilişkin ad alanını düzenleyin ve Enter tuşuna basın.

     Ad, **Sınıf Ayrıntıları** penceresinde, ilişkilendirme satırındaki Özellikler penceresi ve kod ' de güncelleştirilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl Yapılır: Üye Gösterimi ile İlişkilendirme Gösterimi Arasında Geçiş (Sınıf Tasarımcısı)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)
