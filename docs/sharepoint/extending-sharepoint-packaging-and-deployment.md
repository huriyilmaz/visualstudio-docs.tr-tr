---
title: paketleme ve dağıtım SharePoint genişletme | Microsoft Docs
description: paketleme ve dağıtım SharePoint genişletin. Dağıtım adımları ve yapılandırma oluşturma. Dağıtım çakışmalarını işleyin. Doğrulama kurallarını özelleştirin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625275"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>paketleme ve dağıtım SharePoint uzat
  SharePoint projeler için paketleme ve dağıtım sürecini genişletebilirsiniz.

## <a name="create-deployment-steps"></a>Dağıtım adımları oluştur
 bir SharePoint projesi dağıtırken, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] bir dizi dağıtım adımını yürütür. Visual Studio, geri çekiliyor ve çözüm ekleme gibi birçok görev için yerleşik dağıtım adımları içerir. Bununla birlikte, kendi dağıtım adımlarınızı da oluşturabilirsiniz.

 dağıtım adımının nasıl oluşturulacağını gösteren bir anlatım için bkz. [izlenecek yol: SharePoint projeler için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Dağıtım yapılandırması oluşturma
 dağıtım yapılandırması, belirli bir proje için yürütülen ancak tüm SharePoint proje öğelerini etkileyebilecek bir dağıtım adımları kümesidir. Her dağıtım yapılandırmasında, proje dağıtıldığında yürütülen bir adım kümesi ve proje geri çekildiğinde yürütülen başka bir küme bulunur. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] , iki yerleşik dağıtım yapılandırması içerir, ancak kendiniz de oluşturabilirsiniz. Bir dağıtım yapılandırması oluşturduğunuzda, oluşturduğunuz yerleşik dağıtım adımlarını ve dağıtım adımlarını dahil edebilirsiniz.

 dağıtım yapılandırması oluşturmayı gösteren bir anlatım için bkz. [izlenecek yol: SharePoint projeler için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>SharePoint bir çözüm dağıtıldığında veya geri çekildiğinde kodu çalıştırma
 SharePoint bir çözüm dağıtıldığında veya geri çekildiğinde ek görevler gerçekleştirmek için olayları işleyebilirsiniz. Visual Studio, aşağıdaki senaryolarda işleyebilmeniz için olaylar oluşturur:

- SharePoint proje öğesi için her dağıtım adımı yürütülmeden önce ve sonra. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- bir SharePoint projesi dağıtıldıktan veya sonra bir proje dağıtıldıktan veya geri çekildikten sonra. daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint projesi dağıtıldığında veya geri çekildiğinde kodu çalıştırma](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Dağıtım çakışmalarını işle
 modüller, Web bölümleri, liste örnekleri ve içerik türleri dahil bazı SharePoint proje öğesi türleri, yerleşik dağıtım çakışması çözümü sağlar. bu proje öğelerinden birini içeren bir çözüm dağıttığınızda, Visual Studio önce, bir dosyanın, dağıttığınız öğedeki bir dosya olarak aynı ada, URL 'ye veya kimliğe sahip SharePoint sitesinde zaten var olup olmadığını denetler. bir çakışma varsa, çakışmayı otomatik olarak çözümleyebilir veya çakışmayı çözmek Visual Studio mi yoksa dağıtımı iptal etmek mi istediğinizi belirlemenizi isteyebilir Visual Studio. daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Bu özelliği, dağıtım çakışmalarını denetleyen ve çözen kendi kodunuzu sunarak genişletebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım çakışmalarını işleme](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Proje dağıtıldıktan önce veya sonra komut satırı işlemlerini Çalıştır
 bir SharePoint çözümü dağıtıldığında bir komut satırı işlemi çalıştırmak istiyorsanız, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> bir nesnenin ve özelliklerini ayarlayabilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> . Visual Studio, proje dağıtıldıktan önce ve sonra bu komutları yürütür.

 Bazı durumlarda, dağıtım çakışmalarını görebilirsiniz. Çakışmaları çözümlemek için çeşitli farklı yollar vardır. daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Doğrulama kurallarını özelleştirme
 Bir çözüm paketini (. wsp) dağıtmadan önce, özelliğin veya paketin geçerli olduğunu doğrulamak için özel özellik ve paket doğrulama kuralları oluşturabilirsiniz. Örneğin, doğrulama sorunlarını çözmesine yardımcı olmak için geliştiricilere bilgi, uyarı veya hata bildirebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [izlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
