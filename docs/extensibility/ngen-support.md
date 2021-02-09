---
title: VSıX v3 'de Ngen desteği | Microsoft Docs
description: Uzantı geliştiricilerinin yönetilen uygulamaların performansını geliştirmek için kullanabileceği bir araç olan yerel görüntü oluşturucuyu nasıl etkinleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc674fbc8930415584eb5bed64f8c9cc67e0a8a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886658"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3’te Ngen desteği

Visual Studio 2017 ve yeni VSıX v3 (sürüm 3) uzantısı bildirim biçimi sayesinde, uzantı geliştiricileri artık yükleme sırasında derlemelerini "NGen" yapabilir.

Aşağıda "NGen" nin ne yaptığını açıklayan bir MSDN alıntısı verilmiştir:

>Yerel Görüntü Oluşturucu (*Ngen.exe*), yönetilen uygulamaların performansını artıran bir araçtır. *Ngen.exe* , derlenmiş işlemciye özgü makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve yerel bilgisayardaki yerel görüntü önbelleğine yüklenir. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.
>
>[Ngen.exe (yerel görüntü Oluşturucu)](/dotnet/framework/tools/ngen-exe-native-image-generator)

"NGen" bir derlemeye yönelik olarak, VSıX "makine başına örnek başına" yüklenmelidir. Bu, tasarımcıda "tüm kullanıcılar" onay kutusunu işaretleyerek etkinleştirilebilir `extension.vsixmanifest` :

![tüm kullanıcıları denetle](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen 'i etkinleştirme

Bir bütünleştirilmiş kod için Ngen 'i etkinleştirmek üzere Visual Studio 'da **Özellikler** penceresini kullanabilirsiniz.

Ayarlanabilir 4 özellik vardır:

1. **Ngen** (Boolean)-true Ise, Visual Studio yükleyicisi derlemeyi "NGen" olur.
2. **Ngen uygulaması** (dize)-Ngen, derleme bağımlılıklarını çözümlemek için bir uygulamanın *app.config* dosyasını kullanma fırsatını sağlar. Bu değer, *app.config* kullanmak istediğiniz bir uygulamaya ayarlanmalıdır (Visual Studio Install dizinine göre).
3. **Ngen mimarisi** (enum)-derlemenizi yerel olarak derlemek için mimari. Seçenekler şunlardır: a. Notbelirtti b. X86 c. X64 d. Tümü
4. **Ngen önceliği** (1 ile 3 arasında bir tamsayı)-Ngen öncelik düzeyi [Ngen.exe öncelik düzeylerinde](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)belgelenmiştir.

İşte **Özellikler** penceresi şu şekilde görünür:

![özelliklerde Ngen](media/ngen-in-properties.png)

Bu, VSıX projesinin *. csproj* dosyasının içindeki proje başvurusuna meta veriler ekler:

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
> İsterseniz. csproj dosyasını doğrudan düzenleyebilirsiniz.

## <a name="extra-information"></a>Ek bilgi

Özellik Tasarımcısı değişiklikleri yalnızca proje başvurularından daha fazlası için geçerlidir; öğeler .NET derlemeleri olduğu sürece, projenizin içindeki öğeler için Ngen meta verilerini de (yukarıda açıklanan yöntemleri kullanarak) ayarlayabilirsiniz.
