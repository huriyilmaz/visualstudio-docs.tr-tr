---
title: Hedeflenen .NET çerçeveleri
description: uygulamanın yalnızca belirtilen sürümde kullanılabilen işlevselliği kullanabilmesi için, projenizin hedeflemesini istediğiniz .NET Framework sürümünü belirtmeyi öğrenin.
ms.date: 12/01/2020
ms.topic: overview
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 7c61cca91c712825596b02cae6481492eecd824e
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431178"
---
# <a name="framework-targeting-overview"></a>Çerçeve hedefleme genel bakış

Visual Studio, projenizin hedeflemesini istediğiniz .net sürümünü belirtebilirsiniz. Framework hedefleme, uygulamanın yalnızca belirtilen Framework sürümünde kullanılabilen işlevselliği kullanmasını garantilemeye yardımcı olur. .NET Framework uygulamaların başka bir bilgisayarda çalışması için, uygulamanın hedeflediği çerçeve sürümü, bilgisayarda yüklü olan framework sürümüyle uyumlu olmalıdır.

bir Visual Studio çözümü, .net 'in farklı sürümlerini hedefleyen projeler içerebilir.  Bununla birlikte, tek bir yapı için başvuru koşulalları kullanarak yalnızca bir .NET sürümü için derleme yapabileceğinizi veya her sürüm için yinelemeli olarak farklı ikili dosyaları derlemeyi istediğinizi unutmayın.  Hedef çerçeveler hakkında daha fazla bilgi için bkz. [hedef çerçeveler](/dotnet/standard/frameworks).

