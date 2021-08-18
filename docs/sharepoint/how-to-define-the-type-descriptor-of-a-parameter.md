---
title: 'Nasıl ekleyebilirsiniz: Parametre Tanımlayıcısının Tür Tanımlayıcısını | Microsoft Docs'
description: İş verileri bağlantısı (BDC) modelinize bir yöntem için parametrenin tür tanımlayıcısını tanımlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ae1570010fc71d6edf56cdf9090f371c218a322a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148902"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Nasıl: Bir parametrenin tür tanımlayıcısını tanımlama
  Tür tanımlayıcısı, bir parametrenin veri türünü tanımlayan özellikler içerir. Tür tanımlayıcısı bir alan, varlık veya varlık koleksiyonu tanımlayabilir. Daha fazla bilgi için bkz. [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Bir parametrenin tür tanımlayıcısını tanımlamak için

1. **BDC Yöntem Ayrıntıları** penceresinde parametrenin tür tanımlayıcısını seçin.

2. Menü çubuğunda Görünüm , Özellikler **Penceresi'ne tıklayın.** 

3. Özellikler **penceresinde** tür tanımlayıcısının özelliklerini ayarlayın.

     Aşağıdaki yordamlar bir tür tanımlayıcısını alan, varlık veya varlık koleksiyonu olarak tanımlamayı açıklar.

### <a name="to-define-a-field"></a>Bir alan tanımlamak için

1. Özellikler **penceresinde,** tür **tanımlayıcısının Name** özelliğini varlığı temsil eden tür içinde bir alanın adıyla ayarlayın (Örneğin: **FirstName**).

2. **TypeName** özelliğinin yanındaki listede uygun veri türünü **(örneğin, Int32) seçin.**

     Diğer isteğe bağlı parametreler hakkında bilgi için bkz. [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>Bir varlık tanımlamak için

1. Özellikler **penceresinde** Name özelliğini **varlığı** açıklayan bir ad olarak ayarlayın (Örneğin: **Kişi).**

2. **TypeName özelliğini** varlığı temsil eden türün tam adı olarak ayarlayın. Bu tür projeniz içinde bir sınıf, çözümünüzde başvurarak bir derlemede tanımlanan bir tür veya BDC nesne modelinde tanımlanan bir tür olabilir.

    - Projenizin bir sınıfı için **TypeName** özelliğinin yanındaki aşağı oku seçin, görüntülenen **iletişim** kutusunda Geçerli Project sekmesini seçin ve ardından projenizin sınıfını seçin.

         Tam ad, ad alanını ve sınıfın adını ve ardından LOB sisteminin adını içerir. Aşağıdaki örnek, **TypeName** özelliğinin değerini projenizin bir sınıfına ayarlar.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Çözümünüzde bir derlemede bulunan bir tür için, tam ad türün adını, derlemenin adını, sürüm numarasını, kültürü ve ortak anahtar belirteci içerir.

         Aşağıdaki örnek, **TypeName** özelliğinin değerini, çözümünüzde başvurarak bir derlemede tanımlanan bir türe ayarlar.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - BDC nesne modelinde tanımlanan bir tür için, tam ad ad alanını ve türün adını içerir.

         Aşağıdaki örnek, **TypeName** özelliğinin değerini BDC nesne modelinde bir türe ayarlar.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. **BDC Yöntem Ayrıntıları** penceresinde tür tanımlayıcısı için görüntülenen listeyi açın ve düzenle'yi **seçin.**

     **BDC Gezgini** penceresi açılır.

4. **BDC Gezgini'nde** tür tanımlayıcısının kısayol menüsünü açın ve Ardından Tür Tanımlayıcısı **Ekle'yi seçin.**

     Varlık türü tanımlayıcısına alt olarak yeni bir tür tanımlayıcısı eklenir. Bu tür tanımlayıcısını bir alan olarak yapılandırma.

5. Varlığın her alanı için bir alt tür tanımlayıcısı eklemek için 4. adımı tekrarlayın.

### <a name="to-define-a-collection-of-entities"></a>Varlık koleksiyonunu tanımlamak için

1. **BDC Yöntem Ayrıntıları** penceresinde, istediğiniz parametrenin tür tanımlayıcısını seçin.

2. Menü çubuğunda Görünüm , Özellikler **Penceresi'ne tıklayın.** 

3. Özellikler **penceresinde** Name özelliğini varlığı **açıklayan** bir ad olarak ayarlayın (Örneğin: **Kişiler).**

4. **IsCollection özelliğini** True olarak **ayarlayın.** Bu, bu tür tanımlayıcısının bir varlık koleksiyonu olduğunu gösterir.

5. **TypeName özelliğini** arabirim başvurusu içeren bir dizeye ve varlığı temsil eden türün <xref:System.Collections.Generic.IEnumerable%601> tam adını ayarlayın. Bu tür projeniz içinde bir sınıf, çözümünüzde başvurarak bir derlemede tanımlanan bir tür veya BDC nesne modelinde tanımlanan bir tür olabilir.

   - Projenizin bir sınıfı için **TypeName** özelliğinin yanındaki aşağı oku seçin, görüntülenen **iletişim** kutusunda Geçerli Project sekmesini seçin ve ardından projenizin sınıfını seçin.

      Tam ad, ad alanını ve sınıfın adını ve ardından LOB sisteminin adını içerir.

      Aşağıdaki örnek, **TypeName** özelliğinin değerini projenizin sınıf koleksiyonuna ayarlar.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.BdcModel1.Contact, BdcModel1]'

   - Çözümünüzde bir derlemede bulunan bir tür için, tam ad türün adını, derlemenin adını, sürüm numarasını, kültürü ve ortak anahtar belirteci içerir.

      Aşağıdaki örnek, **TypeName** özelliğinin değerini, çözümünüzde başvurarak bir derlemedeki tür koleksiyonuna ayarlar.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]'

   - BDC nesne modelinde tanımlanan bir tür için, tam ad yalnızca ad alanını ve türün adını içerir.

      Aşağıdaki örnek, **TypeName** özelliğinin değerini BDC nesne modelinde tanımlanan tür koleksiyonuna ayarlar.

      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]'

6. **BDC Yöntem Ayrıntıları** penceresinde tür tanımlayıcısı için görüntülenen listeyi açın ve düzenle'yi **seçin.**

    **BDC Gezgini** penceresi açılır.

7. **BDC Gezgini'nde** tür tanımlayıcısının kısayol menüsünü açın ve Ardından Tür Tanımlayıcısı **Ekle'yi seçin.**

    Koleksiyon türü tanımlayıcısına alt olarak yeni bir tür tanımlayıcısı eklenir. Bu tür tanımlayıcısını varlık olarak yapılandırma.

## <a name="see-also"></a>Ayrıca bkz.
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl kullanılır: Modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Nasıl yapılanlar: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
