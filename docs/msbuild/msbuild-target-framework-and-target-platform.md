---
title: MSBuild hedef çerçevesi ve hedef platform | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32960d46b4c7ae9b37cfec6cff97eb0540b868a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596781"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild hedef çerçevesi ve hedef platform
Bir proje, .NET Framework belirli bir sürümü ve belirli bir yazılım mimarisi olan bir *hedef platform*olan bir *hedef çerçeve*üzerinde çalışmak üzere oluşturulabilir.  Örneğin, 2,0 bitlik bir platformda .NET Framework ' de çalışacak bir uygulamayı, 802x86 işlemci ailesi ("x86") ile uyumlu 32 bir şekilde hedefleyebilirsiniz. Hedef Framework ve hedef platformun birleşimi *hedef bağlam*olarak bilinir.

> [!IMPORTANT]
> Bu makalede, hedef çerçeve belirtmenin eski yolu gösterilmektedir. SDK stilindeki projeler Netstandard gibi farklı Targetçerçeveleri etkinleştirir. Daha fazla bilgi için bkz. [hedef çerçeveler](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Hedef çerçeve ve profil
 Hedef çerçeve, projenizin üzerinde çalışmak üzere oluşturulduğu .NET Framework belirli sürümüdür. Bir hedef Framework belirtimi, bu Framework sürümü için özel derleyici özellikleri ve derleme başvuruları sağladığından gereklidir.

 Şu anda .NET Framework aşağıdaki sürümleri kullanılabilir:

- .NET Framework 2,0 (Visual Studio 2005 ' de bulunur)

- .NET Framework 3,0 ([!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]dahil)

- .NET Framework 3,5 ([!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]dahil)

- .NET Framework 4.5.2

- .NET Framework 4,6 ([!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)]dahil)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4,7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4,8

.NET Framework sürümleri, her birinin başvuru için kullanılabilir hale getiren derlemeler listesinde diğerinden farklıdır. Örneğin, projeniz .NET Framework sürüm 3,0 veya üzerini hedeflediğinden, Windows Presentation Foundation (WPF) uygulamaları derlenemez.

Hedef Framework, proje dosyasında `TargetFrameworkVersion` özelliğinde belirtilmiştir. Visual Studio tümleşik geliştirme ortamındaki (IDE) proje özelliği sayfalarını kullanarak bir projenin hedef çerçevesini değiştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/visual-studio-multi-targeting-overview.md). `TargetFrameworkVersion` için kullanılabilir değerler `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, `v4.7.1`, `v4.7.2`ve `v4.8`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 *Hedef profil* , hedef Framework 'ün bir alt kümesidir. Örneğin, .NET Framework 4 Istemci profili MSBuild derlemelerine başvuruları içermez.

 > [!NOTE]
 > Hedef profiller yalnızca [taşınabilir sınıf kitaplıkları](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library)için geçerlidir.

 Hedef profil bir proje dosyasında `TargetFrameworkProfile` özelliğinde belirtilmiştir. IDE 'deki proje özelliği sayfalarında Target-Framework denetimini kullanarak hedef profilini değiştirebilirsiniz.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Hedef platform
 *Platform* , belirli bir çalışma zamanı ortamını tanımlayan donanım ve yazılım birleşimidir. Örneğin,

- `x86`, Intel 80x86 işlemcisi üzerinde çalışan 32 bitlik bir Windows işletim sistemini veya eşdeğerini belirler.

- `x64`, Intel x64 işlemci veya BT eşdeğeri üzerinde çalışan 64 bitlik bir Windows işletim sistemi belirler.

- `Xbox` Microsoft Xbox 360 platformunu belirtir.

*Hedef platform* , projenizin üzerinde çalışmak üzere oluşturulduğu özel platformdur. Hedef platform bir proje dosyasında `PlatformTarget` Build özelliğinde belirtilmiştir. Hedef platformu, proje özelliği sayfalarını veya IDE 'deki **Configuration Manager** kullanarak değiştirebilirsiniz.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

*Hedef yapılandırma* , hedef platformun bir alt kümesidir. Örneğin, `x86``Debug` yapılandırması çoğu kod iyileştirmesini içermez. Hedef yapılandırma bir proje dosyasında `Configuration` Build özelliğinde belirtilmiştir. Proje özellik sayfaları veya **Configuration Manager**kullanarak hedef yapılandırmayı değiştirebilirsiniz.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
<PropertyGroup>

```

## <a name="see-also"></a>Ayrıca bkz.
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
