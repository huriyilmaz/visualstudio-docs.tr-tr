---
title: SharePoint paketleme ve dağıtımını genişletme | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bb98e2b1c83ff06570a77dc84ce6a7bf690f81d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967474"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>SharePoint paketleme ve dağıtımını genişletme
  SharePoint projeleri için paketleme ve dağıtım sürecini genişletebilirsiniz.

## <a name="create-deployment-steps"></a>Dağıtım adımları oluştur
 Bir SharePoint projesi dağıtırken, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] bir dizi dağıtım adımını yürütür. Visual Studio, geri çekiliyor ve çözüm ekleme gibi birçok görev için yerleşik dağıtım adımları içerir. Bununla birlikte, kendi dağıtım adımlarınızı da oluşturabilirsiniz.

 Dağıtım adımının nasıl oluşturulacağını gösteren bir anlatım için bkz. [Izlenecek yol: SharePoint projeleri için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Dağıtım yapılandırması oluşturma
 Dağıtım yapılandırması, belirli bir proje için yürütülen ancak tüm SharePoint proje öğelerini etkileyebilecek bir dağıtım adımları kümesidir. Her dağıtım yapılandırmasında, proje dağıtıldığında yürütülen bir adım kümesi ve proje geri çekildiğinde yürütülen başka bir küme bulunur. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] , iki yerleşik dağıtım yapılandırması içerir, ancak kendiniz de oluşturabilirsiniz. Bir dağıtım yapılandırması oluşturduğunuzda, oluşturduğunuz yerleşik dağıtım adımlarını ve dağıtım adımlarını dahil edebilirsiniz.

 Dağıtım yapılandırması oluşturmayı gösteren bir anlatım için bkz. [Izlenecek yol: SharePoint projeleri için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Bir SharePoint çözümü dağıtıldığında veya geri çekildiğinde kodu çalıştırma
 Bir SharePoint çözümü dağıtıldığında veya geri çekildiğinde ek görevleri gerçekleştirmek için olayları işleyebilirsiniz. Visual Studio, aşağıdaki senaryolarda işleyebilmeniz için olaylar oluşturur:

- Her dağıtım adımı bir SharePoint proje öğesi için yürütülmeden önce ve sonra. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Bir SharePoint projesi dağıtıldıktan veya geri çekildikten önce ve sonra. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint projesi dağıtıldığında veya geri çekildiğinde kodu çalıştırma](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Dağıtım çakışmalarını işle
 Modüller, Web bölümleri, liste örnekleri ve içerik türleri de dahil olmak üzere bazı SharePoint proje öğesi türleri, yerleşik dağıtım çakışması çözümü sağlar. Bu proje öğelerinden birini içeren bir çözüm dağıttığınızda, Visual Studio ilk olarak SharePoint sitesinde dağıttığınız öğedeki bir dosya olarak aynı ada, URL 'ye veya KIMLIĞE sahip bir dosyanın var olup olmadığını denetler. Bir çakışma varsa, Visual Studio çakışmayı otomatik olarak çözümleyebilir veya Visual Studio 'Nun çakışmayı çözmesi veya dağıtımı iptal etmek isteyip istemediğinizi belirlemenizi isteyebilir. Daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Bu özelliği, dağıtım çakışmalarını denetleyen ve çözen kendi kodunuzu sunarak genişletebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım çakışmalarını işleme](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Proje dağıtıldıktan önce veya sonra komut satırı işlemlerini Çalıştır
 Bir SharePoint çözümü dağıtıldığında bir komut satırı işlemi çalıştırmak istiyorsanız, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> bir nesnenin ve özelliklerini ayarlayabilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> . Visual Studio, proje dağıtıldıktan önce ve sonra bu komutları yürütür.

 Bazı durumlarda, dağıtım çakışmalarını görebilirsiniz. Çakışmaları çözümlemek için çeşitli farklı yollar vardır. Daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtım sorunlarını giderme](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Doğrulama kurallarını özelleştirme
 Bir çözüm paketini (. wsp) dağıtmadan önce, özelliğin veya paketin geçerli olduğunu doğrulamak için özel özellik ve paket doğrulama kuralları oluşturabilirsiniz. Örneğin, doğrulama sorunlarını çözmesine yardımcı olmak için geliştiricilere bilgi, uyarı veya hata bildirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [İzlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
