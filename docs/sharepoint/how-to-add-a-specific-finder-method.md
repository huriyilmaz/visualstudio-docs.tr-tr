---
title: 'Nasıl yapılır: belirli bir bulucu yöntemi ekleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 403213b6dcd87251df0b24333c759c8de8720afd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014820"
---
# <a name="how-to-add-a-specific-finder-method"></a>Nasıl yapılır: belirli bir bulucu yöntemi ekleme
  *Belirli bir bulucu* yöntemi oluşturarak tek bir varlık örneği döndürebilirsiniz. Iş verileri bağlantısı (BDC) hizmeti, bir kullanıcı iş verileri Web bölümünde veya dış listede bir varlık seçtiğinde belirli Bulucu yöntemini yürütür. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Belirli bir bulucu yöntemi oluşturmak için

1. **IVB tasarımcısında**bir varlık seçin.

    Visual Studio 'da **BDC tasarımcısına** bir varlık ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Menü çubuğunda, **View**  >  **diğer Windows**ve **BDC Yöntem ayrıntılarını**görüntüle ' yi seçin.

    **IVB yöntemi ayrıntıları** penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

3. **Yöntem Ekle** listesinde, **belirli bulucu yöntemi oluştur**' u seçin.

    Visual Studio, modele aşağıdaki öğeleri ekler. Bu öğeler **BDC Yöntem ayrıntıları** penceresinde görüntülenir.

   - Bir yöntemi.

   - Yöntemi için bir giriş parametresi.

   - Yöntemi için bir dönüş parametresi.

   - Her parametre için bir tür tanımlayıcısı.

   - Yöntemi için bir yöntem örneği.

     Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Visual Studio **Özellikler** penceresini açın.

5. Dönüş parametresinin tür tanımlayıcısını bir varlık türü tanımlayıcısı olarak yapılandırın. Bir varlık türü tanımlayıcısı oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Varlığa bir bulucu yöntemi eklediyseniz bu adımı gerçekleştirmeniz gerekmez. Visual Studio, Finder yönteminde tanımladığınız tür tanımlayıcısını kullanır.

   > [!NOTE]
   > Varlık türünün tanımlayıcı alanı, otomatik olarak oluşturulan bir veritabanı tablosundaki bir alanı temsil ediyorsa, tanımlayıcı alanının **salt okunurdur** özelliğini **true**olarak ayarlayın.

6. **Yöntem ayrıntıları** penceresinde, yönteminin Yöntem örneğini seçin.

7. **Özellikler penceresinde**, **dönüş parametresi adı** özelliğini yöntemin dönüş parametresinin adı olarak ayarlayın. Yöntem örneği özellikleri hakkında daha fazla bilgi için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. **Çözüm Gezgini**' de, varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

    Varlık hizmeti kod dosyası kod düzenleyicisinde açılır. Varlık hizmeti kod dosyası hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Belirli Bulucu yöntemine kod ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Bir veri kaynağından bir kayıt alır.

   - BDC hizmetine bir varlık döndürür.

     Aşağıdaki örnek, SQL Server için AdventureWorks örnek veritabanından bir kişi döndürür.

     > [!NOTE]
     > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