> [!TIP]
> Farklı platformlar için de uygulama hedefleyebilirsiniz. Daha fazla bilgi için bkz. [Çoklu hedefleme](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Framework hedefleme özellikleri

Framework Hedefleme aşağıdaki özellikleri içerir:

- önceki bir framework sürümünü hedefleyen bir projeyi açtığınızda Visual Studio, projeyi otomatik olarak yükseltebilir veya hedefi olduğu gibi bırakabilir.

- bir .NET Framework projesi oluşturduğunuzda, hedeflemek istediğiniz .NET Framework sürümünü belirtebilirsiniz.

- Çoklu çerçeveleri tek bir projede [hedefleyebilirsiniz](/dotnet/standard/frameworks#how-to-specify-target-frameworks) .

- Aynı çözümdeki birçok projenin her birinde .NET 'in farklı bir sürümünü hedefleyebilirsiniz.

- Mevcut projenin hedeflediği .NET sürümünü değiştirebilirsiniz.

   projenin hedeflediği .net sürümünü değiştirdiğinizde Visual Studio, başvurularda ve yapılandırma dosyalarında gerekli değişiklikleri yapar.

daha önceki bir framework sürümünü hedefleyen bir projede çalışırken, Visual Studio geliştirme ortamını dinamik olarak aşağıdaki gibi değiştirir:

- **Yeni öğe Ekle** iletişim kutusu, **Yeni Başvuru Ekle** iletişim kutusu ve hedeflenen sürümde kullanılamayan seçimleri atlamak için **hizmet başvurusu Ekle** iletişim kutusu içindeki öğelere filtre uygular.

- **Araç kutusundaki** özel denetimleri filtreleyerek, hedeflenen sürümde mevcut olmayan olanları kaldırabilir ve birden fazla denetim kullanılabilir olduğunda yalnızca en güncel denetimleri gösterebilirsiniz.

- Hedeflenen sürümde kullanılamayan dil özelliklerini atlamak için **IntelliSense** 'e filtre uygular.

- **Özellikler** penceresindeki özellikleri, hedeflenen sürümde mevcut olmayan olanları atlamak için filtreler.

- Hedeflenen sürümde kullanılamayan seçenekleri atlamak için menü seçeneklerini filtreler.

- Derlemeler için, derleyici sürümünü ve hedeflenen sürüm için uygun olan derleyici seçeneklerini kullanır.

> [!NOTE]
> - Framework hedefleme, uygulamanızın doğru şekilde çalışacağını garanti etmez. Hedeflenen sürüme karşı çalıştığından emin olmak için uygulamanızı test etmeniz gerekir.
> - 2,0 .NET Framework aşağıdaki framework sürümlerini hedeflenemez.

## <a name="select-a-target-framework-version"></a>Hedef çerçeve sürümü seçin

bir .NET Framework projesi oluşturduğunuzda, bir proje şablonu seçtikten sonra hedef .NET Framework sürümünü seçebilirsiniz. Kullanılabilir çerçeveler listesi, seçilen şablon türü için geçerli olan yüklü çerçeve sürümlerini içerir. .NET Framework olmayan proje şablonları için, örneğin .net Core şablonları için, **çerçeve** açılan listesi görünmez.

::: moniker range="vs-2017"

![VS 2017 ' deki çerçeve açılan düzeyi](media/vside-newproject-framework.png)

::: moniker-end

::: moniker range=">=vs-2019"

![VS 2019 ' de çerçeve açılan kutusu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="change-the-target-framework"></a>Hedef çerçeveyi değiştirme

mevcut bir Visual Basic, C# veya F # projesinde, proje özellikleri iletişim kutusunda hedef .net sürümünü değiştirirsiniz. C++ projelerinin hedef sürümünü değiştirme hakkında daha fazla bilgi için, bkz. [hedef Framework ve platform araç takımını değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset) .

1. **Çözüm Gezgini**, değiştirmek istediğiniz proje için sağ tıklama menüsünü açın ve ardından **Özellikler**' i seçin.

1. **Özellikler** penceresinin sol sütununda **uygulama** sekmesini seçin.

   ![Project özellikleri uygulama sekmesi](../ide/media/vs_slnexplorer_properties_applicationtab.png)

   > [!NOTE]
   > UWP uygulaması oluşturduktan sonra, Windows veya .net 'in hedeflenen sürümünü değiştiremezsiniz.

1. **Hedef çerçeve** listesinde, istediğiniz sürümü seçin.

1. Görüntülenen doğrulama iletişim kutusunda **Evet** düğmesini seçin.

   Projenin yüklemesi kaldırılır. Yeniden yüklediğinde, yeni seçtiğiniz .NET sürümünü hedefler.

> [!NOTE]
> Kodunuz, hedeflenmeden farklı bir .NET sürümüne başvurular içeriyorsa, kodu derlerken veya çalıştırdığınızda hata iletileri görünebilir. Bu hataları gidermek için başvuruları değiştirin. Bkz. [.net hedefleme hatalarında sorun giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

> [!TIP]
> Hedef çerçeveye bağlı olarak, proje dosyasında aşağıdaki yollarla temsil edilebilir:
>
> - Bir .NET Core uygulaması için: `<TargetFramework>netcoreapp2.1</TargetFramework>`
> - .NET Standard bir uygulama için: `<TargetFramework>netstandard2.0</TargetFramework>`
> - .NET Framework bir uygulama için:`<TargetFrameworkVersion>v4.7.2</TargetFrameworkVersion>`

## <a name="resolve-system-and-user-assembly-references"></a>Sistem ve Kullanıcı derleme başvurularını çözümle

.NET sürümünü hedeflemek için, önce uygun derleme başvurularını yüklemeniz gerekir. .Net [İndirmeleri](https://www.microsoft.com/net/download/windows) sayfasına farklı .NET sürümleri için geliştirici paketleri indirebilirsiniz.

.NET Framework projeleri için, **başvuru ekle** iletişim kutusu, hedef .NET Framework sürümüne ait olmayan sistem derlemelerini devre dışı bırakarak, bir projeye istem dışı eklenememelidir. (sistem derlemeleri .NET Framework sürümde bulunan *.dll* dosyalardır.) Hedeflenen sürümden daha yüksek bir çerçeve sürümüne ait olan başvurular çözümlenmeyecektir ve bu tür bir başvuruya bağlı olan denetimler eklenemez. böyle bir başvuruyu etkinleştirmek istiyorsanız, projenin .NET Framework hedefini başvuruyu içeren bir tane olarak sıfırlayın.

Derleme başvuruları hakkında daha fazla bilgi için bkz. [tasarım zamanında derlemeleri çözümleme](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>LINQ 'ı etkinleştir

.NET Framework 3,5 veya sonraki bir sürümü hedeflediğinizde, **System. Core** 'a yönelik bir başvuru ve <xref:System.Linq> (yalnızca Visual Basic ' de) için bir proje düzeyi içeri aktarma otomatik olarak eklenir. lınq özelliklerini kullanmak istiyorsanız, `Option Infer` (yalnızca Visual Basic) öğesini de açmanız gerekir. hedefi önceki bir .NET Framework sürümü olarak değiştirirseniz başvuru ve içeri aktarma otomatik olarak kaldırılır. Daha fazla bilgi için bkz. [LINQ Ile çalışma](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef çerçeveler](/dotnet/standard/frameworks)
- [Çoklu hedefleme (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Nasıl yapılır: hedef Framework ve platform araç takımını değiştirme (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
