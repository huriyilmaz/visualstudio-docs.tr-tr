---
title: 'Nasıl yapılır: bir yönteme parametre ekleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6d0496d0fd6a347683d56630990e50af585520ba
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016717"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Nasıl yapılır: bir yönteme parametre ekleme
  Yöntemine bilgi iletmek veya bir yöntemden bilgi döndürmek için bir parametre kullanın. Tüm yöntemler en az bir parametreye sahip olmalıdır. Oluşturmak istediğiniz yöntem türünü desteklemek için bir parametre tasarlamak hakkında daha fazla bilgi için, bkz. [Iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

 Bir yöntemine parametre eklediğinizde, Visual Studio Parameter öğesini projenizdeki model dosyasının XML 'e ekler. Bir parametre öğesinin öznitelikleri hakkında daha fazla bilgi için bkz. [parametresi](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>Bir yönteme parametre eklemek için

1. Bir varlığa bir yöntem ekleyin.

2. Menü çubuğunda, **View**  >  **diğer Windows**  >  **bdc yöntemi ayrıntılarını**görüntüle ' yi seçin.

     **IVB yöntemi ayrıntıları** penceresi açılır. Daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

3. **BDC Yöntem ayrıntıları** penceresinde, yönteminin düğümünü genişletin ve ardından **Parametreler** düğümünü genişletin.

4. **Parametre Ekle** listesinde **parametre oluştur**' u seçin.

     **Parametreler** düğümünün altında yeni bir parametre görüntülenir.

5. Menü çubuğunda **View**  >  **Özellikler penceresini**görüntüle ' yi seçin.

6. **Özellikler** penceresinde, **ad** özelliğini anlamlı olan herhangi bir ad olarak ayarlayın. Örneğin, yöntem müşterileri döndürecektir, **GetCustomers**yöntemine ad yazabilirsiniz.

7. **BDC Yöntem ayrıntıları** penceresinde, parametrenin yönü için görüntülenen listeyi açın ve ardından **ın**, **InOut**, **Out**veya **Return**öğesini seçin.

     Oluşturmakta olduğunuz tür yöntemi için hangi yöne seçim yapabileceğiniz hakkında daha fazla bilgi için bkz. [bir iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Parametrenin tür tanımlayıcısını değiştirin. Daha fazla bilgi için bkz. [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Ayrıca bkz.
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
