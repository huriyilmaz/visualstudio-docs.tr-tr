---
title: 'Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b3ae803576c98a86a45d175af45aa28b3852134
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016843"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama
  Bir tür tanımlayıcısı, bir parametrenin veri türünü tanımlayan özellikler içerir. Bir tür tanımlayıcısı bir alanı, varlığı veya bir varlık koleksiyonunu tanımlayabilir. Daha fazla bilgi için bkz. [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Bir parametrenin tür tanımlayıcısını tanımlamak için

1. **BDC Yöntem ayrıntıları** penceresinde, parametrenin tür tanımlayıcısını seçin.

2. Menü çubuğunda **Görünüm**, **Özellikler penceresi**' ni seçin.

3. **Özellikler** penceresinde, tür tanımlayıcısının özelliklerini ayarlayın.

     Aşağıdaki yordamlar bir tür tanımlayıcısının alan, varlık veya varlık koleksiyonu olarak nasıl tanımlanacağını açıklamaktadır.

### <a name="to-define-a-field"></a>Bir alan tanımlamak için

1. **Özellikler** penceresinde, tür tanımlayıcısının **Name** özelliğini varlığı temsil eden türdeki bir alanın adı olarak ayarlayın (örneğin: **FirstName**).

2. **TypeName** özelliğinin yanındaki listede uygun veri türünü (örneğin, **Int32**) seçin.

     Diğer isteğe bağlı parametreler hakkında daha fazla bilgi için bkz. [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>Bir varlık tanımlamak için

1. **Özellikler** penceresinde, **ad** özelliğini varlığı tanımlayan bir ad olarak ayarlayın (örneğin: **iletişim**).

2. **TypeName** özelliğini, varlığı temsil eden türün tam nitelikli adı olarak ayarlayın. Bu tür, projenizdeki bir sınıf, çözümünüzde başvurduğunuz bir derlemede tanımlanan bir tür veya IVB nesne modelinde tanımlı bir tür olabilir.

    - Projenizdeki bir sınıf için **TypeName** özelliğinin yanındaki aşağı oku seçin, görüntülenen Iletişim kutusunda **geçerli proje** sekmesini seçin ve ardından projenizdeki sınıfı seçin.

         Tam nitelikli ad, sınıfın ad alanını ve adını ve ardından LOB sisteminin adını içerir. Aşağıdaki örnek, **TypeName** özelliğinin değerini projenizdeki bir sınıfa ayarlar.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Çözümünüzdeki derlemede bulunan bir tür için, tam nitelikli ad, türün adını, derleme adını, sürüm numarasını, kültürü ve ortak anahtar belirtecini içerir.

         Aşağıdaki örnek, **TypeName** özelliğinin değerini, çözümünüzde başvurduğunuz bir derlemede tanımlanan bir türe ayarlar.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - IVB nesne modelinde tanımlı bir tür için, tam nitelikli ad ad alanını ve türün adını içerir.

         Aşağıdaki örnek, **TypeName** ÖZELLIĞININ değerini BDC nesne modelindeki bir tür olarak ayarlar.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. **BDC Yöntem ayrıntıları** penceresinde, tür tanımlayıcısı için görüntülenen listeyi açın ve ardından **Düzenle**' yi seçin.

     **IVB Gezgini** penceresi açılır.

4. **IVB Gezgini**' nde, tür tanımlayıcısının kısayol menüsünü açın ve **tür tanımlayıcısı Ekle**' yi seçin.

     Yeni bir tür tanımlayıcısı, varlık türü tanımlayıcısına alt öğe olarak eklenir. Bu tür tanımlayıcısını bir alan olarak yapılandırın.

5. Varlığın her alanı için bir alt tür tanımlayıcısı eklemek için 4. adımı yineleyin.

### <a name="to-define-a-collection-of-entities"></a>Bir varlık koleksiyonu tanımlamak için

1. **BDC Yöntem ayrıntıları** penceresinde istediğiniz parametrenin tür tanımlayıcısını seçin.

2. Menü çubuğunda **Görünüm**, **Özellikler penceresi**' ni seçin.

3. **Özellikler** penceresinde, **ad** özelliğini varlığı tanımlayan bir ad olarak ayarlayın (örneğin: **kişiler**).

4. **IsCollection** özelliğini **true**olarak ayarlayın. Bu, bu tür tanımlayıcısının bir varlık koleksiyonu olduğunu gösterir.

5. **TypeName** özelliğini, arabirime yönelik bir başvuru <xref:System.Collections.Generic.IEnumerable%601> ve varlığı temsil eden türün tam adını içeren bir dizeye ayarlayın. Bu tür, projenizdeki bir sınıf, çözümünüzde başvurduğunuz bir derlemede tanımlanan bir tür veya IVB nesne modelinde tanımlı bir tür olabilir.

   - Projenizdeki bir sınıf için **TypeName** özelliğinin yanındaki aşağı oku seçin, görüntülenen Iletişim kutusunda **geçerli proje** sekmesini seçin ve ardından projenizdeki sınıfı seçin.

      Tam nitelikli ad, sınıfın ad alanını ve adını ve ardından LOB sisteminin adını içerir.

      Aşağıdaki örnek, **TypeName** özelliğinin değerini projenizdeki bir sınıf koleksiyonuna ayarlar.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace. BdcModel1. Contact, BdcModel1] '

   - Çözümünüzdeki derlemede bulunan bir tür için, tam nitelikli ad, türün adını, derleme adını, sürüm numarasını, kültürü ve ortak anahtar belirtecini içerir.

      Aşağıdaki örnek, **TypeName** özelliğinin değerini çözümünüzde başvurduğunuz bir derlemede bir tür koleksiyonuna ayarlar.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace. Contact, myAssemblyName, Version = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089] '

   - IVB nesne modelinde tanımlı bir tür için, tam nitelikli ad yalnızca ad alanını ve türün adını içerir.

      Aşağıdaki örnek, **TypeName** ÖZELLIĞININ değerini BDC nesne modelinde tanımlı bir tür koleksiyonuna ayarlar.

      `System.Collections.Generic.IEnumerable`1 [Microsoft. BusinessData. Runtime. DynamicType] '

6. **BDC Yöntem ayrıntıları** penceresinde, tür tanımlayıcısı için görüntülenen listeyi açın ve ardından **Düzenle**' yi seçin.

    **IVB Gezgini** penceresi açılır.

7. **IVB Gezgini**' nde, tür tanımlayıcısının kısayol menüsünü açın ve **tür tanımlayıcısı Ekle**' yi seçin.

    Yeni bir tür tanımlayıcısı, koleksiyon türü tanımlayıcısına alt öğe olarak eklenir. Bu tür tanımlayıcısını bir varlık olarak yapılandırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
