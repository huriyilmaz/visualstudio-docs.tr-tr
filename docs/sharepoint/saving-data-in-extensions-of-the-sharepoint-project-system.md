---
title: SharePoint Project System | Uzantılarına Veri Kaydetme Microsoft Docs
titleSuffix: ''
description: Uzantı içeren bir SharePoint projesi kapatılamadıktan sonra devam eden dize verilerini kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 671571551483c4eff71c1324e1c53c7cbb43ff9c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635553"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Verileri proje sisteminin uzantılarına SharePoint kaydetme
  Bir proje sistemini SharePoint, bir proje kapatılana kadar devam eden dize SharePoint kaydedebilirsiniz. Veriler genellikle belirli bir proje öğesiyle veya projenin kendisiyle ilişkilendirilr.

 Kalıcı olarak kalıcı olarak gerekli olan verileriniz varsa, arabirimi uygulayan SharePoint araçları nesne modelinde herhangi bir nesneye veri <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> ebilirsiniz. Daha fazla bilgi için [bkz. Özel verileri SharePoint uzantılarıyla ilişkilendirme.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

## <a name="save-data-that-is-associated-with-a-project-item"></a>Bir proje öğesiyle ilişkili verileri kaydetme
 Belirli bir SharePoint proje öğesiyle ilişkili verileriniz (örneğin, bir proje öğesine ekley istediğiniz bir özelliğin değeri) olduğunda, verileri proje öğesi *için .spdata* dosyasına kaydedebilirsiniz. Bunu yapmak için bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> nesnenin özelliğini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> kullanın. Bu özellge ekleyemediniz veriler, proje öğesinin *.spdata* **dosyasındaki ExtensionData** öğesine kaydedilir. Daha fazla bilgi için bkz. [ExtensionData Öğesi.](../sharepoint/extensiondata-element.md)

 Aşağıdaki kod örneği, özel bir proje öğesi türünde tanımlanan bir dize özelliğinin değerini kaydetmek için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> özelliğinin SharePoint gösterir. Bu örneği daha büyük bir örnek bağlamında görmek için bkz. Nasıl kullanılır: Proje öğesi türünde özel [SharePoint özelliği ekleme.](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet14":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet14":::

## <a name="save-data-that-is-associated-with-a-project"></a>Bir projeyle ilişkili verileri kaydetme
 SharePoint projelerine ekley istediğiniz bir özelliğin değeri gibi proje düzeyinde verileriniz olduğunda, verileri proje dosyasına *(.csproj* dosyası veya *.vbproj* dosyası) veya proje kullanıcı seçeneği dosyasına *(.csproj.user* dosyası veya *.vbproj.user* dosyası) kaydedebilirsiniz. Verileri kaydetmek için seçtiğiniz dosya, verilerin nasıl kullanılmalarını istediğinize bağlıdır:

- Verilerin SharePoint projesini açan tüm geliştiriciler tarafından kullanılabilir olması için verileri proje dosyasına kaydedin. Bu dosya her zaman kaynak denetimi veritabanlarına iade edilir, bu nedenle bu dosyada yer alan veriler projeyi kullanıma alan diğer geliştiriciler tarafından kullanılabilir.

- Verilerin yalnızca SharePoint projesini Visual Studio proje kullanıcı seçeneği dosyasına kaydeden geçerli geliştirici tarafından kullanılabilir olması gerekir. Bu dosya genellikle kaynak denetimi veritabanlarına iade edilemez, bu nedenle bu dosyada yer alan veriler projeyi kullanıma alan diğer geliştiriciler tarafından kullanılamaz.

### <a name="save-data-to-the-project-file"></a>Verileri proje dosyasına kaydetme
 Verileri proje dosyasına kaydetmek için nesneyi bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesneye dönüştür ve ardından yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> kullanın. Aşağıdaki kod örneği, bir proje özelliğinin değerini proje dosyasına kaydetmek için bu yöntemin nasıl kullanılagelmektedir. Bu örneği daha büyük bir örnek bağlamında görmek için bkz. Nasıl 2012: SharePoint [ekleme.](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet3":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet3":::

 Visual Studio otomasyon nesne modelinde veya tümleştirme nesne modelinde nesneleri diğer türlere dönüştürme hakkında daha fazla bilgi için bkz. SharePoint proje sistemi türleri ve diğer Visual Studio <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> [proje türleri arasında dönüştürme.](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)

### <a name="save-data-to-the-project-user-option-file"></a>Verileri proje kullanıcı seçeneği dosyasına kaydetme
 Verileri proje kullanıcı seçeneği dosyasına kaydetmek için bir nesnenin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> özelliğini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> kullanın. Aşağıdaki kod örneği, bir proje özelliğinin değerini proje kullanıcı seçeneği dosyasına kaydetmek için bu özelliğin nasıl kullanılageldi? Bu örneği daha büyük bir örnek bağlamında görmek için bkz. Nasıl 2012: SharePoint [ekleme.](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [Proje SharePoint genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Özel verileri SharePoint araçları uzantılarıyla ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Proje sistemi SharePoint diğer proje türleri arasında Visual Studio dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
