---
title: Üçüncü taraf çözümleyicileri yükleme
ms.date: 08/27/2020
description: Visual Studio'da üçüncü taraf çözümleyicileri yükleme hakkında bilgi Visual Studio. Çözümleyici paketlerini .vsix dosyalarına yükleme ve NuGet bakın.
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
ms.openlocfilehash: a31fbbc8a0e655418425416ffdcae3aa16810788
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075326"
---
# <a name="install-third-party-analyzers"></a>Üçüncü taraf çözümleyici yükleme

Visual Studio çekirdek bir dizi .NET Compiler Platform (*Roslyn*) çözümleyicisi içerir. Bu çözümleyiciler her zaman açık. Ek çözümleyicileri, NuGet olarak veya *VSIX* dosyalarında Visual Studio olarak yükleyebilirsiniz.

## <a name="to-install-nuget-analyzer-packages"></a>Çözümleyici NuGet yüklemek için

1. Uygulamanın üzerine yüklemek istediğiniz çözümleyici paketini www.nuget.org.

   Örneğin, kod tabanınıza stil sorunlarını [görmek için StyleCop.Analyzers'ı](https://www.nuget.org/packages/stylecop.analyzers/) yüklemek istiyor olabilirsiniz.

2. Paket Yöneticisi Konsolu'nu veya Visual Studio kullanıcı [arabirimini kullanarak](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) paketi [Paket Yöneticisi yükleyin.](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)

   > [!NOTE]
   > Her www.nuget.org çözümleyici paketinin uygulama sayfasında, konsola yapıştırmak Paket Yöneticisi **gösterilir.** Hatta metni panoya kopyalamak için kullanışlı bir düğme bile vardır.

   Çözümleyici derlemeleri yüklenir ve BaşvuruLar **Çözümleyicileri Çözüm Gezgini** **içinde**  >  **görünür.**

## <a name="to-install-vsix-analyzers"></a>VSIX çözümleyicilerini yüklemek için

::: moniker range="vs-2017"

1. Bu Visual Studio Araçlar Uzantıları **ve** > **Güncelleştirmeler'i seçin.**

   Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak çözümleyici uzantısını doğrudan Market'te bulup [Visual Studio indirebilirsiniz.](https://marketplace.visualstudio.com)

::: moniker-end

::: moniker range=">=vs-2019"

1. Bu Visual Studio Uzantıları  > **Yönet'i seçin.**

   Uzantıları **Yönet iletişim** kutusu açılır.

   > [!NOTE]
   > Alternatif olarak çözümleyici uzantısını doğrudan Market'te bulup [Visual Studio indirebilirsiniz.](https://marketplace.visualstudio.com)

::: moniker-end

2. Sol **bölmede** Çevrimiçi'ni genişletin ve **Market'Visual Studio seçin.**

3. Arama kutusuna yüklemek istediğiniz çözümleyici uzantısının adını yazın.

4. **İndir**'i seçin.

   Uzantı indirilir.

5. **Tamam'ı** seçerek iletişim kutusunu kapatın ve ardından VSIX Yükleyicisi'Visual Studio tüm **örneklerini kapatın.**

   **VSIX Yükleyicisi** iletişim kutusu açılır.

   ![Microsoft Code Analysis için VSIX yükleyicisi](media/vsix-installer-code-analysis.png)

6. Yüklemeyi **başlatmak** için Değiştir'i seçin.

7. Bir veya iki dakika sonra yükleme tamamlanır. **Kapat**’ı seçin.

8. Yeniden Visual Studio açın.

::: moniker range="vs-2017"

Uzantının yüklü olup olmadığını kontrol etmek için Araçlar Uzantıları ve  >  **Güncelleştirmeler'i seçin.** Uzantılar **ve Güncelleştirmeler** iletişim kutusunda, sol tarafta **Yüklü** kategorisini seçin ve ardından uzantıyı adıyla arayın.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantının yüklü olup olmadığını kontrol etmek için Uzantıları **Yönet'i**  >  **seçin.** Uzantıları **Yönet iletişim** kutusunda, sol tarafta **Yüklü** kategorisini seçin ve ardından uzantıyı adıyla arayın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Kod çözümleyicilerini Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de kod çözümleyicilere genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [.NET çözümleyicilerini yükleme](../code-quality/install-net-analyzers.md)
