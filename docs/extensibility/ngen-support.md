---
title: VSIX v3'te Ngen desteği | Microsoft Dokümanlar
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702409"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3’te Ngen desteği

Visual Studio 2017 ve yeni VSIX v3 (sürüm 3) uzantı lı manifesto formatı ile uzantı geliştiricileri artık montaj sırasında montajlarını "ngen" olarak kullanabilirler.

Aşağıda "ngen" ne açıklar MSDN bir alıntıdır:

>Yerli Görüntü Jeneratör *(Ngen.exe)* yönetilen uygulamaların performansını artıran bir araçtır. *Ngen.exe,* derlenmiş işlemciye özgü makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve bunları yerel bilgisayardaki yerel görüntü önbelleğine yükler. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.
>
>[kaynak: Ngen.exe (Yerli Görüntü Jeneratörü)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Bir derlemeyi "ngen" etmek için VSIX'nin "makine başına örnek başına" yüklenmesi gerekir. `extension.vsixmanifest` Bu, tasarımcıdaki "tüm kullanıcılar" onay kutusunu işaretleyerek etkinleştirilebilir:

![tüm kullanıcıları kontrol edin](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen nasıl etkinleştirilir?

Bir derleme için ngen'i etkinleştirmek için Visual Studio'daki **Özellikler** penceresini kullanabilirsiniz.

Ayarlanabilen 4 özellik vardır:

1. **Ngen** (Boolean) - Eğer doğruysa, Visual Studio yükleyici montaj "ngen" olacaktır.
2. **Ngen uygulaması** (string) - Ngen, derleme bağımlılıklarını gidermek için bir uygulamanın *app.config* dosyasını kullanma olanağı sağlar. Bu değer, *app.config* kullanmak istediğiniz bir uygulamaya ayarlanmalıdır (Visual Studio yükleme dizinine göre).
3. **Ngen Architecture** (enum) - Derlemenizi doğal olarak derlemek için mimari. Seçenekler şunlardır: a. Belirtilmeyen b. X86 c. X64 d. Tümü
4. **Ngen Önceliği** (1 ile 3 arasında bir ara) - Ngen Priority düzeyi [Ngen.exe öncelik düzeylerinde](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)belgelenmiştir.

**Özellikler** penceresinden iş başında bir bakış aşağıda verilmiştir:

![özellikleri ngen](media/ngen-in-properties.png)

Bu, VSIX projesinin *.csproj* dosyasının içindeki proje başvurusuna meta veri ekler:

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
> İsterseniz .csproj dosyasını doğrudan edinebilirsiniz.

## <a name="extra-information"></a>Ekstra bilgi

Özellik tasarımcısı değişiklikleri proje başvurularından daha fazlası için geçerlidir; öğeler .NET derlemeleri olduğu sürece projenizin içindeki öğeler için Ngen meta verilerini de (yukarıda açıklanan yöntemlerle) ayarlayabilirsiniz.
