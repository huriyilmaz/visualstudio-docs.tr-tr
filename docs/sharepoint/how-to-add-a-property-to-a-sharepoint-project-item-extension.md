---
title: 'Nasıl yapılır: bir SharePoint proje öğe uzantısına özellik ekleme | Microsoft Docs'
titleSuffix: ''
description: Visual Studio 'da zaten yüklü olan herhangi bir SharePoint proje öğesine bir özellik eklemek için bir SharePoint proje öğesi uzantısı kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2634035435679bd5ab2627f803ff9d2c1dc5a863
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215454"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Nasıl yapılır: bir SharePoint proje öğe uzantısına özellik ekleme
  Visual Studio 'da zaten yüklü olan herhangi bir SharePoint proje öğesine bir özellik eklemek için bir proje öğesi uzantısı kullanabilirsiniz. Özelliği, proje öğesi **Çözüm Gezgini** seçildiğinde **Özellikler** penceresinde görünür.

 Aşağıdaki adımlarda zaten bir proje öğesi uzantısı oluşturmuş olduğunuz varsayılır. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Proje öğesi uzantısına bir özellik eklemek için

1. Bir proje öğesi türüne eklemekte olduğunuz özelliği temsil eden bir public özelliği olan bir sınıf tanımlayın. Bir proje öğesi türüne birden çok özellik eklemek istiyorsanız, tüm özellikleri aynı sınıfta veya farklı sınıflarda tanımlayabilirsiniz.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Uygulamanızın yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *projectItemType* parametresinin olayını işleyin.

3. Olayın olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> , Özellikler sınıfınızın bir örneğini <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> olay bağımsız değişkenleri parametresi koleksiyonuna ekleyin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, olay alıcısı proje öğesine **örnek özelliği** adlı bir özelliğin nasıl ekleneceğini gösterir.

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs" id="Snippet8":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb" id="Snippet8":::

### <a name="understand-the-code"></a>Kodu anlama
 `CustomProperties`Olayın her gerçekleştiği her seferinde sınıfın aynı örneğinin kullanıldığından emin olmak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> , kod örneği, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Bu olay ilk kez gerçekleştiğinde, Properties nesnesini proje öğesinin özelliğine ekler. Bu olay yeniden her gerçekleştiğinde kod bu nesneyi alır. <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>Verileri proje öğeleriyle ilişkilendirmek için özelliğini kullanma hakkında daha fazla bilgi için bkz. [SharePoint Araçları uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Özellik değerindeki değişiklikleri kalıcı hale getirmek için, için **ayarlanan** erişimci `ExampleProperty` yeni değeri <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> özelliğin ilişkilendirildiği nesnenin özelliğine kaydeder. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>Proje öğeleriyle verileri kalıcı hale getirmek için özelliğini kullanma hakkında daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Özel özelliklerin davranışını belirtin
 Özel bir özelliğin nasıl göründüğünü tanımlayabilir ve ad alanından Özellik tanımına öznitelikler uygulayarak **Özellikler** penceresinde nasıl davranacağını belirleyebilirsiniz <xref:System.ComponentModel> . Aşağıdaki öznitelikler birçok senaryoda faydalıdır:

- <xref:System.ComponentModel.DisplayNameAttribute>: **Özellikler** penceresinde görünen özelliğin adını belirtir.

- <xref:System.ComponentModel.DescriptionAttribute>: Özellik seçildiğinde **Özellikler** penceresinin alt kısmında görünen açıklama dizesini belirtir.

- <xref:System.ComponentModel.DefaultValueAttribute>: Özelliğin varsayılan değerini belirtir.

- <xref:System.ComponentModel.TypeConverterAttribute>: **Özellikler** penceresinde görüntülenen dize ile dize olmayan bir özellik değeri arasında bir özel dönüşüm belirtir.

- <xref:System.ComponentModel.EditorAttribute>: Özelliği değiştirmek için kullanılacak özel bir düzenleyici belirtir.

## <a name="compile-the-code"></a>Kodu derle
 Bu örnekler, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Nasıl yapılır: bir SharePoint proje öğesi uzantısına kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
