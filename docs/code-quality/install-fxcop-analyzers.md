---
title: FxCop çözümleyicilerini yükleme
ms.date: 08/03/2018
description: Visual Studio 'da FxCop çözümleyicileri yüklemeyi öğrenin. Bu Çözümleyicileri, bir NuGet paketi veya VSıX uzantısı olarak nasıl yükleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e9950941680f9e251fe9c589a1df1d0314f149a7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435527"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Visual Studio 'da FxCop çözümleyicileri 'ni yükler

Microsoft, eski analizde en önemli "FxCop" kurallarını içeren [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)adlı bir çözümleyiciler kümesi oluşturdu. Bu çözümleyiciler, kodunuzu güvenlik, performans ve tasarım sorunlarıyla ilgili diğer kullanıcılar arasında denetler.

Bu FxCop çözümleyicileri 'ni, Visual Studio 'ya bir NuGet paketi veya VSıX uzantısı olarak yükleyebilirsiniz. Her birinin olumlu ve olumsuz yönleri hakkında bilgi edinmek için bkz. [NuGet Package vs. VSIX uzantısı](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension).

## <a name="nuget-package"></a>NuGet paketi

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16,3 ve sonraki sürümlerde, [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketini doğrudan projenin kod analizi özellikleri sayfasından yükleyebilirsiniz:

1. **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın, **Özellikler** ' i seçin ve ardından **Kod Analizi** sekmesini seçin.

   ![Visual Studio 'da Özellikler sayfasından FxCop çözümleyicileri paketini yükler](media/install-fxcop-properties-page.png)

2. **Yükle** ’yi seçin.

   Visual Studio, Microsoft. CodeAnalysis. Fxcopçözümleyiciler paketinin en son sürümünü yüklüyor. Derlemeler, **başvuru** Çözümleyicileri altında **Çözüm Gezgini** görüntülenir  >  **Analyzers**.

   ![Çözüm Gezgini içinde düğüm Çözümleyicileri](media/solution-explorer-analyzers-node.png)

Visual Studio 2019 ' nin eski bir sürümünü kullanıyorsanız, paketi [Paket Yöneticisi konsolunu](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) veya [Paket Yöneticisi Kullanıcı arabirimini](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)kullanarak yükleyebilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

1. Visual Studio sürümünüze bağlı olarak [hangi çözümleyici paketi sürümünün yükleneceğini saptayın](#fxcopanalyzers-package-versions) .

2. Paketi, paket [Yöneticisi konsolunu](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) veya [Paket Yöneticisi Kullanıcı arabirimini](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)kullanarak Visual Studio 'ya yükler.

   > [!NOTE]
   > Her çözümleyici paketi için nuget.org sayfasında, **Paket Yöneticisi konsoluna** yapıştırmanın komutu gösterilmektedir. Metni panoya kopyalamak için kullanışlı bir düğme de vardır.
   >
   > ![Paket Yöneticisi konsolu komutunu gösteren NuGet.org sayfası](media/nuget-package-manager-command.png)

   Çözümleyici derlemeleri yüklenir ve **başvuru** Çözümleyicileri altında **Çözüm Gezgini** görüntülenir > **Analyzers**.

::: moniker-end

### <a name="custom-installation"></a>Özel yükleme

Örneğin, paketin farklı bir sürümünü belirtmek için özel yüklemede, projenin kod analizi özellikleri sayfasında üç nokta (...) düğmesini seçin. Bu düğme, arama dizesi olarak "Microsoft. CodeAnalysis. Fxcopçözümleyiciler" ile NuGet Paket Yöneticisi 'ni açar.

![Visual Studio 'daki Özellikler sayfasından özel FxCop çözümleyicileri paketini yükler](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Visual Studio sürümünüze bağlı olarak [hangi çözümleyici paketi sürümünün](#fxcopanalyzers-package-versions) yükleneceğini saptayın. Paketi, [Paket Yöneticisi kullanıcı arabiriminden](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)da yükleyebilirsiniz.

### <a name="fxcopanalyzers-package-versions"></a>Fxcopçözümleyiciler paket sürümlerini

Visual Studio sürümünüz için FxCop çözümleyicileri paketinin hangi sürümünün yükleneceğini öğrenmek için aşağıdaki yönergeleri kullanın:

| Visual Studio sürüm | FxCop Çözümleyicisi paket sürümü |
| - | - |
| Visual Studio 2019 (tüm sürümler) | [en son](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 sürüm 15,9 | [2.9.10](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.9.10) |
| Visual Studio 2017 sürüm 15,5-15,8 | [2.6.4](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.4) |
| Visual Studio 2017 sürüm 15,3-15,4 | [2.3.0-Beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 sürüm 15,0-15,2 | [2.0.0-Beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 güncelleştirme 2 ve 3 | [1.2.0-Beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 Güncelleştirme 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSıX

::: moniker range="vs-2017"

Visual Studio 2017 sürüm 15,5 ve sonraki sürümlerde, yönetilen projeler için tüm FxCop çözümleyicileri içeren [Microsoft Code Analysis 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) uzantısını yükleyebilirsiniz.

1. Visual Studio 'da **Araçlar** > **Uzantılar ve güncelleştirmeler** ' i seçin.

   **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak, uzantıyı doğrudan [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)indirin.

2. Sol bölmedeki **çevrimiçi** ' i genişletin ve ardından **Visual Studio Market** ' yi seçin.

3. Arama kutusuna "kod analizi" yazın ve **Microsoft kod analizi 2017** uzantısını arayın.

   ![Microsoft Kod Analizi 2017 uzantısı](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft kod analizi 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) uzantısı, yönetilen projeler Için tüm FxCop çözümleyicileri içerir. Bu uzantıyı yüklemek için:

1. Visual Studio 'da **Uzantılar** > **Yönet uzantılar** ' ı seçin.

   **Uzantıları Yönet** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak, uzantıyı doğrudan [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)indirin.

2. Sol bölmedeki **çevrimiçi** ' i genişletin ve ardından **Visual Studio Market** ' yi seçin.

3. Arama kutusuna "kod analizi" yazın ve **Microsoft kod analizi 2019** uzantısını arayın.

   ![Microsoft Kod Analizi 2019 uzantısı](media/manage-extensions-code-analysis.png)

::: moniker-end

4. **İndir** 'i seçin.

   Uzantı indirilir.

5. İletişim kutusunu kapatmak için **Tamam** ' ı seçin ve ardından **VSIX yükleyicisini** başlatmak için Visual Studio 'nun tüm örneklerini kapatın.

   **VSIX yükleyicisi** iletişim kutusu açılır.

   ::: moniker range="vs-2017"

   ![Microsoft kod analizi için VSıX yükleyicisi](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. Yüklemeyi başlatmak için **Değiştir** ' i seçin.

   Bir dakikadan veya ikinin ardından yükleme tamamlanır.

7. **Kapat** ' ı seçin ve ardından Visual Studio 'yu yeniden açın.

::: moniker range="vs-2017"

Uzantının yüklü olup olmadığını denetlemek isterseniz, **Araçlar**  >  **Uzantılar ve güncelleştirmeler** ' i seçin. **Uzantılar ve güncelleştirmeler** iletişim kutusunda, sol taraftaki **yüklü** kategoriyi seçin ve ardından uzantıyı ada göre arayın.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantının yüklü olup olmadığını denetlemek isterseniz, **uzantıları**  >  **Yönet uzantılar** ' ı seçin. **Uzantıları Yönet** iletişim kutusunda, sol taraftaki **yüklü** kategoriyi seçin ve uzantıyı ada göre arayın.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod Çözümleyicileri 'ne genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [Visual Studio 'da kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)
- [Eski çözümleyicinden kod Çözümleyicileri 'ne geçiş](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
