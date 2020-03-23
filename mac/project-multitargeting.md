---
title: Çok hedefli projeler
description: Bu belge, Mac için Visual Studio'da çok hedefli projelerin nasıl kurulabildiğini anlatan bir genel bakış sağlar.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451442"
---
# <a name="projects-with-multiple-target-frameworks"></a>Birden çok hedef çerçevesi olan projeler
Mac için Visual Studio'da, bir Xamarin veya .NET Core projesini .NET Framework'ün çeşitli sürümlerinden herhangi birinde ve çeşitli sistem platformlarından herhangi birinde çalışacak şekilde yapılandırabilirsiniz. Örneğin, bir projeyi hem .NET Framework 4.6 hem de .NET Core 3.1'de çalışacak şekilde hedefleyebilirsiniz. 

Hedef çerçeveler hakkında daha fazla bilgi için [Hedef çerçevelerine](/dotnet/standard/frameworks)bakın.

> [!NOTE] 
> Bu konu Mac için Visual Studio için geçerlidir. Windows'daki Visual Studio için [Çerçeve hedefleme genel bakışına](/visualstudio/ide/visual-studio-multi-targeting-overview)bakın.

## <a name="targeting-multiple-frameworks"></a>Birden çok çerçeveyi hedefleme

Hedef çerçeveler proje dosyanızda belirtilir ve projenize sağ tıklayarak ve **Dosyayı Düzenleme komutuna > Araçları** seçerek düzenleme yapabilirsiniz. Tek bir hedef çerçevesi belirtildiğinde, TargetFramework öğesini kullanın. Aşağıdaki konsol uygulaması proje dosyası ,NET Core 3.0'ı nasıl hedeflenebildiğini gösterir:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Birden çok hedef çerçevesi olan çoğul TargetFrameworks öğesini kullanın:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

[Birden çok çerçeveyi](/dotnet/standard/frameworks#how-to-specify-target-frameworks)hedefleme hakkında daha fazla bilgi edinin.

## <a name="working-with-code-in-a-multi-target-project"></a>Çok hedefli bir projede kodla çalışma
Birden çok hedef çerçevesi olan bir projede c# dosyasını düzenlerken, düzenleyici deneyiminizi yönlendirmek için hangi hedef çerçeveyi kullanmak istediğinizi belirtebilirsiniz (örneğin, bu çerçeve tarafından desteklenmeyen bir API kullanıyorsanız uyarıları gösterebilirsiniz). Düzenleyici penceresinin sol üst köşesindeki **Hedef Çerçeve** seçiciyi kullanarak hedef çerçeveyi değiştirebilirsiniz.

![Düzenleyici penceresinin üst kısmında bulunan hedef çerçeveyi değiştirmek için hedef çerçeve seçiciyi kullanma](media/project-multitargeting-framework-selector.png)

Bazen uygulamanızın hedeflediğiniz platforma bağlı olarak farklı API'leri aramanız gerekir. Bunu yapmak için, belirli bir platform için kod derlemek için koşullu kod yazabilirsiniz:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Kod yazarken, IntelliSense otomatik tamamlama önerilerinde uyarılar görürsünüz ve uygulamanızın desteklediği hedef çerçevelerden herhangi biri için belirli API'lerin eksik olup olmadığını size bildirebilirsiniz.

![IntelliSense'de gösterilen bir uyarı iletisi, bir API belirli bir hedef çerçeve için çalışmaz. Örnek metin: namespace System.Buffers, SharedUtils (netstandard2.0) - Mevcut değil. Bağlam ı değiştirmek için gezinti çubuğunu kullanabilirsiniz.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve hedeflemegenel bakış (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [SDK tarzı projelerde hedef çerçeveler](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
