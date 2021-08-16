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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dcb73396c1c73c69c851134dac3302f9e0ffbae5bc3d7c67a4cccfa171b14e53
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409676"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>SharePoint çözümleri için özellik ve paket doğrulamaları oluşturma

  Visual Studio tarafından oluşturulan çözüm paketini doğrulamak için özel doğrulama kuralları oluşturabilirsiniz. Bir özelliğin veya paketin tamamında, **Packagingexplorer**'daki bir paketin veya özelliğin bağlam menüsünden **Doğrula** ' yı seçerek tam doğrulama yapabilirsiniz. bir paketin veya özelliğin geçerli bir durumda olup olmadığını anlamak için projeye yeni SharePoint proje öğeleri veya özellikler eklediğinizde, kısmi doğrulama gerçekleştirilir.

### <a name="to-create-a-custom-package-validation-rule"></a>Özel bir paket doğrulama kuralı oluşturmak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. Composition

3. Aşağıdaki arabirimlerden birini uygulayan bir sınıf oluşturun:

    - Bir paket doğrulama kuralı oluşturmak için <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> arabirimini uygulayın.

    - Bir özellik doğrulama kuralı oluşturmak için <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> arabirimini uygulayın.

4. <xref:System.ComponentModel.Composition.ExportAttribute>Sınıfını sınıfına ekleyin. bu öznitelik, Visual Studio doğrulama kuralınızı bulmasını ve yüklemesini sağlar. <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>Veya <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> türünü öznitelik oluşturucusuna geçirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde nasıl özel bir özellik doğrulama kuralı oluşturulacağı gösterilmektedir.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint.

- System. ComponentModel. Composition.

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [paketleme ve dağıtım SharePoint uzat](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
