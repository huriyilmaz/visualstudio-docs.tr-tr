---
title: VSIX v3'te Ngen desteği | Microsoft Docs
description: Geliştiricilerin yönetilen uygulamaların performansını geliştirmek için kullanabileceği bir araç olan Yerel Görüntü Oluşturucu'su etkinleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0ca58451057c1cea15e0e99ff221595d525c1732
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094574"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3’te Ngen desteği

Visual Studio 2017 ve yeni VSIX v3 (sürüm 3) uzantı bildirimi biçimiyle, uzantı geliştiricileri artık yükleme zamanında derlemelerini "ngen" kullanabilir.

Msdn'den "ngen" ifadesinin ne yaptığını açıklayan bir alıntı aşağıda verilmiştir:

>Yerel Görüntü Oluşturucu (*Ngen.exe*), yönetilen uygulamaların performansını geliştiren bir araçtır. *Ngen.exe* işlemciye özgü makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve bunları yerel bilgisayarda yerel görüntü önbelleğine yüklür. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.
>
>Ngen.exe [ (Yerel Görüntü Oluşturucu)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Bir derlemeyi "ngen" olarak ifade etmek için VSIX'in "makine başına örnek başına" yüklü olması gerekir. Bu, tasarımcıda "tüm kullanıcılar" onay kutusu denetlenerek `extension.vsixmanifest` etkinleştirilebilir:

![tüm kullanıcıları denetleme](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen'i etkinleştirme

Bir derlemede ngen'i etkinleştirmek için, bir **derlemede** Özellikler penceresini Visual Studio.

Ayarlanabilirsiniz 4 özellik vardır:

1. **Ngen** (Boole) - True ise, Visual Studio yükleyici derlemeyi "ngen" olarak belirtir.
2. **Ngen uygulaması** (dize) - Ngen, derleme bağımlılıklarını çözümlemek için *bir uygulamanınapp.config* dosyası kullanma fırsatı sağlar. Bu değer, kullanmak istediğiniz *uygulamanın* app.config(yükleme dizininin Visual Studio olarak) ayarlanır.
3. **Ngen Mimarisi** (enum) - Derlemenizi yerel olarak derlemek için mimari. Seçenekler şunlardır: a. Belirtilmemiş b. X86 c. X64 d. Tümü
4. **Ngen Önceliği** (1 ile 3 arasında tamsayı) - Ngen Öncelik düzeyi, öncelik [Ngen.exe belgelenmiş.](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)

Özellikler penceresinin nasıl **ilerler?**

![özelliklerde ngen](media/ngen-in-properties.png)

Bu, VSIX projesinin *.csproj* dosyasının içinde proje başvurusuna meta veriler ekler:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Tercih ederseniz .csproj dosyasını doğrudan düzenleyebilirsiniz.

## <a name="extra-information"></a>Ek bilgiler

Özellik tasarımcısı değişiklikleri yalnızca proje başvuruları için geçerli değildir; Öğeler .NET derlemeleri olduğu sürece projenizin içindeki öğeler için de (yukarıda açıklanan yöntemlerin aynısını kullanarak) Ngen meta verilerini ayarlayın.
