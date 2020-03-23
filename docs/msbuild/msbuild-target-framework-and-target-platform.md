---
title: MSBuild Hedef Çerçeve ve Hedef Platformu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3cccb9bb87d03d1fb285babe2a02cf30cfb9ed9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633206"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild hedef çerçevesi ve hedef platformu

Bir proje, .NET Framework'ün belirli bir sürümü olan *bir hedef çerçeve*ve belirli bir yazılım mimarisi olan bir hedef *platform*üzerinde çalışacak şekilde oluşturulabilir.  Örneğin, 802x86 işlemci ailesiyle ("x86") uyumlu 32 bitlik bir platformda .NET Framework 2.0 üzerinde çalışacak bir uygulamayı hedefleyebilirsiniz. Hedef çerçevesi ve hedef platformunun birleşimi *hedef bağlam*olarak bilinir.

> [!IMPORTANT]
> Bu makalede, bir hedef çerçeve belirtmek için eski yolu gösterir. SDK tarzı projeler netstandard gibi farklı TargetFrameworks sağlar. Daha fazla bilgi için [Hedef çerçevelerine](/dotnet/standard/frameworks)bakın.

## <a name="target-framework-and-profile"></a>Hedef çerçeve ve profil

 Hedef çerçeve, .NET Framework'ün projenizin üzerinde çalışmak üzere oluşturulmuş olduğu özel sürümüdür. Bir hedef çerçevenin belirtimi, derleyici özelliklerini ve çerçevenin o sürümüne özel derleme başvuruları sağladığından gereklidir.

 Şu anda .NET Framework'ün aşağıdaki sürümleri kullanılabilir:

- .NET Framework 2.0 (Visual Studio 2005'e dahil)

- .NET Framework 3.0 (Windows Vista'ya dahil)

- .NET Framework 3.5 (Visual Studio 2008'e dahil)

- .NET Çerçevesi 4.5.2

- .NET Framework 4.6 (Visual Studio 2015'e dahil)

- .NET Framework 4.6.1

- .NET Çerçevesi 4.6.2

- .NET Çerçevesi 4.7

- .NET Çerçevesi 4.7.1

- .NET Çerçevesi 4.7.2

- .NET Çerçevesi 4.8

.NET Framework'ün sürümleri, her birinin başvuruda bulunabilen derlemeler listesinde birbirinden farklıdır. Örneğin, projeniz .NET Framework sürüm 3.0 veya üzerini hedeflemedikçe Windows Presentation Foundation (WPF) uygulamalarını oluşturamazsınız.

Hedef çerçeve proje dosyasındaki `TargetFrameworkVersion` özellikte belirtilir. Visual Studio tümleşik geliştirme ortamındaki (IDE) proje özelliği sayfalarını kullanarak proje için hedef çerçeveyi değiştirebilirsiniz. Daha fazla bilgi için [bkz: .NET Framework'ün bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md). Kullanılabilir değerler `TargetFrameworkVersion` , `v2.0` `v3.0`, `v3.5` `v4.5.2` `v4.6` `v4.6.1` `v4.6.2`, , `v4.7`, `v4.7.1` `v4.7.2`, `v4.8`, , , ve .

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 *Hedef profil,* hedef çerçevenin bir alt kümesidir. Örneğin, .NET Framework 4 İstemci profili MSBuild derlemelerine yapılan başvuruları içermez.

 > [!NOTE]
 > Hedef profiller yalnızca [taşınabilir sınıf kitaplıkları](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library)için geçerlidir.

 Hedef profil, proje `TargetFrameworkProfile` dosyasındaki özellikte belirtilir. IDE'deki proje özelliği sayfalarındaki hedef çerçeve denetimini kullanarak hedef profili değiştirebilirsiniz.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Hedef platform

 *Platform,* belirli bir çalışma zamanı ortamını tanımlayan donanım ve yazılımın birleşimidir. Örneğin,

- `x86`Intel 80x86 işlemci veya eşdeğeri üzerinde çalışan 32 bit Windows işletim sistemini belirtir.

- `x64`Intel x64 işlemci veya eşdeğeri üzerinde çalışan 64 bit Windows işletim sistemini belirtir.

- `Xbox`Microsoft Xbox 360 platformlarını belirler.

*Hedef platform,* projenizin üzerinde çalışmak üzere oluşturulmuş özel bir platformdur. Hedef platform, proje `PlatformTarget` dosyasındaki yapı özelliğinde belirtilir. IDE'deki proje özelliği sayfalarını veya **Configuration Manager'ı** kullanarak hedef platformu değiştirebilirsiniz.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

*Hedef yapılandırma,* hedef platformun bir alt kümesidir. Örneğin, `x86``Debug` yapılandırma çoğu kod optimizasyonu içermez. Hedef yapılandırma, proje `Configuration` dosyasındaki yapı özelliğinde belirtilir. Proje özelliği sayfalarını veya **Configuration Manager'ı**kullanarak hedef yapılandırmayı değiştirebilirsiniz.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
<PropertyGroup>

```

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
