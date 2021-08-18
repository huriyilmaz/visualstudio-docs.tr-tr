---
title: Paketleme ve SharePoint dağıtım | Microsoft Docs
description: Paketleme ve SharePoint genişletme. Dağıtım adımlarını ve yapılandırmalarını oluşturun. Dağıtım çakışmalarını işleme. Doğrulama kurallarını özelleştirme.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: bdb02592d55cc05781a77d2c88aecf3982f1c4fe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106906"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Paketleme SharePoint dağıtımı genişletme
  Projelerin paketleme ve dağıtım SharePoint genişletebilirsiniz.

## <a name="create-deployment-steps"></a>Dağıtım adımları oluşturma
 Bir SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] dağıtarak bir dizi dağıtım adımı yürütür. Visual Studio, geri çekme ve çözüm ekleme gibi birçok görev için yerleşik dağıtım adımları içerir. Ancak kendi dağıtım adımlarınızı da oluşturabilirsiniz.

 Dağıtım adımı oluşturma adımını gösteren bir izlenecek yol için bkz. Adım adım kılavuz: Proje oluşturmak için [özel SharePoint oluşturma.](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

## <a name="create-deployment-configurations"></a>Dağıtım yapılandırmaları oluşturma
 Dağıtım yapılandırması, verilen bir proje için yürütülen bir dağıtım adımları kümesidir, ancak proje öğelerinin SharePoint etkileyebilir. Her dağıtım yapılandırması, proje dağıtıldığında yürütülen bir adım kümesi ve proje geri çekıldığında yürütülen başka bir küme içerir. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] iki yerleşik dağıtım yapılandırması içerir, ancak kendi dağıtım yapılandırmanızı da oluşturabilirsiniz. Dağıtım yapılandırması yapılandırmasını oluşturmak için yerleşik dağıtım adımlarını ve dağıtım adımlarını dahil edin.

 Dağıtım yapılandırmasının nasıl oluşturulacaklarını gösteren bir izlenecek yol için bkz. Adım adım: Proje oluşturmak için [özel SharePoint oluşturma.](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Bir çözüm dağıtıldığında SharePoint geri çekiliyorsa kod çalıştırma
 Bir çözüm dağıtıldığında veya geri çekiliyorsa, SharePoint görevleri gerçekleştirmek için olayları işebilirsiniz. Visual Studio aşağıdaki senaryolarda işleyilebilecek olaylara neden olur:

- Bir proje öğesi için her dağıtım adımı yürütülmeden önce SharePoint sonra. Daha fazla bilgi için, [bkz. How to: Run code when deployment steps are executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Bir proje dağıtıldıktan SharePoint sonra veya geri çekiliyor. Daha fazla bilgi için, [bkz. How to: Run code when a SharePoint isdeployed or geri çekilebilir.](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)

## <a name="handle-deployment-conflicts"></a>Dağıtım çakışmalarını işleme
 Modüller, Web SharePoint, liste örnekleri ve içerik türleri dahil olmak üzere proje öğelerinin bazı türleri yerleşik dağıtım çakışması çözümü sağlar. Bu proje öğelerine sahip bir çözüm dağıtıyorsanız, Visual Studio önce SharePoint sitesinde dağıtıyorsanız öğede dosya olarak aynı ad, URL veya kimlik ile bir dosyanın mevcut olup olmadığını denetler. Bir çakışma varsa, Visual Studio otomatik olarak çözüme kavuşturabilirsiniz veya çakışmayı çözümlemek mi yoksa dağıtımı iptal etmek mi Visual Studio olup olmadığınızı belirlemenizi ister. Daha fazla bilgi için [bkz. Paketleme SharePoint Dağıtım sorunlarını giderme.](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)

 Dağıtım çakışmalarını kontrol alan ve çözen kendi kodunuzu sağlayarak bu özelliği genişletebilirsiniz. Daha fazla bilgi için, [bkz. How to: Handle deployment conflicts](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Proje dağıtıldıktan önce veya dağıtıldıktan sonra komut satırı işlemlerini çalıştırma
 Bir SharePoint çözümü dağıtıldığında bir komut satırı işlemi çalıştırmak için nesnenin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> özelliklerini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> ayarlayın. Visual Studio önce ve proje dağıtıldıktan sonra bu komutları yürütür.

 Bazı durumlarda dağıtım çakışmaları olabilir. Çakışmaları çözmenin birkaç farklı yolu vardır. Daha fazla bilgi için [bkz. Paketleme ve SharePoint sorunlarını giderme.](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)

## <a name="customize-validation-rules"></a>Doğrulama kurallarını özelleştirme
 Bir çözüm paketini (.wsp) dağıtmadan önce, Özellik veya paketin geçerli olduğunu doğrulamak için özel Özellik ve paket doğrulama kuralları oluşturabilirsiniz. Örneğin, doğrulama sorunlarını düzeltmelerine yardımcı olmak için geliştiricilere bilgileri, uyarıları veya hataları bildirebilirsiniz. Daha fazla bilgi için, [bkz. How to: Create custom feature and package validation rules for SharePoint .](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Dağıtım adımları yürütülürken kod çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Adım adım kılavuz: Proje oluşturmak için özel SharePoint oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Nasıl kullanılır: Özel özellik ve paket doğrulama kuralları oluşturma SharePoint oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
