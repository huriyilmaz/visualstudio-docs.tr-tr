---
title: 'Nasıl Yapılır: Sınıf Tasarımcısı Kullanarak Tür Oluşturma'
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881a8ed7f1aceb5f97eaed1f0b9285951d1d39f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590182"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Nasıl yapilir: Sınıf Tasarımcısı'nı kullanarak türleri oluşturma

C# ve Visual Basic projeleri için yeni türler tasarlamak için bunları sınıf diyagramında oluşturun. Varolan türleri görmek için [bkz.](how-to-view-existing-types.md)

## <a name="create-a-new-type"></a><a name="CreateType"></a>Yeni bir tür oluşturma

1. Araç **Kutusunda**, **Sınıf Tasarımcısı**altında, bunlardan birini sınıf diyagramına sürükleyin:

    - **Sınıf** veya **Özet Sınıf**

    - **Sabit Listesi**

    - **Arabirim**

    - **Yapı** (VB) veya **Yapı** (C#)

    - **Temsilci**

    - **Modül** (sadece VB)

2. Türü adlandırın. Daha sonra erişim düzeyini seçin.

3. Tür için başlangıç kodunu eklemek istediğiniz dosyayı seçin:

    - Yeni bir dosya oluşturmak ve geçerli projeye eklemek için **yeni dosya oluştur'u** seçin ve dosyayı adlandırın.

    - Varolan bir dosyaya kod eklemek **için varolan dosyaya ekle'yi**seçin.

         Çözümünüzde birden çok uygulama arasında kod paylaşan bir proje varsa, uygulama projesindeki sınıf diyagramına yeni bir tür ekleyebilirsiniz, ancak yalnızca ilgili sınıf dosyası aynı uygulama projesindeyse veya paylaşılan projedeyse.

4. Şimdi, türü tanımlamak için diğer öğeleri ekleyin:

    |||
    |-|-|
    |**Için**|**Ekle**|
    |Sınıflar, soyut sınıflar, yapılar veya struct'lar|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem), yıkıcılar (yöntem) ve türü tanımlayan sabitler|
    |Numaralandırmalar|Numaralandırmayı oluşturan alan değerleri|
    |Arabirimler|Yöntemler, özellikler ve arabirimi oluşturan olaylar|
    |Temsilci|Temsilciyi tanımlayan parametreler|
    |Modül|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem) ve modülü tanımlayan sabitler|

     Bkz. [Üye Oluşturma.](creating-and-configuring-type-members.md#create-members)

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a>Bir türe özel bir öznitelik uygulama

1. Bir sınıf diyagramında türe ait şekle tıklayın.

2. **Özellikler'de,** tür için Özel **Öznitelikler** özelliğinin yanında, elips (...) düğmesini tıklatın.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

   Özel öznitelikler türüne uygulanır.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a>Bir tür üyesine özel bir öznitelik uygulama

1. Bir sınıf diyagramında kendi türünün şeklinde üyenin adına veya Sınıf Ayrıntıları penceresinde satırına tıklayın.

2. **Özellikler'de,** üyenin **Özel Öznitelikleri** özelliğini bulun.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

   Özel öznitelikler türüne uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılacağını: Türler Arasında Devralma Oluşturma](how-to-create-inheritance-between-types.md)
- [Nasıl yapılacağını: Türler Arasında İlişkilendirme Oluşturma](how-to-create-associations-between-types.md)
- [Tür Üyeleri Oluşturma ve Yapılandırma](creating-and-configuring-type-members.md)
- [Sınıfları ve Türleri Tasarlama](designing-and-viewing-classes-and-types.md)
