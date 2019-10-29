---
title: Iş verilerini SharePoint ile tümleştirme | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06d9e8059db8daa1c27b8c1d5fecc50940b7facb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986384"
---
# <a name="integrate-business-data-into-sharepoint"></a>İş verilerini SharePoint ile tümleştirme
  İş verilerini SharePoint ile tümleştirebilirsiniz. İş verileri [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel, SAP veya bir Web hizmeti gibi arka uç sunucu uygulamalarından gelebilir. Kullanıcılar, SharePoint 'te dış listeleri veya Iş verileri Web Bölümleri kullanarak iş verilerini görüntüleyebilir, ekleyebilir, güncelleştirebilir veya silebilir.  Kullanıcılar bu verilere Microsoft Outlook gibi bir Microsoft Office uygulamasına çevrimdışı de erişebilirler. Daha fazla bilgi için bkz. [dış verileri nerede gösterebileceğiniz](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Verileri SharePoint ile bütünleştirmek için, Iş verileri bağlantısı (BDC) hizmeti için bir model oluşturun. BDC hizmeti, iş uygulamalarındaki verilerle ilgili bilgileri depolayan SharePoint 'teki bir uygulamadır. Daha fazla bilgi için bkz. [Iş verileri bağlantısı (BDC) hizmeti](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Visual Studio 'da modeller
 Visual Studio 'daki modeller, arka uç veri kaynaklarından veri almak ve güncelleştirmek için özel kod yazmanıza olanak tanır. Ayrıca, birden çok veri kaynağından verileri toplayabilirsiniz. Örneğin, bir [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] veritabanından ve bir Web hizmetinden veri içeren müşterilerin bir listesini görüntüleyebilirsiniz.

 Ayrıca, SharePoint 'e zaten dağıtılan modelleri de içeri aktarabilirsiniz. Bir modeli içeri aktardıktan sonra, özel kod ekleyebilir veya yalnızca Visual Studio 'Yu kullanarak modeli birden çok SharePoint sunucu çiftini paketleyebilir ve dağıtabilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Visual Studio 'da model tasarlama
 Bir tasarımcı ve çeşitli araç pencereleri kullanarak bir model tasarlayabilirsiniz. Modeli tasarlarken, Visual Studio model XML 'i oluşturur. Daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

 Model varlıkları ve yöntemleri içerir.

### <a name="entities"></a>varlıklar
 Bir varlık bir alan koleksiyonunu açıklar. Örneğin, bir varlık veritabanındaki bir tabloyu temsil edebilir. Bir varlık, SharePoint 'te dış içerik türü olarak görünür. Dış içerik türleri hakkında daha fazla bilgi için bkz. [dış Içerik türleri nelerdir?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Yöntemler
 Bir yöntemi, bir dış içerik türünün tüketicilerinin bir varlık alanları üzerinde bir eylem gerçekleştirmesine olanak sağlar. Örneğin, bir Güncelleştirici yöntemi, kullanıcıların `Address` ve `BirthDate` `Customer` varlığının alanları olduğu bir müşterinin adresini ve Doğum tarihini değiştirmesine olanak sağlayabilir.

 Visual Studio, modelinizdeki her varlık için bir hizmet kodu dosyası oluşturur. Modelinize bir yöntem eklediğinizde, Visual Studio hizmet kodu dosyasında karşılık gelen bir yöntem oluşturur. Uygun görevi gerçekleştirmek için her bir yönteme kod ekleyin. Örneğin, modele bir Oluşturucu yöntemi eklerseniz, Visual Studio, hizmet kodu dosyanızda bir Oluşturucu yöntemi oluşturur. Bu yöntem, bir kullanıcı modeli temel alan bir listede **Yeni öğe** DÜĞMESINE tıkladığında BDC hizmeti tarafından çağrılır. Bu nedenle, bir veri kaynağına yeni veri ekleyen Oluşturucu yöntemine kod ekleyin. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)|Yeni bir model oluşturma veya SharePoint 'ten dışarı aktardığınız bir modeli içeri aktarma işlemini gösterir.|
|[İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio tasarım araçlarını kullanarak bir modelin öğelerinin nasıl tasarlanacağını açıklar.|
|[BCS kullanarak çözüm oluştururken SharePoint Designer ve Visual Studio ile ne zaman kullanılacağı](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|BDC için bir model oluşturmak üzere Visual Studio 'Yu kullanmayı veya SharePoint Designer 'ı kullanmayı seçmenize yardımcı olur.|
