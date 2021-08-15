---
title: Iş verilerini SharePoint ile tümleştirme | Microsoft Docs
description: iş verileri bağlantısı (BDC) hizmeti için bir model oluşturarak iş verilerinin SharePoint tümleştirme hakkında üst düzey bir özet okuyun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a68921a43a889b8a36204e3703c2e0003618b8139639d1cfab6ae8018ddb4eca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352879"
---
# <a name="integrate-business-data-into-sharepoint"></a>İş verilerini SharePoint ile tümleştirme
  İş verilerini SharePoint ile tümleştirebilirsiniz. İş verileri [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)] , Siebel, SAP veya bir Web hizmeti gibi arka uç sunucu uygulamalarından gelebilir. kullanıcılar SharePoint içindeki dış listeleri veya iş verileri Web Bölümleri kullanarak iş verilerini görüntüleyebilir, ekleyebilir, güncelleştirebilir veya silebilir.  kullanıcılar bu verilere Microsoft Outlook gibi bir Microsoft Office uygulamasına çevrimdışı de erişebilirler. Daha fazla bilgi için bkz. [dış verileri nerede gösterebileceğiniz](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 verileri SharePoint ile bütünleştirmek için, iş verileri bağlantısı (BDC) hizmeti için bir model oluşturun. ivb hizmeti, iş uygulamalarındaki verilerle ilgili bilgileri depolayan SharePoint bir uygulamadır. Daha fazla bilgi için bkz. [Iş verileri bağlantısı (BDC) hizmeti](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Visual Studio modeller
 Visual Studio modeller, arka uç veri kaynaklarından veri almak ve güncelleştirmek için özel kod yazmanıza olanak tanır. Ayrıca, birden çok veri kaynağından verileri toplayabilirsiniz. Örneğin, bir [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] veritabanından ve bir Web hizmetinden veri içeren müşterilerin bir listesini görüntüleyebilirsiniz.

 Ayrıca, SharePoint için zaten dağıtılan modelleri de içeri aktarabilirsiniz. bir modeli içeri aktardıktan sonra, modeli paketlemek ve birden çok SharePoint sunucu çiftliklerini dağıtmak için özel kod ekleyebilir veya yalnızca Visual Studio kullanabilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Visual Studio model tasarlama
 Bir tasarımcı ve çeşitli araç pencereleri kullanarak bir model tasarlayabilirsiniz. modeli tasarlarken, Visual Studio model XML 'sini oluşturur. Daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

 Model varlıkları ve yöntemleri içerir.

### <a name="entities"></a>Varlıklar
 Bir varlık bir alan koleksiyonunu açıklar. Örneğin, bir varlık veritabanındaki bir tabloyu temsil edebilir. Bir varlık SharePoint dış içerik türü olarak görünür. Dış içerik türleri hakkında daha fazla bilgi için bkz. [dış Içerik türleri nelerdir?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Yöntemler
 Bir yöntemi, bir dış içerik türünün tüketicilerinin bir varlık alanları üzerinde bir eylem gerçekleştirmesine olanak sağlar. Örneğin, bir Güncelleştirici yöntemi kullanıcıların, `Address` ve `BirthDate` varlık alanları olan bir müşterinin adresini ve Doğum tarihini değiştirmesine olanak sağlayabilir `Customer` .

 Visual Studio modelinizdeki her varlık için bir hizmet kodu dosyası oluşturur. modelinize bir yöntem eklediğinizde Visual Studio, hizmet kodu dosyasında karşılık gelen bir yöntem oluşturur. Uygun görevi gerçekleştirmek için her bir yönteme kod ekleyin. örneğin, modele bir oluşturucu yöntemi eklerseniz, Visual Studio hizmet kodu dosyanızda bir oluşturucu yöntemi oluşturur. Bu yöntem, bir kullanıcı modeli temel alan bir listede **Yeni öğe** DÜĞMESINE tıkladığında BDC hizmeti tarafından çağrılır. Bu nedenle, bir veri kaynağına yeni veri ekleyen Oluşturucu yöntemine kod ekleyin. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)|Yeni bir model oluşturma veya SharePoint dışarı aktardığınız bir modeli içeri aktarma işlemini gösterir.|
|[İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio tasarım araçlarını kullanarak bir modelin öğelerinin nasıl tasarlanacağını açıklar.|
|[BCS kullanarak çözüm oluştururken SharePoint tasarımcı ile Visual Studio ne zaman kullanılır](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Visual Studio kullanıp kullanmayacağınızı veya SharePoint tasarımcısını kullanarak BDC için bir model oluşturmayı belirlemenize yardımcı olur.|
