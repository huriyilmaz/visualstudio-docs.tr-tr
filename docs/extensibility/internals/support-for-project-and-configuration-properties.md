---
title: Project ve Yapılandırma Özellikleri desteği | Microsoft Docs
description: Visual Studio IDE'de proje ve yapılandırma genişletilmiş özelliklerini görüntüleyemeyen kendi proje türünüz için bir özellik sayfası sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5d29e1d4b280454f8f5724dce207a6cf527b2c0d79b95b8ce799b88c8a7bf34e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121337792"
---
# <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
Tümleşik **geliştirme** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortamındaki (IDE) Özellikler penceresi proje ve yapılandırma özelliklerini görüntüler. Kullanıcının uygulamanıza ait özellikleri ayarlay için kendi proje türünüz için bir özellik sayfası sebilirsiniz.

 Çözüm Gezgini'de bir **proje** düğümü Project sonra  Project  tıklayarak proje ve yapılandırma özelliklerini içeren bir iletişim kutusu açabilirsiniz. ve [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] içinde ve bu dillerden türetilen proje türleri, bu iletişim kutusu Genel, Ortam, Seçenekler İletişim Kutusu'nda sekmeli [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir sayfa olarak [görünür.](../../ide/reference/general-environment-options-dialog-box.md) Daha fazla bilgi için [bkz. Derlemede Değil: Kılavuz:](/previous-versions/bb166517(v=vs.100))Project ve Yapılandırma Özelliklerini (C#) Görüntüleme.

 Projeler için Yönetilen Paket Çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Kaynak kodu ve derleme yönergelerini Projeler için [MPF - Visual Studio 2013.](https://github.com/tunnelvisionlabs/MPFProj10)

## <a name="persistence-of-project-and-configuration-properties"></a>Project Ve Yapılandırma Özelliklerinin Kalıcılığı
 Project ve yapılandırma özellikleri, proje türüyle ilişkili herhangi bir dosya adı uzantısına sahip olan bir proje dosyasında (örneğin, .csproj, .vbproj ve .myproj) kalıcıdır. Dil projeleri genellikle proje dosyasını oluşturmak için bir şablon dosyası kullanır. Ancak, proje türlerini ve şablonları ilişkilendirmek için birkaç yol vardır. Daha fazla bilgi için [bkz. Şablon Dizini Açıklaması (. Vsdir) Dosyaları.](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Project yapılandırma özellikleri şablon dosyasına öğeler ek tarafından oluşturulur. Bu özellikler daha sonra bu şablonu kullanan proje türü kullanılarak oluşturulan tüm projelerde kullanılabilir. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]projelerinin ve MPFProj'un her ikisi de şablon dosyaları için [Derlemede Değil: MSBuild Genel](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) Bakış şemasını kullanır. Bu dosyaların her yapılandırma için bir PropertyGroup bölümü vardır. Projelerin özellikleri genellikle bir Yapılandırma bağımsız değişkeni null dizeye ayarlanmış olan ilk PropertyGroup bölümünde kalıcıdır.

 Aşağıdaki kod, temel bir proje dosyasının MSBuild gösterir.

```
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Name>SomeProjectSix</Name>
    <SchemaVersion>2.0</SchemaVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
    <Optimize>false</Optimize>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <Optimize>true</Optimize>
```

 Bu proje dosyasında ve `<Name>` `<SchemaVersion>` proje özellikleridir ve bir yapılandırma `<Optimize>` özelliğidir.

 Proje dosyasının proje ve yapılandırma özelliklerini kalıcı yapmak projenin sorumluluğundadır.

> [!NOTE]
> Bir proje, yalnızca varsayılan değerlerinden farklı özellik değerlerini kalıcı hale getirmekle kalıcılığı iyi hale getirmek için kullanılır.

## <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
 sınıfı `Microsoft.VisualStudio.Package.SettingsPage` proje ve yapılandırma özellik sayfalarını kullanır. varsayılan uygulaması, `SettingsPage` genel özellik kılavuzunda bir kullanıcıya genel özellikler sunar. yöntemi, `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` proje özelliği kılavuzları için `SettingsPage` 'den türetilen sınıfları seçer. yöntemi, `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` yapılandırma özelliği kılavuzları için `SettingsPage` 'den türetilen sınıfları seçer. Uygun özellik sayfalarını seçmek için proje türünüz bu yöntemleri geçersiz kılmalı.

 sınıfı `SettingsPage` ve `Microsoft.VisualStudio.Package.ProjectNode` sınıfı, proje ve yapılandırma özelliklerini kalıcı yapmak için şu yöntemleri sağlar:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` ve `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` proje özelliklerini kalıcı olarak bulundurabilirsiniz.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` ve `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` yapılandırma özelliklerini kalıcı olarak kalıcı olarak bulundurabilirsiniz.

  > [!NOTE]
  > ve sınıflarının uygulamaları, proje dosyasından proje MSBuild özelliklerini almak ve ayarlamak için `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` `Microsoft.Build.BuildEngine` (MSBuild) yöntemlerini kullanır.

  Türetilen sınıf, `SettingsPage` proje dosyasının proje veya yapılandırma özelliklerini kalıcı yapmak için ve `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` uygulamalı.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute ve Kayıt Defteri Yolu
 'den `SettingsPage` türetilen sınıflar VSPackage'lar arasında paylaşılacak şekilde tasarlanmıştır. VSPackage'ın 'den türetilmiş bir sınıf oluşturması `SettingsPage` için, sınıfından türetilmiş `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` bir sınıfa bir `Microsoft.VisualStudio.Shell.Package` ekleyin.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb" id="Snippet1":::

 Özniteliğin ekli olduğu VSPackage önemli değildir. Bir VSPackage ile kaydedilene, oluşturulacak herhangi bir nesnenin sınıf kimliği (CLSID), çağrısının onu oluştura çalışması [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> için kaydedilir.

 Oluşturulacak bir nesnenin kayıt defteri yolu , sözcüğü, CLSID ve nesne türünün guid değeri <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> birleştirerek belirlenir. `MyProjectPropertyPage`Sınıfın guid değeri {3c693da2-5bca-49b3-bd95-ffe0a39dd723} ve UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp ise kayıt defteri yolu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723} olur.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Project ve Yapılandırma Özelliği Öznitelikleri ve Düzeni
 , ve öznitelikleri, genel bir özellik sayfasındaki proje ve yapılandırma özelliklerinin <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute> <xref:System.ComponentModel.DescriptionAttribute> düzenini, etiketlemesini ve açıklamasını belirler. Bu öznitelikler sırasıyla seçeneğin kategorisini, görünen adını ve açıklamasını belirler.

> [!NOTE]
> Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanır ve [Projeler için MPF'de](https://github.com/tunnelvisionlabs/MPFProj10)tanımlanır - Visual Studio 2013.

 Aşağıdaki kod parçasını düşünün:

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb" id="Snippet2":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs" id="Snippet2":::

 Yapılandırma `MyConfigProp` özelliği, yapılandırma özelliği sayfasında, **Kategorim kategorisinde Yapılandırma** Özelliğim olarak **görünür.** Seçenek seçiliyse açıklama panelinde **Açıklamam** olarak görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)
- [Projeler](../../extensibility/internals/projects.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)