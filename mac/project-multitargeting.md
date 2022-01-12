---
title: Çok hedefli projeler
description: Bu belgede, birden çok hedefli projelerin Mac için Visual Studio.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 12/12/2019
ms.topic: how-to
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 15a9f85ba1421c034c8fc49825a75d0832b9bc7e
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803966"
---
# <a name="projects-with-multiple-target-frameworks"></a>Birden çok hedef çerçeveye sahip projeler
Bu Mac için Visual Studio, bir Xamarin veya .NET Core projesini .NET Framework'nin çeşitli sürümlerinden herhangi biri üzerinde ve çeşitli sistem platformlarından herhangi biri üzerinde çalıştıracak şekilde yapılandırabiliyorsunuz. Örneğin, hem .NET Framework 4.6 hem de .NET Core 3.1'de çalıştıracak bir projeyi hedefleysiniz. 

Hedef çerçeveler hakkında daha fazla bilgi için [bkz. Hedef çerçeveler.](/dotnet/standard/frameworks)

> [!NOTE] 
> Bu konu, Mac için Visual Studio. Visual Studio hakkında daha fazla Windows bkz. [Çerçeve hedeflemeye genel bakış.](/visualstudio/ide/visual-studio-multi-targeting-overview)

## <a name="targeting-multiple-frameworks"></a>Birden çok çerçeveyi hedefleme

Hedef çerçeveler proje dosyanız içinde belirtilir. Bu çerçeveleri, projenize sağ tıklar ve Araçlar'ı > **komutuyla düzenleyebilirsiniz.** Tek bir hedef çerçeve belirtilirse TargetFramework öğesini kullanın. Aşağıdaki konsol uygulaması proje dosyası .NET Core 3.0'ın nasıl hedeflen olduğunu gösteriyor:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Birden çok hedef çerçeve ile çoğul TargetFrameworks öğesini kullanın:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Birden çok çerçeveyi hedefleme [hakkında daha fazla bilgi.](/dotnet/standard/frameworks#how-to-specify-target-frameworks)

## <a name="working-with-code-in-a-multi-target-project"></a>Çok hedefli projede kodla çalışma
Birden çok hedef çerçeveye sahip bir projede bir C# dosyasını düzenlerken, düzenleyici deneyiminize kılavuz olarak kullanmak istediğiniz hedef çerçeveyi belirtebilirsiniz (örneğin, bu çerçeve tarafından desteklenmiyor bir API kullanıyorsanız uyarıları gösterme). Düzenleyici penceresinin sol üst köşesindeki **Hedef** Çerçeve seçicisini kullanarak hedef çerçeveyi değiştirebilirsiniz.

![Düzenleyici penceresinin üst kısmında bulunan hedef çerçeveyi değiştirmek için hedef çerçeve seçiciyi kullanma](media/project-multitargeting-framework-selector.png)

Bazen, uygulamanın hedeflediğimiz platforma bağlı olarak farklı API'ler çağırmanız gerekir. Bunu yapmak için, belirli bir platform için kod derlemek için koşullu kod yazabilirsiniz:

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

Kod yazarken, IntelliSense otomatik tamamlama önerilerinde, uygulamanın desteklediği hedef çerçevelerden herhangi biri için belirli API'ler eksikse bunu size haber vererek uyarılar görürsünüz.

![IntelliSense'te gösterilen bir uyarı iletisi, API belirtilen hedef çerçeve için çalışmaz. Örnek metin: namespace System.Buffers, SharedUtils (netstandard2.0) - Kullanılamıyor. Bağlam değiştirmek için gezinti çubuğunu kullanabilirsiniz.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve hedeflemeye genel bakış (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [SDK stili projelerde hedef çerçeveler](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
