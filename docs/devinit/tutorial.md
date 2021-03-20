---
title: Öğretici
description: Devınit öğreticisi.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5fc53a534b592b4f6a4799100ce16b1d45049457
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671800"
---
# <a name="tutorial"></a>Öğretici

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

Bu öğreticide, devinit ve Codespaces ile [Eshoponweb deposunu](https://github.com/andysterland/eShopOnWeb) ayarlamayı inceleyeceğiz. Bu öğreticide, [Başlarken sayfasında](getting-started-with-devinit.md)açıklandığı gibi devınit 'in zaten kullanılabildiği varsayılmaktadır.

## <a name="step-1-determining-setup-steps"></a>1. Adım: kurulum adımlarını belirleme

[Başlarken sayfasında](getting-started-with-devinit.md)belirtildiği gibi, ilk adım her zaman projenizin hangi bağımlılıklar ve kurulum adımlarını belirlemektir. Bu, belirli projeye göre farklılık gösterir, ancak dikkate alınması gereken birkaç soru vardır:

- Projenizin bağlı olduğu çalışma zamanları veya SDK 'lar nelerdir?
- Projeniz için herhangi bir paket (örneğin, Chocolatey) gerekiyor mu?
- Kurulum işleminiz herhangi bir eylemin alınmasını gerektiriyor (örneğin, bir komut dosyası çalıştırılıyor)?
- Projenizin, Visual Studio ile birlikte yüklenen herhangi bir şeye örtük bağımlılıkları var mı?
  - Bu durumda, bunları devinit kurulumuna de eklemek iyi bir fikirdir. Bu şekilde, Visual Studio yüklemesine yönelik bir bağlantısı kullanmaktan kaçınabilirsiniz.

Bu bilgileri belirlemenin en iyi yöntemlerinden biri, şu anda deponuz için sahip olduğunuz el ile kurulum adımlarını araştırmaya yöneliktir. EShopOnWeb için, işlenmesi gereken birkaç nokta vardır:

- .NET Core SDK en son sürümünü yükleme
- .NET Entity Framework Core araçları CLı 'nın en son sürümünü yükleme
- SQL Server 2019 Express yükleniyor
- .NET Entity Framework CLı kullanarak yerel veritabanını en son geçişe güncelleştirme

Daha sonra, bunu devinit bağlamında nasıl gerçekleştireceğinizi inceleyeceğiz.

## <a name="step-2-the-devinitjson"></a>2. Adım: .devinit.js

İlk olarak, [ dosya üzerinde bir.devinit.js](devinit-json.md) oluşturmak ve depomızın köküne yerleştirmek istiyoruz. Bu dosya, daha sonra bir komutun parçası olarak yürütülecek bir dizi adım içerir `devinit init` . Dosyaya nelerin ekleneceğini belirlemek için `.devinit.json` , kurulum adımları listemizi alıp [devinit araçları](devinit-tool-list.md)listesiyle karşılaştırıyoruz. Şimdi, yukarıdaki kurulum adımları ile başlayalım.

| Adım                                                              | Bunu bizim için işleyebilir.                                                                        |
| :---------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------  |
| En son .NET Core SDK yüklensin                                      | **Evet**! [ `require-dotnetcoresdk` Aracı](tool-require-dotnetcoresdk.md) kullanbiliriz                  |
| .NET Entity Framework Core araçları CLı 'yı yükler                      | **Evet**! [ `dotnet-toolinstall` Aracı](tool-dotnet-toolinstall.md) kullanbiliriz                        |
| SQL Server 2019 Express 'ı yükler                                   | **Evet**! [ `choco-install` Aracı](tool-choco-install.md) kullanbiliriz                                  |
| .NET Entity Framework kullanarak yerel veritabanını güncelleştirme                 | **Hayır**, ancak devınit 'i bir komut dosyasıyla birleştirerek yine de bunu yaptık!                               |

Artık bu iletişime bir temel ile başlayalım `.devinit.json` . [ `.devinit.json` Şemaya](https://json.schemastore.org/devinit.schema-2.0)bir başvuru ve boş bir bölüm dahil edeceğiz `run` :

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": []
}
```

Şimdi bazı araçlar ekleyelim!

İlk olarak, ekleyeceğiz [`require-dotnetcoresdk`](tool-require-dotnetcoresdk.md) . Bu aracın belgelerinden en son SDK sürümünü yüklemek için varsayılan davranışın olduğunu görebiliriz. Bu, tam olarak yaptığımız bir şeydir `.devinit.json` .

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

İkinci olarak, [`dotnet-toolinstall`](tool-dotnet-toolinstall.md) `dotnet-ef` Aracı küresel olarak yüklemek için ekleyeceğiz. Belgelerde, `input` araç adını belirtmek için alanını ve `additionalOptions` Genel kapsamı belirtmek için alanı kullandığımızda görüyoruz:

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    }
  ]
}
```

Son olarak, [`choco-install`](tool-choco-install.md) paketi yüklemek için ekleyeceğiz `sql-server-express` .

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    },
    {
      "comments": "Install SQL Server 2019 Express",
      "tool": "choco-install",
      "input": "sql-server-express"
    }
  ]
}
```

Artık `.devinit.json` tamamlandığımız için, devınit 'i çalıştırmanın ve yerel veritabanını güncelleştiren bir kurulum betiği üzerinde çalışmamız gerekir.

## <a name="step-3-the-setup-script"></a>3. Adım: kurulum betiği

Çalışan devınit 'i ve yerel veritabanını güncelleştirmeyi işlemek için gerekli komutları yürüten bir komut dosyası oluşturacağız. Adlı depo kökünde boş bir PowerShell betiği oluşturalım `PostCloneSetup.ps1` . İlk olarak, öğesine bir çağrı ekleyeceğiz `devinit init` :

```powershell
devinit init
```

Yürütüldüğünde, ' `devinit init` nin bölümünde tanımlanan tüm araçları çalıştıracaktır `run` `.devinit.json` .

Son olarak, `dotnet ef database update` Yerel veritabanını güncelleştirmek için çağırmak istiyoruz:

```powershell
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

