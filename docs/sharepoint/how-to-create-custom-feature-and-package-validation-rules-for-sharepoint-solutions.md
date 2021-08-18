---
title: SharePoint çözümleri için özellik ve paket doğrulamaları oluşturma
titleSuffix: ''
description: Uygulama tarafından oluşturulan çözüm paketini doğrulamak veya bir özelliğin tamamını Visual Studio için özel doğrulama kuralları oluşturun.
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
ms.openlocfilehash: a8cf9b5aa392e04865b0755fdc7dc8933c77bac1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135916"
---
# <a name="create-feature-and-package-validations-for-sharepoint-solutions"></a>SharePoint çözümleri için özellik ve paket doğrulamaları oluşturma

  Uygulama tarafından oluşturulan çözüm paketini doğrulamak için özel doğrulama kuralları Visual Studio. Bir paketin bağlam menüsünden Doğrula'ya  veya **PackagingExplorer'daki** Özellik'e seçerek özelliğin veya paketin tamamında tam doğrulama gerçekleştirebilirsiniz. Paket veya Özelliğin geçerli bir durumda SharePoint proje öğeleri veya Özellikler'i projeye eklerken kısmi doğrulama gerçekleştirilir.

### <a name="to-create-a-custom-package-validation-rule"></a>Özel paket doğrulama kuralı oluşturmak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Aşağıdaki arabirimlerden birini uygulayan bir sınıf oluşturun:

    - Paket doğrulama kuralı oluşturmak için arabirimini <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> kullanın.

    - Özellik doğrulama kuralı oluşturmak için arabirimini <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> kullanın.

4. sınıfına <xref:System.ComponentModel.Composition.ExportAttribute> ekleyin. Bu öznitelik, Visual Studio kuralınızı bulmanızı ve yüklemenizi sağlar. veya <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> türünü <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> öznitelik oluşturucuya ilet.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, özel bir Özellik doğrulama kuralının nasıl oluşturul olduğunu gösteriyor.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint.

- System.ComponentModel.Composition.

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için, [bkz. deploy extensions for the SharePoint tools in Visual Studio.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Paketleme SharePoint dağıtımı genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
