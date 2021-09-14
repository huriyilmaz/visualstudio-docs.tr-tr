---
title: Proje öğesi türüne SharePoint özelliği ekleme
description: Özel bir proje öğesi türüne SharePoint özelliği ekleyin. özelliği, Özellikler penceresi öğesi seçili olduğunda Çözüm Gezgini.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: cde438dc6a43f158d119ac380a28bd276c04c7e1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625149"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Nasıl kullanılır: Özel bir proje öğesi türüne SharePoint özelliği ekleme
  Özel bir proje SharePoint türü tanımladığınız zaman, proje öğesine özellik eklersiniz. özelliği, proje öğesi **Çözüm Gezgini.** 

 Aşağıdaki adımlarda, proje öğesi türünüz için kendi SharePoint tanımlandığı varsayılacaktır. Daha fazla bilgi için [bkz. Nasıl SharePoint proje öğesi türü tanımlama.](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Proje öğesi türünün tanımına özellik eklemek için

1. Özel proje öğesi türüne eklemekte olduğunu özelliği temsil eden genel özelliği ile bir sınıf tanımlayın. Özel bir proje öğesi türüne birden çok özellik eklemek için, tüm özellikleri aynı sınıfta veya farklı sınıflarda tanımlayabilirsiniz.

2. Uygulama <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *projectItemTypeDefinition parametresinin olayını işleyerek.*

3. Olayın olay işleyicisinde, olay bağımsız değişkenleri parametresinin koleksiyonuna özel özellikler <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> sınıfınıza bir örnek ekleyin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, özel bir proje öğesi türüne **Örnek Özellik adlı bir** özelliğin nasıl ekli olduğunu gösterir.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet11":::

### <a name="understand-the-code"></a>Kodu anlama
 Olay her oluştuğunda sınıfın aynı örneğinin kullanıla olduğundan emin olmak için, kod örneği properties nesnesini bu olay ilk kez oluştuğunda proje öğesinin `CustomProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> özelliğine kaydeder. Kod, bu olay yeniden oluştuğunda bu nesneyi almaya devam eder. proje öğeleriyle veri kaydetmek için özelliğini kullanma hakkında daha fazla bilgi için bkz. Özel verileri <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [SharePoint araçları uzantılarıyla ilişkilendirme.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

 Özellik değerindeki değişiklikleri kalıcı  yapmak için, için küme erişimcisi, yeni değeri özelliğin `ExampleProperty` ilişkili olduğu nesnenin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> özelliğine kaydeder. Proje öğeleriyle verileri kalıcı hale almak için özelliğini kullanma hakkında daha fazla bilgi için bkz. Verileri proje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> [sistemi SharePoint uzantılarına kaydetme.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

### <a name="specify-the-behavior-of-custom-properties"></a>Özel özelliklerin davranışını belirtme
 Özellik tanımına ad alanı özniteliklerini uygulayarak  Özellikler penceresinde özel bir özelliğin nasıl görüntülendiğinde ve <xref:System.ComponentModel> nasıl davranacağını tanımlayabilirsiniz. Aşağıdaki öznitelikler birçok senaryoda yararlıdır:

- <xref:System.ComponentModel.DisplayNameAttribute>: Özellikler penceresinde görünen özelliğin **adını** belirtir.

- <xref:System.ComponentModel.DescriptionAttribute>: Özellik seçildiğinde Özellikler penceresinin alt kısmında **görünen** açıklama dizesini belirtir.

- <xref:System.ComponentModel.DefaultValueAttribute>: Özelliğin varsayılan değerini belirtir.

- <xref:System.ComponentModel.TypeConverterAttribute>: Özellikler penceresinde görüntülenen dize ile dize olmayan bir özellik **değeri** arasında özel bir dönüştürme belirtir.

- <xref:System.ComponentModel.EditorAttribute>: Özelliğini değiştirmek için kullanmak üzere özel bir düzenleyici belirtir.

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örnekleri, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Proje öğesini dağıtma
 Diğer geliştiricilerin proje öğenizi kullanmalarını sağlamak için bir proje şablonu veya proje öğesi şablonu oluşturun. Daha fazla bilgi için [bkz. Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

 Proje öğesini dağıtmak için derleme, şablon ve proje öğesiyle dağıtmak istediğiniz diğer dosyalar için bir uzantı [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] (VSIX) paketi oluşturun. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Nasıl yapabilirsiniz: Özel bir proje öğesi türüne SharePoint menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Özel proje SharePoint türleri tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
