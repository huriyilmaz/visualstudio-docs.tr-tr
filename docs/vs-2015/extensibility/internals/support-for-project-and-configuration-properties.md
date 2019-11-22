---
title: Proje ve yapılandırma özellikleri için destek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301069"
---
# <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tümleşik geliştirme ortamındaki (IDE) **Özellikler** penceresi, proje ve yapılandırma özelliklerini görüntüleyebilir. Kullanıcının uygulamanızın özelliklerini ayarlayabilmesi için kendi proje türüne yönelik bir özellik sayfası sağlayabilirsiniz.  
  
 **Çözüm Gezgini** ' de bir proje düğümü seçip **Proje** menüsünde **Özellikler** ' e tıklayarak, proje ve yapılandırma özelliklerini içeren bir iletişim kutusu açabilirsiniz. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ve [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]ve bu dillerden türetilmiş proje türlerinde, bu iletişim kutusu [Genel, ortam, Seçenekler Iletişim kutusunda](../../ide/reference/general-environment-options-dialog-box.md)sekmeli bir sayfa olarak görünür. Daha fazla bilgi için bkz. [derlemede değil: Izlenecek yol: proje ve yapılandırma özellikleri (C#) gösteriliyor](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Projeler için yönetilen paket çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Kaynak kodunu ve derleme talimatlarını [Projeler Için MPF](https://archive.codeplex.com/?p=mpfproj12)' de bulabilirsiniz-Visual Studio 2013.  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Proje ve yapılandırma özelliklerinin kalıcılığı  
 Proje ve yapılandırma özellikleri proje türüyle ilişkili bir dosya adı uzantısına sahip bir proje dosyasında (örneğin,. csproj,. vbproj ve. Myproj) kalıcı hale getirilir. Dil projeleri genellikle proje dosyası oluşturmak için bir şablon dosyası kullanır. Ancak, proje türlerini ve şablonlarını ilişkilendirmenin bazı yolları vardır. Daha fazla bilgi için bkz. [nib: Visual Studio şablonları](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) ve [şablon dizini açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Proje ve yapılandırma özellikleri, şablon dosyasına öğeler eklenerek oluşturulur. Bu özellikler daha sonra bu şablonu kullanan proje türü kullanılarak oluşturulan herhangi bir proje için kullanılabilir. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projeleri ve MPFProj her ikisi de şablon dosyaları için [Not ın Build: MSBuild genel bakış](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) şemasını kullanır. Bu dosyalar her yapılandırma için bir PropertyGroup bölümüne sahiptir. Projelerin özellikleri genellikle boş bir dizeye ayarlanmış bir yapılandırma bağımsız değişkenine sahip olan ilk PropertyGroup bölümünde kalıcıdır.  
  
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
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Özniteliğin eklendiği VSPackage önemli değildir. Bir VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]kaydedildiğinde, oluşturulabilecek herhangi bir nesnenin sınıf kimliği (CLSID), <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> çağrısının onu oluşturabilmesi için kaydedilir.  
  
 Oluşturulabilen bir nesnenin kayıt defteri yolu, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, sözcük, CLSID ve nesne türünün GUID 'sini birleştirerek belirlenir. `MyProjectPropertyPage` sınıfında {3c693da2-5bca-49B3-bd95-ffe0a39dd723} GUID 'si varsa ve UserRegistryRoot, HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp ise ardından kayıt defteri yolu HKEY_CURRENT_USER \Software\microsoft\visualstudio\8.0exp\clsıd\\{3c693da2-5bca-49B3-bd95-ffe0a39dd723} olur.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Proje ve yapılandırma özelliği öznitelikleri ve düzeni  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>ve <xref:System.ComponentModel.DescriptionAttribute> öznitelikleri, bir genel özellik sayfasında proje ve yapılandırma özelliklerinin yerleşimini, etiketlenmesini ve açıklamasını tespit ediyor. Bu öznitelikler, sırasıyla bu seçeneğin kategorisini, görünen adını ve açıklamasını tespit edin.  
  
> [!NOTE]
> Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanın ve [Projeler Için MPF 'de tanımlanmıştır-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Aşağıdaki kod parçasını göz önünde bulundurun:  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 `MyConfigProp` Configuration özelliği, yapılandırma özelliği sayfasında **, kategorisinde bulunan**My **config özelliği** olarak görünür. Seçenek **belirlenmişse açıklama panelinde**açıklama açıklaması görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlemede değil: İzlenecek yol: proje ve yapılandırma özelliklerini (C#) gösterme](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Özellik sayfaları ekleme ve kaldırma](../../extensibility/adding-and-removing-property-pages.md)   
 [VSPackage durumu](../../misc/vspackage-state.md)   
 [Projeler](../../extensibility/internals/projects.md)   
 [Nib: Visual Studio şablonları](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
