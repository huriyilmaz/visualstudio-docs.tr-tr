---
title: VSIX v3 ile uzantılar klasörünü dışarıdan yükleme | Microsoft Docs
description: uzantılar klasörünün dışında Visual Studio SDK uzantısı varlıklarını yükleme ve hangi konumların geçerli olduğu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f09b6d8a586a03aea8401a9125d6d1c43b77c845
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158261"
---
# <a name="install-outside-the-extensions-folder"></a>Uzantılar klasörünün dışına yükleme

Visual Studio 2017 ve vsıx v3 (sürüm 3) ile başlayarak, uzantı varlıkları uzantılar klasörünün dışında yüklenebilir. şu anda, şu konumlar geçerli yükleme konumları olarak etkindir (burada [ınstalldir] Visual Studio örneğinin yükleme diziniyle eşlenir):

* [INSTALLDIR] \ MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Lisanslar
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [ınstalldir] \Common7\IDE\VC\VCTargets (yalnızca Visual Studio 2017 için desteklenir; Visual Studio 2019 ve üzeri için kullanım dışıdır)

> [!NOTE]
> vsıx biçimi, Visual Studio install klasörü yapısını dışarıdan yüklemenize izin vermez. 

Bu dizinlere yüklemeyi desteklemek için VSıX, "makine başına örnek başına" yüklenmelidir. Bu, uzantısı. valtmanifest tasarımcısında "tüm kullanıcılar" onay kutusu seçilerek etkinleştirilebilir:

![tüm kullanıcıları denetle](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>InstallRoot nasıl ayarlanır

Yükleme dizinlerini ayarlamak için Visual Studio **Özellikler** penceresini kullanabilirsiniz. Örneğin, `InstallRoot` bir proje başvurusunun özelliğini yukarıdaki konumlardan birine ayarlayabilirsiniz:

![kök özelliklerini yükler](media/install-root-properties.png)

Bu, `ProjectReference` VSIX projesinin. csproj dosyasının içindeki karşılık gelen özelliğe bazı meta verileri ekler:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> İsterseniz. csproj dosyasını doğrudan düzenleyebilirsiniz.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>InstallRoot altında bir alt yol ayarlama

Öğesinin altındaki bir alt yolu yüklemek isterseniz `InstallRoot` , özelliği özelliği gibi ayarlayarak bunu yapabilirsiniz `VsixSubPath` `InstallRoot` . örneğin, proje başvurusunun çıktısının ' [ınstalldir] \ MSBuild \MyCompany\MySDK\1.0 ' öğesine yüklenmesini istiyoruz. Bunu özellik Tasarımcısı ile kolayca yapabiliriz:

![alt yolu ayarla](media/set-subpath.png)

Karşılık gelen. csproj değişiklikleri şöyle görünür:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Ek bilgi

Özellik Tasarımcısı değişiklikleri yalnızca proje başvurularından daha fazlası için geçerlidir; `InstallRoot` projenizin içindeki öğeler için meta verileri de (yukarıda açıklanan yöntemleri kullanarak) ayarlayabilirsiniz.
