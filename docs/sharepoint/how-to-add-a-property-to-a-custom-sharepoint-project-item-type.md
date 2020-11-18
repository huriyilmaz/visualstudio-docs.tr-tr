---
title: Özel SharePoint proje öğesi türüne Özellik Ekle
description: Özel bir SharePoint proje öğe türüne özellik ekleyin. Özelliği, proje öğesi Çözüm Gezgini seçildiğinde Özellikler penceresi görüntülenir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b62f41ff6b185469a61681a8845c4e96d044695
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850188"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme
  Özel bir SharePoint proje öğesi türü tanımladığınızda, proje öğesine bir özellik ekleyebilirsiniz. Özelliği, proje öğesi **Çözüm Gezgini** seçildiğinde **Özellikler** penceresinde görünür.

 Aşağıdaki adımlarda, kendi SharePoint proje öğesi türünü zaten tanımlamış olduğunuz varsayılır. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Proje öğesi türünün tanımına bir özellik eklemek için

1. Özel proje öğesi türüne eklemekte olduğunuz özelliği temsil eden bir public özelliği olan bir sınıf tanımlayın. Özel bir proje öğesi türüne birden çok özellik eklemek istiyorsanız, tüm özellikleri aynı sınıfta veya farklı sınıflarda tanımlayabilirsiniz.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Uygulamanızın yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *projectItemTypeDefinition* parametresinin olayını işleyin.

3. Olaya ilişkin olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> , özel özellikler sınıfınızın bir örneğini <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> olay bağımsız değişkenleri parametresi koleksiyonuna ekleyin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, özel bir proje öğesi türüne **örnek özelliği** adlı bir özelliğin nasıl ekleneceğini gösterir.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Kodu anlama
 `CustomProperties`Olayın her gerçekleştiği her seferinde sınıfın aynı örneğinin kullanıldığından emin olmak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> , kod örneği, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Bu olay ilk kez gerçekleştiğinde, Properties nesnesini proje öğesinin özelliğine kaydeder. Bu olay yeniden her gerçekleştiğinde kod bu nesneyi alır. <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>Proje öğeleriyle verileri kaydetmek için özelliğini kullanma hakkında daha fazla bilgi için bkz. [SharePoint Araçları uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Özellik değerindeki değişiklikleri kalıcı hale getirmek için, için **ayarlanan** erişimci `ExampleProperty` yeni değeri <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> özelliğin ilişkilendirildiği nesnenin özelliğine kaydeder. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>Proje öğeleriyle verileri kalıcı hale getirmek için özelliğini kullanma hakkında daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Özel özelliklerin davranışını belirtin
 Özel bir özelliğin nasıl göründüğünü tanımlayabilir ve ad alanından Özellik tanımına öznitelikler uygulayarak **Özellikler** penceresinde nasıl davranacağını belirleyebilirsiniz <xref:System.ComponentModel> . Aşağıdaki öznitelikler birçok senaryoda faydalıdır:

- <xref:System.ComponentModel.DisplayNameAttribute>: **Özellikler** penceresinde görünen özelliğin adını belirtir.

- <xref:System.ComponentModel.DescriptionAttribute>: Özellik seçildiğinde **Özellikler** penceresinin alt kısmında görünen açıklama dizesini belirtir.

- <xref:System.ComponentModel.DefaultValueAttribute>: Özelliğin varsayılan değerini belirtir.

- <xref:System.ComponentModel.TypeConverterAttribute>: **Özellikler** penceresinde görüntülenen dize ile dize olmayan bir özellik değeri arasında bir özel dönüşüm belirtir.

- <xref:System.ComponentModel.EditorAttribute>: Özelliği değiştirmek için kullanılacak özel bir düzenleyici belirtir.

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örnekleri, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-project-item"></a>Proje öğesini dağıtma
 Diğer geliştiricilerin Proje öğesini kullanmasını sağlamak için bir proje şablonu veya proje öğesi şablonu oluşturun. Daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Proje öğesini dağıtmak için [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme, şablon ve proje öğesiyle dağıtmak istediğiniz diğer dosyalar için bir uzantı (VSIX) paketi oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Nasıl yapılır: özel bir SharePoint proje öğe türüne kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
