---
title: MSBuild kullanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704282"
---
# <a name="using-msbuild"></a>MSBuild Kullanma
MSBuild, oluşturulacak proje öğelerini tam olarak açıklayan, görev oluşturan ve yapılandırmalar oluşturan proje dosyaları oluşturmak için iyi tanımlanmış, genişletilebilir bir XML biçimi sağlar.

## <a name="general-msbuild-considerations"></a>Genel MSBuild Hususlar
 MSBuild proje dosyaları, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] örneğin, .csproj ve [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbproj dosyaları, oluşturma zamanında kullanılan verileri içerir, ancak tasarım zamanında kullanılan verileri de içerebilir. Oluşturma zamanı [verileri, Öğe Öğesi (MSBuild)](../../msbuild/item-element-msbuild.md) ve Özellik Öğesi [(MSBuild)](../../msbuild/property-element-msbuild.md)dahil olmak üzere MSBuild ilkelleri kullanılarak depolanır. Proje türüne ve ilgili proje alt türlerine özgü veriler olan tasarım zamanı verileri, bunun için ayrılmış serbest biçimli XML'de depolanır.

 MSBuild yapılandırma nesneleri için yerel destek yok, ancak yapılandırmaya özgü verileri belirtmek için koşullu öznitelikleri sağlar. Örnek:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Koşullu öznitelikleri hakkında daha fazla bilgi için [koşullu yapılara](../../msbuild/msbuild-conditional-constructs.md)bakın.

### <a name="extending-msbuild-for-your-project-type"></a>Proje Türünüz için MSBuild'i Genişletme
 MSBuild arabirimleri ve API'ler gelecekteki [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sürümlerinde değişebilir. Bu nedenle, yönetilen paket çerçevesi (MPF) sınıflarını kullanmak akıllıcadır, çünkü değişikliklere karşı koruma sağlarlar.

 Projeler için Yönetilen Paket Çerçevesi (MPFProj), yeni proje sistemi oluşturmak ve yönetmek için yardımcı sınıflar sağlar. Projeler için MPF - Visual [Studio 2013'te](https://github.com/tunnelvisionlabs/MPFProj10)kaynak kodu ve derleme yönergelerini bulabilirsiniz.

 Projeye özel MPF sınıfları aşağıdaki gibidir:

|Sınıf|Uygulama|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`sınıf MSBuild öğeleri için bir sarmalayıcıdır.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Tek Dosya Jeneratörleri vs MSBuild Görevleri
 Tek dosya jeneratörlerine yalnızca tasarım zamanında erişilebilir, ancak MSBuild görevleri tasarım zamanında ve oluşturma zamanında kullanılabilir. Bu nedenle, maksimum esneklik için kodu dönüştürmek ve oluşturmak için MSBuild görevlerini kullanın. Daha fazla bilgi için [Bkz. Özel Araçlar.](../../extensibility/internals/custom-tools.md)

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild Başvurusu](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [Özel Araçlar](../../extensibility/internals/custom-tools.md)
