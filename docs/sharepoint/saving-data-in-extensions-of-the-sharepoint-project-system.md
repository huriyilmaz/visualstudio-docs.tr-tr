---
title: SharePoint proje sisteminin uzantılarında veri kaydetme | Microsoft Docs
titleSuffix: ''
description: Uzantı içeren bir SharePoint projesi kapatıldıktan sonra devam eden dize verilerini kaydetmeyi öğrenin.
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
ms.openlocfilehash: 9746877749f5364203216bc87472228739dd23c2cf2505159097833410a0e14d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409299"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>SharePoint proje sisteminin uzantılarında veri kaydetme
  SharePoint proje sistemini genişlettiğinizde, bir SharePoint projesi kapatıldıktan sonra devam eden dize verilerini kaydedebilirsiniz. Veriler genellikle belirli bir proje öğesiyle veya projenin kendisiyle ilişkilendirilir.

 Kalıcı hale getirilmesi gerekmeyen verileriniz varsa, bu verileri, arabirimi uygulayan SharePoint araçları nesne modelinde herhangi bir nesneye ekleyebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> . Daha fazla bilgi için bkz. [SharePoint Araçları uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Bir proje öğesiyle ilişkili verileri kaydetme
 Bir proje öğesine eklediğiniz bir özelliğin değeri gibi belirli bir SharePoint proje öğesiyle ilişkili verileriniz varsa, verileri proje öğesi için *. spdata* dosyasına kaydedebilirsiniz. Bunu yapmak için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> bir nesnenin özelliğini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> . Bu özelliğe eklediğiniz veriler, proje öğesi için *. spdata* dosyasındaki **ExtensionData** öğesine kaydedilir. Daha fazla bilgi için bkz. [ExtensionData öğesi](../sharepoint/extensiondata-element.md).

 Aşağıdaki kod örneği, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> özel bir SharePoint proje öğesi türünde tanımlanan bir dize özelliğinin değerini kaydetmek için özelliğinin nasıl kullanılacağını gösterir. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet14":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet14":::

## <a name="save-data-that-is-associated-with-a-project"></a>Bir projeyle ilişkili verileri kaydetme
 SharePoint projelerine eklediğiniz bir özelliğin değeri gibi proje düzeyi verileriniz varsa, verileri proje dosyasına ( *. csproj* dosyası veya *. vbproj* dosyası) veya proje Kullanıcı seçenek dosyasına ( *. csproj. User* dosyası veya *. vbproj. User* dosyası) kaydedebilirsiniz. Verileri kaydetmek için seçtiğiniz dosya, verilerin nasıl kullanılmasını istediğinize bağlıdır:

- Verilerin SharePoint projesini açan tüm geliştiriciler tarafından kullanılabilmesini istiyorsanız, verileri proje dosyasına kaydedin. Bu dosya her zaman kaynak denetim veritabanlarına iade edilir, bu nedenle bu dosyadaki veriler projeyi kullanıma alan diğer geliştiriciler tarafından kullanılabilir.

- Verilerin yalnızca SharePoint projesini Visual Studio 'da açık olan güncel geliştirici için kullanılabilir olmasını istiyorsanız, verileri proje Kullanıcı seçenek dosyasına kaydedin. Bu dosya genellikle kaynak denetimi veritabanlarına iade edilmez, bu nedenle bu dosyadaki veriler projeyi kullanıma alan diğer geliştiriciler için kullanılamaz.

### <a name="save-data-to-the-project-file"></a>Verileri proje dosyasına kaydet
 Proje dosyasına verileri kaydetmek için bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesneyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> nesnesine dönüştürün ve sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> yöntemini kullanın. Aşağıdaki kod örneğinde bir proje özelliğinin değerini proje dosyasına kaydetmek için bu yöntemin nasıl kullanılacağı gösterilmektedir. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet3":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet3":::

 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>Nesneleri Visual Studio Otomasyon nesne modeli veya Tümleştirme nesne modelindeki diğer türlere dönüştürme hakkında daha fazla bilgi için bkz. [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Verileri proje Kullanıcı seçenek dosyasına kaydet
 Proje Kullanıcı seçenek dosyasına veri kaydetmek için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> bir nesnenin özelliğini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> . Aşağıdaki kod örneğinde, proje özelliğinin değerini proje Kullanıcı seçenek dosyasına kaydetmek için bu özelliğin nasıl kullanılacağı gösterilmektedir. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [SharePoint Araç Uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
