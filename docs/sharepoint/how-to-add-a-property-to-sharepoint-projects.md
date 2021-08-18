---
title: 'nasıl yapılır: SharePoint projelerine özellik ekleme | Microsoft Docs'
description: bir SharePoint projesine özellik eklemek için bir proje uzantısı kullanın. Çözüm Gezgini içinde projeyi seçtiğinizde bir özellik Özellikler penceresi görüntülenir.
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
ms.openlocfilehash: 9daebc52f63acdf6e165ea162c90189fab534193
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149032"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>nasıl yapılır: SharePoint projelerine özellik ekleme
  herhangi bir SharePoint projesine bir özellik eklemek için bir proje uzantısı kullanabilirsiniz. Özellik, proje **Çözüm Gezgini** seçildiğinde **Özellikler** penceresinde görünür.

 Aşağıdaki adımlarda zaten bir proje uzantısı oluşturmuş olduğunuz varsayılır. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>SharePoint projesine özellik eklemek için

1. SharePoint projelerine eklemekte olduğunuz özelliği temsil eden bir public özelliği olan bir sınıf tanımlayın. Birden çok özellik eklemek istiyorsanız, tüm özellikleri aynı sınıfta veya farklı sınıflarda tanımlayabilirsiniz.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Uygulamanızın yönteminde, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> *ProjectService* parametresinin olayını işleyin.

3. Olayın olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> , Özellikler sınıfınızın bir örneğini <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> olay bağımsız değişkenleri parametresi koleksiyonuna ekleyin.

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, SharePoint projelerine nasıl iki özellik ekleneceğini gösterir. Bir özellik, projenin verilerini proje Kullanıcı seçenek dosyasında ( *. csproj. User* dosyası veya *. vbproj. User* dosyası) devam ettirir. Diğer özellik, projenin verilerini proje dosyasında (*. csproj* dosyası veya *. vbproj* dosyası) devam ettirir.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet1":::

### <a name="understand-the-code"></a>Kodu anlama
 `CustomProjectProperties`Olayın her gerçekleştiği her seferinde sınıfın aynı örneğinin kullanıldığından emin olmak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> , kod örneği, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> Bu olay ilk kez gerçekleştiğinde, Özellikler nesnesini projenin özelliğine ekler. Bu olay yeniden her gerçekleştiğinde kod bu nesneyi alır. verileri projelerle ilişkilendirmek için özelliğini kullanma hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> bkz. [SharePoint araçları uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Özellik değerlerinde değişiklikleri kalıcı hale getirmek için, özellikler için **ayarlanan** erişimciler aşağıdaki API 'leri kullanır:

- `CustomUserFileProperty` , <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> değerini proje Kullanıcı seçenek dosyasına kaydetmek için özelliğini kullanır.

- `CustomProjectFileProperty` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> değerini proje dosyasına kaydetmek için yöntemini kullanır.

  bu dosyalardaki kalıcı veriler hakkında daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Özel özelliklerin davranışını belirtin
 Özel bir özelliğin nasıl göründüğünü tanımlayabilir ve ad alanından Özellik tanımına öznitelikler uygulayarak **Özellikler** penceresinde nasıl davranacağını belirleyebilirsiniz <xref:System.ComponentModel> . Aşağıdaki öznitelikler birçok senaryoda faydalıdır:

- <xref:System.ComponentModel.DisplayNameAttribute>: **Özellikler** penceresinde görünen özelliğin adını belirtir.

- <xref:System.ComponentModel.DescriptionAttribute>: Özellik seçildiğinde **Özellikler** penceresinin alt kısmında görünen açıklama dizesini belirtir.

- <xref:System.ComponentModel.DefaultValueAttribute>: Özelliğin varsayılan değerini belirtir.

- <xref:System.ComponentModel.TypeConverterAttribute>: **Özellikler** penceresinde görüntülenen dize ile dize olmayan bir özellik değeri arasında bir özel dönüşüm belirtir.

- <xref:System.ComponentModel.EditorAttribute>: Özelliği değiştirmek için kullanılacak özel bir düzenleyici belirtir.

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint projelerini genişlet](../sharepoint/extending-sharepoint-projects.md)
- [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
