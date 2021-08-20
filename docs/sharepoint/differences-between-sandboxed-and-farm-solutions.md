---
title: Korumalı ve Grup çözümleri arasındaki farklılıklar | Microsoft Docs
description: Korumalı ve Grup çözümleri arasındaki farkları anlayın. Visual Studio her iki çözüm türüyle hata ayıklamanın nasıl yaklaşımının nasıl yapılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7f6cc328c33f4aca45833bf5fd61977cef571c58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149279"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Korumalı ve Grup çözümleri arasındaki farklılıklar
  bir SharePoint çözümü derlerken, SharePoint sunucusuna dağıtılır ve hata ayıklayıcı, hata ayıklaması için iliştirir. Çözümde hata ayıklamak için kullanılan işlem, Korumalı çözüm özelliğinin ayarına bağlıdır: Korumalı çözüm veya Grup çözümü.

 Daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Grup çözümleri
 IIS çalışan işleminde (W3WP.exe) barındırılan Grup çözümleri, tüm grubu etkileyebilecek kodu çalıştırır. korumalı çözüm özelliği "grup çözümü" olarak ayarlanmış bir SharePoint projesinde hata ayıkladığınızda, sistem ııs uygulama havuzu, ııs çalışan işlemi tarafından kilitlenen tüm dosyaları serbest bırakmak için SharePoint veya özelliği dağıtmadan önce geri dönüştürür. yalnızca SharePoint projesinin site URL 'sini sunan ııs uygulama havuzu geri dönüştürüldü.

## <a name="sandboxed-solutions"></a>Korumalı çözümler
 SharePoint kullanıcı kodu çözümü çalışan işleminde (SPUCWorkerProcess.exe) barındırılan korumalı çözümler, yalnızca çözümün site koleksiyonunu etkileyebilecek kodu çalıştırır. Korumalı çözümler IIS çalışan işleminde çalışmadığından, ne IIS uygulama havuzu ne de IIS sunucusunun yeniden başlatılması gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SPUserCodeV4 hizmetinin SharePoint otomatik olarak tetiklediği ve denetimlerinde hata ayıklayıcıyı spucworkerprocess işlemine iliştirir. SPUCWorkerProcess işleminin çözümün en son sürümünü yüklemek için geri dönüştürülmesi gerekli değildir.

## <a name="either-type-of-solution"></a>Her iki çözüm türü
 Her iki çözüm türü ile [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] de hata ayıklayıcıyı tarayıcıya ekler ve istemci tarafı komut dosyası hata ayıklamayı etkinleştirir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Bu amaçla betik hata ayıklama altyapısını kullanır. Betik hata ayıklamasını etkinleştirmek için, istendiğinde varsayılan tarayıcı ayarlarını değiştirmeniz gerekir.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] yalnızca geçerli siteyi çalıştıran W3WP veya SPUCWorkerProcess işlemlerine hata ayıklayıcıyı iliştirir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ayrıca, yönetilen COM Plus ve Workflow hata ayıklama altyapılarını da iliştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerinde hata ayıklama](../sharepoint/debugging-sharepoint-solutions.md)
- [SharePoint çözümleri oluşturun ve hata ayıklayın](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md)
