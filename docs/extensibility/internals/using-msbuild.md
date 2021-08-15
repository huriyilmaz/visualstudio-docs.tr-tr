---
title: MSBuild | Microsoft Docs
description: MSBuild, proje dosyaları oluşturmak için, oluşturulması gereken proje öğelerini, derleme görevlerini ve derleme yapılandırmalarını tam olarak açıklayan genişletilebilir bir XML biçimi sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 47a6d8298b8ddcbeb3878f81beee8f00881be74c84c097b68e6a2563fd810546
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375721"
---
# <a name="using-msbuild"></a>MSBuild Kullanma
MSBuild, derleme görevleri ve derleme yapılandırmaları için proje öğelerini tam olarak açıklayan proje dosyaları oluşturmak için iyi tanımlanmış, genişletilebilir bir XML biçimi sağlar.

## <a name="general-msbuild-considerations"></a>Genel MSBuild Önemli Noktalar
 MSBuild [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj ve .vbproj dosyaları gibi proje dosyaları, derleme zamanında kullanılan verileri içerir, ancak tasarım zamanında kullanılan [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] verileri de içerebilir. Derleme zamanı verileri, Item Öğesi [(MSBuild MSBuild)](../../msbuild/property-element-msbuild.md)ve Özellik Öğesi [(MSBuild)](../../msbuild/item-element-msbuild.md) dahil olmak üzere temel öğeler kullanılarak depolanır. Proje türüne ve ilgili tüm proje alt türlerine özgü tasarım zamanı verileri, bu veriler için ayrılmış serbest biçimli XML'de depolanır.

 MSBuild, yapılandırma nesneleri için yerel desteğine sahip değildir, ancak yapılandırmaya özgü verileri belirtmek için koşullu öznitelikler sağlar. Örnek:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Koşullu öznitelikler hakkında daha fazla bilgi için [bkz. Koşullu Yapılar.](../../msbuild/msbuild-conditional-constructs.md)

### <a name="extending-msbuild-for-your-project-type"></a>MSBuild Türünüz için Project Genişletme
 MSBuild arabirimleri ve API'ler gelecek sürümlerinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] değişebilir. Bu nedenle, değişikliklere karşı koruma sağlarlar çünkü yönetilen paket çerçevesi (MPF) sınıflarını kullanmak ihtiyatlı bir iştir.

 Projeler için Yönetilen Paket Çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Kaynak kodu ve derleme yönergelerini Projeler için [MPF - Visual Studio 2013.](https://github.com/tunnelvisionlabs/MPFProj10)

 Projeye özgü MPF sınıfları aşağıdaki gibidir:

|Sınıf|Uygulama|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`sınıfı, öğeleri MSBuild.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Tek Dosya Oluşturucular ve MSBuild Görevleri
 Tek dosya oluşturuculara yalnızca tasarım zamanında erişilebilir, ancak MSBuild görevleri tasarım zamanında ve derleme zamanında kullanılabilir. Bu nedenle, maksimum esneklik için kod MSBuild ve oluşturmak üzere görevleri kullanın. Daha fazla bilgi için bkz. [Özel Araçlar](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild Başvuru](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Özel Araçlar](../../extensibility/internals/custom-tools.md)
