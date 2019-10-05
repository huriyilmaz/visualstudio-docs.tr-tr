---
title: Roslyn çözümleyicilerini yükleme
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a09c44962b2737407a3ce7274ccb9c9664908dcf
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974946"
---
# <a name="install-net-compiler-platform-code-analyzers"></a>.NET Compiler Platform kodu Çözümleyicileri yüklemesi

Visual Studio temel bir .NET Compiler Platform (*Roslyn*) Çözümleyicileri kümesi içerir. Bu çözümleyiciler her zaman açıktır. NuGet paketleri olarak ya da *VSIX* dosyalarında Visual Studio uzantıları olarak ek çözümleyiciler yükleyebilirsiniz.

## <a name="to-install-nuget-analyzer-packages"></a>NuGet çözümleyici paketlerini yüklemek için

1. Www.nuget.org üzerine yüklemek istediğiniz çözümleyici paketini bulun.

   Örneğin, kodunuzu güvenlik ve performans sorunlarıyla ilgili olarak denetlemek için [Microsoft FxCop çözümleyicileri 'ni yüklemek](install-fxcop-analyzers.md#nuget-package) isteyebilirsiniz. Veya kod tabanınızdaki stil sorunlarını aramak için [Stylecopçözümleyicileri](https://www.nuget.org/packages/stylecop.analyzers/) ' ni de yükleyemezsiniz.

2. Paketi, paket [Yöneticisi konsolunu](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) veya [Paket Yöneticisi Kullanıcı arabirimini](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)kullanarak Visual Studio 'ya yükler.

   > [!NOTE]
   > Her çözümleyici paketi için www.nuget.org sayfasında, **Paket Yöneticisi konsoluna**yapıştırmanın komutu gösterilmektedir. Metni panoya kopyalamak için kullanışlı bir düğme de vardır.

   Çözümleyici derlemeleri yüklenir ve  > **Çözümleyicileri** **başvuruları**altında **Çözüm Gezgini** görüntülenir.

## <a name="to-install-vsix-analyzers"></a>VSıX Çözümleyicileri yüklemek için

::: moniker range="vs-2017"

1. Visual Studio 'da **araçlar** > **Uzantılar ve güncelleştirmeler**' i seçin.

   **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak, çözümleyici uzantısını doğrudan [Visual Studio Market](https://marketplace.visualstudio.com)bulabilir ve indirebilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio 'da **uzantılar** > uzantıları **Yönet**' i seçin.

   **Uzantıları Yönet** iletişim kutusu açılır.

   > [!NOTE]
   > Alternatif olarak, çözümleyici uzantısını doğrudan [Visual Studio Market](https://marketplace.visualstudio.com)bulabilir ve indirebilirsiniz.

::: moniker-end

2. Sol bölmedeki **çevrimiçi** ' i genişletin ve ardından **Visual Studio Market**' yi seçin.

3. Arama kutusuna, yüklemek istediğiniz çözümleyici uzantısının adını yazın. Örneğin, kodunuzu güvenlik ve performans sorunlarıyla ilgili olarak denetlemek için [Microsoft FxCop çözümleyicileri 'ni yüklemek](install-fxcop-analyzers.md#vsix) isteyebilirsiniz.

4. **İndir**' i seçin.

   Uzantı indirilir.

5. İletişim kutusunu kapatmak için **Tamam** ' ı seçin ve ardından **VSIX yükleyicisini**başlatmak için Visual Studio 'nun tüm örneklerini kapatın.

   **VSIX yükleyicisi** iletişim kutusu açılır.

   ![Microsoft kod analizi için VSıX yükleyicisi](media/vsix-installer-code-analysis.png)

6. Yüklemeyi başlatmak için **Değiştir** ' i seçin.

7. Bir dakikadan veya ikinin ardından yükleme tamamlanır. **Kapat**' ı seçin.

8. Visual Studio 'Yu yeniden açın.

::: moniker range="vs-2017"

Uzantının yüklenip yüklenmediğini denetlemek isterseniz, **araçlar** > **Uzantılar ve güncelleştirmeler**' i seçin. **Uzantılar ve güncelleştirmeler** iletişim kutusunda, sol taraftaki **yüklü** kategoriyi seçin ve ardından uzantıyı ada göre arayın.

::: moniker-end

::: moniker range=">=vs-2019"

Uzantının yüklenip yüklenmediğini denetlemek istiyorsanız, uzantıları  > **Uzantıları Yönet** **' i seçin**. **Uzantıları Yönet** iletişim kutusunda, sol taraftaki **yüklü** kategoriyi seçin ve uzantıyı ada göre arayın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Visual Studio 'da kod Çözümleyicileri kullanma](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da kod Çözümleyicileri 'ne genel bakış](../code-quality/roslyn-analyzers-overview.md)
- [FxCop çözümleyicileri 'ni yükler](../code-quality/install-fxcop-analyzers.md)