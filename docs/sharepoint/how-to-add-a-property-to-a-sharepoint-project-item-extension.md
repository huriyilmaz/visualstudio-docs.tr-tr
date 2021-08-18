---
title: 'Nasıl yapabilirsiniz: SharePoint Project Öğe Uzantısına Özellik Ekleme | Microsoft Docs'
titleSuffix: ''
description: Bir SharePoint proje öğesi uzantısını kullanarak, önceden SharePoint bir proje öğesine özellik Visual Studio.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 482e0e3a797f0906792868a022bea4f7e5aa329e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136137"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Nasıl yapabilirsiniz: Bir SharePoint proje öğesi uzantısına özellik ekleme
  Bir proje öğesi uzantısını kullanarak, önceden SharePoint bir proje öğesine özellik Visual Studio. özelliği, proje öğesi **Çözüm Gezgini.** 

 Aşağıdaki adımlarda, zaten bir proje öğesi uzantısı oluşturduğunuz varsayılacaktır. Daha fazla bilgi için, [bkz. How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Proje öğesi uzantısına özellik eklemek için

1. Bir proje öğesi türüne eklemekte olduğunu özelliği temsil eden genel özelliği ile bir sınıf tanımlayın. Bir proje öğesi türüne birden çok özellik eklemek için, tüm özellikleri aynı sınıfta veya farklı sınıflarda tanımlayabilirsiniz.

2. Uygulama <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *projectItemType* parametresinin olayını işle.

3. Olayın olay <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> işleyicisinde, olay bağımsız değişkenleri parametresinin koleksiyonuna özellikler <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> sınıfınıza bir örnek ekleyin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, Olay Alıcısı proje öğesine **Örnek Özellik adlı bir** özelliğin nasıl ekli olduğunu gösterir.

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs" id="Snippet8":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb" id="Snippet8":::

### <a name="understand-the-code"></a>Kodu anlama
 Olay her oluştuğunda sınıfın aynı örneğinin kullanıla olduğundan emin olmak için, kod örneği bu olay ilk kez oluştuğunda properties nesnesini proje öğesinin `CustomProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> özelliğine ekler. Kod, bu olay yeniden oluştuğunda bu nesneyi almaya devam eder. Verileri proje öğeleriyle ilişkilendirmek için özelliğini kullanma hakkında daha fazla bilgi için bkz. Özel verileri <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [SharePoint araçları uzantılarıyla ilişkilendirme.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

 Özellik değerindeki değişiklikleri kalıcı  yapmak için, için küme erişimcisi, yeni değeri özelliğin `ExampleProperty` ilişkili olduğu nesnenin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> özelliğine kaydeder. Proje öğeleriyle verileri kalıcı hale almak için özelliğini kullanma hakkında daha fazla bilgi için bkz. Verileri proje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> [sistemi SharePoint uzantılarına kaydetme.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

### <a name="specify-the-behavior-of-custom-properties"></a>Özel özelliklerin davranışını belirtme
 Ad alanı özniteliklerini özellik tanımına uygulayarak  Özellikler penceresinde özel bir özelliğin nasıl görüntülendiğinde ve <xref:System.ComponentModel> nasıl davranacağını tanımlayabilirsiniz. Aşağıdaki öznitelikler birçok senaryoda yararlıdır:

- <xref:System.ComponentModel.DisplayNameAttribute>: Özellikler penceresinde görünen özelliğin **adını** belirtir.

- <xref:System.ComponentModel.DescriptionAttribute>: Özellik seçildiğinde Özellikler penceresinin alt kısmında **görünen** açıklama dizesini belirtir.

- <xref:System.ComponentModel.DefaultValueAttribute>: Özelliğin varsayılan değerini belirtir.

- <xref:System.ComponentModel.TypeConverterAttribute>: Özellikler penceresinde görüntülenen dize ile dize olmayan bir özellik **değeri** arasında özel bir dönüştürme belirtir.

- <xref:System.ComponentModel.EditorAttribute>: Özelliğini değiştirmek için kullanmak üzere özel bir düzenleyici belirtir.

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnekler, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapabilirsiniz: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Nasıl yapabilirsiniz: Bir proje öğesi uzantısına SharePoint menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Proje SharePoint genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [Adım adım kılavuz: SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
