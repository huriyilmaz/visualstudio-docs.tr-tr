---
title: Proje ve yapılandırma özellikleri için destek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf0581eee4fade779d89143f4633f1b87d3ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723155"
---
# <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamındaki (IDE) **Özellikler** penceresi, proje ve yapılandırma özelliklerini görüntüleyebilir. Kullanıcının uygulamanızın özelliklerini ayarlayabilmesi için kendi proje türüne yönelik bir özellik sayfası sağlayabilirsiniz.

 **Çözüm Gezgini** ' de bir proje düğümü seçip **Proje** menüsünde **Özellikler** ' e tıklayarak, proje ve yapılandırma özelliklerini içeren bir iletişim kutusu açabilirsiniz. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]ve bu dillerden türetilmiş proje türlerinde, bu iletişim kutusu [Genel, ortam, Seçenekler Iletişim kutusunda](../../ide/reference/general-environment-options-dialog-box.md)sekmeli bir sayfa olarak görünür. Daha fazla bilgi için bkz. [derlemede değil: Izlenecek yol: proje ve yapılandırma özellikleri (C#) gösteriliyor](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Projeler için yönetilen paket çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Kaynak kodunu ve derleme talimatlarını [Projeler Için MPF](https://github.com/tunnelvisionlabs/MPFProj10)' de bulabilirsiniz-Visual Studio 2013.

## <a name="persistence-of-project-and-configuration-properties"></a>Proje ve yapılandırma özelliklerinin kalıcılığı
 Proje ve yapılandırma özellikleri proje türüyle ilişkilendirilmiş herhangi bir dosya adı uzantısına sahip bir proje dosyasında (örneğin,. csproj,. vbproj ve. Myproj) kalıcı hale getirilir. Dil projeleri genellikle proje dosyası oluşturmak için bir şablon dosyası kullanır. Ancak, proje türlerini ve şablonlarını ilişkilendirmenin bazı yolları vardır. Daha fazla bilgi için bkz [. Şablon dizin açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Proje ve yapılandırma özellikleri, şablon dosyasına öğeler eklenerek oluşturulur. Bu özellikler daha sonra bu şablonu kullanan proje türü kullanılarak oluşturulan herhangi bir proje için kullanılabilir. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projeleri ve MPFProj her ikisi de şablon dosyaları için [Not ın Build: MSBuild genel bakış](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) şemasını kullanır. Bu dosyalar her yapılandırma için bir PropertyGroup bölümüne sahiptir. Projelerin özellikleri genellikle boş bir dizeye ayarlanmış bir yapılandırma bağımsız değişkenine sahip olan ilk PropertyGroup bölümünde kalıcıdır.

 Aşağıdaki kod, temel bir MSBuild proje dosyasının başlangıcını gösterir.

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

 Bu proje dosyasında, `<Name>` ve `<SchemaVersion>` proje özellikleridir ve `<Optimize>` bir yapılandırma özelliğidir.

 Proje dosyasının proje ve yapılandırma özelliklerinin kalıcı hale getirilmesi, projenin sorumluluğundadır.

> [!NOTE]
> Bir proje, yalnızca varsayılan değerlerinden farklı özellik değerlerini kalıcı hale getirerek kalıcılığı iyileştirebilirler.

## <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
 `Microsoft.VisualStudio.Package.SettingsPage` sınıfı, proje ve yapılandırma özellik sayfalarını uygular. `SettingsPage` varsayılan uygulanması, genel özellik kılavuzundaki bir kullanıcıya genel özellikler sunar. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` yöntemi, proje özelliği kılavuzları için `SettingsPage` türetilmiş sınıfları seçer. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` yöntemi, yapılandırma özelliği kılavuzları için `SettingsPage` türetilmiş sınıfları seçer. Proje türü, uygun özellik sayfalarını seçmek için bu yöntemleri geçersiz kılmalıdır.

 `SettingsPage` sınıfı ve `Microsoft.VisualStudio.Package.ProjectNode` sınıfı, proje ve yapılandırma özelliklerini kalıcı hale getirmek için bu yöntemleri sunar:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` ve kalıcı proje özellikleri `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`.

- yapılandırma özelliklerini `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` ve `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` kalıcı hale getirin.

  > [!NOTE]
  > `Microsoft.VisualStudio.Package.SettingsPage` ve `Microsoft.VisualStudio.Package.ProjectNode` sınıflarının uygulamaları proje dosyasından proje ve yapılandırma özelliklerini almak ve ayarlamak için `Microsoft.Build.BuildEngine` (MSBuild) yöntemlerini kullanır.

  `SettingsPage` türettiğiniz sınıf proje dosyasının proje veya yapılandırma özelliklerinin kalıcı hale getirilmesi için `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` ve `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` uygulamalıdır.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute ve kayıt defteri yolu
 `SettingsPage` türetilen sınıflar VSPackages genelinde paylaşılmak üzere tasarlanmıştır. Bir VSPackage 'ın `SettingsPage`türetilen bir sınıf oluşturmasını mümkün kılmak için, `Microsoft.VisualStudio.Shell.Package`türetilen bir sınıfa `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` ekleyin.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Özniteliğin eklendiği VSPackage önemli değildir. Bir VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kaydedildiğinde, oluşturulabilecek herhangi bir nesnenin sınıf kimliği (CLSID), <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> çağrısının onu oluşturabilmesi için kaydedilir.

 Oluşturulabilen bir nesnenin kayıt defteri yolu, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, sözcük, CLSID ve nesne türünün GUID 'sini birleştirerek belirlenir. `MyProjectPropertyPage` sınıfı {3c693da2-5bca-49B3-bd95-ffe0a39dd723} ve UserRegistryRoot değeri HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp ise, kayıt defteri yolu HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\ olur 8.0 exp \ CLSID\\{3c693da2-5bca-49B3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Proje ve yapılandırma özelliği öznitelikleri ve düzeni
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>ve <xref:System.ComponentModel.DescriptionAttribute> öznitelikleri, bir genel özellik sayfasında proje ve yapılandırma özelliklerinin yerleşimini, etiketlenmesini ve açıklamasını tespit ediyor. Bu öznitelikler, sırasıyla bu seçeneğin kategorisini, görünen adını ve açıklamasını tespit edin.

> [!NOTE]
> Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanın ve [Projeler Için MPF 'de tanımlanmıştır-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Aşağıdaki kod parçasını göz önünde bulundurun:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 `MyConfigProp` Configuration özelliği, yapılandırma özelliği sayfasında **, kategorisinde bulunan**My **config özelliği** olarak görünür. Seçenek **belirlenmişse açıklama panelinde**açıklama açıklaması görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)
- [Projeler](../../extensibility/internals/projects.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
