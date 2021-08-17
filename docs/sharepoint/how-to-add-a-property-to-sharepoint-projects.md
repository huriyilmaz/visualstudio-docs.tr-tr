---
title: 'Nasıl SharePoint: SharePoint Projelerine Özellik | Microsoft Docs'
description: Bir proje uzantısını kullanarak bir SharePoint ekleyin. Proje, Özellikler penceresi projesini seçerek Çözüm Gezgini.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c6b7e0d5a361321f1173688c8501a97d14b7e326119c4854c0fcd4310f1ac5ea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425346"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Nasıl yapılanlar: SharePoint projelerine özellik ekleme
  Herhangi bir proje için bir özellik eklemek üzere proje uzantısını SharePoint kullanabilirsiniz. özelliği, proje **Çözüm Gezgini.** 

 Aşağıdaki adımlarda, zaten bir proje uzantısı oluşturduğunuz varsayılacaktır. Daha fazla bilgi için, [bkz. How to: Create a SharePoint project extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Bir SharePoint projesine özellik eklemek için

1. Uygulama projelerine eklemekte olduğunu özelliği temsil eden genel bir özelliği SharePoint tanımlayın. Birden çok özellik eklemek için aynı sınıfta veya farklı sınıflarda tüm özellikleri tanımlayabilirsiniz.

2. Uygulama <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> projectService parametresinin *olaylarını işle.*

3. Olayın olay <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> işleyicisinde, olay bağımsız değişkenleri parametresinin koleksiyonuna özellikler <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> sınıfınıza bir örnek ekleyin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, projelerine iki özelliğin nasıl SharePoint gösterir. Bir özellik, verilerini proje kullanıcı seçeneği dosyasında *(.csproj.user* dosyası veya *.vbproj.user dosyası) kalıcı* olarak bulundurmaktadır. Diğer özellik, verilerini proje dosyasında *(.csproj* dosyası veya *.vbproj dosyası) kalıcı* olarak bulundurmaktadır.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet1":::

### <a name="understand-the-code"></a>Kodu anlama
 Olay her oluştuğunda sınıfın aynı örneğinin kullanılır olduğundan emin olmak için, kod örneği bu olay ilk kez ortaya çıkarken properties nesnesini projenin `CustomProjectProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> özelliğine ekler. Kod, bu olay yeniden oluştuğunda bu nesneyi almaya devam eder. Verileri projelerle ilişkilendirmek için özelliğini kullanma hakkında daha fazla bilgi için bkz. Özel <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> verileri SharePoint araçları [uzantılarıyla ilişkilendirme.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

 Özellik değerlerde yapılan değişiklikleri kalıcı yapmak için **özelliklere** ait küme erişimcileri aşağıdaki API'leri kullanır:

- `CustomUserFileProperty` değerini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proje kullanıcı seçeneği dosyasına kaydetmek için özelliğini kullanır.

- `CustomProjectFileProperty` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> değerini proje dosyasına kaydetmek için yöntemini kullanır.

  Bu dosyalarda verileri kalıcı hale toplama hakkında daha fazla bilgi için bkz. Verileri proje [sisteminin SharePoint kaydetme.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

### <a name="specify-the-behavior-of-custom-properties"></a>Özel özelliklerin davranışını belirtme
 Ad alanı özniteliklerini özellik tanımına uygulayarak  Özellikler penceresinde özel bir özelliğin nasıl görüntülendiğinde ve <xref:System.ComponentModel> nasıl davranacağını tanımlayabilirsiniz. Aşağıdaki öznitelikler birçok senaryoda yararlıdır:

- <xref:System.ComponentModel.DisplayNameAttribute>: Özellikler penceresinde görünen özelliğin **adını** belirtir.

- <xref:System.ComponentModel.DescriptionAttribute>: Özellik seçildiğinde Özellikler penceresinin alt kısmında **görünen** açıklama dizesini belirtir.

- <xref:System.ComponentModel.DefaultValueAttribute>: Özelliğin varsayılan değerini belirtir.

- <xref:System.ComponentModel.TypeConverterAttribute>: Özellikler penceresinde görüntülenen dize ile dize olmayan bir özellik **değeri** arasında özel bir dönüştürme belirtir.

- <xref:System.ComponentModel.EditorAttribute>: Özelliğini değiştirmek için kullanmak üzere özel bir düzenleyici belirtir.

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- Microsoft.VisualStudio.Shell

- Microsoft.VisualStudio.Shell.Interop

- Microsoft.VisualStudio.Shell.Interop.8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint genişletme](../sharepoint/extending-sharepoint-projects.md)
- [Nasıl yapabilirsiniz: SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Nasıl yapabilirsiniz: Projelerinize kısayol menü SharePoint ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Proje SharePoint genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
