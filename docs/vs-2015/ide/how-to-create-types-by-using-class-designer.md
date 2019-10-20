---
title: 'Nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d05b8a492768dfe9163d7ede55c2bf4aef084c26
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668022"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Nasıl Yapılır: Sınıf Tasarımcısı Kullanarak Tür Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C# .net ve Visual Basic .NET projeleri için yeni türler tasarlamak üzere bunları bir sınıf diyagramında oluşturun. Varolan türleri görmek için bkz. [nasıl yapılır: varolan türleri görüntüleme (sınıf Tasarımcısı)](../ide/how-to-view-existing-types-class-designer.md).

- [Yeni bir tür oluştur](#CreateType)

- [Türe özel bir öznitelik uygulama](#CustAttributeType)

- [Bir tür üyesine özel bir öznitelik uygulama](#CustAttributeMember)

## <a name="CreateType"></a>Yeni bir tür oluştur

1. Araç Kutusu'nda, Sınıf Tasarımcısı'nın altında aşağıdakilerden birini bir sınıf diyagramına sürükleyin:

    - **Sınıf** veya **soyut sınıf**

    - **Yardımının**

    - **Arayüz**

    - **Yapı** (vb) veya **struct** (C#)

    - **Ğini**

    - **Modül** (yalnızca vb)

2. Türü adlandırın. Daha sonra erişim düzeyini seçin.

3. Tür için başlangıç kodunu eklemek istediğiniz dosyayı seçin:

    - Yeni bir dosya oluşturmak ve geçerli projeye eklemek için **yeni dosya oluştur** ' u seçin ve dosyayı adlandırın.

    - Varolan bir dosyaya kod eklemek için **varolan dosyaya ekle**' yi seçin.

         Çözümünüz birden çok uygulama arasında kod paylaşan bir proje içeriyorsa, uygulama projesindeki sınıf diyagramına yeni bir tür ekleyebilirsiniz, ancak yalnızca karşılık gelen sınıf dosyası aynı uygulama projesinde ise veya paylaşılan projem ise.

4. Şimdi, türü tanımlamak için diğer öğeleri ekleyin:

    |||
    |-|-|
    |**Bekleniyor**|**Add**|
    |Sınıflar, soyut sınıflar, yapılar veya struct'lar|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem), yıkıcılar (yöntem) ve türü tanımlayan sabitler|
    |Numaralandırmalar|Numaralandırmayı oluşturan alan değerleri|
    |Arabirimler|Yöntemler, özellikler ve arabirimi oluşturan olaylar|
    |Temsilci|Temsilciyi tanımlayan parametreler|
    |Modül|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem) ve modülü tanımlayan sabitler|

     Bkz. [üyeleri oluşturma](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

## <a name="CustAttributeType"></a>Türe özel bir öznitelik uygulama

1. Bir sınıf diyagramında türe ait şekle tıklayın.

2. Özellikler penceresi, türün **özel öznitelikler** özelliğinin yanındaki üç nokta (...) düğmesine tıklayın.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

     İşiniz bittiğinde özel öznitelikler türe uygulanır.

## <a name="CustAttributeMember"></a>Bir tür üyesine özel bir öznitelik uygulama

1. Bir sınıf diyagramında kendi türünün şeklinde üyenin adına veya Sınıf Ayrıntıları penceresinde satırına tıklayın.

2. Özellikler penceresi, üyenin **özel öznitelikler** özelliğini bulun.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

     İşiniz bittiğinde özel öznitelikler türe uygulanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: türler arasında devralma oluşturma (sınıf Tasarımcısı)](../ide/how-to-create-inheritance-between-types-class-designer.md) [nasıl yapılır: türler arasında ilişkilendirme oluşturma (sınıf Tasarımcısı)](../ide/how-to-create-associations-between-types-class-designer.md) [Tür üyeleri oluşturma ve yapılandırma (sınıf Tasarımcısı)](../ide/creating-and-configuring-type-members-class-designer.md) [sınıf diyagramları ile çalışma (sınıf Tasarımcısı)](../ide/working-with-class-diagrams-class-designer.md) [Sınıfları ve türleri tasarlama (sınıf Tasarımcısı)](../ide/designing-classes-and-types-class-designer.md)
