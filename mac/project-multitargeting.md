---
title: Çoklu hedefleme projeleri
description: bu belgede, Mac için Visual Studio içinde çok hedefli projelerin nasıl ayarlanacağı hakkında bir genel bakış sunulmaktadır.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 003c2f683b52f3def4037dd2274f3e4f3c322cd37927508b59ffb85e721065e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121438608"
---
# <a name="projects-with-multiple-target-frameworks"></a>Birden çok hedef çerçeve içeren projeler
Mac için Visual Studio, bir Xamarin veya .net Core projesini .NET Framework çeşitli sürümlerinden herhangi birinde ve çeşitli sistem platformlarından herhangi birinde çalışacak şekilde yapılandırabilirsiniz. örneğin, bir projeyi hem .NET Framework 4,6 hem de .net Core 3,1 üzerinde çalışacak şekilde hedefleyebilirsiniz. 

Hedef çerçeveler hakkında daha fazla bilgi için bkz. [hedef çerçeveler](/dotnet/standard/frameworks).

> [!NOTE] 
> bu konu Mac için Visual Studio için geçerlidir. Windows Visual Studio için bkz. [Framework hedefleme genel bakış](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Çoklu çerçeveleri hedefleme

Proje dosyanızda, projenize sağ tıklayıp **araçlar > dosya Düzenle** komutunu seçerek düzenleyebileceğiniz hedef çerçeveler belirtilir. Tek bir hedef çerçeve belirtildiğinde, TargetFramework öğesini kullanın. Aşağıdaki konsol uygulaması proje dosyası, .NET Core 3,0 ' nin nasıl hedefleyeceğinizi göstermektedir:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Birden çok hedef çerçeve ile çoğul Targetçerçeveler öğesini kullanın:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

[Çoklu çerçeveleri hedefleme](/dotnet/standard/frameworks#how-to-specify-target-frameworks)hakkında daha fazla bilgi edinin.

## <a name="working-with-code-in-a-multi-target-project"></a>Çoklu hedef projede kodla çalışma
Birden çok hedef çerçeve içeren bir projede bir C# dosyasını düzenlediğinizde, düzenleyici deneyiminize kılavuzluk etmek için kullanmak istediğiniz hedef Framework 'ü belirtebilirsiniz (örneğin, bu Framework tarafından desteklenmeyen bir API kullanıyorsanız, uyarıları gösterir). Hedef çerçevesini, düzenleyici penceresinin sol üst köşesindeki **hedef Framework** seçicisini kullanarak değiştirebilirsiniz.

![Düzenleyici penceresinin en üstünde bulunan hedef Framework 'ü değiştirmek için hedef çerçeve seçicisini kullanma](media/project-multitargeting-framework-selector.png)

Bazen uygulamanızın hedeflediği platforma bağlı olarak farklı API 'Leri çağırmanız gerekir. Bunu yapmak için, belirli bir platform için kod derlemek üzere koşullu kod yazabilirsiniz:

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

Kod yazarken, IntelliSense otomatik tamamlama önerilerinde uyarılar görürsünüz. Bu, uygulamanızın desteklediği hedef çerçevelerin hiçbirinde belirli API 'Lerin eksik olup olmadığını bilmenizi sağlar.

![IntelliSense 'de gösterilen bir uyarı iletisi, belirtilen hedef çerçeve için bir API çalışmayacak. Örnek metin: ad alanı System. buffers, SharedUtils (Netstandard 2.0)-kullanılamaz. Bağlam değiştirmek için gezinti çubuğunu kullanabilirsiniz.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve hedefleme genel bakış (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [SDK stilindeki projelerde hedef çerçeveler](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
