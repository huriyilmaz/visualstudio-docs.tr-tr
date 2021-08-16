---
title: Üçüncü taraf Çözümleyicileri yüklensin
ms.date: 08/27/2020
description: Visual Studio ' de üçüncü taraf Çözümleyicileri yüklemeyi öğrenin. bkz. vsıx dosyaları ve NuGet çözümleyici paketlerinde çözümleyiciler nasıl yüklenir.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: fbbeffb8d0ec0ffb8d7532ca117e32afd5d24d9c77aefa3ed4f5b1407fa20aa8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420996"
---
# <a name="install-third-party-analyzers"></a>Üçüncü taraf çözümleyici yükleme

Visual Studio temel bir .NET Compiler Platform (*roslyn*) çözümleyicileri kümesi içerir. Bu çözümleyiciler her zaman açıktır. NuGet paketleri olarak veya *vsıx* dosyalarında Visual Studio uzantıları olarak ek çözümleyiciler yükleyebilirsiniz.

## <a name="to-install-nuget-analyzer-packages"></a>NuGet çözümleyicisi paketlerini yüklemek için

1. Www.nuget.org üzerine yüklemek istediğiniz çözümleyici paketini bulun.

   Örneğin, kod tabanınızdaki stil sorunlarını aramak için [StyleCop. çözümleyiciler](https://www.nuget.org/packages/stylecop.analyzers/) yüklemek isteyebilirsiniz.

2. paketi, [Paket Yöneticisi konsolunu](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) veya [Paket Yöneticisi kullanıcı arabirimini](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)kullanarak Visual Studio.

   > [!NOTE]
   > her çözümleyici paketinin www.nuget.org sayfası, **Paket Yöneticisi konsoluna** yapıştırmanın komutunu gösterir. Metni panoya kopyalamak için kullanışlı bir düğme de vardır.

   Çözümleyici derlemeleri yüklenir ve **başvuru** Çözümleyicileri altında **Çözüm Gezgini** görüntülenir  >  .

## <a name="to-install-vsix-analyzers"></a>VSıX Çözümleyicileri yüklemek için

::: moniker range="vs-2017"

1. Visual Studio ' de **araçlar** > **uzantılar ve güncelleştirmeler**' i seçin.

   **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

   > [!NOTE]
   > alternatif olarak, çözümleyici uzantısını doğrudan [Visual Studio marketi](https://marketplace.visualstudio.com)'nden bulabilir ve indirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio, **uzantıları** > **yönet uzantıları**' nı seçin.

   **Uzantıları Yönet** iletişim kutusu açılır.

   > [!NOTE]
   > alternatif olarak, çözümleyici uzantısını doğrudan [Visual Studio marketi](https://marketplace.visualstudio.com)'nden bulabilir ve indirebilirsiniz.

::: moniker-end

2. sol bölmedeki **çevrimiçi** ' i genişletin ve ardından **Visual Studio market**' i seçin.

3. Arama kutusuna, yüklemek istediğiniz çözümleyici uzantısının adını yazın.

4. **İndir**'i seçin.

   Uzantı indirilir.

5. iletişim kutusunu kapatmak için **tamam** ' ı seçin ve ardından **vsıx yükleyicisini** başlatmak için Visual Studio tüm örneklerini kapatın.

   **VSIX yükleyicisi** iletişim kutusu açılır.

   ![Microsoft Code Analysis için VSıX yükleyicisi](media/vsix-installer-code-analysis.png)

6. Yüklemeyi başlatmak için **Değiştir** ' i seçin.

7. Bir dakikadan veya ikinin ardından yükleme tamamlanır. **Kapat**’ı seçin.

8. Visual Studio tekrar açın.

::: moniker range="vs-2017"

Uzantının yüklü olup olmadığını denetlemek isterseniz, **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin. **Uzantılar ve güncelleştirmeler** iletişim kutusunda, sol taraftaki **yüklü** kategoriyi seçin ve ardından uzantıyı ada göre arayın.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantının yüklü olup olmadığını denetlemek isterseniz, **uzantıları**  >  **Yönet uzantılar**' ı seçin. **Uzantıları Yönet** iletişim kutusunda, sol taraftaki **yüklü** kategoriyi seçin ve uzantıyı ada göre arayın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Visual Studio 'de kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'de kod Çözümleyicileri 'ne genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [.NET çözümleyicilerini yükleme](../code-quality/install-net-analyzers.md)
