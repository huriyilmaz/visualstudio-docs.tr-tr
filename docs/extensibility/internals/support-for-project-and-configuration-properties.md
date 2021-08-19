---
title: Project ve yapılandırma özellikleri için destek | Microsoft Docs
description: proje ve yapılandırma genişletilmiş özelliklerini görüntüleyebilen Visual Studio ıde 'de kendi proje türü için bir özellik sayfası sağlamayı öğrenin.
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
ms.openlocfilehash: 2e692af27d6a5a0fb07362aafa9109151a1a7bbf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158976"
---
# <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tümleşik GELIŞTIRME ortamındaki (IDE) Özellikler penceresi, proje ve yapılandırma özelliklerini görüntüleyebilir. Kullanıcının uygulamanızın özelliklerini ayarlayabilmesi için kendi proje türüne yönelik bir özellik sayfası sağlayabilirsiniz.

 **Çözüm Gezgini** ' de bir proje düğümü seçip **Project** menüsündeki **özellikler** ' e tıklayarak, proje ve yapılandırma özelliklerini içeren bir iletişim kutusu açabilirsiniz. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Ve içinde [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ve bu dillerden türetilmiş proje türlerinde, bu Iletişim kutusu [Genel, ortam, Seçenekler iletişim kutusunda](../../ide/reference/general-environment-options-dialog-box.md)sekmeli bir sayfa olarak görünür. daha fazla bilgi için bkz. [derlemede değil: izlenecek yol: Project ve yapılandırma özelliklerini gösterme (C#)](/previous-versions/bb166517(v=vs.100)).

 Projeler için yönetilen paket çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Kaynak kodunu ve derleme talimatlarını [Projeler Için MPF](https://github.com/tunnelvisionlabs/MPFProj10)' de bulabilirsiniz-Visual Studio 2013.

## <a name="persistence-of-project-and-configuration-properties"></a>Project ve yapılandırma özelliklerinin kalıcılığı
 Project ve yapılandırma özellikleri proje türüyle ilişkilendirilmiş herhangi bir dosya adı uzantısına sahip bir proje dosyasında (örneğin,. csproj,. vbproj ve. myproj) kalıcı hale getirilir. Dil projeleri genellikle proje dosyası oluşturmak için bir şablon dosyası kullanır. Ancak, proje türlerini ve şablonlarını ilişkilendirmenin bazı yolları vardır. Daha fazla bilgi için bkz [. Şablon dizin açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Project ve yapılandırma özellikleri, şablon dosyasına öğeler eklenerek oluşturulur. Bu özellikler daha sonra bu şablonu kullanan proje türü kullanılarak oluşturulan herhangi bir proje için kullanılabilir. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]projeler ve mpfproj her ikisi de şablon dosyaları için [Not for Build: MSBuild genel bakış](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) şemasını kullanır. Bu dosyalar her yapılandırma için bir PropertyGroup bölümüne sahiptir. Projelerin özellikleri genellikle boş bir dizeye ayarlanmış bir yapılandırma bağımsız değişkenine sahip olan ilk PropertyGroup bölümünde kalıcıdır.

 aşağıdaki kod, temel bir MSBuild proje dosyasının başlangıcını gösterir.

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

 Bu proje dosyasında `<Name>` ve `<SchemaVersion>` Proje özellikleridir ve `<Optimize>` bir yapılandırma özelliğidir.

 Proje dosyasının proje ve yapılandırma özelliklerinin kalıcı hale getirilmesi, projenin sorumluluğundadır.

> [!NOTE]
> Bir proje, yalnızca varsayılan değerlerinden farklı özellik değerlerini kalıcı hale getirerek kalıcılığı iyileştirebilirler.

## <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
 `Microsoft.VisualStudio.Package.SettingsPage`Sınıfı, proje ve yapılandırma özellik sayfalarını uygular. Varsayılan uygulama, `SettingsPage` genel özellik kılavuzundaki bir kullanıcıya genel özellikler sunar. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`Yöntemi, `SettingsPage` Proje özelliği kılavuzlarından türetilmiş sınıfları seçer. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`Yöntemi, `SettingsPage` yapılandırma özelliği kılavuzlarından türetilmiş sınıfları seçer. Proje türü, uygun özellik sayfalarını seçmek için bu yöntemleri geçersiz kılmalıdır.

 `SettingsPage`Sınıfı ve sınıfı, `Microsoft.VisualStudio.Package.ProjectNode` Proje ve yapılandırma özelliklerini kalıcı hale getirmek için bu yöntemleri sunar:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` ve `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` Proje özelliklerini kalıcı hale getirin.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` ve `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` yapılandırma özelliklerini kalıcı hale getirin.

  > [!NOTE]
  > ve sınıflarının uygulamaları proje `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` `Microsoft.Build.BuildEngine` dosyasından proje ve yapılandırma özelliklerini almak ve ayarlamak için (MSBuild) yöntemlerini kullanır.

  İçinden türettiğiniz sınıf proje `SettingsPage` `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` dosyasının proje veya yapılandırma özelliklerini kalıcı hale getirmek ve sürdürmek için gerekir.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute ve kayıt defteri yolu
 Sınıfından türetilmiş sınıflar `SettingsPage` , VSPackages genelinde paylaşılmak üzere tasarlanmıştır. Bir VSPackage 'dan türetilmiş bir sınıf oluşturmasını mümkün kılmak için `SettingsPage` , `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` öğesinden türetilmiş bir sınıfa öğesine ekleyin `Microsoft.VisualStudio.Shell.Package` .

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb" id="Snippet1":::

 Özniteliğin eklendiği VSPackage önemli değildir. Bir VSPackage ile kaydettirilirse [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , oluşturulabilecek herhangi bir nesnenin sınıf kimliği (CLSID), bir çağrısının oluşturulabilmesi için kaydedilir <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> .

 Oluşturulabilen bir nesnenin kayıt defteri yolu <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> ,, sözcük, CLSID ve nesne türünün GUID 'si birleştirilerek belirlenir. `MyProjectPropertyPage`Sınıfında {3c693da2-5bca-49B3-bd95-ffe0a39dd723} ve UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp bir GUID varsa, kayıt defteri yolu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\ {3c693da2-5bca-49B3-bd95-ffe0a39dd723} olur.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Project ve yapılandırma özelliği öznitelikleri ve düzeni
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute> Ve öznitelikleri, <xref:System.ComponentModel.DescriptionAttribute> bir genel özellik sayfasında proje ve yapılandırma özelliklerinin yerleşimini, etiketlenmesini ve açıklamasını tespit ediyor. Bu öznitelikler, sırasıyla bu seçeneğin kategorisini, görünen adını ve açıklamasını tespit edin.

> [!NOTE]
> Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanın ve [Projeler Için MPF 'de tanımlanmıştır-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Aşağıdaki kod parçasını göz önünde bulundurun:

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb" id="Snippet2":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs" id="Snippet2":::

 `MyConfigProp`Yapılandırma özelliği, yapılandırma özelliği sayfasında, kategorisinde, **My My** **config özelliği** olarak görünür. Seçenek **belirlenmişse açıklama panelinde** açıklama açıklaması görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)
- [Projeler](../../extensibility/internals/projects.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)