Artık kurulum komut dosyası tamamlandığına göre, `.devcontainer.json` codespace kurulumu sırasında yürütülecek bir dosya eklememiz gerekir.

## <a name="step-4-the-devcontainerjson"></a>4. Adım: .devcontainer.js

Codespace 'in oluşturulması sırasında kurulum betiğimizin çalıştırılmasından emin olmak için bir `.devcontainer.json` Dosya kullanacağız. Diğer dosyalara benzer şekilde, bu, depo köküne yerleştirilmelidir.

Dosyasında, `.devcontainer.json` yalnızca bir parçası olarak kurulum komut dosyası 'nı çağırmanız gerekiyor `postCreateCommand` . Bu, codespace oluşturma sürecinin bir parçası olarak yürütülür:

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```

Hepsi bu!

## <a name="step-5-trying-it-out"></a>5. Adım: deneyin

Artık kurulum adımlarımız olduğuna göre, [gerçek](https://github.com/andysterland/eShopOnWeb)depoyu kullanarak bunu canlı bir codespace 'e deneyelim.

İlk olarak, Visual Studio 'Yu kullanarak bir codespace oluşturacağız:

:::image type="content" source="media/eshoponweb-github-codespaces-prompt.png" alt-text="Codespace oluşturma":::

Codespace oluşturma başladıktan sonra, içindeki kurulum sürecimizin ilerlemesini izleyebiliriz `C:\.vsonline\.vsoshared\vmTerminal.dat` :

:::image type="content" source="media/eshoponweb-watching-progress.png" alt-text="Kurulum ilerlemesini izleme":::

Tamamlandıktan sonra, `Web.csproj` her şeyin doğru şekilde çalıştığından emin olmak için uygulamayı ile çalıştıralım:

:::image type="content" source="media/eshoponweb-csproj.png" alt-text="Projeyi çalıştırma":::

Uygulama oluşturulup başladıktan sonra, Web tarayıcımızda alışverişi görebiliriz:

:::image type="content" source="media/eshoponweb-live.png" alt-text="Siteyi görüntüleme":::

Bu nedenle, kurulum sürecimiz doğru şekilde çalıştık ve artık eShopOnWeb projesinde geliştirmeye hazırsınız!
