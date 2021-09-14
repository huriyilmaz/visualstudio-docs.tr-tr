---
title: Korumalı Alan ve Grup Çözümleri arasındaki farklar | Microsoft Docs
description: Korumalı alan ve grup çözümleri arasındaki farkları anlama. Her iki Visual Studio hata ayıklama yaklaşımlarının nasıl olduğunu bilirsiniz.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625274"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Korumalı alan ve grup çözümleri arasındaki farklar
  Bir çözüm derle SharePoint, SharePoint sunucusuna dağıtır ve hata ayıklamak için bir hata ayıklayıcısı iliştirer. Çözümde hata ayıklamak için kullanılan işlem Korumalı Çözüm özelliğinin ayarına bağlıdır: korumalı alanlı çözüm veya grup çözümü.

 Daha fazla bilgi için [bkz. Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

## <a name="farm-solutions"></a>Grup çözümleri
 IIS çalışan işlemi (W3WP.exe) içinde barındırılan grup çözümleri, tüm grubu etkileyebilecek kodu çalıştırın. Korumalı Çözüm özelliği "grup çözümü" olarak ayarlanmış bir SharePoint projesinde hata ayıklarken, IIS çalışan işlemi tarafından kilitlenmiş tüm dosyaları serbest bırakmak için sistemin IIS uygulama havuzu SharePoint geri çekilmeden veya dağıtmadan önce geri dönüştürülmektedir. Yalnızca projenin site URL'sini SharePoint IIS uygulama havuzu geri dönüştürülmektedir.

## <a name="sandboxed-solutions"></a>Korumalı alan çözümleri
 SharePoint kod çözümü çalışan SharePoint (SPUCWorkerProcess.exe) barındırılan korumalı alanlı çözümler, çözümün yalnızca site koleksiyonunu etkileyebilecek kodu çalıştırın. Korumalı alanlı çözümler IIS çalışan işleminde çalışmaması nedeniyle, ne IIS uygulama havuzu ne de IIS sunucusunun yeniden başlatılması gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]hata ayıklayıcıyı, spusercodeV4 hizmetinin otomatik olarak tetikleye SharePoint SPUCWorkerProcess işlemine iliştirer. SPUCWorkerProcess işleminin çözümün en son sürümünü yüklemek için geri dönüşümü gerekmez.

## <a name="either-type-of-solution"></a>Her iki çözüm türü
 Her iki çözüm türüyle [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] de istemci tarafı betik hata ayıklamasını etkinleştirmek için hata ayıklayıcıyı tarayıcıya iliştirer. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bu amaç için betik hata ayıklama altyapısını kullanır. Betik hata ayıklamayı etkinleştirmek için, istendiğinde varsayılan tarayıcı ayarlarını değiştirebilirsiniz.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , hata ayıklayıcıyı yalnızca geçerli siteyi çalıştıran W3WP veya SPUCWorkerProcess işlemlerine iliştirer. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayrıca, yönetilen COM Plus ve iş akışı hata ayıklama altyapılarını ekler.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama SharePoint çözümleri](../sharepoint/debugging-sharepoint-solutions.md)
- [Çözüm oluşturma ve SharePoint ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Korumalı alanlı çözümde dikkat edilmesi gerekenler](../sharepoint/sandboxed-solution-considerations.md)
