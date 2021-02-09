---
title: SharePoint çözümleri için özellik ve paket doğrulamaları oluşturma
titleSuffix: ''
description: Visual Studio tarafından oluşturulan çözüm paketini doğrulamak veya bir özelliğin tamamını doğrulamak için özel doğrulama kuralları oluşturun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8c6514487ff791948787a4f9d319ff0fba9f1e02
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885696"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>SharePoint çözümleri için özellik ve paket doğrulamaları oluşturma

  Visual Studio tarafından oluşturulan çözüm paketini doğrulamak için özel doğrulama kuralları oluşturabilirsiniz. Bir özelliğin veya paketin tamamında, **Packagingexplorer**'daki bir paketin veya özelliğin bağlam menüsünden **Doğrula** ' yı seçerek tam doğrulama yapabilirsiniz. Bir paketin veya özelliğin geçerli bir durumda olup olmadığını anlamak için projeye yeni SharePoint proje öğeleri veya özellikleri eklediğinizde kısmi doğrulama gerçekleştirilir.

### <a name="to-create-a-custom-package-validation-rule"></a>Özel bir paket doğrulama kuralı oluşturmak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. Composition

3. Aşağıdaki arabirimlerden birini uygulayan bir sınıf oluşturun:

    - Bir paket doğrulama kuralı oluşturmak için <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> arabirimini uygulayın.

    - Bir özellik doğrulama kuralı oluşturmak için <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> arabirimini uygulayın.

4. <xref:System.ComponentModel.Composition.ExportAttribute>Sınıfını sınıfına ekleyin. Bu öznitelik, Visual Studio 'Nun doğrulama kuralınızı bulmasını ve yüklemesini sağlar. <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>Veya <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> türünü öznitelik oluşturucusuna geçirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde nasıl özel bir özellik doğrulama kuralı oluşturulacağı gösterilmektedir.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. Composition.

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları Için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
