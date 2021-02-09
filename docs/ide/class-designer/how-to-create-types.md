---
title: 'Nasıl Yapılır: Sınıf Tasarımcısı Kullanarak Tür Oluşturma'
description: C# ve Visual Basic projeleri için bir sınıf diyagramında oluşturarak yeni türler tasarlamayı öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 6102d5252564834f1de7c533e763d7b08a8f9fb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880547"
---
# <a name="how-to-create-types-by-using-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma

C# ve Visual Basic projelerine yönelik yeni türler tasarlamak için bunları bir sınıf diyagramında oluşturun. Varolan türleri görmek için bkz. [nasıl yapılır: varolan türleri görüntüleme](how-to-view-existing-types.md).

## <a name="create-a-new-type"></a><a name="CreateType"></a> Yeni bir tür oluştur

1. **Araç kutusunda**, **Sınıf Tasarımcısı** altında, bunlardan birini bir sınıf diyagramına sürükleyin:

    - **Sınıf** veya **soyut sınıf**

    - **Sabit listesi**

    - **Arabirim**

    - **Yapı** (vb) veya **Yapı** (C#)

    - **Temsilci**

    - **Modül** (yalnızca vb)

2. Türü adlandırın. Daha sonra erişim düzeyini seçin.

3. Tür için başlangıç kodunu eklemek istediğiniz dosyayı seçin:

    - Yeni bir dosya oluşturmak ve geçerli projeye eklemek için **yeni dosya oluştur** ' u seçin ve dosyayı adlandırın.

    - Varolan bir dosyaya kod eklemek için **varolan dosyaya ekle**' yi seçin.

         Çözümünüz birden çok uygulama arasında kod paylaşan bir proje içeriyorsa, uygulama projesindeki sınıf diyagramına yeni bir tür ekleyebilirsiniz, ancak yalnızca karşılık gelen sınıf dosyası aynı uygulama projesinde ise veya paylaşılan projem ise.

4. Şimdi, türü tanımlamak için diğer öğeleri ekleyin:

    |**Bekleniyor**|**Ekle**|
    |-|-|
    |Sınıflar, soyut sınıflar, yapılar veya struct'lar|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem), yıkıcılar (yöntem) ve türü tanımlayan sabitler|
    |Numaralandırmalar|Numaralandırmayı oluşturan alan değerleri|
    |Arabirimler|Yöntemler, özellikler ve arabirimi oluşturan olaylar|
    |Temsilci|Temsilciyi tanımlayan parametreler|
    |Modül|Yöntemler, özellikler, alanlar, olaylar, yapıcılar (yöntem) ve modülü tanımlayan sabitler|

     Bkz. [üyeleri oluşturma](creating-and-configuring-type-members.md#create-members).

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> Türe özel bir öznitelik uygulama

1. Bir sınıf diyagramında türe ait şekle tıklayın.

2. **Özellikler**' de, türün **özel öznitelikler** özelliğinin yanındaki üç nokta (...) düğmesine tıklayın.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

   Özel öznitelikler türe uygulanır.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> Bir tür üyesine özel bir öznitelik uygulama

1. Bir sınıf diyagramında kendi türünün şeklinde üyenin adına veya Sınıf Ayrıntıları penceresinde satırına tıklayın.

2. **Özellikler**' de üyenin **özel öznitelikler** özelliğini bulun.

3. Satır başına bir olmak üzere, bir ya da daha fazla özel öznitelik ekleyin. Bunları ayraçlar içine almayın.

   Özel öznitelikler türe uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: türler arasında devralma oluşturma](how-to-create-inheritance-between-types.md)
- [Nasıl yapılır: türler arasında Ilişkilendirme oluşturma](how-to-create-associations-between-types.md)
- [Tür Üyeleri Oluşturma ve Yapılandırma](creating-and-configuring-type-members.md)
- [Sınıfları ve Türleri Tasarlama](designing-and-viewing-classes-and-types.md)
