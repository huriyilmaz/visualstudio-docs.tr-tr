---
title: Proje ve Yapılandırma Özellikleri Desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704896"
---
# <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
Tümleşik geliştirme [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortamındaki **Özellikler** penceresi (IDE) proje ve yapılandırma özelliklerini görüntüleyebilir. Kullanıcının uygulamanız için özellikler ayarlayabilmesi için kendi proje türünüz için bir özellik sayfası sağlayabilirsiniz.

 **Çözüm Gezgini'nde** bir proje düğümü seçip **Proje** menüsünde **Özellikler'i** tıklatarak, proje ve yapılandırma özelliklerini içeren bir iletişim kutusu açabilirsiniz. Bu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]dillerde türetilen proje türlerinde ve proje türlerinde, bu iletişim kutusu [Genel, Çevre, Seçenekler İletişim Kutusu'nda](../../ide/reference/general-environment-options-dialog-box.md)sekmeli bir sayfa olarak görünür. Daha fazla bilgi için [bkz: Yapıda Değil: Walkthrough: Project ve Configuration Properties (C#) açığa çıkarma.](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)

 Projeler için Yönetilen Paket Çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Projeler için MPF - Visual [Studio 2013'te](https://github.com/tunnelvisionlabs/MPFProj10)kaynak kodu ve derleme yönergelerini bulabilirsiniz.

## <a name="persistence-of-project-and-configuration-properties"></a>Proje ve Yapılandırma Özelliklerinin Kalıcılığı
 Proje ve yapılandırma özellikleri, proje türüyle ilişkili herhangi bir dosya adı uzantısı olan bir proje dosyasında (örneğin, .csproj, .vbproj ve .myproj) kalıcıdır. Dil projeleri genellikle proje dosyasını oluşturmak için bir şablon dosyası kullanır. Ancak, proje türlerini ve şablonları ilişkilendirmenin aslında birkaç yolu vardır. Daha fazla bilgi için [Şablon Dizin Açıklaması'na bakın (. Vsdir) Dosyalar](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Proje ve yapılandırma özellikleri şablon dosyasına öğeler eklenerek oluşturulur. Bu özellikler daha sonra bu şablonu kullanan proje türünü kullanarak oluşturulan herhangi bir proje için kullanılabilir. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]projeler ve MPFProj hem [Yapı'da Değil: ŞABLON](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) dosyaları için MSBuild Genel Bakış şema sını kullanır. Bu dosyaların her yapılandırma için bir Özellik Grubu bölümü bulunur. Projelerin özellikleri genellikle null dize ayarlanmış bir Yapılandırma bağımsız değişkeni olan ilk PropertyGroup bölümünde kalıcıdır.

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

 Bu proje `<Name>` dosyasında `<SchemaVersion>` ve proje `<Optimize>` özellikleri ve bir yapılandırma özelliğidir.

 Proje dosyasının proje ve yapılandırma özelliklerini sürdürmek projenin sorumluluğundadır.

> [!NOTE]
> Proje, yalnızca varsayılan değerlerinden farklı özellik değerlerini kalıcı olarak sağlayarak kalıcılığı en iyi duruma getirebilir.

## <a name="support-for-project-and-configuration-properties"></a>Proje ve Yapılandırma Özellikleri için Destek
 Sınıf `Microsoft.VisualStudio.Package.SettingsPage` proje ve yapılandırma özelliği sayfalarını uygular. Varsayılan uygulama, `SettingsPage` genel bir özellik tablosunda bir kullanıcıya ortak özellikler sunar. Yöntem, `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` proje özelliği `SettingsPage` ızgaraları için türetilen sınıfları seçer. Yöntem, `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` yapılandırma özellik `SettingsPage` ızgaraları için türetilen sınıfları seçer. Proje türünüz, uygun özellik sayfalarını seçmek için bu yöntemleri geçersiz kılmalıdır.

 Sınıf `SettingsPage` ve `Microsoft.VisualStudio.Package.ProjectNode` sınıf, proje ve yapılandırma özelliklerini sürdürmek için şu yöntemleri sunar:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`ve `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` proje özelliklerini devam etti.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`ve `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` yapılandırma özelliklerini devam etti.

  > [!NOTE]
  > Ve `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` sınıfların uygulamaları, proje `Microsoft.Build.BuildEngine` ve yapılandırma özelliklerini proje dosyasından almak ve ayarlamak için (MSBuild) yöntemlerini kullanır.

  Türetdiğiniz sınıfın `SettingsPage` proje `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` dosyasının proje veya yapılandırma özelliklerini uygulaması ve `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` kalıcı olarak sürmesi gerekir.

## <a name="provideobjectattribute-and-registry-path"></a>ObjectAttribute ve Kayıt Defteri Yolu sağlama
 Türetilen `SettingsPage` sınıflar VSPackages arasında paylaşılacak şekilde tasarlanmıştır. VsPackage'ın türetilen bir sınıf oluşturmasını `SettingsPage`mümkün `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` kılmak için, `Microsoft.VisualStudio.Shell.Package`türetilen bir sınıfa a ekleyin.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Özniteliğin bağlı olduğu VSPackage önemsizdir. Bir VSPackage ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kaydedildiğinde, oluşturulabilecek herhangi bir nesnenin sınıf kimliği (CLSID) <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> kaydedilir, böylece bir çağrı oluşturabilirsiniz.

 Oluşturulabilen bir nesnenin kayıt defteri yolu, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>sözcük, CLSID ve nesne türünün guid'i birleştirilerek belirlenir. `MyProjectPropertyPage` Sınıfın bir guida 'sı varsa {3c693da2-5bca-49b3-bd95-ffe0a39ddd723} ve UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, sonra kayıt HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723} olacaktır.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Proje ve Yapılandırma Özellik Öznitelikleri ve Düzeni
 , <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute> ve öznitelikler, genel bir özellik sayfasında proje ve yapılandırma özelliklerinin düzenini, etiketlemesini ve açıklamasını belirler. Bu öznitelikler, sırasıyla seçeneğin kategorisini, görüntü adını ve açıklamasını belirler.

> [!NOTE]
> Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanın ve Projeler için MPF tanımlanır [- Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Aşağıdaki kod parçasını göz önünde bulundurun:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 Yapılandırma `MyConfigProp` özelliği, yapılandırma özelliği sayfasında **Kategorim, Benim Kategorimdeki Config Özelliğim** olarak görünür. **My Category** Seçenek seçilirse, açıklama, **Açıklamam**, açıklama panelinde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellik Sayfaları Ekleme ve Kaldırma](../../extensibility/adding-and-removing-property-pages.md)
- [Projeler](../../extensibility/internals/projects.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
