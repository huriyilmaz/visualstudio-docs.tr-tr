---
title: FxCop çözümleyicilerini yükleme
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508777"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Visual Studio'ya FxCop analizörlerini yükleyin

Microsoft, [microsoft.codeanalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)adlı bir analizçiler kümesi oluşturdu, eski analizden en önemli "FxCop" kurallarını içeren. Bu çözümleyiciler, diğerlerinin yanı sıra güvenlik, performans ve tasarım sorunları için kodunuzu denetler.

Bu FxCop analizörlerini NuGet paketi olarak veya Visual Studio'ya VSIX uzantısı olarak yükleyebilirsiniz. Her birinin artıları ve eksileri hakkında bilgi edinmek için [NuGet paketine vs. VSIX uzantısına](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)bakın.

## <a name="nuget-package"></a>NuGet paketi

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16.3 ve sonraki sürümlerinde, [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketini doğrudan projenin Kod Analizi özellikleri sayfasından yükleyebilirsiniz:

1. **Çözüm Gezgini'ndeki**proje düğümüne sağ tıklayın, **Özellikler'i**seçin ve ardından **Kod Çözümlemesi** sekmesini seçin.

   ![Visual Studio özellikleri sayfasından FxCop analizörleri paketi yükleyin](media/install-fxcop-properties-page.png)

2. **Yükle**’yi seçin.

   Visual Studio, Microsoft.CodeAnalysis.FxCopAnalyzers paketinin en son sürümünü yükler. Derlemeler **Çözüm** >  **Gezgini'nde** Başvuru**çözümleyicileri**altında görünür.

   ![Çözüm Gezgini'nde çözümleyici düğümü](media/solution-explorer-analyzers-node.png)

Visual Studio 2019'un eski bir sürümünü kullanıyorsanız, [Paketi Paket Yöneticisi Konsolu](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) veya Paket Yöneticisi [UI'yi](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)kullanarak yükleyin.

::: moniker-end

::: moniker range="vs-2017"

1. Visual Studio sürümünüze göre [hangi çözümleyici paket sürümünün](#fxcopanalyzers-package-versions) yüklenmesini belirleyin.

2. Paketi Visual Studio'ya [Paket Yöneticisi Konsolu](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) veya [Paket Yöneticisi UI'yi](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)kullanarak yükleyin.

   > [!NOTE]
   > Her çözümleyici paketinin nuget.org **sayfası, Paket Yöneticisi Konsoluna**yapıştırman için komutu gösterir. Metni panoya kopyalamak için kullanışlı bir düğme bile vardır.
   >
   > ![Paket Yöneticisi Konsol komutunu gösteren NuGet.org sayfası](media/nuget-package-manager-command.png)

   Çözümleyici derlemeleri yüklenir ve **Çözüm** > **Gezgini'nde** Başvuru **çözümleyicileri altında görünürler.**

::: moniker-end

### <a name="custom-installation"></a>Özel kurulum

Özel yükleme için, örneğin paketin farklı bir sürümünü belirtmek için, projenin Kod Analizi özellikleri sayfasındaki elips (...) düğmesini seçin. Bu düğme, arama dizesi olarak "Microsoft.CodeAnalysis.FxCopAnalyzers" ile NuGet paket yöneticisini açar.

![Visual Studio özellikleri sayfasından özel FxCop analizörleri paketi yükleyin](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Visual Studio sürümünüze göre [hangi çözümleyici paket sürümünün](#fxcopanalyzers-package-versions) yüklenmesini belirleyin. [Paketi Paket Yöneticisi UI'den](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)de yükleyebilirsiniz.

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers paket sürümleri

Visual Studio sürümünüz için FxCop çözümleyicipaketinin hangi sürümünü yükleyeceklerini belirlemek için aşağıdaki yönergeleri kullanın:

| Visual Studio sürüm | FxCop analizör paketi sürümü |
| - | - |
| Visual Studio 2019 (tüm sürümler)<br />Visual Studio 2017 sürüm 15.8 ve sonrası | [en son](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 sürüm 15.5 ile 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 sürüm 15.3 ile 15.4 arası | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 sürüm 15.0 ile 15.2 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 güncelleme 2 ve 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Güncelleştirme 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>Vsıx

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15.5 ve sonraki sürümlerinde, yönetilen projeler için tüm FxCop çözümleyicilerini içeren [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) uzantısını yükleyebilirsiniz.

1. Visual Studio'da **Araç** > **Uzantıları ve Güncelleştirmeleri'ni**seçin.

   **Uzantılar ve Güncelleştirmeler** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak, uzantısı doğrudan [Visual Studio Marketplace'ten](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)indirin.

2. Sol bölmede **Çevrimiçi'yi** genişletin ve ardından **Visual Studio Marketplace'i**seçin.

3. Arama kutusunda "kod çözümlemesi" yazın ve **Microsoft Code Analysis 2017** uzantısını arayın.

   ![Microsoft Code Analysis 2017 uzantısı](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft Code Analysis 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) uzantısı, yönetilen projeler için tüm FxCop çözümleyicilerini içerir. Bu uzantıyı yüklemek için:

1. Visual Studio'da **Uzantıları** > **Yönet Uzantıları'nı**seçin.

   **Uzantıları Yönet** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak, uzantısı doğrudan [Visual Studio Marketplace'ten](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)indirin.

2. Sol bölmede **Çevrimiçi'yi** genişletin ve ardından **Visual Studio Marketplace'i**seçin.

3. Arama kutusunda "kod çözümlemesi" yazın ve **Microsoft Code Analysis 2019** uzantısını arayın.

   ![Microsoft Code Analysis 2019 uzantısı](media/manage-extensions-code-analysis.png)

::: moniker-end

4. **Download** (İndir) seçeneğini belirleyin.

   Uzantı indirilir.

5. İletişim kutusunu kapatmak için **Tamam'ı** seçin ve **ardından VSIX Yükleyicisini**başlatmak için Visual Studio'nun tüm örneklerini kapatın.

   **VSIX Installer** iletişim kutusu açılır.

   ::: moniker range="vs-2017"

   ![Microsoft Kod Analizi için VSIX yükleyici](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Yüklemeyi başlatmak için **Değiştir'i** seçin.

   Bir veya iki dakika sonra yükleme tamamlar.

7. **Kapat'ı**seçin ve Visual Studio'yı yeniden açın.

::: moniker range="vs-2017"

Uzantın yüklü olup olmadığını denetlemek istiyorsanız, **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ni**seçin. **Uzantılar ve Güncelleştirmeler** iletişim kutusunda, soldaki **Yüklü** kategoriyi seçin ve ardından uzantıyı ada göre arayın.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantın yüklü olup olmadığını denetlemek istiyorsanız, **Uzantıları** > **Yönet Uzantıları'nı**seçin. Uzantıları **Yönet** iletişim kutusunda, soldaki **Yüklü** kategoriyi seçin ve ardından uzantıyı ada göre arayın.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da kod analizörlerinin genel görünümü](../code-quality/roslyn-analyzers-overview.md)
- [Visual Studio'da kod çözümleyicilerini kullanma](../code-quality/use-roslyn-analyzers.md)
- [Eski çözümlemeden kod çözümleyicilerine geçiş](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
