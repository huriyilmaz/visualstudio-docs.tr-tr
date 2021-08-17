---
title: 'Nasıl: Yöntem Parametrelerine Parametre | Microsoft Docs'
description: Bir iş verileri bağlantısı (BDC) yöntemine parametre eklemeyi öğrenin. Bu yöntem, yöntemine bilgi eklemenize veya yöntemden bilgi geri dönmenize olanak sağlar.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 1023044ebcd765a411aa6edfb358f5f6191ed7028d5e8559fe020e27f7d57ade
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121332345"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Nasıl: Yönteme parametre ekleme
  Yöntemine bilgi almak veya yöntemden bilgi almak için bir parametre kullanın. Tüm yöntemlerin en az bir parametresi olmalıdır. Oluşturmak istediğiniz yöntem türünü desteklemek için parametre tasarlama hakkında daha fazla bilgi için bkz. İş Verileri Bağlantı [Modeli Tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

 Bir yönteme parametre eklerken, Visual Studio projenizin model dosyasının XML'ine Parameter öğesini ekler. Parametre öğesinin öznitelikleri hakkında daha fazla bilgi için bkz. [Parametre.](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14))

### <a name="to-add-a-parameter-to-a-method"></a>Bir yönteme parametre eklemek için

1. Varlığa bir yöntem ekleyin.

2. Menü çubuğunda BDC Yöntem **Ayrıntıları'Windows**  >    >  **Diğer Öğeleri Görüntüle'yi seçin.**

     **BDC Yöntem Ayrıntıları** penceresi açılır. Daha fazla bilgi için bkz. [BDC Model Tasarım Araçlarına Genel Bakış.](../sharepoint/bdc-model-design-tools-overview.md)

3. **BDC Yöntem Ayrıntıları** penceresinde yöntemin düğümünü ve ardından Parametreler **düğümünü** genişletin.

4. Parametre **Ekle listesinde Parametre** **Oluştur'a tıklayın.**

     Parametreler düğümünün altında yeni **bir parametre** görüntülenir.

5. Menü çubuğunda Özellikler Penceresini **Görüntüle'yi**  >  **seçin.**

6. Özellikler **penceresinde** Name özelliğini **mantıklı** herhangi bir ad olarak ayarlayın. Örneğin, yöntem müşterileri iade ederse, yöntemi **GetCustomers olarak ad veebilirsiniz.**

7. **BDC Yöntem Ayrıntıları** penceresinde, parametresinin yönü için görüntülenen listeyi açın ve sonra In **,** **InOut**, **Out** veya Return 'i **seçin.**

     Oluşturmakta olduğunu tür yöntemi için hangi yönde seçecekleri hakkında daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

8. Parametrenin tür tanımlayıcısını değiştirme. Daha fazla bilgi [için, bkz. How to: Define the type descriptor of a parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Ayrıca bkz.
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl kullanılır: Modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Nasıl: Bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
