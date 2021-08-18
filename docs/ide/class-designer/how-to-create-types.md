---
title: 'Nasıl Yapılır: Sınıf Tasarımcısı Kullanarak Tür Oluşturma'
description: C# için yeni türler tasarlamayı ve Visual Basic diyagramda proje oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 51379952830a518b6a5f57cfed75d632f3c3f0c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102031"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Nasıl Sınıf Tasarımcısı kullanarak türler oluşturma

C# için yeni türler tasarlamak Visual Basic projelerini sınıf diyagramında oluşturun. Mevcut türleri görmek için [bkz. Nasıl 2.](how-to-view-existing-types.md)

## <a name="create-a-new-type"></a><a name="CreateType"></a> Yeni tür oluşturma

1. Araç **Kutusunda,** Sınıf Tasarımcısı **altında,** bunlardan birini bir sınıf diyagramına sürükleyin:

    - **Sınıf** veya **Soyut Sınıf**

    - **Sabit listesi**

    - **Arabirim**

    - **Yapı** (VB) veya **Yapı** (C#)

    - **Temsilci**

    - **Modül** (yalnızca VB)

2. Türü adlandırın. Daha sonra erişim düzeyini seçin.

3. Tür için başlangıç kodunu eklemek istediğiniz dosyayı seçin:

    - Yeni bir dosya oluşturmak ve bunu geçerli projeye eklemek için Yeni dosya **oluştur'a tıklayın ve** dosyayı olarak ad girin.

    - Mevcut bir dosyaya kod eklemek için Var olan dosyaya **ekle'yi seçin.**

         Çözümünüz birden çok uygulama arasında kod paylaşan bir projeye sahipse, uygulama projesinde bir sınıf diyagramına yeni bir tür eklersiniz, ancak yalnızca karşılık gelen sınıf dosyası aynı uygulama projesinde veya paylaşılan projede ise.

4. Şimdi, türü tanımlamak için diğer öğeleri ekleyin:

    |**Için**|**Ekle**|
    |-|-|
    |Sınıflar, soyut sınıflar, yapılar veya struct'lar|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem), yıkıcılar (yöntem) ve türü tanımlayan sabitler|
    |Numaralandırmalar|Numaralandırmayı oluşturan alan değerleri|
    |Arabirimler|Yöntemler, özellikler ve arabirimi oluşturan olaylar|
    |Temsilci|Temsilciyi tanımlayan parametreler|
    |Modül|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem) ve modülü tanımlayan sabitler|

     Bkz. [Üye Oluşturma.](creating-and-configuring-type-members.md#create-members)

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Bir türe özel öznitelik uygulama

1. Bir sınıf diyagramında türe ait şekle tıklayın.

2. **Özellikler'de,** **türün Özel Öznitelikler** özelliğinin yanında üç nokta (...) düğmesine tıklayın.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

   Özel öznitelikler türe uygulanır.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Tür üyesine özel öznitelik uygulama

1. Bir sınıf diyagramında kendi türünün şeklinde üyenin adına veya Sınıf Ayrıntıları penceresinde satırına tıklayın.

2. **Özellikler'de,** üyenin **Özel Öznitelikler özelliğini** bulun.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

   Özel öznitelikler türe uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl: Türler Arasında Devralma Oluşturma](how-to-create-inheritance-between-types.md)
- [Nasıl kurulur: Türler Arasında İlişki oluşturma](how-to-create-associations-between-types.md)
- [Tür Üyeleri Oluşturma ve Yapılandırma](creating-and-configuring-type-members.md)
- [Sınıfları ve Türleri Tasarlama](designing-and-viewing-classes-and-types.md)
