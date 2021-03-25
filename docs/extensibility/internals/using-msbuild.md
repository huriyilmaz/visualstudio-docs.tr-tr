---
title: MSBuild 'i kullanma | Microsoft Docs
description: MSBuild, oluşturulacak proje öğelerini tam olarak tanımlayan proje dosyaları oluşturmak, görevleri derlemek ve derleme yapılandırması için genişletilebilir bir XML biçimi sağlar.
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
ms.workload:
- vssdk
ms.openlocfilehash: 8891d9674a952f0272855c8b9203109ad2e22468
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090700"
---
# <a name="using-msbuild"></a>MSBuild Kullanma
MSBuild, oluşturulacak proje öğelerini tam olarak tanımlayan proje dosyaları oluşturmak, görevleri derlemek ve derleme yapılandırması için iyi tanımlanmış, genişletilebilir XML biçimi sağlar.

## <a name="general-msbuild-considerations"></a>Genel MSBuild konuları
 MSBuild proje dosyaları, örneğin [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . csproj ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . vbproj dosyaları, derleme zamanında kullanılan verileri içerir, ancak tasarım zamanında kullanılan verileri de içerebilir. Derleme zamanı verileri, [öğe öğesi (MSBuild)](../../msbuild/item-element-msbuild.md) ve [özellik öğesi (MSBuild)](../../msbuild/property-element-msbuild.md)dahil olmak üzere MSBuild temel öğeleri kullanılarak depolanır. Proje türüne ve ilgili proje alt türlerine özgü veriler olan tasarım zamanı verileri, için ayrılmış serbest biçimli XML 'de depolanır.

 MSBuild, yapılandırma nesneleri için yerel destek içermez, ancak yapılandırmaya özgü verileri belirtmek için koşullu öznitelikler sağlar. Örnek:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Koşullu öznitelikler hakkında daha fazla bilgi için bkz. [koşullu yapılar](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Proje türü için MSBuild 'i genişletme
 MSBuild arabirimleri ve API 'Ler, gelecekteki sürümlerinde değişebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu nedenle, değişikliklerden koruma sağladığından yönetilen paket çerçevesi (mpf) sınıflarının kullanılması akıllıca olur.

 Projeler için yönetilen paket çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Kaynak kodunu ve derleme talimatlarını [Projeler Için MPF](https://github.com/tunnelvisionlabs/MPFProj10)' de bulabilirsiniz-Visual Studio 2013.

 Projeye özgü MPF sınıfları aşağıdaki gibidir:

|Sınıf|Uygulama|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` sınıf, MSBuild öğeleri için bir sarmalayıcı.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Tek dosya üreteçleri ve MSBuild görevleri karşılaştırması
 Tek dosya oluşturucularından yalnızca tasarım zamanında erişilebilir, ancak MSBuild görevleri tasarım zamanında ve derleme zamanında kullanılabilir. Bu nedenle, en yüksek esneklik için, kodu dönüştürmek ve oluşturmak için MSBuild görevlerini kullanın. Daha fazla bilgi için bkz. [özel araçlar](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild başvurusu](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Özel araçlar](../../extensibility/internals/custom-tools.md)
