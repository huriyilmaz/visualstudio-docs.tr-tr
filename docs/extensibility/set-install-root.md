---
title: VSIX v3 ile uzantıları klasörü dışında yükleme | Microsoft Dokümanlar
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700176"
---
# <a name="install-outside-the-extensions-folder"></a>Uzantılar klasörünün dışına yükleme

Visual Studio 2017 ve VSIX v3 (sürüm 3) ile başlayarak, uzantı varlıkları uzantılar klasörünün dışına yüklenebilir. Şu anda, aşağıdaki konumlar geçerli yükleme konumları olarak etkinleştirilir ([INSTALLDIR] Visual Studio örneğinin yükleme dizinine eşlenir):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Şemalar
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Lisanslar
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (sadece Visual Studio 2017 için desteklenir; Visual Studio 2019 ve sonrası için amortismana hazırdır)

> [!NOTE]
> VSIX biçimi Visual Studio yükleme klasör yapısı dışında yüklemek için izin vermez. 

Bu dizinlere yüklemeyi desteklemek için VSIX'nin "makine başına örnek başına" yüklenmesi gerekir. Bu uzantı.vsixmanifest tasarımcı "tüm kullanıcılar" onay kutusu denetleyerek etkinleştirilebilir:

![tüm kullanıcıları kontrol edin](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>InstallRoot nasıl ayarlanır?

Yükleme dizinlerini ayarlamak için Visual Studio'daki **Özellikler** penceresini kullanabilirsiniz. Örneğin, proje başvurusu `InstallRoot` özelliğini yukarıdaki konumlardan birine ayarlayabilirsiniz:

![kök özelliklerini yükleme](media/install-root-properties.png)

Bu, VSIX projesinin `ProjectReference` .csproj dosyasının içindeki ilgili özelliğe bazı meta veriler ekler:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> İsterseniz .csproj dosyasını doğrudan edinebilirsiniz.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>InstallRoot altında bir alt yol ayarlama

Eğer altında bir alt patine yüklemek `InstallRoot`istiyorsanız, bunu `VsixSubPath` `InstallRoot` özelliği sadece özellik gibi ayarlayarak yapabilirsiniz. Örneğin, proje başvurumuzun çıktısını '[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0' olarak yüklemek istediğimizi varsayın. Biz mülkiyet tasarımcısı ile kolayca yapabilirsiniz:

![alt patina ayarlama](media/set-subpath.png)

Karşılık gelen .csproj değişiklikleri aşağıdaki gibi görünecektir:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Ekstra bilgi

Özellik tasarımcısı değişiklikleri proje başvurularından daha fazlası için geçerlidir; projenizin `InstallRoot` içindeki öğeler için meta verileri de ayarlayabilirsiniz (yukarıda açıklanan yöntemlerle).
