---
title: MSBuild hedef çerçevesi ve hedef platform | Microsoft Docs
description: Hedef .NET Framework sürümünde ve hedef platformda veya yazılım mimarisinde çalıştırmak için MSBuild projesi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 958f33a39126f8f48cf29bad1c25c7d962513ed0
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533868"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild hedef çerçevesi ve hedef platformu

Bir proje, .NET Framework belirli bir sürümü ve belirli bir yazılım mimarisi olan bir *hedef platform* olan bir *hedef çerçeve* üzerinde çalışmak üzere oluşturulabilir.  Örneğin, 80x86 işlemci ailesi ("x86") ile uyumlu bir 32 bit platformda .NET Framework 2,0 ' de çalışacak bir uygulamayı hedefleyebilirsiniz. Hedef Framework ve hedef platformun birleşimi *hedef bağlam* olarak bilinir.

> [!IMPORTANT]
> Bu makalede, hedef çerçeve belirtmenin eski yolu gösterilmektedir. SDK stilindeki projeler Netstandard gibi farklı Targetçerçeveleri etkinleştirir. Daha fazla bilgi için bkz. [hedef çerçeveler](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Hedef çerçeve ve profil

 Hedef çerçeve, projenizin üzerinde çalışmak üzere oluşturulduğu .NET Framework belirli sürümüdür. Bir hedef Framework belirtimi, bu Framework sürümü için özel derleyici özellikleri ve derleme başvuruları sağladığından gereklidir.

 Şu anda .NET Framework aşağıdaki sürümleri kullanılabilir:

- .NET Framework 2,0 (Visual Studio 2005 ' de bulunur)

- .NET Framework 3,0 (Windows Vista 'da bulunur)

- .NET Framework 3,5 (Visual Studio 2008 ' de bulunur)

- .NET Framework 4.5.2

- .NET Framework 4,6 (Visual Studio 2015 ' de bulunur)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4,7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4,8

.NET Framework sürümleri, her birinin başvuru için kullanılabilir hale getiren derlemeler listesinde diğerinden farklıdır. Örneğin, projeniz .NET Framework sürüm 3,0 veya üzerini hedeflediğinden, Windows Presentation Foundation (WPF) uygulamaları derlenemez.

Hedef çerçeve, `TargetFrameworkVersion` Proje dosyasındaki özelliğinde belirtilmiştir. Visual Studio tümleşik geliştirme ortamındaki (IDE) proje özelliği sayfalarını kullanarak bir projenin hedef çerçevesini değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md). İçin kullanılabilir değerler,,,,,,, `TargetFrameworkVersion` `v2.0` `v3.0` `v3.5` `v4.5.2` `v4.6` `v4.6.1` `v4.6.2` `v4.7` , `v4.7.1` , `v4.7.2` , ve `v4.8` .

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 *Hedef profil* , hedef Framework 'ün bir alt kümesidir. Örneğin, .NET Framework 4 Istemci profili MSBuild derlemelerine başvuruları içermez.

 > [!NOTE]
 > Hedef profiller yalnızca [taşınabilir sınıf kitaplıkları](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library)için geçerlidir.

 Hedef profil, `TargetFrameworkProfile` bir proje dosyasındaki özelliğinde belirtilmiştir. IDE 'deki proje özelliği sayfalarında Target-Framework denetimini kullanarak hedef profilini değiştirebilirsiniz.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Hedef platform

 *Platform* , belirli bir çalışma zamanı ortamını tanımlayan donanım ve yazılım birleşimidir. Örneğin,

- `x86` Intel 80x86 işlemcisi üzerinde veya eşdeğeri olan 32 bitlik bir Windows işletim sistemi belirler.

- `x64` Intel x64 işlemcisinde veya eşdeğer bir bilgisayarda çalışan 64 bitlik bir Windows işletim sistemi belirler.

- `Xbox` Microsoft Xbox 360 platformunu belirtir.

*Hedef platform* , projenizin üzerinde çalışmak üzere oluşturulduğu özel platformdur. Hedef platform `PlatformTarget` bir proje dosyasındaki Build özelliğinde belirtilmiştir. Hedef platformu, proje özelliği sayfalarını veya IDE 'deki **Configuration Manager** kullanarak değiştirebilirsiniz.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

*Hedef yapılandırma* , hedef platformun bir alt kümesidir. Örneğin, `x86` `Debug` yapılandırma çoğu kod iyileştirmesini içermez. Hedef yapılandırma `Configuration` bir proje dosyasındaki Build özelliğinde belirtilir. Proje özellik sayfaları veya **Configuration Manager** kullanarak hedef yapılandırmayı değiştirebilirsiniz.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
</PropertyGroup>

```

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
